---
title: '减少 Docker 日志大小'
date: '2025-03-26T01:26:49+08:00'
draft: false
tags: ['Docker']
keywords: ['Docker']
author: "Yuki"
---

> 翻译原文：https://linuxiac.com/reducing-docker-logs-file-size/

## **前言**
Docker 是一个十分优秀的工具，能帮助我们快速设置和执行所需的程序，但是我们经常忽略其运行中所产生的日志。

然而最近，我发现我的服务器磁盘空间几乎快满了，通过调查发现 Docker 容器一年内产生了将近 14GB log 文件。

本文将帮助你学习如何快速检查 Docker 日志，减少它们，并且通过设置以防止在未来变得越来越大。

Docker 容器是无状态的，这意味着它们的日志会在容器重新创建的时候被删除。但很多人忽略了一个很关键的细节：**【重启和重建】** Docker 容器。

因此，在继续讨论前，我们先来明确这个重要的问题。

## **重启 vs 重建 Docker 容器**
让我们回到上面的案例，在过去一年里，服务被多次重启，意味着 Docker 容器经历了多次停止和启动。但是，他们的日志文件一直保留着并持续增长。

这种情况发生的原因是我们在讨论重启而不是重建 Docker 容器。当服务重启时，Docker 守护进程会优雅地停止正在运行的容器，然后自动启动它。

相同的，当使用 "systemctl restart docker" 命令重启 Docker 服务的时候，也是同样的行为。

十分重要的概念是：Docker 日志只有在 Docker 容器被删除和被重建的时候才会被重置。简单地停止和重启 Docker 容器不会导致日志重置。

了解了这一点，接着就可以学习如何检查 Docker 容器使用了多少系统空间。

## 检查 Docker 日志大小
Docker 日志通常被保留在本机的以下地址（如果没有被特别指定的话）：

`/var/lib/docker/containers/<container-id>/<container-id>-json.log`

每个 Docker 容器在 `/var/lib/docker/containers/` 都有自己的目录，在每个容器的目录内，你都能找到 "-json.log" 的容器日志文件。

这些文件默认以 JSON 格式结构化，并捕获容器的标准输出（stdout）和标准错误（stderr）流。

想查看所有 Docker 容器的日志大小并按从大到小排列，你可以使用下面的命令：

`find /var/lib/docker/containers/ -name "*json.log" | xargs du -h | sort -hr`

![docker-logs](/images/Reducing-Docker-Logs-Size/docker-logs.png)

现在，我们可以看到所有的 Docker 容器日志，但是我们怎么匹配上这些 ID 和具体的容器呢？

## **通过 ID 找到具体 Docker 容器名**
现在我们找到了日志较大的那个文件，ID 就是 `/var/lib/docker/containers/<container-id>`
如下，使用 "13d26f5771352d299b64804d706b75d549c84afbe8b99927e806bfffbc5e579e"

![docker-logs-id](/images/Reducing-Docker-Logs-Size/docker-logs-id.png)

命令如下：

`docker inspect --format='{{.Name}}' <container_id>`

所以我们可以使用命令：

`docker inspect --format='{{.Name}}' 13d26f5771352d299b64804d706b75d549c84afbe8b99927e806bfffbc5e579e`

我们就可以获取到 Docker 容器名了
![docker-id-container](/images/Reducing-Docker-Logs-Size/docker-id-container.png)

我们已经通过容器 ID 确认了容器名，如果想二次通过容器名来确认容器所对应的日志文件也可以通过 `docker inspect <container_name>` 来输出其日志路径。

![docker-inspect-logpath](/images/Reducing-Docker-Logs-Size/docker-inspect-logpath.png)

或者也可以通过下面的命令获取到 LogPath：

`docker inspect --format='{{.LogPath}}' <container_name>`

![docker-inspect-logpath-2](/images/Reducing-Docker-Logs-Size/docker-inspect-logpath-2.png)

现在我们已经可以找到我们需要的数据了，接着可以开始清理数据释放磁盘空间了。

## **清理 Docker 容器日志**
我们可以通过`truncate`命令来清理单个日志内的所有文件，只需要提供日志文件的完整路径，比如：

`truncate -s 0 /var/lib/docker/containers/13d26f5771352d299b64804d706b75d549c84afbe8b99927e806bfffbc5e579e/13d26f5771352d299b64804d706b75d549c84afbe8b99927e806bfffbc5e579e-json.log`

![docker-truncate-logs](/images/Reducing-Docker-Logs-Size/docker-truncate-logs.png)

如果你想更激进一些，**清楚所有日志**，可以使用下面的命令（确保你清醒的状态下执行）：

`truncate -s 0 /var/lib/docker/containers/*/*-json.log`

## **设置 Docker 日志大小限制**
上述方法提供了一个临时解决和 Docker 大日志的方式，但是，经常定期执行命令非常麻烦。

一个更好、更彻底的解决方式是直接限制 Docker 日志文件大小。当日志文件达到限制后，Docker 守护进程会自动轮转这些日志文件，然后按照命名规范存档，比如 `<container_id>-json.log.1`，`<container_id>-json.log.2`。

这可以确保日志文件不会不受控制的增长。我们可以通过修改 Docker daemon 配置来使日志自动轮转，具体配置在下面的文件，如果没有的话就创建它：

`vim /etc/docker/daemon.json`

然后，复制以下内容到文件内保存：

```
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}
```

简单说就是设置日志的类型为 "json-file"，json 格式的文件，每个文件最大 10m，最多保留 3个文件。

以下是我开发机的配置：

![docker-daemon-conf](/images/Reducing-Docker-Logs-Size/docker-daemon-conf.png)

修改完成需要重启下 Docker 服务：

`systemctl restart docker`

需要注意的是，**上面的变动只会影响到新创建的 Docker 容器，如果是已经存在的则不会受影响**，如果想旧的容器也生效，可以删除（`docker rm -r <container_id_or_name>`），然后重新启动。

如果使用的是 Docker Compose，只需要到 "docker-compose.yaml" 同级目录执行：

`docker compose down`

等停止完后再启动就可以了：

`docker compose up -d`

修改完成后，使用 inspect 就可以看到容器关于日志的配置：

`docker inspect <container_id_or_name> | grep LogConfig -A8`

![docker-container-log-conf](/images/Reducing-Docker-Logs-Size/docker-container-log-conf.png)

## **结论**
管理 Docker 日志大小有助于维护高效和可持续的服务器环境，本文提供了一种管理 Docker 日志大小的策略，并确保使用 Docker 日志的轮转和清理功能，避免日志无序累计。

可以参阅[官方文档](https://docs.docker.com/engine/daemon/)，获取更多有关 "daemon.json" 配置文件的详细信息。

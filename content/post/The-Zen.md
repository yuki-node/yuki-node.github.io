---
title: '计算机之禅'
date: '2026-01-02T18:43:17+08:00'
draft: false
tags: []
keywords: []
author: "Yuki"
---

> 本文收集一些与计算机相关的禅意。

## 前言

无意间发现了一篇博客：[What to read before starting (or interviewing) at GitHub](https://ben.balter.com/2021/02/01/what-to-read-before-starting-or-interviewing-at-github/)，这篇博客收集了一些在 GitHub 工作或者面试 Github 之前需要阅读的文章，很多公司内部应该都有类似这样的文章。

作者是 Github 的 Hubber 赋能部门总监，这个职位应该是规划 Github 内部员工体系、文化建设相关部门的负责人。Hubber 是 Github 对员工的独特称呼，强调员工都是这个『中心（Hub）』的一份子。

这个作者的博客真的像宝藏一样，里面的内容都非常有价值。可以学习到很多组织文化、沟通、效率等方面的知识。

当我看到 The Zen of Github 的时候，突发奇想，也收集了一些计算机相关的一些禅意。

这些禅意或者哲学，不仅仅指导着语言的使用和设计，同时也是社区文化、价值观的一种体现。

## Github 之禅

来源：[The Zen of Github](https://ben.balter.com/2015/08/12/the-zen-of-github/)，作者是 Github 早期员工，思考如何培养一个组织的品味（Taste），于是受 Python 之禅的影响，写出了 Github 之禅。

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Responsive is better than fast. | 响应性优于单纯的速度快。 |
> | It’s not fully shipped until it’s fast. | 性能达标才算真正发布。 |
> | Practicality beats purity. | 实用胜过纯粹。 |
> | Approachable is better than simple. | 易于上手胜过简单直接。 |
> | Mind your words, they are important. | 注意你的言辞，它们很重要。 |
> | Speak like a human. | 像普通人一样说话。 |
> | Half measures are as bad as nothing at all. | 半途而废和什么都不做一样糟糕。 |
> | Encourage flow. | 鼓励流动。 |
> | Non-blocking is better than blocking. | 非阻塞优于阻塞。 |
> | Favor focus over features. | 专注核心胜过堆砌功能。 |
> | Avoid administrative distraction. | 避免行政性干扰。 |
> | Design for failure. | 为失败而设计。 |
> | Keep it logically awesome. | 保持逻辑上的优雅。 |

有个彩蛋是请求 Github API 的章鱼猫路径时，会随机返回其中一句：[https://api.github.com/octocat](https://api.github.com/octocat)

```Bash

               MMM.           .MMM
               MMMMMMMMMMMMMMMMMMM
               MMMMMMMMMMMMMMMMMMM      _____________________________________________
              MMMMMMMMMMMMMMMMMMMMM    |                                             |
             MMMMMMMMMMMMMMMMMMMMMMM   | Half measures are as bad as nothing at all. |
            MMMMMMMMMMMMMMMMMMMMMMMM   |_   _________________________________________|
            MMMM::- -:::::::- -::MMMM    |/
             MM~:~ 00~:::::~ 00~:~MM
        .. MMMMM::.00:::+:::.00::MMMMM ..
              .MM::::: ._. :::::MM.
                 MMMM;:::::;MMMM
          -MM        MMMMMMM
          ^  M+     MMMMMMMMM
              MMMMMMM MM MM MM
                   MM MM MM MM
                   MM MM MM MM
                .~~MM~MM~MM~MM~~.
             ~~~~MM:~MM~~~MM~:MM~~~~
            ~~~~~~==~==~~~==~==~~~~~~
             ~~~~~~==~==~==~==~~~~~~
                 :~==~==~==~==~~
```

## Go 之禅

来源：[The Zen of Go](https://dave.cheney.net/2020/02/23/the-zen-of-go)，作者是 Go pkg 核心贡献者，几乎每届 GopherCon 都有极高质量的演讲。Go 之禅来源于 2020年在以色列的一次分享，完整视频：[https://www.youtube.com/watch?v=yd_rtwYaXps](https://www.youtube.com/watch?v=yd_rtwYaXps)。

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Each package fulfils a single purpose. | 每个包只做一件事。 |
> | Handle errors explicitly. | 显式处理错误。 |
> | Return early rather than nesting deeply. | 尽早返回，避免深层嵌套。 |
> | Leave concurrency to the caller. | 把并发留给调用方。 |
> | Before you launch a goroutine, know when it will stop. | 在启动 goroutine 之前，要知道它何时会停止。 |
> | Avoid package level state. | 避免使用包级状态。 |
> | Simplicity matters. | 简洁很重要。 |
> | Write tests to lock in the behaviour of your package’s API. | 编写测试以锁定你包的 API 行为。 |
> | If you think it’s slow, first prove it with a benchmark. | 如果你觉得它慢，先用基准测试证明。 |
> | Moderation is a virtue. | 适度是一种美德。 |
> | Maintainability counts. | 可维护性很重要。 |

其实除了 Go 之禅外，还有 Go 语言作者曾在 Gopherfest 2015年分享过的：[Go Proverbs - Simple, Poetic, Pithy](https://go-proverbs.github.io/)，完整视频：[https://www.youtube.com/watch?v=PAAkCSZUG1c](https://www.youtube.com/watch?v=PAAkCSZUG1c)。

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Don't communicate by sharing memory, share memory by communicating. | 不要通过共享内存来通信，要通过通信来共享内存。 |
> | Concurrency is not parallelism. | 并发不等于并行。 |
> | Channels orchestrate; mutexes serialize. | Channel 用于编排；互斥锁用于串行化。 |
> | The bigger the interface, the weaker the abstraction. | 接口越大，抽象越弱。 |
> | Make the zero value useful. | 让零值也有用。 |
> | interface{} says nothing. | interface{} 什么也没说明。 |
> | Gofmt's style is no one's favorite, yet gofmt is everyone's favorite. | Gofmt 的风格不是任何人的最爱，但 gofmt 却是所有人的最爱。 |
> | A little copying is better than a little dependency. | 少量复制优于少量依赖。 |
> | Syscall must always be guarded with build tags. | Syscall 必须始终用构建标签保护起来。 |
> | Cgo must always be guarded with build tags. | Cgo 必须始终用构建标签保护起来。 |
> | Cgo is not Go. | Cgo 不是 Go。 |
> | With the unsafe package there are no guarantees. | 使用 unsafe 包没有任何保证。 |
> | Clear is better than clever. | 清晰优于聪明。 |
> | Reflection is never clear. | 反射从不清晰。 |
> | Errors are values. | 错误是值。 |
> | Don't just check errors, handle them gracefully. | 不要只检查错误，要优雅地处理它们。 |
> | Design the architecture, name the components, document the details. | 设计架构，命名组件，记录细节。 |
> | Documentation is for users. | 文档是给用户看的。 |
> | Don't panic. | 别慌。 |

## Python 之禅

这个应该是流传最广的经典之作了，以上两篇也是受其启发而创作的。

来源：[The Zen of Python](https://peps.python.org/pep-0020/)，作者是 Tim Peters，来源于 1999年社区的一次讨论：[https://groups.google.com/g/comp.lang.python/c/B_VxeTBClM0/m/L8W9KlsiriUJ](https://groups.google.com/g/comp.lang.python/c/B_VxeTBClM0/m/L8W9KlsiriUJ)，真的很有年代感了，另外这篇讨论也挺有意思的，这个 Thread 讨论的是要不要用 Java 作为底层语言去实现 Python2.0。

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Beautiful is better than ugly. | 优美胜于丑陋。 |
> | Explicit is better than implicit. | 明确胜于隐晦。 |
> | Simple is better than complex. | 简单胜于复杂。 |
> | Complex is better than complicated. | 复杂胜于繁琐。 |
> | Flat is better than nested. | 扁平胜于嵌套。 |
> | Sparse is better than dense. | 稀疏胜于密集。 |
> | Readability counts. | 可读性很重要。 |
> | Special cases aren't special enough to break the rules. | 特例不足以打破规则。 |
> | Although practicality beats purity. | 虽然实用胜于纯粹。 |
> | Errors should never pass silently. | 错误绝不应该悄无声息地被忽略。 |
> | Unless explicitly silenced. | 除非你明确让它沉默。 |
> | In the face of ambiguity, refuse the temptation to guess. | 面对歧义，拒绝猜测的诱惑。 |
> | There should be one-- and preferably only one --obvious way to do it. | 做一件事应该有一种——最好也只有一种——显而易见的方法。 |
> | Although that way may not be obvious at first unless you're Dutch. | 虽然除非你是荷兰人，否则一开始可能并不显而易见。 |
> | Now is better than never. | 现在胜于永不。 |
> | Although never is often better than *right* now. | 虽然永不往往胜于“立刻”就做。 |
> | If the implementation is hard to explain, it's a bad idea. | 如果实现难以解释，那就是个坏主意。 |
> | If the implementation is easy to explain, it may be a good idea. | 如果实现容易解释，它可能是个好主意。 |
> | Namespaces are one honking great idea -- let's do more of those! | 命名空间是一个非常棒的主意——让我们多用它吧！ |

同样有个彩蛋，在任何 Python 环境中输入以下包就可以看到：

```python
import this
```

## C++ 哲学

来源：[C++ Philosophy](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-philosophy)

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Express ideas directly in code. | 用代码直接表达想法。 |
> | Write in ISO Standard C++. | 使用符合 ISO 标准的 C++ 编写。 |
> | Express intent. | 表达意图。 |
> | Ideally, a program should be statically type safe. | 理想情况下，程序应当是静态类型安全的。 |
> | Prefer compile-time checking to run-time checking. | 优先选择编译期检查，而不是运行时检查。 |
> | What cannot be checked at compile time should be checkable at run time. | 编译期无法检查的内容，应当能在运行时检查。 |
> | Catch run-time errors early. | 尽早捕获运行时错误。 |
> | Don't leak any resources. | 不要泄漏任何资源。 |
> | Don't waste time or space. | 不要浪费时间或空间。 |
> | Prefer immutable data to mutable data. | 优先选择不可变数据，而不是可变数据。 |
> | Encapsulate messy constructs, rather than spreading through the code. | 封装杂乱的结构，而不是让它们散落在代码中。 |
> | Use supporting tools as appropriate. | 适当使用辅助工具。 |
> | Use support libraries as appropriate. | 适当使用支撑库。 |

C++ 哲学其实还有一条广为流传，但是不在文档里面的：

> | 原文 | 翻译 |
> | --- | --- |
> | You don't pay for what you don't use. | 你不支付你不使用的成本。 |

## Unix 哲学

最后一个是 Unix 哲学，Unix 哲学的总结其实经过了很多版本的迭代，从 Wikipedia 上就可以看出来：[The Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)，这里我记录的是《Unix 变成艺术》里总结的 17条，这 17条即使经历了二十多年仍然是我喜欢的计算机界的哲学。

原文：[http://www.catb.org/esr/writings/taoup/html/ch01s06.html](http://www.catb.org/esr/writings/taoup/html/ch01s06.html)，这一张的第二页就是十分著名的 ["KISS"(Keep It Simple, Stupid!)](http://www.catb.org/~esr/writings/taoup/html/ch01s07.html) 原则。

原文和翻译：

> | 原文 | 翻译 |
> | --- | --- |
> | Rule of Modularity: Write simple parts connected by clean interfaces. | 模块化原则：编写简单的部件，并用清晰的接口连接起来。 |
> | Rule of Clarity: Clarity is better than cleverness. | 清晰性原则：清晰胜于巧妙。 |
> | Rule of Composition: Design programs to be connected to other programs. | 组合原则：设计程序以便能够与其他程序连接。 |
> | Rule of Separation: Separate policy from mechanism; separate interfaces from engines. | 分离原则：将策略与机制分离；将接口与引擎分离。 |
> | Rule of Simplicity: Design for simplicity; add complexity only where you must. | 简洁原则：为简单而设计；只在必须时增加复杂性。 |
> | Rule of Parsimony: Write a big program only when it is clear by demonstration that nothing else will do. | 简约原则：只有当明确证明没有其他选择时，才编写大型程序。 |
> | Rule of Transparency: Design for visibility to make inspection and debugging easier. | 透明原则：为可见性而设计，让检查与调试更容易。 |
> | Rule of Robustness: Robustness is the child of transparency and simplicity. | 鲁棒性原则：鲁棒性是透明与简单的产物。 |
> | Rule of Representation: Fold knowledge into data so program logic can be stupid and robust. | 表示原则：将知识融入数据，让程序逻辑可以简单且健壮。 |
> | Rule of Least Surprise: In interface design, always do the least surprising thing. | 最少惊讶原则：在接口设计中，总是做最不令人惊讶的事。 |
> | Rule of Silence: When a program has nothing surprising to say, it should say nothing. | 沉默原则：当程序没有什么意外要说时，它就应该保持沉默。 |
> | Rule of Repair: When you must fail, fail noisily and as soon as possible. | 修复原则：当你必须失败时，要尽快并且大声地失败。 |
> | Rule of Economy: Programmer time is expensive; conserve it in preference to machine time. | 经济原则：程序员时间很昂贵；应优先节省它，而不是机器时间。 |
> | Rule of Generation: Avoid hand-hacking; write programs to write programs when you can. | 生成原则：避免手工硬改；能写程序来写程序时就这么做。 |
> | Rule of Optimization: Prototype before polishing. Get it working before you optimize it. | 优化原则：先做原型再打磨；先让它能用，再去优化。 |
> | Rule of Diversity: Distrust all claims for “one true way”. | 多样性原则：不信任所有关于“唯一正确方式”的说法。 |
> | Rule of Extensibility: Design for the future, because it will be here sooner than you think. | 可扩展性原则：为未来而设计，因为它会比你想象得更快到来。 |

## 总结

这是一次特别的计算机考古经历，每次看到这些禅道和哲学，都惊叹于前辈们的智慧和经验，这些原则和指导方针在计算机界一直都是非常有价值的。尤其是在这个 AI Coding 导致代码量暴增的时代，简单、透明、可维护性、鲁棒性等这些原则还能继续被准守么。

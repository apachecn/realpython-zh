# 与 Dane Hillard 的 Python 社区访谈

> 原文：<https://realpython.com/interview-dane-hillard/>

今天和我一起的还有[Dane Hillard](https://realpython.com/team/dhillard/),[it haka](https://www.ithaka.org)的首席 web 应用程序开发人员和《Python Pro 的[T5】实践的作者。戴恩也是*真正的 Python*](https://realpython.com/asins/1617296082/) [教程作者](https://realpython.com/team/dhillard/)。

在这次采访中，我们讨论了各种主题，包括代码复杂性、Python 包维护和爆米花。事不宜迟，让我们欢迎戴恩。

谢谢你参加我的采访，戴恩。我想以我们对所有来宾一样的方式开始:你是如何开始编程的，你是什么时候开始使用 Python 的？

![Dane Hillard](img/7d6d2940043c0d9037cf56063696011b.png)

戴恩:谢谢你让我回来！*真正的 Python* 是一个花更多时间的好地方。我对编程的一些最初体验对许多来自 LiveJournal 和 MySpace 时代的孩子来说是一样的——我定期定制我的个人资料页面和主题，以确保我的焦虑漫谈看起来是最好的。

大约在同一时间，我开始在 [Rhinoceros](https://www.rhino3d.com/) 中做一些 3D 建模，作为一个主要的艺术出口，但它也提供了一些我修补过的脚本功能。我和一个朋友非常喜欢 [Liero](https://en.wikipedia.org/wiki/Liero) ，我甚至做了一些定制的武器给我们玩。所以总的来说，一个令人讨厌的开始来自于一些无关紧要的兴趣。

我在学校学过 C++和 MATLAB，我的第一份实习和全职工作就是用这些语言完成的。一路走来，我学会了 Perl，并用它找到了我的第二份工作。

在那里学到大量 SQL 优化知识的同时，我也开始和一个朋友一起做一些业余项目。他是一个喜欢 Rails 的人，所以我开始接触 Ruby。我一直在用 PHP 和 Spring 为我的摄影作品[运行一个网站，决定接下来试试 Rails。“按照惯例编码”的范例当时并不完全符合我的想法。](https://www.danehillard.com)

当我最终决定我的网站需要一个更好的版本时，我四处寻找与 Rails 相似的流行的 web 框架，最终找到了 Django。从那以后 Python 就成了我的最爱！这是一条曲折的道路，但我喜欢它带我到目前为止。

**Ricky:** *这些天你最感兴趣的 Python 话题是什么？*

**Dane:** Python 包维护是我最近的一个重点。我维护着几个小型开源项目，如 [apiron](https://github.com/ithaka/apiron) 和[django-web reference](https://github.com/easy-as-python/django-webmention)，我还在 ITHAKA 内部维护着十几个软件包。拥有一个可重复但可迭代的过程，一个固执但灵活的过程，变得非常有价值。

这一切都归结到工具！忘记在一个或两个包中进行更改会导致以后更多的上下文切换，所以尽管包之间仍然有一些重复的任务，但它们更像是菜谱，而不是为每个包重新发明轮子。

我已经尝试了几种依赖管理的解决方案，比如 Pipenv 和 poem，但是我想要的是能够经受住打包中涉及的所有工具的挑战的解决方案，比如 pytest、mypy、Black 和 Pylint 等等。

目前，我已经相当舒适地适应了使用 tox 和`setup.cfg`来管理大部分事情的工作流程。我也在关注`pyproject.toml`。

现在所有这些方面都有了一些自动化，我花了更多的时间来考虑代码的复杂性。我在我的书里谈了一点，但是知道足够写一些东西并不意味着它在实践中总是得到适当的关注！我被我们在整个组织中使用的模式所吸引，并为这些模式找到正确的设计，帮助我们更快更安全地前进。

我最近一直在使用 [Radon](https://radon.readthedocs.io/en/latest/) 来快速方便地访问 Python 复杂性统计数据。我已经很快确定了我们经常接触的几个代码区域，它们的复杂性对于解决是有价值的。我们还使用 [SonarQube](https://www.sonarqube.org/) 来跟踪这些数据。每个人都应该看看 [Anthony Shaw 的采访](https://realpython.com/interview-anthony-shaw/)，了解更多关于他制作的工具。

虽然这些采访是关于社区成员的个人故事，但我也试图给我们的读者留下一些可操作的东西，他们可以带走并应用到他们的代码中。因此，考虑到这一点，你能给出哪些大多数人可能没有意识到的实用技巧呢？

通过用一个将条件映射到动作的字典来替换条件集，你可以显著地降低很多代码的复杂性。我经常惊讶于使用这种重构会有多少代码崩溃。

Sandi Metz 有一个伟大的演讲，关于镀金玫瑰形中的重构。梅斯谈到了把转换的原因和转换时要做的事情分开。我强烈推荐观看这个和她所有其他的演讲。

**瑞奇:** *你是这里的教程作者*真正的 Python *同时也是《Python Pro *的* [练习的作者。你希望人们读这本书时能从中得到什么？你在写这本书的时候学到了什么？](https://thepythonpro.com)*

**戴恩:**这真是个好问题。人们很容易认为一本书涵盖了某人几十年来一直在做的事情，我相信这有时是真的。不过，我在写这本书的时候确实学到了很多。它迫使你做一些结构化的研究，并批判性地审视你当前理解的替代方案。

在写这本书的时候，我学到的最重要的事情之一就是**耦合**的概念。经常听说我们想要松耦合的代码，但是对我来说，这从来都不是一个很实际的想法。

我开始把面向对象编程中的耦合看作是对象扮演的角色，以及对象如何相互传递消息。这种心理模型揭示了代码中的许多尴尬之处，这通常可以通过尝试为这些交互编写测试来证明。

你会看到这一点在 Metz 的演讲中得到了很好的体现——她最初是一名 Smalltalk 程序员，这些想法通常可以追溯到那群人。

瑞奇: *你谈到过为公共利益而编码。到目前为止你是如何做到的，你对未来有什么想法吗？*

戴恩:我坚信集体知识的力量。开源*软件*经常这样做，但我认为它需要继续发展。[投资开放基础设施](https://investinopen.org)是一位同事最近分享的一个很好的例子。他们不只是说，“这里有一堆你可以使用的技术，”而是把它带到一个新的水平，并提供战略，研究，社区，等等。

**里基:** *现在只剩下最后几个问题了。你在业余时间还做些什么？除了 Python 和编程，你还有什么其他的爱好和兴趣？*

**戴恩:** [我是一名歌手兼词曲作者](https://littleleviathan.com/)，但我最近没怎么写作。我很喜欢在隔离期间学习打掩护。我已经喝了不少酒，唱了不少亚历克西·默多克盖尔歌曲。我最近最喜欢的是达米安·赖斯的《T4》和狐狸乐队的《群岛》。

我一直在做一些与食物相关的事情。在去疫情之前，我开始了一个酸面团的兴趣爱好，在穿越整个州之后，我刚刚回到这个爱好上。我最近发现营养酵母是人类已知的最好的爆米花配料之一，所以一定要去试试。对我来说，加点辣椒粉、蒜盐、黑胡椒和香草味道很好。

里基: *谢谢你加入我，戴恩！*

* * *

如果你想就我们今天谈论的任何事情与戴恩取得联系，那么你可以通过他的网站或 T2 的推特联系他。

如果你想让我采访 Python 社区中的某个人，请在下面留下评论或在 Twitter 上联系我。编码快乐！
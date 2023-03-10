# Bruno Oliveira 的 Python 社区访谈

> 原文：<https://realpython.com/interview-bruno-oliveira/>

今天和我一起的还有[布鲁诺·奥利维拉](https://twitter.com/nicoddemus)，他可能是最著名的 [`pytest`](https://docs.pytest.org/en/latest/) 核心开发者。在这次采访中，我们涵盖了将大型代码库从 C++迁移到 Python，如何开始使用`pytest`，以及他对黑暗灵魂的热爱。

**里基:** *欢迎来到真正的 Python，布鲁诺。我很高兴你能加入我们。让我们像对待所有客人一样开始:你是如何开始编程的，你是什么时候开始使用 Python 的？*

布鲁诺:嗨，瑞奇。谢谢你邀请我。

![Bruno Oliveira](img/14d941f714d6b94e4728bb1276532b0c.png)

我大约在 23 年前开始编程。我刚开始接触计算机时，我的一个朋友给我看了这本关于 Visual Basic 的书，我非常惊讶你能自己编写计算器。

过了一段时间，我爸爸给我买了《德尔福圣经》。我如饥似渴，过了一会儿，我开始用 DirectX 编程，制作非常简单的游戏。

之后，我上了大学，在第二学期，我设法得到了一份实习工作，从事一个图像处理的 Delphi 应用程序。实习结束后，我加入了 [ESSS](https://www.esss.co/en/) ，这是我至今工作的公司。

我在 ESSS 的角色是一名技术领导者，负责管理我所从事项目的技术方面，包括设计和日常代码审查。我目前参与了四个项目。

与其他技术负责人一起，我还开发和监督我们的高级工作，例如将所有代码从一个 Python 版本迁移到下一个版本，解决我们 CI 中的问题，实现开发工作流，等等。

在 ESSS，我们专门为石油和天然气行业开发工程应用。当我加入时，所有东西都用 C++编写，团队自己开发所有东西，包括多平台 GUI 库。在我被雇佣大约一年后，我们开始研究 Python(当时是 2.4 版本)，以及如何将它与 PyQt 结合起来快速开发我们的应用程序。

今天，我们的绝大部分代码都是用 Python 编写的，还有一些 C++用于模拟和数值计算。2019 年 1 月，我们完成了所有项目从 Python 2 到 Python 3(当时是 3.5 版)的迁移，这是一项涉及整个团队在四年多时间里尽可能工作的努力。

**里基:** *你成为* `pytest` *的核心开发者已经有一段时间了。你是如何发现* `pytest` *的，为什么会一跃成为它的贡献者之一？*

**Bruno:** 自从我们开始使用 Python，我们立即看到了自动化测试的价值，这不仅仅是因为 Python 是动态的。当我们所有的代码都是普通的 C++时，应用程序会一直崩溃，即使有编译器也相对安全。

我们有机地发展了我们的测试代码库，增加了对 Qt、并行性、丰富的测试集合等的支持。2013 年左右，我发现了`pytest`，被图书馆惊艳到了。它包含了我们在内部实现的所有东西以及一堆我们想要的东西，它还具有一个非常有表现力的插件系统，然后可以扩展到尚未提供的功能。

我一直喜欢自动化测试，所以大约在那个时候我创建了`pytest-qt`插件，而`pytest-mock`就在那之后被创建了。然后，我开始参与邮件列表，并贡献错误修复和新功能。最终，`pytest`， [Holger Krekel](https://twitter.com/hpk42) 的创造者，把我变成了核心开发者。

几年后，我们设法用`pytest`和插件替换了我们所有的定制测试代码库。

**瑞奇:** *本次面试时，* `pytest` *6.0 目前处于发布候选人阶段。新版本最让你兴奋的是什么？有什么新特性可能会改变人们测试代码的方式吗？*

**Bruno:** 我认为对许多人来说最令人兴奋的特性是`pytest`现在是完全类型注释的，允许用户使用`mypy`对他们的测试代码进行类型检查。这花了好几个月的努力，由我们最新的核心贡献者之一， [Ran Benita](https://github.com/bluetech) 带头。

另一个期待已久的特性是使用`pyproject.toml`文件进行配置的能力。

**里奇:** *你还与 Packt 出版社合作写了一本书，名为* [pytest 快速入门指南:用简单且可维护的测试编写更好的 Python 代码](https://realpython.com/asins/1789347564/) *。你是如何找到写书的体验的，这个过程对你自己的 Python 测试有什么帮助？*

**Bruno:** 虽然尝试写出与我们通常在编程书籍和文章中看到的不同的代码示例很有趣，比如《黑暗灵魂》和《电视参考》，但老实说，总体体验有点令人疲惫。

这与出版商和编辑无关，他们真的帮了大忙。只是我不认为我对它有热情，所以与编程相比，一切都是艰苦的工作，编程是我喜欢的东西，给我带来快乐。

但总体体验是积极的。必须以一种易于理解的方式写下一堆模式，比如如何将大型测试套件从`unittest`移植到`pytest`，这帮助我将它们固化在脑海中。

对于任何阅读这篇文章的初学者来说，为什么测试你的代码很重要，以及如何开始使用 `pytest` *？*

Bruno: 编写自动化测试与大多数人在编写新代码时已经做的事情没有太大区别。通常他们会打开 REPL 快速尝试一些东西，就像这样:

>>>

```py
>>> from mymodule import mysum
>>> mysum(4, 5)
9
>>> mysum(1, -1)
0
>>> # Woot! it works
```

人们可能还会在模块中的`if __name__ == __main__:`下编写一些快速代码，如下所示:

```py
if __name__ == "__main__":
    print(mysum(4, 5))
    print(mysum(1, -1))
    # See that it prints '9' and '0' and woot! it works
```

虽然这适合于查看事情是否在工作，但是跨越到编写自动化测试是非常简单的。我们需要做的就是创建一个`test_mymodule.py`文件，并编写以下内容:

```py
def test_mysum():
    assert mysum(4, 5) == 9
    assert mysum(1, -1) == 0
```

就是这样。现在你可以执行`pytest`，它会检查`mysum()`还在工作。当你已经知道某个功能可以工作的时候，测试它可能看起来很傻，但是重要的是要意识到这个自动化测试确保了这个功能在将来会*保持工作*。您添加的测试越多，您的整个系统一直被验证的就越多。

对我来说，这是自动化测试最精彩的部分。它不仅确保了您的系统能够工作，而且确保了它在未来能够继续工作，即使您决定重构一切。至少，它会指出你可能犯的任何错误。手动测试无法扩展。

**里基:** *现在我的最后几个问题。你在业余时间还做些什么？除了 Python 和编程，你还有什么其他的爱好和兴趣？*

**布鲁诺:**我真的很喜欢看电视剧(谁不喜欢？)和在我的电脑上玩游戏。我是一个超级黑暗灵魂迷，我真的很喜欢和我的朋友一起玩像*《巫师 3》*这样丰富的角色扮演游戏和多人合作游戏。

谢谢你加入我的节目，布鲁诺。这是我的荣幸。

* * *

如果你想和布鲁诺联系，你可以在推特上找到他。你也可以拿一本他的《T2》书。

如果你想让我采访 Python 社区中的某个人，请在下面留下评论或在 Twitter 上联系我。

编码快乐！
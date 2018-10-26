## Chapter 49、Pros and cons of end-to-end learning

**端到端学习的优点和缺点**

考虑我们前面例子中相同的语音流水线：

![49-0](http://oow6unnib.bkt.clouddn.com/myl-c49-0.jpg)

该流水线的很多部分是“手工设计”的：

- MFCCs是一个手工设计的音频特征的集合。尽管它们提供了一个音频输入的合理总结，它们也通过丢弃一些信息来简化输入信号。
- 音素是语言学家的发明。它们是说话声音的不完美表示。在某种程度上，音素是对现实较差的近似，强制算法使用音素表示将限制语音系统的性能。

这些手工设计的组件限制了语音系统的潜在性能。然而，允许手工设计的组件也有一些优点：

- MFCC特征对不影响内容的某些语音属性（如说话者的音高）具有鲁棒性。因此，它们有助于简化学习算法的问题。
- 在某种程度上，音素是语音的合理表示，它们也能帮助学习算法理解基本的声音要素，从而提高其性能。

拥有更多手工设计的组件通常可以让语音系统以更少的数据学习。通过MFCCs捕获的手工设计的知识，以及音素“补充”的学习算法从数据中获取的知识。当我们没有太多数据时，这些知识是有用的。

现在，考虑端到端系统：

![49-1](http://oow6unnib.bkt.clouddn.com/myl-c49-1.jpg)

该系统缺乏手工设计的知识。因此，当训练集很小时，它可能比手工设计的流水线要差。

但当训练集很大时， 那么它不会受到MFCC或基于音素表示的局限性的阻碍。如果学习算法是一个足够大的神经网络，并且训练数据足够多，那么它就有可能做的很好，甚至可能达到最优错误率。

当“两端”（输入端和输出端）都有很多标注数据时，端到端学习系统将表现良好。在该样例中，我们需要一个<音频，转录>对的大数据集。当该类型数据不可用时，请谨慎使用端到端学习方式处理。

如果你正在致力于一个机器学习问题，其训练集非常小，大部分算法的知识将不得不来自于你的洞察。即，来自于“手工设计”的组件。

如果你选择不使用端到端系统，你将不得不决定流水线中的步骤，以及如何将它们组合起来。在接下来的几个章节中，我们将为设计这些流水线提供一些建议。

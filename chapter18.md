## Chapter 18、How big should the Eyeball and Blackbox dev sets be?

**Eyeball 和 Blackbox 开发集应该多大？**

![0](http://oow6unnib.bkt.clouddn.com/myl-c17-0.jpg)

你的 Eyeball 开发集应该足够大，大到可以让你了解到算法的主要错误类别。如果你正在从事一项人类表现很好的任务（如识别图像中的猫），以下是一些粗略的指导方针：

- 一个使你的分类器犯错10次的 Eyeball 开发集将被认为是非常小的。只有10个错误，很难准确估计不同错误类别的影响。但如果您的数据非常少，而且不能负担的起更多 Eyeball 开发集，有总比没有好，这将有助于项目的优先顺序。
- 如果分类器在 eyeball 开发集上样本上犯了约20个错误，你将会开始大致了解主要的错误来源。
- 如果有约50个错误，你将会比较好的了解主要的错误来源。
- 如果有约100个错误，你将会很清楚主要的错误来源。我见过有人手动分析更多的错误——有时候多达500个。只要你有足够多的数据，这将是无害的。

假设你的分类器有5%的错误率。为了确保在 Eyeball 开发集中有约100个错误标记的样本，Eyeball 开发集应该有约2000个样本（因为 0.05*2000 = 100）。分类器的错误率越低，为了获得足够多的错误来分析，Eyeball 开发集需要越大。

如果你正在做一个连人都做不好的任务，那么检查 Eyeball 开发集的联系将不会有什么帮助，因为很难找出算法不能正确分类一个样本的原因。这种情景下，你可能会忽略 Eyeball  开发集。我们将在后续章节中讨论这些问题的指导方针。

![0](http://oow6unnib.bkt.clouddn.com/myl-c17-1.jpg)

Blackbox 开发集该如何？我们之前说过，开发集有约1000-10000个样本是正常的 。为了完善这个表述，尽管更多的数据几乎没什么坏处，一个有1000-10000个样本的 Blackbox 开发集通常会为你提供足够的数据去调超参和选择模型。一个含有100个样本的 Blackbox 开发集比较小，但仍然有用。

如果你有一个小的开发集，那么你可能没有足够的数据将其分成足够大的 Eyeball 和 Blackbox 开发集来满足他们的目的。相反，你的整个开发集可能不得不用作 Eyeball 开发集——即，你将手动检查所有的开发集数据。

在 Eyeball 和 Blackbox 开发集之间，我认为 Eyeball 开发集更重要（假设你正在研究一个人类能够很好解决的问题，检查这些样本能帮你获得洞察力）。如果你只有一个 Eyeball 开发集，你可以在这个开发集上进行错误分析、模型选择和调超参。只有一个 Eyeball 开发集的缺点是过拟合开发集的风险更大。

如果你有数据的充足访问权限，那么 Eyeball 开发集的大小将主要取决于你有时间去手动分析样本的数量。例如，我很少看到有人手动分析超过1000个错误。



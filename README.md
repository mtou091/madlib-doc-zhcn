# madlib-doc-zhcn
apapche madlib使用手册不完全中文翻译

madlib是pivotal公司开发的机器学习库，可以使用sql进行数据挖掘和机器学习。

目前我和spark的mlib配合使用，spark下用的scala。

两者相对而言spark的算法要丰富一点，但基本的madlib也够用。

使用scala进行spark数据挖掘要重新学习一门门语言。scala确实比较美妙，有兴趣的可以看看。不过我遇到一些连多一门数据库方言都不愿意接触的人，所以madlib也是一个相当好的选择。

如果你会sql，你只要话5分钟再稍微多了解一点postgresql的sql中的数组怎么操作的，你再看madlib就不会觉得有任何困难。（然后你再学madlib发现还是跳进一个大坑，原来我当年学的线性代数全喂狗了啊！@！#@！#！@￥）


关于机器学习

madlib的文档里面有对各种算法的说明，但是要开始机器学习，间一线找本书翻翻机器学习有哪几个主要算法。

我看的是《机器学习实战》，作者Peter Harrington。里面用python实现了机器学习的几个算法，按作者说其实就是实现了那篇著名论文《数据挖掘十大算法》里面的9种算法。

摸索了几个星期，本来想写一个机器学习的概要总结，一看书里第一章就有（囧）。我就不动手了，直接打在这里，给一个机器学习的概貌。（以下介绍都是出资书里面，有误导的地方别打我）

机器学习的主要任务就是分类。
要使用机器学习算法进行分类，首先要做的就是算法训练，即学习如何分类。通常我们为算法准备大量已分类数据作为训练集，每个训练样本有N个特征，一个目标变量。（以鸟为例，鸟的体重，翼展，脚蹼，后背颜色等是特征，鸟的种类是目标变量）机器学习算法就是得到特征和目标变量的关系。然后下次直接输入特征就能得到目标变量了。
所以机器学习有训练数据和样本数据，训练数据来训练算法，样本数据来检测算法准确率。
机器学习的另一项任务是回归，就是用来预测数值型数据。和上面类似，输入特征，得到一个预测的值。
分类算法的目标变量是标称型数据（结果只在有限目标集），回归算法的目标变量是连续型。
回归和分类都属于监督学习。称为监督学习，是因为这类算法必须知道预测什么，即要知道目标变量的分类信息。
（哎呀，打了这么多名词，心好累！）
与监督学习对应的是无监督学习，没有类别信息，也不会给定目标值。
无监督学习中，将将数据集合分成由类似对象组成的多个类的过程称为聚类。江寻找描述数据统计值的过程成为密度统计。

机器学习的几个算法分类(别多看这个表，有毒)

*监督学习    +k近邻算法                                 线性回归
             +朴素贝叶斯算法                            局部加权线性回归
			 +支持向量机                                Ridge线性回归
			 +决策树                                    Lasso最小回归系数估计
*无监督学习  +k-均值                                    最大其望算法
             +DBSCAN                                    Parzen窗设计

通俗讲 监督学习里k近邻算法，决策树，朴素贝叶斯，Logistic回归，支持向量机都可用于分类。回归和树回归用来做数据预测。无监督学习里K-均值用来做聚类。Apriori对数据进行关联分析。

使用平台：
机器学习不一定需要大数据平台，个人电脑也可以，不过数据量没那么大而已。
madlib的另一个好处就是可以和postgresql集成在一起，postgresql9.6的并行计算快得飞起，所以不用担心你电脑cpu跑不满。正式环境建议还是部署在多节点的分布式数据库greenplum或者hawq集群上。当然，你有NB的单机服务器就当我没说过。
这里我本地的平台是Debian jessie+postgresql 9.6.1+madlib 1.9.1
另外我在centos7上也部署过postgresql9.6.1+madlib 1.9.1
安装步骤会在后面提到。

最后啰嗦一下，
翻译这个的目的是我英文太烂，看完英文文档印象不深，容易忘记。另外我们也想让其他的同事也能用起来，然后我也想了解深入一点，所以就有这个。（前方预警，里面文档格式比较乱，主要是我不想把时间浪费在排版上，排版再漂亮反正一遍也看不懂，多看几遍以后估计就习惯了）




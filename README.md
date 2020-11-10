# A-stock-prediction-algorithm-based-on-machine-learning
**（陆续更新）重新整理过的基于机器学习的股票价格预测算法，里面包含了基本的回测系统以及各种不同的机器学习算法的股票价格预测，包含：LSTM算法、Prophet算法、AutoARIMA、朴素贝叶斯、SVM等**  
#### 强烈推荐大家去看看sklearn库的文档，地址：[https://sklearn.apachecn.org ] 

### 11-10
**大家好，很高兴有这么多小伙伴能给我的代码star，之前一段时间在弄爬虫的相关技术，没有怎么关心股票回测和机器学习方面的内容。今晚我重新测试后，我发现原来的一些包已经不能用了，而且tushare库也很快就会关闭，因此，我之后的时间会尝试来修改一下这部分的内容。主要的重心是数据的获取、可视化和及时性上，欢迎大家能够和我一起学习，希望我能冲到100star；
ps：这个只是工作之外的爱好哈，另外股市有风险**

### 4-11  
**机器学习算法/LR.py**  
线性回归算法，线性回归是利用数理统计中的回归分析，来确定两种或两种以上变量间相互依赖的定量关系的一种统计分析方法，运用十分广泛。在这里的调用和其他的sklearn库文件没有什么区别。

### 4-10  
**机器学习算法/DecisionTree.py**  
决策树算法，这里也是直接调用的sklearn库。和随机森林算法的思路过程没什么不同，也是先构建x_test, y_test, x_train, y_train,然后放入模型里进行拟合。其算法效果和随机森林差别不大。

### 4-9  
**机器学习算法/Randomforest.py**  
随机森林算法，给出一个y指标是T+1日对于T日是否看涨。在这里需要调整的参数是在new一个模型的时候给出的max_depth和n_estimators。通过给出node（分隔点）来确定训练集和测试集。在这里有一个roc_auc_score()函数，是用来测试该算法对于预测而言有没有偏袒。  

### 4-7  
**基本面机器学习算法/NBM.py**  
朴素贝叶斯算法，在这个例子中使用的是通过之前季度的财务报表中的各种指标，来预测下一季度的财务报表中的情况，朴素贝叶斯算法其实非常简单，可以自己实现，在这里使用的是sklearn.naive_bayes中的GaussianNB。主要的调用规则是：  
import from sklearn.naive_bayes import GaussianNB  
clf = GaussianNB()  
clf.fit()  
clf.predict()  

### 3-15
**机器学习算法/kNN.py**  
kNN算法，即k-近邻算法，KNN是通过测量不同特征值之间的距离进行分类。它的思路是：如果一个样本在特征空间中的k个最相似(即特征空间中最邻近)的样本中的大多数属于某一个类别，则该样本也属于这个类别，其中K通常是不大于20的整数。KNN算法中，所选择的邻居都是已经正确分类的对象。该方法在定类决策上只依据最邻近的一个或者几个样本的类别来决定待分样本所属的类别。

### 3-13  
**机器学习算法/SVM.py**  
支持向量机(Support Vector Machine)，通过SVM算法对该数据集第N+1日的收盘价相对于第N日的收盘价涨跌情况进行分析，若第N+1日的收盘价相对于第N日收盘价为涨，则记为1,；反之，记为0。由于SVM算法为监督学习算法，因此在训练的过程中算法会根据实际的涨跌情况对学习算法进行修正。对于测试集中的部分，预测每一个交易日的股价涨跌情况，并以真实涨跌情况进行测算，计算在测试集中算法预测的正确率。SVM算法包中提供了多种核函数，在这里提供了三种。

**机器学习算法/Prophet.py**  
Prophet算法，也称为预言家算法。Prophet属于时间序列模型。相对于ARIMA模型，Prophet模型的优势在于可以不考虑缺失值的填充问题。另外，Prophet模型的拟合速度远比ARIMA模型更快。

### 3-12  
**机器学习算法/AutoARIMA.py**  
差分回归积分移动平均模型(Autoregressive Integrated Moving Average Model)，通过给定d,p,q值，实现在给定的范围内自动寻找最优解，主要给定两种方法，一是一次性预测（即单一预测，使用训练集的数据直接给出所有测试集天数的预测值），另一种是按天预测，（即每日回归，每一个预测期的单位数据都用之前的数据作为训练集进行预测）

**机器学习算法/LSTM.py**  
长短神经网络，一种特殊的循环神经网络，用于处理和预测时间序列中间隔和延迟相对较长的重要事件。LSTM通过三个这样的本结构来实现信息的保护和控制。这三个门分别输入门、遗忘门和输出门。由于该神经网络随着时间变化具有数据的遗忘性，所以一次性预测与按天预测并没有较大的不同，但是该神经网络算法比较复杂，感兴趣的可以参考别的文献，在这里只是实现了基本的功能。

### 3-11  
**回测.py**  
提供了一个基本的回测demo，实现股票基本的买入卖出，考虑佣金和印花税

**传统技术面分析算法/Moving_Average.py**  
移动平均算法，通过移动窗口的方式进行股票预测，传入窗口长度参数可以进行预测，支持tushare接口直接获取数据并即时进行预测

**传统技术面分析算法/Relative_strength_index.py**  
相对强度指数，相对强弱指数RSI是根据一定时期内上涨点数和涨跌点数之和的比率制作出的一种技术曲线。返回计算期内的相对强度指数计算情况

### 2020-3-10
创建项目，README文件

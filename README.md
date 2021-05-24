# lihongyi-2021-colab
本人在学习李宏毅老师2021年机器学习深度学习课程时使用的colab文件。  
原文件来源于[课程官网](https://speech.ee.ntu.edu.tw/~hylee/ml/2021-spring.html)。我是在colab上直接运行，然后从那边直接上传过来的。  
本项目中的文件都对原始文件做了修改，包括撰写自己的注释、增加自己的代码等。
1. [Google Colab Tutorial.ipynb](https://github.com/PolarisRisingWar/lihongyi-2021-colab/blob/main/Google_Colab_Tutorial.ipynb)
2. [Pytorch Tutorial.ipynb](https://github.com/PolarisRisingWar/lihongyi-2021-colab/blob/main/Pytorch_Tutorial.ipynb)
3. HW1<br>
&nbsp;1. [官方提供的simple baseline](https://github.com/PolarisRisingWar/lihongyi-2021-colab/blob/main/HW1_simple_baseline.ipynb)<br>
&nbsp;2. [medium baseline](https://github.com/PolarisRisingWar/lihongyi-2021-colab/blob/main/HW1_medium_baseline.ipynb)<br>
&nbsp;3. [试图冲击strong baseline，没冲过去](https://github.com/PolarisRisingWar/lihongyi-2021-colab/blob/main/HW1_strong_baseline.ipynb)<br>
调参调到一半被colab关GPU了，不调了睡觉了。public score最低调到1.01048，但是private score比medium baseline跑出来的结果还高，有被坑到。主要做的工作是特征选择medium baseline中的特征加上通过SelectKBest方法选出前20个特征中不在其内的值；网络维持1层线性模型，维度为input_dim→44→1；batch_size改为100。  
参考[这篇代码](https://github.com/wolfparticle/machineLearningDeepLearning/blob/main/homework_code/hw1/HW1_local%E5%8F%82%E8%80%83%E4%BB%A3%E7%A0%81/HW1_local.ipynb)为想要继续炼丹的选手提供建议：1. 原baseline中的训练集-验证集拆分是直接分层选择，可以用sklearn的train_test_split方法改成随机拆分。2. 原baseline的训练集和测试集是分开做归一化的，这篇代码中的解决方法是训练集照常做归一化，测试集使用训练集的均值和方差做归一化；我之前也见过将训练集和测试集合并在一起然后做归一化的，或许可以一试。3. 特征选择的方式可以使用高相关性。（虽然原则上我认为这个……并不是要点）。4. 损失函数从MSELoss改成了均方根误差（毕竟kaggle上就用的RMSE，我没想到这一点确实是大失误）。  
虽然但是当我看到上述代码在本地跑出来loss居然比kaggle上高的时候我就不想调了……虽然当我看到medium baseline那个特征选择本地结果变差那么多线上结果变好那么多的时候我就已经觉得不妙了，但是我委实妹想到这居然那么不妙。我不调了，我不能为难自己，我是个非酋，命运是不会在调参时垂青我的，我以后还要炼很多丹，我不能被坑死在这里。  
话说我调参感觉确实有很多机械重复的部分，想搞个那种自动调参的工具来。

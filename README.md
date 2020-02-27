# 率土之滨账号模型分析
-   本项目是我学完python之后的练手之作,正好遇上我想买一个率土之滨的IOS
账号，因此写了这个项目用来获取藏宝阁中所有IOS端的率土之滨账号,同时分析每个账号的性价比，对拥有的武将进行估价

使用流程   
1.运行Get_Attribute.py,获取所有账号的属性集,包含一个账号可能拥有的所有属性(玉符,武将,战法等)
获取的数据保存在Attribute_Set.txt,存入data目录下   
2.运行Get_Account.py,输入需要搜寻的起始页码和目的页码,获取期间所有账号的信息,转化成属性集的向量,存储在Account_info.txt中,保存在data目录下  
3.运行regression.py,采用交叉测试岭回归的方法,对所有账号建立一个模型,模型保存在modeltest.txt下,多次运行选取误差最小的模型手动保存在model.txt中  
4.运行Calculated_value,将所有数据在模型中运行,输出预测价格和真实价格用以对照,同时输出对账号价值影响最大的属性

使用结论  
1.由于账号的价格是人为确定的,所以很容易出现偏高或者偏低的情况,很显然,当预测模型预测的账号价格低于真实价格的百分比越大的时候,
这个账号往往拥有更高可能性是一个高性价比的账号  
2.在建立完成模型之后,我试图通过查找模型中属性之间权重的大小来确定哪些属性是影响一个账号高价值的因素,
令我行为的是,在尝试了多个模型之后——尽管他们的参数各有不同,但是某些武将,例如(皇甫嵩,弓诸葛,刘备,关兴&张苞,严颜)等几乎每次都能在价值参数中名列前茅,
和之前不同的是,这不是通过我作为一个玩家的经验得出的,而是机器学习通过3000个账号的数据分析得出的.  
3.另一个现象是,新出的武将或者战法(于吉,以直报怨,伺机而动,甚至是今年的新春侍女),尽管他们的强度并不是很高,但是依然拥有很高的价值参数.
我猜测是因为拥有新武将有更大的可能是最近仍然在玩甚至充值的账号,因此他们会体现在账号整体的价值更高  
4.相反,价值参数最低,对一个账号最严重的扣分项,在不同的模型之间却保持不变,分别为武将中的率土一载和战法中的青囊秘要,同时,许多模型也表示
钟会,妹喜也是比较严重的扣分项,这很显然是反直觉的,因为他们也是新英雄,我把这归结于数据不够以及模型计算之间产生的误差  
5.总体而言,建立的数个模型大体上是符合常理的--皇甫嵩这样的将确实值钱,而拥有疾风突击这样的战法确实容易扣分,在之后学习了更好的预测值算法之后
我会继续尝试重新建立模型


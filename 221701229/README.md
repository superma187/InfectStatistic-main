# InfectStatistic-221701229
##疫情统计

 [作业要求链接](https://edu.cnblogs.com/campus/fzu/2020SpringW/homework/10281)

 [博客链接](https://www.cnblogs.com/sup187/p/12260807.html)
> ##
1、日志文本
假设有一家统计网站每天都会提供一个对应的日志文本，记录国内各省前一天的感染情况，如它2020-01-23发布的日志文本可能长这样：

福建 新增 感染患者 23人

福建 新增 疑似患者 2人

浙江 感染患者 流入 福建 12人

湖北 疑似患者 流入 福建 2人

安徽 死亡 2人

新疆 治愈 3人

福建 疑似患者 确诊感染 2人

新疆 排除 疑似患者 5人

// 该文档并非真实数据，仅供测试使用

该日志中出现以下几种情况：

1、<省> 新增 感染患者 n人

2、<省> 新增 疑似患者 n人

3、<省1> 感染患者 流入 <省2> n人

4、<省1> 疑似患者 流入 <省2> n人

5、<省> 死亡 n人

6、<省> 治愈 n人

7、<省> 疑似患者 确诊感染 n人

8、<省> 排除 疑似患者 n人

PS：

日志中各种情况的出现顺序不定，省出现的顺序不定，出现哪些省不定，省出现几次不定。

该日志文件的命名遵守对应的规范： 年-月-日.log.txt ，如2020-01-22.log.txt。

文件日期并不一定连续，若某天的日志缺失，默认为该天的情况没有变化。认为日志提供的最早一天的前一天不存在任何感染情况。如只提供2020-01-23，2020-01-25

则可认为2020-01-24增长变化都为0。-date不会提供在日志最晚一天后的日期，若提供应给与日期超出范围错误提示。

2-11补充

可能出现的所有省（已经按照拼音排好序）：

安徽
北京
重庆
福建
甘肃
广东
广西
贵州
海南
河北
河南
黑龙江
湖北
湖南
吉林
江苏
江西
辽宁
内蒙古
宁夏
青海
山东
山西
陕西
上海
四川
天津
西藏
新疆
云南
浙江
现在请你撰写程序，读取传入的log目录下的所有日志，来实现需求

  ...\
      \--log
        \--2020-01-22.log.txt
        \--2020-01-23.log.txt
2、需求
需要你的程序能够列出全国和各省在某日的感染情况

命令行（win+r cmd）cd到项目src下，之后输入命令：

$ java InfectStatistic list -date 2020-01-22 -log D:/log/ -out D:/output.txt
会读取D:/log/下的所有日志，然后处理日志和命令，在D盘下生成ouput.txt文件列出2020-01-22全国和所有省的情况（全国总是排第一个，别的省按拼音先后排序）


全国 感染患者22人 疑似患者25人 治愈10人 死亡2人

福建 感染患者2人 疑似患者5人 治愈0人 死亡0人

浙江 感染患者3人 疑似患者5人 治愈2人 死亡1人

// 该文档并非真实数据，仅供测试使用
list命令 支持以下命令行参数：

-log 指定日志目录的位置，该项必会附带，请直接使用传入的路径，而不是自己设置路径

-out 指定输出文件路径和文件名，该项必会附带，请直接使用传入的路径，而不是自己设置路径

-date 指定日期，不设置则默认为所提供日志最新的一天。你需要确保你处理了指定日期之前的所有log文件

-type 可选择[ip： infection patients 感染患者，sp： suspected patients 疑似患者，cure：治愈 ，dead：死亡患者]，使用缩写选择，如 -type ip 表示

只列出感染患者的情况，-type sp cure则会按顺序【sp, cure】列出疑似患者和治愈患者的情况，不指定该项默认会列出所有情况。

-province 指定列出的省，如-province 福建，则只列出福建，-province 全国 浙江则只会列出全国、浙江

注：java InfectStatistic表示执行主类InfectStatistic，list为命令，-date代表该命令附带的参数，-date后边跟着具体的参数值，如2020-01-22。-type 的多
个参数值会用空格分离，每个命令参数都在上方给出了描述，每个命令都会携带一到多个命令参数

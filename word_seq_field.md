# 在word中插入带章节编号的公式编号：形如(x.x)

## 首先前提是建立好多级编号，多级编号的建立方法：

胡乱敲几行标题进去，并选中，然后选择新建多级列表，n级编号链接到标题n样式，在弹出的窗口里一级一级的调，下面是三级标题的分别的设置情况

![biaoti1](./images/%E6%A0%87%E9%A2%981.png)

![biaoti1](./images/%E6%A0%87%E9%A2%982.png)

![biaoti1](./images/%E6%A0%87%E9%A2%983.png)

因为学校要求1级（章节标题）标题居中，因此编号后面空1个汉字符的要求不方便通过制表位的方式实现（此时制表符的位置不好确定）；但是2级和3级标题，由于都是居左排布，所以空1个汉字符的位置都可以算出来，当然这样的缺陷是节的数目不能超过9，否则空间会发生挤兑；

然后是比较坑的多级标题兑现环节。上面操作完了以后，刚刚一开始选中的随便输入的标题估计会一起变成一个级别的标题；

这时不要慌，操作逻辑是挨个选中，挨个改列表级别；office貌似不支持一步到位直接插入某一级别的标题；

## 建立好多级标题后，就可以创建域代码

**{STYLEREF "标题 1" \l \n \t \* MERGEFORMAT}{SEQ thuseq \* Arabic \s 1 \* MERGEFORMAT}**

选中，ctrl+F9，转换成域代码，应该就成了，注意"标题 1"货真价实地就是刚刚设置多级列表的时候将1级标题的样式的名字（可以看上面截的图）；而“thuseq”这个字段则纯是爱怎么叫怎么叫的自定义名称；

上面这段域代码是两段代码合成的，分别由{}包裹，第一个查询1级标题编号（\t开关去掉“第1章”里的非区分字段，也就是汉字“第”和“章”），其余两个开关的作用可以在域代码插入选项里查询其意思；值得一提的是，STYLEREF这个域代码，隶属于引用类别，而不是编号类别，因为编号的意思创建新的编号，而我们这里的目的实际上是引用已经存在的编号；

第2个对1级标题重新编号，由\s 1开关定义。关于这段域代码的理解，可以看油管上“https://youtu.be/WtR_XnIb-Eo” 这个大婶的视频；

可以在两个{}{}之间手动添“.”，并包裹上()，使得最终的格式是(x.x)

## alt+F9，将上述域代码转换成编号(x,x)

然后copy住，进入office，选项，校对，定义自动更正代码，以后就不用每次都敲上面那一大段域代码了。

接下来就可以纵享丝滑。
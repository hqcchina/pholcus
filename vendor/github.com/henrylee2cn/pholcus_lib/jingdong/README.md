根据京东新的页面规则进行了修改

1.以前是修改url中的page参数就可以得到每页的值。但是现在京东做了修改。
![Imgur](http://i.imgur.com/ssQHdz3.png)
现在点击第二页的时候，url中的page参数会是3，修改page现在不能得到所有的商品信息的。page=2的时候的内容，会在你的页面滚动到中间的时候通过异步的方式来加载。

2.我们输入的关键字总共有多少页商品的显示方式也修改了。这个参数现在改到了一段javasript代码中，通过js来生成页面代码。
![Imgur](http://i.imgur.com/4WEIgTs.png)

3.在存入结果的时候，我判断了一下title为空的情况。这个是因为，京东会在一些商品里面加入广告的，但是这个广告的html结构是和商品是一样的，这样我们的规则在解析的时候会得到这个无效的信息，需要去掉。
如下图:
![Imgur](http://i.imgur.com/KYZJBqp.png)

这个爬虫整体的过程就是。

1. 先访问参数page=1的url，使用正则表达式得到这个关键字一共有多少页商品
2. 根据两种加载方式(url的直接返回和异步加载)，生成所有的url。
3. 分析页面结构，得到相关的值

第一次写，写的不好的或错的地方希望大家多多包涵。^_^
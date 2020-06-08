# day04
## *任务*
* 数据解析
* lxml库
* DOM树与xpath解析原理
* xpath语法
## *笔记*
* 数据解析
    * 概念：从响应数据中抽取出目标数据的过程，就叫数据解析
    * 解析方法：re,xpath,BS4,Pyquery
* lxml库
    * 安装lxml：pip install lxml
    * lxml库使用：
        ```
        #导包
        from lxml import etree

        #发送请求
        res = requests.get(....)

        #实例化获取相应数据
        tree = etree.HTML(res.text) #etree加载的是响应数据的文件形式

        #xpath解析
        tag_text_attri = tree.xpath('xpath表达式')
        ```
* DOM树与xpath解析原理
    * DOM：DOM是Document Object Model的缩写，即文档对象模型。W3C已于2000年11月13日推出了DOM level 2规范。DOM是HTML和XML文档的编程接口规范，它与平台和语言是无关的，因而可以用各种语言和在各种平台上实现。该模型定义了HTML和XML文件在内存中文档结构，提供了对HTML和XML文件的访问、存取方法。利用DOM规范，可以实现DOM文档和XML之间的相互转换，对相应DOM文档的内容进行遍历或其他操作。如果要自由的操纵XML文件，就要用到DOM规范。
    * DOM的原理：简单的说，就是通过解析XML文档，为XML文档在逻辑上建立一个树模型，树的节点是一个个对象。我们通过存取这些对象就能够操作XML文档中的内容了。
    * DOM的优缺点
        * DOM的优势主要表现在：易用性强，使用DOM时，将把所有的XML文档信息都存于内存中，并且遍历简单，支持XPath，增强了易用性。
        * DOM 的缺点主要表现在：效率低，解析速度慢，内存占用量过高，对于大文件来说几乎不可能使用。另外效率低还表现在大量的消耗时间，因为使用DOM进行解析时，将为文档的每个element、attribute、processing-instrUCtion和comment都创建一个对象，这样在DOM机制中所运用的大量对象的创建和销毁无疑会影响其效率。
    * DOM树
        ![image](F:\积云\month06\day04\DOM树.png)
    * xpath解析原理：根据DOM节点的结构关系，来进行定位
* xpath语法
    * 基本语法
        * .：当前节点
        * /：根节点
        * //：任意节点
        * nodename：节点名定位
        * nodename[@attribute='value']：根据节点的属性进行定位
        * @attribue：获取节点的属性值
        * text()：获取节点的文本
    * 属性匹配
        * 单属性多值匹配：当节点的一个属性的多个值时，根据其中的一个进行定位 --> contains函数
        * 多属性匹配：用节点的多个属性共同定位节点
            ```
            <div name='divtag' class="item">多属性匹配</div>
            <div name='divtag' class="item2">多属性匹配2</div>
            输入：//div[@name="divtag" and @class="item"] 定位到第一个div
            ```
    * 按序选择
        * 索引选择：[6] --->索引从第6开始，跟python有区别
        * 位置函数：position()
        * last()函数:定位最后一个，last()-1定位倒数第二个
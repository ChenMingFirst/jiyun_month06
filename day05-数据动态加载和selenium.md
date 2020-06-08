# day05
## *任务*
* 数据动态加载的概念
* selenium的介绍
* selenium的安装与配置
* selenium常用的API
## *笔记*
* 动态数据加载
    * 数据动态加载：执行js代码从而获得的数据
    * 动态数据加载和爬虫的关系
        ```
            requests模块
                            -->发起请求过程中不能执行js代码
            scrapy  框架
        ```
* selenium的介绍
    * 概念：selenium是一个web自动化测试框架，程序员可以通过代码来控制浏览器，比如说打开网页，关闭浏览器，点击一下，比图说拖动，向下滚动，向左右滚动
    * 作用：帮助抓取动态加载的数据，避免反爬
* selenium的安装与配置
    * 安装
        * 安装chrome浏览器
        * selenium框架：pip install selenium
        * 驱动程序下载
            1. 查看浏览器的版本
            2. 选择对应的版本
* selenium的使用
    * 安装完成后将selenium包放入py文件的目录下
    * 导入：from selenium import webdirver
    * 请求chrome浏览器
        ```
        browser = webdriver.Chrome('./chromedriver.exe')
        url = 'url地址'
        browser.get(url=url)
        js = 'window.scrollTo(0,
        html = browser.page_source
        ```
    * 滚动请求
        ```
        browser = webdriver.Chrome('./chromedriver.exe')
        url = 'url地址'
        browser.get(url=url)
        js = 'window.scrollTo(0,document.body.scrollHeight)'    #document.body.scrollHeight：垂直滚动一页
        for i in range(3): #循环三次即滚动三次
            browser.execute_script(js)
        html = browser.page_source
        ```
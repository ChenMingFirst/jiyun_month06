# day02
## *任务*
* 爬虫概述
    * 爬虫概念
    * 爬虫语言
    * 爬虫分类
    * 爬虫课程概览
* 网络模型
    * TCP/IP五层模型
    * HTTP与HTTPS协议
    * TCP与UDP
* 服务器常见端口(默认端口)
* os模块与sys模块(课外作业，自己查)

## *笔记*
* 爬虫概述
    * 爬虫的概念：
        * 爬虫又叫网页蜘蛛，是模拟人操作客户端向服务器发起请求，抓取数据的自动化程序或脚本
    * 爬虫的作用：
        * 模拟：用爬虫程序伪装出人的行为，避免被服务器识别为爬虫程序
        * 客户端：浏览器、app都可以实现人与服务器之间的交互行为，应用客户端从服务器获取数据
        * 自动化：数据量较小可以人工获取，但往往在公司里爬取的数据量在百万条、千万条级别，所以要程序自动化获取数据
    * 爬虫语言:PHP，C/C+，Java， Python， Golang， node]
        * 对比:
            * PHP:并发能力差，对多进程和多线程支持不好，数据量较大时爬虫效率较低
            * C/C++:语言效率高，但学习成本高，对程序员的技术能力要求较高，所以目前还停留在研究层面，市场需求量很小
            * java: Python爬虫的主要竞争对手，由于]ava语言的特点，代码臃肿，代码量大，维护成本重构成本高，开发效率低，但目前市场上岗位需求比较旺盛
            * Python:语法简单，学习成本较低，对新手比较友好. Python语言良好的生态，大量库和框架的支持是的 Python爬虫目前处于爬虫图的主导地位
    * 爬虫分类
        * 通用爬虫
        * 聚焦爬虫
    * 爬虫的作用：
        * 通用爬虫:搜索引擎
            * 实例:百度，搜狗， Google的搜索引撃
            * 功能:访问网页-＞抓取数据-数据处理-＞提供检索服务
        * 工作流程：
            * 给定一个起始URL，存于爬取队列中
            * 爬虫程序从队列中取出ur1，爬取数据
            * 解析爬取数据，获取网页内的所有u1，需要的数据，放入爬取队列
            * 重复第二个步骤
        * 使搜索引擎获取网站链接
            * 主动将ur1提交给搜索引撃(https://ziyuan.baidu.com/linksubmit/url)
            * 在其他热门网站设置友情连接
            * 百度和DNS服务商合作，收录新网站
    * 网站排名(SEO):
        * 根据 Pagerank值进行排名(流量，点击率)
        * 百度竞价排名，钱多就靠前排
    * 缺点
        * 抓取的内容多数无用
        * 无法精确获取数据
    * 协议: robots协议--＞约定哪些内容允许哪些爬虫抓取
        * 无需遵守，该协议适用于通用爬虫同样也适用于聚焦爬虫，而我们写的是聚焦爬虫
        * 査看方法:(网站url+/robots.txt)如(https://www.baidu.com/robots.txt)
* 网络模型
    * TCP/IP五层模型(无论在笔试还是面试中必须按顺序)
        * 应用层：https/http/ftp
        * 传输层：UDP/TCP
        * 网络层：IP
        * 数据链路层：ARP(了解)     
        * 物理层：以太网协议
    * HTTP与HTTPS协议的区别
        * https协议需要到ca申请证书，因而需要一定费用，现阶段国内各大云厂商也提供免费的证书。
        * http是超文本传输协议，信息是明文传输https则是具有安全性的ss1加密传输协议。
        * http和htps使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443
        * https的连接很简单，是无状态的HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全(尽管HTPS安全，但是传输的效率没有http高)
    * TCP与UDP
    * TCP协议:是一种面向连接的，可靠的，基于字节流的传输层通信协议
        * 有序性:数据包编号，判断数据包的正确次序
        * 正确性:使用 checksum!函数检查数据包是否损坏，发送接收时都会计算校验和
        * 可靠性:发送端有超时重发，并有确认机制识别错误和数据的丢失
        * 可控性:滑动窗口协议与拥塞控制算法控制数据包的发送速度
    * UDP协议:用户数据报协议，面向无连接的传输层协议，传输不可靠
        * 无连接，数据可能丢失或损坏
        * 报文小，传输速度快
        * 吞吐量大的网络传输，可以在一定程度上承受数据丢失
* 服务器常见端口(默认端口)
    * ftp:File Transfer Protoco1的缩写，即文件传输协议.端口:21
    * ssh: Secure She11的缩写，用于远程登录会话.端口:22
    * MYSQL:关系型数据库，端口:306
    * Mcngodb:非关系型数据库，端口:27017
    * Redis:非关系型数据库，端口:6379


* os模块
    * 作用：
        * OS模块简单的来说它是一个Python的系统编程的操作模块，可以处理文件和目录这些我们日常手动需要做的操作。
        * 在自动化测试中,经常需要查找操作文件,比如查找配置文件(从而读取配置文件的信息),查找测试报告等等,经常会对大量文件和路径进行操作,这就需要依赖os模块
    * os模块中常用的属性函数：
        * 1、os.getcwd()：查看当前所在目录（路径）
        ```
        import os
        print(os.getcwd())
        ```
        * os.chdir()：切换目录（路径）
        ```
        import os
        os.chdir(r'/etc/sysconfig/')
        print(os.getcwd())
        ```
        * os.curdir：返回当前目录字符串名、os.pardir：返回当前目录的父目录的字符串名
        ```
        import os
        print(os.curdir)
        print(os.pardir)
        ```
        * os.makedirs()：生成一个多层递归目录
        ```
        import os
        os.makedirs('/home/test/xuan')
        ```
        * os.removedirs()：若目录为空，则删除，并递归到上一级目录，如若也为空，则删除，依次类推
        ```
        import os
        os.removedirs('test/xuan')
        ```
        * os.mkdir()：创建一个目录
        ```
        import os
        os.mkdir('test')        #只能创建一个目录
        os.mkdir('abc/123/xxx')

        Traceback (most recent call last)：
        File "<stdin>", line 1, in <module>
        FileNotFoundError： [Errno 2] No such file or directory： 'abc/123/xxx'
        ```
        * os.rmdir()：删除一个目录，若目录不为空则无法删除，报错
        ```
        import os
        os.mkdir('test/abc')    #在test下创建一个abc；
        os.rmdir('test')        #无法删除test；
        Traceback (most recent call last)：
        File "<stdin>", line 1, in <module>
        OSError： [Errno 39] Directory not empty： 'test'
        os.rmdir('test/abc')    #可以删除abc，因为abc目录下为空；
        ```
        * os.listdir()：显示指定目录下，所有的文件和子目录，包括隐藏文件
        ```
        >>> import os
        dirs = os.listdir('/root')
        print(dirs)

        ['.bash_logout', '.bash_profile', '.cshrc', '.tcshrc', '.bashrc', 'full_stack', 'jf_blog', 'node-v8.9.4-linux-x64', '.bash_history', '.config', '.npm', '.pki', '.ssh', '.gitconfig', '.oracle_jre_usage', '.cache', '.python_history', 'douban', 'mysql57-community-release-el7-10.noarch.rpm', '.mysql_history', '.viminfo']
        ```
        * os.remove()：删除文件，不能删除文件夹
        * os.stat()：获取文件/目录信息,并可以获取到文件的大小
        ```
        >>> import os
        info = os.stat('/test')
        print(info)
        os.stat_result(st_mode=16877, st_ino=102688292, st_dev=64769, st_nlink=4, st_uid=0, st_gid=0, st_size=42, st_atime=1562827140, st_mtime=1562827137, st_ctime=1562827137)

        print(info.st_size)
        42
        ```
        * os.sep：输出操作系统特定的路径分隔符 ，如：windows 为‘\\’,Linux为‘/’
        ```
        import os
        s = os.sep
        print(s)

        /
        ```
        * os.pathsep：输出用于分割文件路径的字符串
        * os.system()：运行shell命令，直接显示（相当于启动一个全新的shell，然后去执行那条命令，命令执行完成过后，shell直接退出）
        ```
        import os
        print(os.system('ls /test/'))    #调用系统命令
        123  hello.txt	qwe
        0
        
        [root@server-7 test]# ls
        123  hello.txt  qwe
        ```
        * os.environ：获取操作系统的环境变量
        ```
        import os
        print(os.environ)

        environ({'XDG_SESSION_ID'： '3393', 'HOSTNAME'： 'server-7.dev', 'TERM'： 'xterm', 'SHELL'： '/bin/bash', 'HISTSIZE'： '1000', 'SSH_CLIENT'： '61.130.182.194 54987 22', 'SSH_TTY'： '/dev/pts/1', 'HISTFILESIZE'： '10000', 'JRE_HOME'： '/usr/java/jdk1.8.0_171/jre', 'USER'： 'root', 'JAVA_BIN'： '/usr/java/jdk1.8.0_171/bin', 'LS_COLORS'： 'rs=0：di=01;34：ln=01;36：mh=00：pi=40;33：so=01;35：do=01;35：bd=40;33;01：cd=40;33;01：or=40;31;01：mi=01;05;37;41：su=37;41：sg=30;43：ca=30;41：tw=30;42：ow=34;42：st=37;44：ex=01;32：*.tar=01;31：*.tgz=01;31：*.arc=01;31：*.arj=01;31：*.taz=01;31：*.lha=01;31：*.lz4=01;31：*.lzh=01;31：*.lzma=01;31：*.tlz=01;31：*.txz=01;31：*.tzo=01;31：*.t7z=01;31：*.zip=01;31：*.z=01;31：*.Z=01;31：*.dz=01;31：*.gz=01;31：*.lrz=01;31：*.lz=01;31：*.lzo=01;31：*.xz=01;31：*.bz2=01;31：*.bz=01;31：*.tbz=01;31：*.tbz2=01;31：*.tz=01;31：*.deb=01;31：*.rpm=01;31：*.jar=01;31：*.war=01;31：*.ear=01;31：*.sar=01;31：*.rar=01;31：*.alz=01;31：*.ace=01;31：*.zoo=01;31：*.cpio=01;31：*.7z=01;31：*.rz=01;31：*.cab=01;31：*.jpg=01;35：*.jpeg=01;35：*.gif=01;35：*.bmp=01;35：*.pbm=01;35：*.pgm=01;35：*.ppm=01;35：*.tga=01;35：*.xbm=01;35：*.xpm=01;35：*.tif=01;35：*.tiff=01;35：*.png=01;35：*.svg=01;35：*.svgz=01;35：*.mng=01;35：*.pcx=01;35：*.mov=01;35：*.mpg=01;35：*.mpeg=01;35：*.m2v=01;35：*.mkv=01;35：*.webm=01;35：*.ogm=01;35：*.mp4=01;35：*.m4v=01;35：*.mp4v=01;35：*.vob=01;35：*.qt=01;35：*.nuv=01;35：*.wmv=01;35：*.asf=01;35：*.rm=01;35：*.rmvb=01;35：*.flc=01;35：*.avi=01;35：*.fli=01;35：*.flv=01;35：*.gl=01;35：*.dl=01;35：*.xcf=01;35：*.xwd=01;35：*.yuv=01;35：*.cgm=01;35：*.emf=01;35：*.axv=01;35：*.anx=01;35：*.ogv=01;35：*.ogx=01;35：*.aac=01;36：*.au=01;36：*.flac=01;36：*.mid=01;36：*.midi=01;36：*.mka=01;36：*.mp3=01;36：*.mpc=01;36：*.ogg=01;36：*.ra=01;36：*.wav=01;36：*.axa=01;36：*.oga=01;36：*.spx=01;36：*.xspf=01;36：', 'MAIL'： '/var/spool/mail/root', 'PATH'： '/usr/java/jdk1.8.0_171/bin：/usr/local/sbin：/usr/local/bin：/usr/sbin：/usr/bin：/usr/local/bin：/usr/java/jdk1.8.0_171/jre/bin：/usr/local/node/bin：/root/bin', 'PWD'： '/home', 'JAVA_HOME'： '/usr/java/jdk1.8.0_171', 'LANG'： 'en_US.UTF-8', 'HISTCONTROL'： 'ignoredups', 'SHLVL'： '1', 'HOME'： '/root', 'GREP_OPTIONS'： '--color=auto', 'LOGNAME'： 'root', 'CLASSPATH'： '.：/usr/java/jdk1.8.0_171/lib/dt.jar：/usr/java/jdk1.8.0_171/lib/tools.jar', 'SSH_CONNECTION'： '61.130.182.194 54987 10.23.230.201 22', 'LESSOPEN'： '||/usr/bin/lesspipe.sh %s', 'XDG_RUNTIME_DIR'： '/run/user/0', 'HISTTIMEFORMAT'： '%Y-%m-%d %H：%M：%S ', '_'： '/usr/local/python3/bin/python3.6', 'OLDPWD'： '/root'})
        ```
        * os.path.split(path)：将path分割成目录和文件名二元组返回
        ```
        import os
        print(os.path.split('/test/123/abc'))

        ('/test/123', 'abc')
        ```
        * os.path.abspath(path)：返回path规范化的绝对路径
        ```
        import os
        print(os.path.abspath('abc'))

        /test/123/abc
        ```
        * os.path.dirname(path)：返回path的目录
        ```
        import os
        print(os.path.dirname('/test/123/abc'))
        
        /test/123
        ```
        * os.path.basename(path)：返回path最后的文件名（一个绝对路径只返回最后的文件名）
        ```   
        import os
        print(os.path.basename('abc'))
        abc

        print(os.path.basename('/test/123/abc'))
        abc
        ```
        * os.path.exists(path)：判断路径是否存在，如果path存在，返回True；如果不存在，返回Flase
        * os.path.isabs(path)：判断是否是绝对路径，如果是，则返回True
        * os.path.isfile(path)：判断是否是一个文件，如果是则返回True，否则返回False
        * os.path.isdir(path)：判断是否是一个存在的目录如果是则返回True，否则返回False
        * os.path.join(path1，[path2],[path3])：将路径和文件名分为一个列表中的两个元素，将它们拼起来，若其中有绝对路径,则之前的path将会被删除.
        ```
        import os
        print(os.path.join('/test/','hello.txt'))
        /test/hello.txt
        print(os.path.join('/test/123','hello.txt'))
        /test/123/hello.txt
        ```
        * os.path.getatime(path):返回path所指向的文件或者目录的最后存取时间;
        * os.path.getmtime(time):返回path所指向的文件或者目录的最后修改时间
        * os.popen('ls'):相当于打开了一个临时的文件存储打开的目录（可以赋给变量，字符串的形式)
        ```
        import os
        a = os.popen('ls').read()
        a
        'douban\nfull_stack\njf_blog\nmysql57-community-release-el7-10.noarch.rpm\nnode-v8.9.4-linux-x64\n'
        print(a)
        douban
        full_stack
        jf_blog
        mysql57-community-release-el7-10.noarch.rpm
        node-v8.9.4-linux-x64
        
        
        
        [root@server-7 ~]# ls -l
        total 32
        drwxr-xr-x 3 root root    36 Jun 23 19:51 douban
        drwxr-xr-x 2 root root    22 Jul 10 14:02 full_stack
        drwxr-xr-x 7 root root  4096 Jul  5 18:10 jf_blog
        -rw-r--r-- 1 root root 25548 Apr  7  2017 mysql57-community-release-el7-10.noarch.rpm
        drwxrwxr-x 7  500  500   111 Jun  5 15:04 node-v8.9.4-linux-x64
        ```




* sys模块
    * 概念：sys —— System-specific parameters and functions（系统特定的参数和功能）
    * sys模块的变量
        变量|	描述
        ---|:---
        sys.path	| 模块搜索路径 path[0] 是当前脚本程序的路径名，否则为 ''
        sys.modules	| 已加载模块的字典
        sys.version	| 版本信息字符串
        sys.version_info |	版本信息的命名元组
        sys.platform |	操作系统平台名称信息
        sys.argv	| 命令行参数 argv[0] 代表当前脚本程序路径名
        sys.copyright	| 获得Python版权相关的信息
        sys.builtin_module_names|	获得Python内建模块的名称（字符串元组）
        标准输入输出时会用到	 |  
        sys.stdin	| 标准输入文件对象，多用于input()
        sys.stdout |	标准输出文件对象,多用于print()
        sys.stderr | 	标准错误输出文件对象, 用于输出错误信息
    * sys模块的方法
        函数名|	描述
        ---|:---
        sys.exit([arg])	|退出程序，正常退出时sys.exit(0)
        sys.getrecursionlimit()	 |
        sys.getrecursionlimit()	|得到递归嵌套层次限制（栈的深度）
        sys.setrecursionlimit(n)|	得到和修改递归嵌套层次限制（栈的深度）
    * 例：
        ```
        #!/usr/bin/python3
        import sys
        
        # sys.argv是一个字符串序列
        print("参数的个数是：",len(sys.argv))
        print(sys.argv)
        for x in sys.argv:
            print("参数是：",x)
        ```
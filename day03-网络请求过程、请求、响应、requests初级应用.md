# day03
## *任务*
* 网络请求过程
* 请求
* 响应
* requests初级应用

## *笔记*
* 网络请求过程
    * URL介绍：URL请求的网址，即统一资源定位符，它可以唯一确定我们想请求的资源，其结构如下
        * https://www.baidu.com/s?wd=%E9%87%91%E9%92%88%E8%8F%87&rsv_spt=1
    * 请求过程：客户端，通常指web浏览器或APP向服务器发起请求，服务器接收请求进行处理，并向客户端发起响应
    * 用django做对比：用户访问yrl --> uwsgi --> 框架：urls.py --> 视图 -->响应 --> uwsgi --> 浏览器 --> 渲染

    * ![image](F:\积云\month06\day03\网络请求过程.png)
* 请求
    * 概念：由客户端向服务器发出的，可分为四部分内容：请求方法（Request  Method）,请求网址（Request URL）,请求头（Request Headers）,请求体（Request Body）
    * 请求方法
        - GET:请求页面，并返回页面内容 #重点
        - POST:用于提交表单数据上传文件，数据包含在请求体 #重点
        - PUT：从客户端向服务器传送的数据取代指定文档中的内容
        - DELETE：请求服务器删除指定页面
        - HEAD：类似于GET请求，只不过返回的响应中没有具体的内容，用于获取报头
        - CONNECT：把服务器当作跳板，让服务器代替客户端访问其他网页
        - OPTIONS:允许客户端查看服务器性能
        - TRACE：回显服务器收到请求，主要用于测试或诊断
    * 重点掌握GET和POST区别：
        * GET请求中的参数包含在URL里面，数据可以在URL中看到，而POST请求的URL不会包含这些数据，POST的数据都是通过表单形式传输的，会包含在请求体中
        * GET请求提交的数据最多只有1024字节，而POST方式没有限制
        * POST请求比GET请求相对安全
    * 请求头：用来说明服务器要使用的附加信息，重点掌握：Accept,Cookie,Referer,User-Agent,Host
        * Accept:请求报头域，用于指定客户端可接受哪些类型的信息 
        * Cookie：也常用于复数形式 Cookies，这是网站为了辨别用户进行会话跟踪而存储在用户本地的数据。它的主要功能是维持当前访问会话。
        * Referer：此内容用来标识这个请求是从那个页面发过来的，服务器可以拿到这一信息并做相应的处理，如作来源统计、防盗链处理等  
        * User-Agent：简称UA，它是特殊的字符串，可以使服务器识别客户使用的操作系统及版本、浏览器及版本等信息。在做爬虫时加上此信息，可以伪装为浏览器：如果不加，很可能会被识别出为爬虫 
        * x-requested-with：XMLHttpRequest #代表ajax请求
        * Accept-Language：指定客户端可接受的语言类型
        * Accept-Encoding：指定客户端可接受的内容编码
        * Content-Type：也叫互联网媒体类型（Internet Media Type）或者MIME类型，在HTTP协议信息头中，它用来表示具体请求中的媒体类型信息。例如，text/html代表HTML格式，image/gif代表GIF图片，application/json代表JSON类型
* 响应
    * 概念：是由服务器返回给客户端的，可以分为三部分：响应状态码（response status code），响应头（response headers），响应体（response body）
    * 响应状态码：用于判断请求后相应状态，如200代表成功，404代表页面找不到，500代表服务器错误
        ```
        100~199——信息性状态码
        100 Continue 说明收到了请求的初始部分，请客户端继续。
        101 Switching Protocols 说明服务器正在根据客户端的指定，将协议切换成Update首部所列的协议

        ​200~299——成功状态码
            200 OK 请求没问题。实体的主体部分 包含了请求的资源
        201 Created 用于创建服务器对象的请求（比如，PUT）
        202 Accepted 请求已被接受，但服务器还未对其执行任何动作。
        203 Non-Authoritative Information 实体首部包含信息不是来至于源端服务器，而是来自资源的一份副本。
        204 No Content 响应报文中包含若干首部和一个状态行，但没有实体的主体部分
        205 Reset Content 另一个主要用于浏览器的代码。负责告知浏览器清除当前页面中的所有HTML表单元素
        206 Partial Content 成功执行了一个部分或Range（范围）请求。

        ​300~399——重定向状态码
        300 Multiple Choices 客户端请求一个实际指向多个资源的URL时会返回这个状态码，比如服务器上有某个HTML文档的英语和法语版本，服务器可以在Location首部包含首选URL
        301 Moved Permanently 在请求的URL已被移除时使用，响应的Location首部中应该包含资源现在所处的URL
        302 Found 与301状态码类似，但是，客户端应该使用Location首部给出的URL来临时定位资源，将来的请求仍应使用老的URL
        303 See Other 告知客户端应该用另一个URL来获取资源
        304 Not Modified 客户端可以通过所包含的请求首部，使其请求变成有条件的，如果客户端发起了一个条件GET请求，而最近资源未被修改的话，就可以用这个状态码来说明资源未被修改
        305 Use Proxy 用来说明必须通过一个代理来访问资源，代理的位置由Location首部给出
        306 （未使用） 当前未使用
        307 Temporary Redirect 与301状态码类似，但客户端应该使用Location首部给出的URL来临时定位资源。将来的请求应该使用老的URL

        ​400~499——客户端错误状态码
        400 Bad Request 用于告诉客户端它发送了一个错误的请求
        401 Unauthorized 与适当的首部一同返回，在这些首部中请求客户端在获取对资源的访问权之前，对自己进行认证
        402 Payment Required 现在这个状态码还未使用，但已经被保留，以作未来之用
        403 Forbidden 用于说明请求被服务器拒绝了
        404 Not Found 用于说明服务器无法找到所请求的URL
        405 Method Not Allowed 发起的请求中带有所请求的URL不支持的方法时，使用此状态码
        406 Not Acceptable 客户端可以指定参数来说明它们愿意接收什么类型的实体，服务器没有与客户端可接受的URL相匹配的资源时，使用此代码
        407 Proxy Authentication Required 与401 状态类似，但用于要求资源进行认证的代理服务器
        408 Request Timeout 如果客户端完成请求所花的时间太长，服务器可以回送此状态码，并关闭连接
        409 Conflict 用于说明请求可能在资源上引发的一些冲突
        410 Gone 与404类似，只是服务器曾经拥有过此资源，主要用于Web站点的维护
        411 Length Required 服务器要求在请求报文中包含content-Length 首部时使用
        412 Precondition Failed 客户端发起了条件请求，且其中一个条件失败了的时候使用
        413 Request Entity Too Large 客户端发送的实体主体部分服务器能够或者希望处理的要大时，使用此状态码
        414 Request URl Too Long 客户端所发请求中的请求URL比服务器能够或者希望处理的要长时，使用此状态码
        415 Unsupported Media Type 服务器无法理解或无法支持客户端所发实体的内容类型时，使用此状态吗
        416 Requested Range Not Satisfiable 请求报文所请求的是指定资源的某个范围，而此范围无效或无法满足时，使用此状态码
        417 Expectation Failed 请求的Expect请求首部包含了一个期望，但服务器无法满足此期望时，使用此状态码

        ​500~599——服务器错误状态码
        500 Internal Server Error 服务器遇到一个妨碍它为请求提供服务的错误时，使用此状态码
        501 Not Implemented 客户端发起的请求超出服务器的能力范围（比如，使用了服务器不支持的请求方法）时，使用此状态码
        502 Bad Gateway 作为代理或网关使用的服务器从请求响应链的下一条链路上收到了一条伪响应（比如，它无法连接到其父网关）时，使用此状态码
        503 Service Unavailable 用来说明服务器现在无法为请求提供服务，但将来可以。
        504 Gateway Timeout 与状态码408类似，只是这里的响应来自一个网关或代理，它们在等待另一服务器对其请求进行响应时超时了
        505 HTTP Version Not Supported 服务器收到的请求使用了它无法或不愿支持的协议版本时，使用此状态码
        ```
        *注意：状态码不能完全代表相应状态，部分网站的状态码时自定义的，一切以响应的数据为准*
    * 响应头:响应头包含了服务器对请求的应答信息
        * Date：标识相应产生的时间
        * Content-Encoding：指定响应内容的编码
        * Server：包含服务器的信息，比如名称、版本号等。
        * Content-Type：文档类型，指定返回的数据类型是什么，如text/html代表返回HTML文档
        * application/x-javascript则代表返回JavaScript文件，image/jpeg则代表返回图片
        * Set-Cookie：设置Cookies。响应头中的Set-Cookie告诉浏览器需要将此内容放在Cookies中，下次请求携带Cookies请求。
        * Expires：指定响应的过期时间，可以使代理服务器或浏览器将加载的内容更新到缓存中，如果再次访问时，就可以直接从缓存中加载，降低服务器负载，缩短加载时间。
    * 响应体：最重要的当属响应体的内容了。响应的正文数据都在响应体中，比如请求网页时，它的响应体就是网页的HTML代码:请求一张图片时，它的响应体就是图片的二进制数据。我们做爬虫请求网页后，要解析的内容就是响应体
* 网页组成：网页可以分为三部分，HTML、CSS、JavaScript
    * HTML：其全称为Hyper Text Markup Language.即超文本标记语言，定义网页的骨架
    * CSS：全称为Cascading Style Sheets.即层叠样式表
    定义了网页的样式
    * JavaScript：简称JS，是一种脚本语言
    定义了网页与用户的交互行为，如下载进度条、提示框、轮播图
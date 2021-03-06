#图解HTTP
##第一章 了解Web及网络基础  
###1.1 使用HTTP协议访问Web
###1.2 HTTP的诞生
- 1.2.1 为知识共享而规划Web
- 1.2.2 Web成长时代
- 1.2.3 驻足不前的HTTP  
 ###1.3 网络基础TCP/IP
- 1.3.1 TCP/IP协议族
- 1.3.2 TCP/IP的分层管理  
TCP/IP协议族里最重要的一点就是分层。TCP/IP协议族按层次分别分为以下4层：应用层、传输层、网络层、数据链路层。  

###1.4 与HTTP关系最密切的协议：IP、TCP和DNS
- 1.4.1 负责传输的IP协议
- 1.4.2 确保可靠性的TCP协议  
为了准确无误地将数据送达目标处，TCP协议采用了三次握手策略。  
1:发送端首先发送一个带SYN标志的数据包给对方。  
2:接收方收到后，回传一个带有SYN/ACK标志的数据包以示确认信息。   
3:发送端再回传一个带ACK标志的数据包，代表”握手“结束  

###1.5 负责域名解析的DNS服务
DNS（Domain Name System）服务和HTTP协议一样位于应用层， 它提供域名到IP地址之间的解析服务。  
###1.6 各种协议与HTTP协议的关系
###1.7 URI和URL
- 1.7.1统一资源标志符（Uniform Resource Identifier）  
- 1.7.2 URI格式：  
http://user:pass@www.example.jp:80/dir/index.html?uid=1#ch1  
http://： 协议方案名  
user:pass: 登录信息（认证）  
www.example.jp:服务器地址  
80:服务器端口号  
dir/index.html:带层次结构的文件路径  
uid:查询字符串  
ch1:片段标志符  

##第二章 简单的HTTP协议  
###2.1 HTTP协议用于客户端和服务端之间的通信  
###2.2 通过请求和响应的交换达成通信  
###2.3 HTTP是不保存状态的协议  
###2.4 请求URI定位资源  
###2.5 告知服务器意图的HTTP方法  
- GET：获取资源
- POST：传输实体主体
- PUT：传输文件
- HEAD：获得报文首部
- DELETE：删除文件
- OPTIONS：查询支持的方法
- TRACE：追踪路径
- CONNECT：要求使用隧道协议连接代理  
  
###2.6 使用方法下达命令
###2.7 持久连接节省通信量
- 2.7.1 持久连接
- 2.7.2 管线化  
持久连接使得多数请求以管线化方式发送请求成为可能。从前发送请求后需要等待并收到响应，才能发送下一次请求。管线化技术出现后，不用等待响应亦可以直接发送下一个请求。这样就可以做到同时并行发哦送多个请求，而不需要一个接一个地等待响应了。   

###2.8 使用Cookie的状态管理

##第三章 HTTP报文内部的HTTP信息
###3.1HTTP报文  
HTTP报文大致可分为报文首部和报文主体两块。两者由最初出现的空行（CR+LF）来划分。并不一定要有报文主体。  
###3.2请求报文及响应报文的结构  
###3.3编码提升传输速率  
- 3.3.1报文主体和实体主体的差异  
报文（message）：是HTTP通信中的基本单位，由8位组字节流组成，通过HTTP通信传输；   
实体（entity）：作为请求或响应的有效载荷数据（补充项）被传输，器内容由实体首部和实体主体组成。  
HTTP报文的主体用于传输请求或者响应的实体主体。  
通常，报文主体等于实体主体。只有当传输过程中进行编码操作时，实体主体的内容发生变化，才导致他和报文主体产生差异。  

- 3.3.2 压缩传输的内容编码 
- 3.3.3 分割发送的分块传输编码   
 
###3.4 发送多种数据的多部分对象集合  
###3.5 获取部分内容的范围请求
###3.6 内容协商返回最合适的内容  
##第四章 返回结果的HTTP状态码
###4.1 状态码告知从服务器返回的请求结果 
状态码的类别：    
1XX:  Informational(信息性状态码); 接收的请求正在处理    
2XX:  Sucess(成功状态码);  请求正常处理完毕     
3XX:  Redirection（重定向状态码）;  需要附加操作以完成请求    
4XX:  Client Error（客户端错误状态码）;  服务器无法处理请求  
5XX:  Server Error（服务器错误状态码）;  服务器处理请求出错  
###4.2 2XX成功
- 200：OK
- 204：No Content
- 206：Partial Content  
  
###4.3 3XX重定向  
- 301：Moved Permanently(永久性重定向)
- 302：Found（临时重定向)
- 303：See Other （资源存在另一个URI，应使用GET方法获取）
- 304：Not Modified (不满足附带条件)  
- 307：Temporary Redirect(临时重定向，不会从POST变为GET)  

###4.4 客户端错误 
- 400： Bad Request (请求报文语法错误)
- 401： Unauthorized (需要认证)
- 403： Forbidden (禁止访问)
- 404： Not Found (找不到资源or服务器拒绝请求而不想说明原因)  

###4.5 服务器错误  
- 500： Internal Server Error （服务器内部错误）
- 503： Server Unavailable （服务器超负载）  

##第五章 与HTTP协作的Web服务器
###5.1 用单台服务器虚拟主机实现多个域名  
###5.2 通信数据转发程序:代理、网关、隧道
###5.3 保存资源的缓存

##第六章 HTTP首部
###6.1 HTTP报文首部  
###6.2 HTTP首部字段
###6.3 HTTP/1.1通用首部字段  
- Cache-Control（缓存控制）
- Connection （控制不再转发+管理持久连接）
- Date（报文创建的日期和时间）
- Pragma（历史遗留，仅作为HTTP/1.0的向后兼容而定义）
- Trailer（报文主体后记录了哪些字段）
- Transfer-Encoding（传输编码方式）
- Upgrade（检测HTTP协议及其其他协议是否可使用更高的版本通信）
- Via（追踪客户端和服务端之前的请求和响应报文的传输路径）
- Warning（与缓存相关相关的问题的警告）  
 
###6.4 请求首部字段  
- Accept（可通知服务器，用户代理你能够股处理的媒体类型及媒体类型的相对优先级）
- Accept-Charset（可通知服务器用户代理支持的字符集及字符集的相对优先顺序）  
- Accept-Encoding（首部字段用来告知服务器用户代理支持的内容编码及内容编码的优先级顺序）
- Accept-Language（用来告知服务器代理能够处理的自然语言集），以及自然语言的相对优先级。
- Authorization（用来告知服务器，用户代理的认证信息）
- Expect（告知服务器，期望出现的某种特定行为）
- Form（告知服务器使用代理的用户的电子邮件地址）
- Host（告知服务器，请求的资源所处的互联网主机名和端口号）
- If-Match（条件请求，服务器接收到附带条件的请求后，只有判断条件为真时，才会执行请求）
- If-Modified-Since（附带条件之一，它会告知服务器若If-Modified-Since）字段早于资源更新时间，则希望能处理该请求）
- If-None-Match（只有和If-Match相反，用于指定If-None-Match字段值的实体标记ETag值与请求资源的ETag不一致时，告知服务器处理该请求）
- If-Range（若指定的If-Range字段值和请求资源的ETag值或时间一致时，作为范围请求处理，反之，则返回全体资源）
- If-Unmodified-Since（和If-Modified-Since作用相反。它的作用是告知服务器，指定的请求资源只有在字段值内指定的日期之后，未发生更新的情况下，才能处理请求。如果在指定日期时间发生了更新，则以状态码412Precondition Failed作为响应返回）
- Max-Forwards (通过TRACE方法或者OPTIONS方法，发送包含首部字段的Max-Forwards)的请求时，该字段以十进制整数形式指定可经过的服务器最大数目。服务器在往下一个服务器转发请求之前，Max-Fawords的值减1后重新赋值。当服务器接收到Max-Forwards值为0的请求时，则不再进行转发，而是直接响应请求
- Proxy-Authorization（接收到从代理服务器发来的认证质询时，客户端会发送包含首部字段Proxy-Authorization的请求，以告知服务器认证所需要的信息）
- Range（只需要获取部分资源的范围请求，包含Range字段可告知服务器资源的指定范围；接收到附带Range首部字段请求的服务器，会在处理请求之后返回状态码为206的响应，无法处理改范围请求是，则会返回状态码200的响应以及全部资源。）
- Refer（Refer会告知服务器请求的原始资源的URI）
- TE（告知服务器客户端能够处理响应的传输编码方式及相对优先级。他和Accept-Encoding的功能很相像，但是用于传输编码。此外，TE还可以指定伴随trailer字段的分块传输编码的方式。应用于后者时，只需要把trailers赋值给该字段值。）
- User-Agent（用于传达浏览器的种类）  

###6.5 响应首部字段 
- Accept-Range（告知客户端服务器是否能处理范围请求，以指定获取服务器某个部分的资源）
- Age（告知客户端，源服务器在多久之前创建了响应，单位为秒）
- ETag（告知客户端实体标识）
- Location（将响应接收方引导至某个与请求URI位置不同的资源，它会配合3XX:Redirection的响应，提供重定向的URI）
- Proxy-Authenticate（把由代理服务器所要求的认证信息发送给客户端）
- Retry-After（告知客户端应该在多久之后再次发送请求）
- Server（告知客户端当前服务器上安装的HTTP服务器应用程序的信息，不单单会标出服务器上的软件应用名称，还可能包括版本号和安装时启用的可选项）
- Vary（当代理服务器接收到带有Vary首部字段指定获取资源的请求时，如果使用的Accept-Language字段值相同，那么就直接从缓存返回响应。反之，则需要从源服务器获取资源后才能作为响应返回）
- WWW-Authenticate(用于HTTP访问认证)

###6.6 实体首部字段  
- Allow（通知客户端能够支持Request-URI指定资源的所有HTTP方法。当服务器接收到不支持的HTTP方法时，会以状态码405 Method Not Allowed作为响应返回。与此同时，还会把所有能支持的HTTP方法写入首部字段Allow后返回）
- Content-Encoding（告知客户端服务器对实体的主体部分选用的内容编码方式。内容编码是指在不丢失实体信息的前提下进行的压缩）
- Content-Language（告知客户端，实体主体使用的自然语言）
- Content-Length（表明实体主体部分的大小）
- Content-Location（给出与实体主体部分相对应的URI。和首部字段Location不同，Content-Location表示的是报文主体返回资源对应的URI。）
- Content-MD5（由MD5算法生成的值，目的在于检查报文主体在传输过程中是否保持完整，以确认传输到达）
- Content-Range（针对范围请求，返回响应时使用的Content-Range，能告知客户端作为响应返回的实体的哪个部分符合范围请求，以字节为单位，表示当前发送部分及整个实体的大小）
- Content-Type（说明了实体主体内对象的媒体类型，和首部字段Accept一样，字段用type/subtype形式赋值）
- Expires（将资源失效的日期告知客户端）
- Last-Modified（指明资源最终修改的时间）

### 6.7为Cookie服务的首部字段
- Set-Cookie
- Cookie

### 6.8其他首部字段
- X-Frame-Options（属于HTTP响应首部，用于控制网站内容在其他Web网站的Frame标签内的显示问题。主要是为了防止点击劫持攻击）
- X-XSS-Protection（属于HTTP响应首部，是针对跨站脚本攻击的一种对策，用于控制浏览器XXS防护机制的开关）
- DNT（属于HTTP请求首部，DNT是Do Not Track的简称，意为拒绝个人信息被收集，是表示拒绝被精准广告追踪的一种方法）
- P3P（属于HTTP响应首部，通过利用P3P（The Platform for Privacy Preferences，在线隐私偏好平台技术）让Web网站上的个人隐私变成一种仅供程序可理解的形式，达到保护用户隐私的目的）

##第七章 确保Web安全的HTTPS
###7.1 HTTP的缺点
HTTP的不足： 

- 通信使用明文（不加密），内容可能遭遇窃听
- 不验证通信方身份，有可能遭遇伪装
- 无法证明报文的完整性，有意有可能已遭篡改

###7.2 HTTP + 加密 + 认证 + 完整性保护 = HTTPS  
- HTTP加上加密处理和认证以及完整性保护后即是HTTPS  
- HTTP是身披SSL外壳的HTTP  
HTTPS并非应用层的一种新协议。只是HTTP通信接口部分用SSL（Secure Socket Layer）和TLS（Transport Layer Security）协议代替而已。  
通常，HTTP直接和TCP通信，当使用SSL时，则先演变成先和SSL通信，再由SSL和TCP通信了，简言之，所谓HTTPS，其实就是身披SSL协议这层外壳的HTTP。  
在采用SSL后，HTTP就拥有了HTTPS的加密、认证和完整性保护的功能了。  
- 相互交换密钥的公开密钥加密技术  
- 证明公开密钥正确性的证书  
- HTTPS的安全通信机制  

##第八章 确认访问用户身份的认证
###8.1 何为认证  
核对信息通常是这些：  

- 密码：只有本人才会知道的字符串信息
- 动态令牌：仅限本人持有的设备内显示的一次性密码
- 数字证书：仅限本人（终端）持有的信息
- 生物认证：指纹和虹膜等本人的生理信息
- IC卡认证：仅限本人持有的信息  

HTTP使用的认证方式：
- BASIC认证（基本认证）
- DIGEST认证（摘要认证）
- SSL客户端认证
- FormBase认证（表单认证）
###8.2 BASIC认证  
step1：当请求的资源需要BASIC认证时，服务器会随状态码401 Authorization Requested，返回带WWW-Authenticate首部字段的响应。该字段包含认证方式（BASIC）及Request-URI安全域字符串（realm）。
  
step2：接收到状态码401的客户端为了通过BASIC认证，需要将用户ID和密码发送给服务器。发送的字符串内容是有用户ID和密码构成，中间以冒号连接后，再经由 Base64编码处理。  

step3：接收到包含首部字段Authorization请求的服务器，会对认证信息进行验证。验证通过，则返回一条包含Request-URI资源的响应。  
###8.3 DIGEST认证
step1：当请求的资源需要BASIC认证时，服务器会随状态码401 Authorization Requested，返回带WWW-Authenticate首部字段的响应。该字段包含质问响应方式认证所需的临时质询码（随机数，nonce）。  
首部字段WWW-Authenticate内必须包含realm和nonce这两个字段的信息，客户端就是依靠向服务端回送这两个值进行认证的。  
  
step2：接收到状态码401的客户端，返回的响应中包含DIGEST认证必须的首部字段Authorization信息。  
首部字段Authorization内必须包含username、realm、nonce、uri和response的字段信息。其中，realm和nonce就是之前从服务器接收到的响应中的字段。  
username是realm限定范围内可进行认证的用户名。  

step3:接收到包含首部字段Authentication请求的服务器，会确认认证信息的正确性。认证通过后则返回包含Request-URI资源的响应。
###8.4 SSL客户端认证
- SSL客户端认证步骤  
 
	step1：接收到需要认证资源的请求，服务器会发送Certificate Request报文，要求客户端提供客户端证书。  

	step2：用户选择将客户端证书后，客户端会把客户端证书信息以Client Certificate报文方式发送给服务器。  

	step3：服务器验证客户端证书通过以后可领取证书内容客户端的公开密钥，然后开始HTTPS加密通信  
- SSL客户端认证采用双因素认证  
- SSL客户端认证必要的费用

###8.5 基于表单认证
基于表单认证的方法并不是在HTTP协议中定义的，客户端会向服务器上的Web应用程序发送登录信息，按登录信息的验证结果认证。  
- 认证多半为基于表单认证
- Session管理及Cookie应用

##第九章
###9.1 基于HTTP的协议
###9.2 消除HTTP瓶颈的SPDY
- HTTP的瓶颈  
1、一条连接只可以发送一个请求  
2、请求只能从客户端发出  
3、请求/响应首部未经压缩就发送。首部信息越多延迟越大  
4、发送冗长的首部，每次互相发送相同的首部造成的浪费较多    
5、可任意选择数据压缩的格式。非强制压缩发送  
Ajax的解决方法:有效利用JavaScript和DOM（Document Object Model）的操作，以达到局部Web页面替换加载的异步通信手段。  
Commet的解决方法:一旦服务器有内容更新了，Comet不会让请求等待，而是直接给客户端返回响应。这是一种通过延迟应答，模拟实现服务器向客户端推送（Server Push）的功能。  
- SPDY的设计与功能  
SPDY没有完全改写HTTP协议，而是在TCP/IP的应用层和传输层之间通过新加会话层的形式运作。同时，考虑到安全性的问题，SPDY规定通信中使用SSL。  
1、多路复用  
2、赋予请求优先级  
3、压缩HTTP首部  
4、推送功能  
5、服务器提示功能  
- SPDY消除Web瓶颈了吗
SPDY基本只是将单个域名（IP地址）的通信多路复用，所以当一个web网站上使用多个域名下的资源，改善效果会受到限制。  
SPDY的确是一种可有效消除HTTP瓶颈的技术，但很多Web网站存在的问题并非仅仅是由HTTP瓶颈所导致。对web本身的速度提升，还应该从其他可细致钻研的地方入手，比如改善Web内容的编写方式。  
###9.3 使用浏览器进行全双工通信的WebSocket
- WebSocket的设计与功能  


  
   



# HTTP协议相关

## request请求

|       Accept        | 指定浏览器或其他客户端可以处理的MIME类型。它的值通常为 **image/png** 或 **image/jpeg** |
| :-----------------: | :--------------------------------------: |
|   Accept-Charset    |        指定浏览器要使用的字符集。比如 ISO-8859-1        |
|   Accept-Encoding   |   指定编码类型。它的值通常为 **gzip** 或**compress**   |
|   Accept-Language   | 指定客户端首选语言，servlet会优先返回以当前语言构成的结果集，如果servlet支持这种语言的话。比如 en，en-us，ru等等 |
|    Authorization    |           在访问受密码保护的网页时识别不同的用户            |
|     Connection      | 表明客户端是否可以处理HTTP持久连接。持久连接允许客户端或浏览器在一个请求中获取多个文件。**Keep-Alive** 表示启用持久连接 |
|   Content-Length    |        仅适用于POST请求，表示 POST 数据的字节数         |
|       Cookie        |          返回先前发送给浏览器的cookies至服务器          |
|        Host         |             指出原始URL中的主机名和端口号             |
|  If-Modified-Since  | 表明只有当网页在指定的日期被修改后客户端才需要这个网页。 服务器发送304码给客户端，表示没有更新的资源 |
| If-Unmodified-Since | 与If-Modified-Since相反， 只有文档在指定日期后仍未被修改过，操作才会成功 |
|       Referer       | 标志着所引用页面的URL。比如，如果你在页面1，然后点了个链接至页面2，那么页面1的URL就会包含在浏览器请求页面2的信息头中 |
|     User-Agent      |   用来区分不同浏览器或客户端发送的请求，并对不同类型的浏览器返回不同的内容   |

<br/>

<br/>

## HttpServletRequest类

requet对象是javax.servlet.http.HttpservletRequest类的实例。

| **Cookie[] getCookies()**返回客户端所有的Cookie的数组 | **Enumeration getAttributeNames()**返回request对象的所有属性名称的集合 | **Enumeration getHeaderNames()**返回所有HTTP头的名称集合 |
| :--------------------------------------: | :--------------------------------------: | :--------------------------------------: |
| **Enumeration getParameterNames()**返回请求中所有参数的集合 | **HttpSession getSession()**返回request对应的session对象，如果没有，则创建一个 | **HttpSession getSession(boolean create)**返回request对应的session对象，如果没有并且参数create为true，则返回一个新的session对象 |
| **Locale getLocale()**返回当前页的Locale对象，可以在response中设置 | **Object getAttribute(String name)**返回名称为name的属性值，如果不存在则返回null。 | **ServletInputStream getInputStream()**返回请求的输入流 |
| **String getAuthType()**返回认证方案的名称，用来保护servlet，比如 "BASIC" 或者 "SSL" 或 null 如果 JSP没设置保护措施 | **String getCharacterEncoding()**返回request的字符编码集名称 | **String getContentType()**返回request主体的MIME类型，若未知则返回null |
| **String getContextPath()**返回request URI中指明的上下文路径 | **String getHeader(String name)**返回name指定的信息头 | **String getMethod()**返回此request中的HTTP方法，比如 GET,，POST，或PUT |
| **String getParameter(String name)**返回此request中name指定的参数，若不存在则返回null | **String getPathInfo()**返回任何额外的与此request URL相关的路径 | **String getProtocol()**返回此request所使用的协议名和版本 |
| **String getQueryString()**返回此 request URL包含的查询字符串 |   **String getRemoteAddr()**返回客户端的IP地址   |   **String getRemoteHost()**返回客户端的完整名称   |
| **String getRemoteUser()**返回客户端通过登录认证的用户，若用户未认证则返回null | **String getRequestURI()**返回request的URI  | **String getRequestedSessionId()**返回request指定的session ID |
| **String getServletPath()**返回所请求的servlet路径 | **String[] getParameterValues(String name)**返回指定名称的参数的所有值，若不存在则返回null | **boolean isSecure()**返回request是否使用了加密通道，比如HTTPS |
| **int getContentLength()**返回request主体所包含的字节数，若未知的返回-1 | **int getIntHeader(String name)**返回指定名称的request信息头的值 |     **int getServerPort()**返回服务器端口号      |

<br/>

<br/>

## respose响应

|        Allow        |      指定服务器支持的request方法（GET，POST等等）       |
| :-----------------: | :--------------------------------------: |
|    Cache-Control    | 指定响应文档能够被安全缓存的情况。通常取值为 **public****，****private** 或**no-cache** 等等。 Public意味着文档可缓存，Private意味着文档只为单用户服务并且只能使用私有缓存。No-cache 意味着文档不被缓存 |
|     Connection      | 命令浏览器是否要使用持久的HTTP连接。**close****值** 命令浏览器不使用持久HTTP连接，而keep-alive 意味着使用持久化连接 |
| Content-Disposition |         让浏览器要求用户将响应以给定的名称存储在磁盘中          |
|  Content-Encoding   |               指定传输时页面的编码规则               |
|  Content-Language   |       表述文档所使用的语言，比如en， en-us,，ru等等       |
|   Content-Length    | 表明响应的字节数。只有在浏览器使用持久化 (keep-alive) HTTP 连接时才有用 |
|    Content-Type     |              表明文档使用的MIME类型               |
|       Expires       |              指明啥时候过期并从缓存中移除              |
|    Last-Modified    | 指明文档最后修改时间。客户端可以 缓存文档并且在后续的请求中提供一个 **If-Modified-Since**请求头 |
|      Location       | 在300秒内，包含所有的有一个状态码的响应地址，浏览器会自动重连然后检索新文档  |
|       Refresh       |            指明浏览器每隔多久请求更新一次页面。            |
|     Retry-After     | 与503 (Service Unavailable)一起使用来告诉用户多久后请求将会得到响应 |
|     Set-Cookie      |             指明当前页面对应的cookie              |

<br/>

<br/>

## HttpServletResponse

| **String encodeRedirectURL(String url)**对sendRedirect()方法使用的URL进行编码 | **String encodeURL(String url)**将URL编码，回传包含Session ID的UR | **boolean containsHeader(String name)**返回指定的响应头是否存在 |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| **boolean isCommitted()**返回响应是否已经提交到客户端  | **void addCookie(Cookie cookie)**添加指定的cookie至响应中 | **void addDateHeader(String name, long date)**添加指定名称的响应头和日期值 |
| **void addDateHeader(String name, long date)**添加指定名称的响应头和日期值 | **void addHeader(String name, String value)**添加指定名称的响应头和值 | **void addIntHeader(String name, int value)**添加指定名称的响应头和int值 |
| **void flushBuffer()**将任何缓存中的内容写入客户端     | **void reset()**清除任何缓存中的任何数据，包括状态码和各种响应头 | **void resetBuffer()**清除基本的缓存数据，不包括响应头和状态码 |
| **void sendError(int sc)**使用指定的状态码向客户端发送一个出错响应，然后清除缓存 | **void sendError(int sc, String msg)**使用指定的状态码和消息向客户端发送一个出错响应 | **void sendRedirect(String location)**使用指定的URL向客户端发送一个临时的间接响应 |
| **void setBufferSize(int size)**设置响应体的缓存区大小 | **void setCharacterEncoding(String charset)**指定响应的编码集（MIME字符集），例如UTF-8 | **void setContentLength(int len)**指定HTTP servlets中响应的内容的长度，此方法用来设置 HTTP Content-Length 信息头 |
| **void setContentType(String type)**设置响应的内容的类型，如果响应还未被提交的话 | **void setDateHeader(String name, long date)**使用指定名称和值设置响应头的名称和内容 | **void setHeader(String name, String value)**使用指定名称和值设置响应头的名称和内容 |
| **void setIntHeader(String name, int value)**使用指定名称和值设置响应头的名称和内容 | **void setLocale(Locale loc)**设置响应的语言环境，如果响应尚未被提交的话 | **void setStatus(int sc)**设置响应的状态码       |

<br/>

<br/>

### 状态码

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fhns4zl9lyj30hj0dv0uu.jpg)

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fhns62t2h6j30ht0duwgp.jpg)

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fhns6vk8wyj30g30duacm.jpg)

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fhns9kys4vj30hs0c8q55.jpg)


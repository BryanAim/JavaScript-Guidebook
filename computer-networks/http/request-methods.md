# HTTP 请求方法

HTTP 定义了一组请求方法，以表明对给定资源执行的操作。

| 请求方法 | 说明                                     |
| -------- | ---------------------------------------- |
| GET      | 主要用于获取信息资源                     |
| HEAD     | 获取报文首部                             |
| POST     | 传输实体文本（主要用于修改服务器上资源） |
| PUT      | 用于传输文件                             |
| DELETE   | 删除文件                                 |
| CONNECT  | 要求用隧道协议连接代理                   |
| OPTIONS  | 询问支持的方法                           |
| TRACE    | 追踪路径                                 |
| PATCH    | 用于对资源应用部分修改                   |

## GET与POST

实际上 HTTP 协议从未规定 GET/POST 的请求长度限制是多少。对 GET 请求参数的限制是来源与浏览器或 Web 服务器，浏览器或 Web 服务器限制了 URL 的长度。为了明确这个概念，我们必须再次强调下面几点：

* HTTP 协议 未规定 GET 和 POST 的长度限制
* GET 的最大长度显示是因为 浏览器和 Web 服务器限制了 URI 的长度
* 不同的浏览器和 Web 服务器，限制的最大长度不一样
* 要支持 IE，则最大长度为 2083byte，若只支持 Chrome，则最大长度 8182byte

**性质**

* GET 请求类似于查找的过程，用户获取数据，可以不用每次都与数据库连接，所以可以使用缓存。
* POST 不同，POST 做的一般是修改和删除的工作，所以必须与数据库交互，所以不能使用缓存。因此 GET 请求适合于请求缓存。

**区别**

| GET                                       | POST                   |
| ----------------------------------------- | ---------------------- |
| 明文传输，通过 URL 传递（不能传敏感信息） | 密文传输，置于请求体中 |
| 受浏览器 URL 长度限制，传输数据量有限     | 不受限                 |
| 参数只能是 ASCII 码，中文需要 URL 编码    | 没有限制               |
| GET 请求参数会完整保留在浏览器记录中      | 不会保留               |
| GET 请求会被浏览器主动缓存                | 不会主动缓存           |

GET 传输数据量限制在 2KB（GET 是通过 URL 提交数据，而 URL 本身对于数据没有限制，但是不同的浏览器对于 URL 是有限制的，比如 IE 浏览器对于 URL 的限制为 2KB，而 Chrome，FireFox 浏览器理论上对于 URL 是没有限制的，它真正的限制取决于操作系统本身），而 POST 对于数据大小是无限制的（真正影响到数据大小的是服务器处理程序的能力）

---

**参考资料：**

* [HTTP 请求方法详解](https://www.cnblogs.com/foodoir/p/5911099.html)
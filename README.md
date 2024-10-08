# WsTextSync

有些时候需要在多个设备之间快速的共享文本（例如PC和VR头显），通过打开浏览器并访问一个使用websocket协议的网页似乎是个不错的办法。

这个程序使用了来自<https://www.dariawan.com/tutorials/spring/spring-boot-websocket-basic-example/>的例子代码。

## 服务端运行方法

1. 安装JDK（1.8或更高版本）。

1. 使用```java -jar```运行构建好的服务程序。例如：

    ```bash
    java -jar demo-0.0.1-SNAPSHOT.jar
    ```

1. 服务程序默认运行在8080端口，如需更改端口号，可参考SpringBoot配置方法进行修改。例如在命令行中加入server.port参数。

    ```bash
    java -jar demo-0.0.1-SNAPSHOT.jar --server.port=80
    ```

1. 服务器默认支持不超过8KiB的文本消息，这个限制可以通过启动时传入指定的大小参数来修改。例如下面的启动参数可以改为640KiB：

    ```bash
    java -Dorg.apache.tomcat.websocket.DEFAULT_BUFFER_SIZE=655360 -jar demo-0.0.1-SNAPSHOT.jar
    ```

## 客户端使用方法

1. 打开浏览器，访问服务器地址，例如：```http://192.168.31.104:8080```。如果服务器上有之前已缓存的信息，会立刻将缓存的信息发送到浏览器，浏览器打开页面的同时就可以看到这些信息他。

1. 在浏览器的文本框内输入文字时将触发input事件，此时浏览器中的脚本程序会将文本框内的内容发送到服务器，服务器将文本内容缓存下来并同步发送到所有打开该页面的浏览器。

# Wireshark 中的 HTTP 请求包和响应包的对应方式
![http-01.png](./images/http-01.png 'http-01.png')

比如要查看下图中编号是 134829 请求的响应包，有以下三种方式：

## 方式一、通过传输控制协议（Transmission Control Protocol）信息识别
1. 打开编号是 134829 的请求信息，点击传输层控制协议（Transmission Control Protocol），然后找到 "[Next Sequence Number: 7171    (relative sequence number)]"
![http-02.png](./images/http-02.png 'http-02.png')

2. 依次查看列表里后续响应信息的传输层控制协议（Transmission Control Protocol）的 "Acknowledgment Number" 字段，找到值是 7171 的响应信息
![http-03.png](./images/http-03.png 'http-03.png')

3. 此时，编号是 135058 的包就是 134829 请求的响应包

## 方式二、通过超文本传输协议（Hypertext Transfer Protocol）信息识别
1. 打开编号是 134829 的请求信息，点击超文本传输协议（Hypertext Transfer Protocol），然后找到 "[Response in frame: 135058]"
![http-04.png](./images/http-04.png 'http-04.png')

2. 双击 "[Response in frame: 135058]" ，可直接跳转到编号是 135058 的响应包，确认响应包的超文本传输协议（Hypertext Transfer Protocol）的 "[Request in frame: 134829]" 字段值，即编号是 134829 的请求包
![http-05.png](./images/http-05.png 'http-05.png')

## 方式三、通过 Wireshark 的请求应响应记识别
这种方式最简单，红框中朝右指向的箭头代表的是请求，绿框中朝左指向的箭头代表的是响应。

![http-06.png](./images/http-06.png 'http-06.png')

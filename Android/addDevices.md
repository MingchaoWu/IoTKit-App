# 添加设备

1.JFG 设备绑定的逻辑。

* 扫描出设备发出的SSID。比如：DOG-000015。前缀以 DOG- 开头。
* 连接上此设备WIFI。可以自行实现，不必使用sdk中的方式.
* 在onLocalMessage中接收此类UDP消息。
* 连接成功后，发送ping 命令。
* 接收且解析到ping_ack。（使用msgpack 包解析。）然后发送fping 命令。
* 接收且解析到fping_ack。

* 发送 _setServerAddress_ 、_setLanguage_

* 最后发送 setWifiCfg ，收到此命令后，设备会关闭AP模式。
* 手机连接回正常网络。
* 登录，登录成功后发送绑定设备的消息。
```java
  JfgAppCmd.getInstance().bindDevice(cid, "abcdef");
```
 后面那个参数填入一个随机数，为后面设备升级预留的接口。
* 在onResult 中判断绑定事件与绑定结果。


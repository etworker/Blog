# iOS集成SIP功能

## 下载doubango/idoubs代码

```
$ mkdir mydoubs
$ cd mydoubs
$ git clone https://github.com/DoubangoTelecom/doubango.git doubango
$ git clone https://github.com/DoubangoTelecom/idoubs.git idoubs
```

## 编译代码

### ios-ngn-stack

使用XCode打开`idoubs/ios-ngn-stack/ios-ngn-stack.xcodeproj`。
修改 Build Setting/Build Option/Enable Bitcode，从Yes改为No，否则后面会报错：
-fembed-bitcode is not supported on versions of iOS prior to 6.0

### idoubs

使用XCode打开`idoubs/ios-ngn-stack/ios-ngn-stack.xcodeproj`。
修改General/identity/Bundle Identifier，随意修改，如`cn.ceyes.idoubs`

## 运行代码

### idoubs

可以直接在手机上运行，暂未找到配置在哪儿

### tests

需要添加 opengl 相关的lib

## 参考文献

- [idoubs/Building_iDoubs_v2_x.md](https://github.com/DoubangoTelecom/idoubs/blob/master/Building_iDoubs_v2_x.md)
- [idoubs DevelopersGuide学习笔记](http://blog.csdn.net/yuanbohx/article/details/8754574)
- [idoubs安装与配置](http://wenku.baidu.com/view/0ede21711711cc7931b716d5.html)
- [基于Doubango的iOS客户端开源框架](http://leopard168.blog.163.com/blog/static/16847184420139215540627/)
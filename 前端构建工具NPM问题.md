#### Npm 问题

###### npm install卡在“sill idealTree buildDeps“问题的两种解决方法

#### 问题原因
这个问题的根源在于淘宝镜像源的域名过期，而实际上需要绑定新的镜像源。早在 2021 年，淘宝就发布了消息称，npm 淘宝镜像已经从 registry.npm.taobao.org 切换到了 registry.npmmirror.com。然而，旧域名于 2022 年 5 月 31 日停止服务，不过直到二月份 HTTPS 证书到期才真正不能用了。

#### 第一种: 换源
最初尝试的解决方法是将镜像源切换为淘宝镜像源：

`npm config set registry registry.npmmirror.com`

然后通过以下命令验证是否成功更换源：

npm config get registry 

但是，这个方法并没有解决问题。

#### 第二种：清理缓存

npm cache clean --force

还是不行

#### 终极解决方案：换源

删除老仓库源
npm config delete registry

更换淘宝源

`npm config set registry registry.npmmirror.com`

重新install

npm install

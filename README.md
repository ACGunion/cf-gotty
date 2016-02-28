## gotty  一个运行在CloudFoundry的webshell

在CF上运行 [gotty](https://github.com/yudai/gotty)

### 安装方式

1. 克隆或下载该repo
2. 在本机执行 `cf push`
3. 在浏览器执行 `https://app-name.cfapps.io:4443` [1].


一旦您安装`Gotty`并且配置且开启一个bash shell , 访问会被一个http基础验证所保护,使用默认密码 用户名"user" 密码:"pwsrocks" 来在浏览器上访问. 一旦您在浏览器上连接成功,你就有了一个bash shell 连接到您在CF上的容器

####保护您的gotty

bash shell 是一个非常强大足矣破坏您全部数据的管理工具,我们使用HTTP基础验证保护它,但是您必须修改默认密码为一个任何人都无法猜到的密码,一旦您使用默认密码,您的gotty和CF环境将面临风险.修改gotty密码只需要编辑`manifest.yml`文件中第九行
`command: $HOME/gotty -p "$PORT" -w -c "您的用户名:您的密码" /bin/bash`

如果不想启动bash 您可以使用其他的`gotty`命令,并且修改`manifest.yml`文件中的第九行.命令及文档请查阅[docs for gotty](https://github.com/yudai/gotty#usage)


[1] - 一边情况下您不需要加4443端口访问,由于CF限制,大多数情况下您只需要访问您的APP域名例如 `https://app-name.your-domain.com`.

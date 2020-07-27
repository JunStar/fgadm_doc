# 配置`GOPATH`
`GOPATH`是一个环境变量，用来表明你写的`Go`项目的存放路径

`GOPATH`路径最好只设置一个，所有的项目代码都放到`GOPATH`的`src`目录下。

## Mac下设置GOPATH
```
#进入编辑模式
vim ~/.bash_profile
#输入如下内容
GOPATH = /Users/junstar/go/
#:wq保存
#GOPATH生效
source ~/.bash_profile
#检测是否设置成功
$GOPATH
bash: /Users/junstar/go: is a directory
```
## Windows下设置GOPATH
Windows平台按下面的步骤将（你的安装目录，例如：`D:\go`）添加到环境变量：
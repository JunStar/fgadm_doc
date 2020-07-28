# 安装node
- 下载安装包

注意，要下载10.21.0版本，下载其他版本，后面会报错
```
#windows官方下载地址速度很慢，使用淘宝nodejs的下载地址
https://cdn.npm.taobao.org/dist/node/v10.21.0/node-v10.21.0-x64.msi
#mac版本直接使用官方下载地址，下载速度挺快的
https://nodejs.org/dist/v10.21.0/node-v10.21.0.pkg
```
- 双击下载的文件按照步骤一步一步安装完成
- 增加nodejs安装目录到环境变量PATH中
    - 如果是windows操作系统，此时你只需要重启
    - 如果是macOS
    ```
    #修改~/.bash_profile文件中的PATH声明，增加上nodejs的安装目录
    vim ~/.bash_profile
    #使修改立即生效
    source ~/.bash_profile
    ```
- 查看nodejs版本和npm版本
```
node -v
npm -v
```
# 设置npm代理
```
npm config set registry=https://registry.npm.taobao.org
```
# 查看npm所有配置，检测代理是否设置成功
```
npm config list
```
# 安装gitbook命令工具
在安装之前，如果你是windows系统，需要执行下面的操作，打开允许系统执行脚本的权限
```
#以管理员身份运行Windows的命令行工具，cmd,Windows PowerShell,Windows Terminal都可以，顺便记录一个快捷键，同时按下Ctrl+Shift+左键点击命令行工具，即可使用管理员身份打开命令行
get-ExecutionPolicy
回复Restricted，表示状态是禁止的
set-ExecutionPolicy RemoteSigned
回复Y，表示允许
```

```
#安装gitbook命令工具
npm install gitbook-cli -g
```

# 安装gitbook
```
#方式一
gitbook -V
#方式二
gitbook init
#两种方式都会自动安装gitbook的最新版本，第二种方式还会初始化gitbook
CLI version: 2.3.2
Installing GitBook 3.2.3

#如果nodejs下载的不是10.21.0版本，会报如下错误

C:\Users\Administrator\AppData\Roaming\npm\node_modules\gitbook-cli\node_modules\npm\node_modules\graceful-fs\polyfills.js:287
      if (cb) cb.apply(this, arguments)
                 ^

TypeError: cb.apply is not a function
    at C:\Users\Administrator\AppData\Roaming\npm\node_modules\gitbook-cli\node_modules\npm\node_modules\graceful-fs\polyfills.js:287:18
    at FSReqCallback.oncomplete (fs.js:177:5)
    
#如果nodejs下载的是10.21.0版本，会操作成功

gitbook@3.2.3 ..\ADMINI~1\AppData\Local\Temp\tmp-167622CeKgVZ7FzW\node_modules\gitbook
├── escape-string-regexp@1.0.5
├── escape-html@1.0.3
├── destroy@1.0.4
├── ignore@3.1.2
├── bash-color@0.0.4
├── gitbook-plugin-livereload@0.0.1
├── cp@0.2.0
├── nunjucks-do@1.0.0
├── github-slugid@1.0.1
├── graceful-fs@4.1.4
......
```

# 开启Gitbook的webservr
- 你需要创建一个目录，作为你的要写书的根目录
- 使用命令行切换到要写书的根目录
- 执行gitbook的初始化
```
gitbook init
```
- 继续在写书的根目录下，开启一个gitbook的webserver

注意，如果是windows，下面的命令需要使用管理员身份运行Windows PowerShell
```
gitbook serve
```
- 找不到fontsettings.js解决办法

执行gitbook serve后，报如下错误
```
Error: ENOENT: no such file or directory, stat 'E:\Gitbook\_book\gitbook\gitbook-plugin-fontsettings\fontsettings.js'
```
报错解释地址
```
https://github.com/GitbookIO/gitbook/blob/3.2.2/lib/output/website/copyPluginAssets.js#L112
```

Mac下解决办法
```
cd ~/.gitbook/versions/版本/lib/output/website/
vim copyPluginAssets.js
修改第112行，将confirm: true 改为 confirm: false
```

Windows下解决办法类似，只是copyPluginAssets.js文件路径不同
```
#使用编辑器打开你如下文件
C:\Users\Administrator\.gitbook\versions\3.2.3\lib\output\website\copyPluginAssets.js
#修改第112行，将confirm: true 改为 confirm: false
```

- 修改完成后，命令行执行gitbook serve
```
Gitbook根目录 > gitbook serve
Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed
info: loading plugin "livereload"... OK
info: loading plugin "highlight"... OK
info: loading plugin "search"... OK
info: loading plugin "lunr"... OK
info: loading plugin "sharing"... OK
info: loading plugin "fontsettings"... OK
info: loading plugin "theme-default"... OK
info: found 1 pages
info: found 0 asset files
info: >> generation finished with success in 0.3s !

Starting server ...
Serving book on http://localhost:4000
```

- 使用浏览器打开http://localhost:4000即可访问到文档，至此Gitbook的安装完成了
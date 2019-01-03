## 介绍
之前在刚开始使用Linux系统时，需要配置一个称手的 vim 学习编程。偶然的机会，加入了 细学python QQ群，这个群给了我很多帮助和启发，谢谢。群主 [阿驹](https://github.com/denglj) 做了一个教学视频，推荐我们使用 **[k-vim](https://github.com/wklken/k-vim)**。配置 vim，肯定少不了智能补全插件 [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)，但是国内安装这个插件很慢，很容易安装失败，因为这个插件异常大，超过 200M。我记得很清楚，我安装了两次才成功安装好这个插件，而且耗时很久。我想应该很多人都会遇到这个问题，会很苦恼。

## 如果安装超时
通过安装 k-vim 自动安装并编译 YouCompleteMe 插件，如果出现 timeout 的错误导致安装失败，根据 [junegunn/vim-plug](https://github.com/junegunn/vim-plug/wiki/faq#youcompleteme-timeout)  的帮助文档，在 vim 中执行如下命令（单独安装 YouCompleteMe，这种情况下不会出现 timeout的异常）：
```bash
:PlugInstall YouCompleteMe
```

## 如果你还是没有安装成功
~~我利用国外的 vps 定时 clone 最新的 YouCompleteMe.git，然后打包，将整个文件 YouCompleteMe.tar.gz 上传至国内的 [七牛云](https://www.qiniu.com/)。我们在国内下载七牛云上面的资源相当快，希望对你有所帮助。~~

由于现在七牛云要求备案域名才能使用他们的服务，所以放弃使用七牛云了（虽然速度很快）。定时拉取最新的 YouCompleteMe.git, 打包整个仓库（包括第三方依赖，排除了.git 文件夹，以此来减小文件大小）。我用阿里云的一个云服务器提供下载服务，速度平易近人，还请见谅。

## **使用方法**
```bash
$ wget -O ~/YouCompleteMe.tar.gz "http://120.78.159.242:8888/YouCompleteMe.tar.gz"
$ cd ~/.vim/bundle
$ tar -zxf ~/YouCompleteMe.tar.gz
```

编译YCM，如果需要对C家族的语言进行语义补全支持（有点耗时）：
```bash
$ cd YouCompleteMe
$ ./install.py --clang-completer
```
如果不需要对C家族的语言进行语义补全支持：
```bash
$ cd YouCompleteMe
$ ./install.py
```
或者使用参数 `--all` 添加所有的补全，包括(c/c++ c# go python php等)。
关于编译，如有疑问，请围观 [YouCompleteMe 官方git仓库](https://github.com/Valloric/YouCompleteMe)。
等待编译结束，然后在 vim 中重新执行如下命令：
```bash
:PlugInstall YouCompleteMe
```
vim 会很快提示你已经安装好 YouCompleteMe 插件。

Ps: 我只是个大自然和 YouCompleteMe 的搬运工。

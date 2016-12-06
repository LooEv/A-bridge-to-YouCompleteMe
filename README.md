## 介绍
之前在刚开始使用Linux系统时，需要配置一个称手的 vim 学习编程。偶然的机会，加入了 细学python QQ群，这个群给了我很多帮助和启发，谢谢。群主 [阿驹](https://github.com/denglj) 做了一个教学视频，推荐我们使用 **[k-vim](https://github.com/wklken/k-vim)**。配置 vim，肯定少不了智能补全插件 [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)，但是国内安装这个插件很慢，很容易安装失败，因为这个插件异常大，超过 200M。我记得很清楚，我安装了两次才成功安装好这个插件，而且耗时很久。我想应该很多人都会遇到这个问题，会很苦恼。

## 如果安装超时
通过安装 k-vim 自动安装并编译 YouCompleteMe 插件，如果出现 timeout 的错误导致安装失败，根据 [junegunn/vim-plug](https://github.com/junegunn/vim-plug/wiki/faq#youcompleteme-timeout)  的帮助文档，在 vim 中执行如下命令（单独安装 YouCompleteMe，这种情况下不会出现 timeout的异常）：
```bash
:PlugInstall YouCompleteMe
```

## 如果你还是没有安装成功
我利用国外的 vps 定时 clone 最新的 YouCompleteMe.git，然后打包，将整个文件 YouCompleteMe.tar.gz 上传至国内的 [七牛云](https://www.qiniu.com/)。我们在国内下载七牛云上面的资源相当快，希望对你有所帮助。

## **使用方法**
**注意**：你 clone 的是国内 coding.net 的 git 仓库，不是你现在看的这个仓库，别搞错了。
```bash
$ wget -O ~/YouCompleteMe.tar.gz "http://ohpunyak1.bkt.clouddn.com/YouCompleteMe.tar.gz?v=9999"
$ cd ~/.vim/bundle
$ tar -zxf ~/YouCompleteMe.tar.gz
```
（为什么要在 YouCompleteMe.tar.gz 文件名后面加上 `?v=9999` 呢？原因请见这篇链接文章的 [额外说明](http://threehao.com/2016/08/22/Github%20Pages%20+%20Hexo/) ）
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

## 声明
此 git 仓库的 README.md 文件很少会更新，但是七牛云上面的 YouCompleteMe.tar.gz 会经常更新，确保与 YouCompleteMe 官方git仓库保持一致。


我的网络带宽也不算好，但是我测试了一下，下载速度还是相当令人满意：
```bash
$ wget http://ohpunyak1.bkt.clouddn.com/YouCompleteMe.tar.gz
--2016-12-06 10:03:31--  http://ohpunyak1.bkt.clouddn.com/YouCompleteMe.tar.gz
Resolving ohpunyak1.bkt.clouddn.com (ohpunyak1.bkt.clouddn.com)... 117.23.1.26, 125.64.133.135, 182.135.132.138, ...
Connecting to ohpunyak1.bkt.clouddn.com (ohpunyak1.bkt.clouddn.com)|117.23.1.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 143262975 (137M) [application/x-gzip]
Saving to: ‘YouCompleteMe.tar.gz’

25% [=============>                                         ] 36,639,259  1.89MB/s  eta 44s
```

Ps: 我只是个大自然和 YouCompleteMe 的搬运工。
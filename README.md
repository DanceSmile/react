# React 中文文档翻译计划 [![Build Status](https://travis-ci.org/discountry/react.svg?branch=master)](https://travis-ci.org/discountry/react)

我们使用 [Jekyll](http://jekyllrb.com/) 静态站点生成器，使用 ([mostly](http://zpao.com/posts/adding-line-highlights-to-markdown-code-fences/)) 处理 Markdown, 文档部署在 [GitHub Pages](http://pages.github.com/).

## 团队协作

### 工具

* [Github](https://github.com)
* [Trello](https://trello.com)
* [Gitlo](http://gitlo.co)

### 翻译人员要求

* 熟悉 JavaScript
* 熟悉 React
* 熟悉 Git/Github 的使用
* 理解数据绑定/函数式编程等React相关概念
* 完整阅读过 React 的英文官方文档
* 能够根据英文文档翻译出通顺易理解的中文句子
* 有开源精神，愿意为社区做出贡献
* 对自己认领的翻译高度负责，及时高质量完成翻译

### 加入翻译组

如果你有充足的时间，并符合上述要求，欢迎你加入我们的翻译组，请用微信扫码入群：

![1495257551.png](https://ooo.0o0.ooo/2017/05/20/591fd1f2e4c50.png)

我们使用 Github issue 管理项目进度。翻译组成员无需直接提出issue，注册完成github和trello之后，可以使用第三方工具gitlo进行协作。

点击[邀请链接](http://gitlo.co/invite/github/discountry/discountry/react)加入翻译组，根据提示连接你的github及trello账号。

在微信群公告内获取trello项目的邀请链接，以获取编辑看板的权限。

[项目trello地址](https://trello.com/b/JD2S3HeP/react-docs-cn)

### 认领翻译

![trello-tasks.png](https://ooo.0o0.ooo/2017/05/10/5911faefad615.png)

新建一个与你 github 名称同名的列表，并将待翻译列表中的待翻译文档拖拽至你的列表中，视为认领翻译（切勿随意编辑他人创建的列表）。

### 提交翻译

所需翻译的文档，都在项目的 [docs](docs/) 文件夹下，你只需要编辑后缀为 `.md` 的 `Markdown` 文档。

完成你所选部分的翻译之后，可以在 [Pull requests](https://github.com/discountry/react/pulls) 页面发起新的 Pull requests 请求合并你的翻译至本仓库中。

注意你提交的 Pull request 当中只能出现 `.md` 文件的改动，请勿随意修改编辑项目其他文件。

## 本地部署

如果你想在本地部署本文档，实时预览你翻译文档的效果，请按照下列说明进行操作。

### 依赖

首先点击右上角的 `fork` 按钮拷贝本项目到你的github账号下

克隆你fork的仓库到电脑本地：

```sh
$ git clone https://github.com/[YourGithubUserName]/react.git
```

在使用jkeyll之前，我们需要先安装好ruby

 - [Ruby](http://www.ruby-lang.org/) (version >= 2.4)
 - [RubyGems](http://rubygems.org/) (version >= 1.3.7)
 - [Bundler](http://gembundler.com/) (使用 `gem install bundler`)

在运行后面的命令之前，你可能需要更新本地的gem，否则可能会遇到ssl错误：

```sh
# 如果网络无法正常连接，你可能需要自备梯子，在命令行开启代理
$ sudo gem update --system
```

请确认自己安装的ruby版本在v2.4以上，否则也可能遇到ssl错误：

```sh
$ ruby -v
# ruby 2.4.0p0 (2016-12-24 revision 57164)
# 如果你需要升级你的 ruby 版本，请使用 [rvm](https://rvm.io/)
$ \curl -sSL https://get.rvm.io | bash -s stable
$ rvm install 2.4
$ rvm use 2.4
```

确认无误后：

```sh
$ cd react/docs
$ bundle install # Might need sudo.
$ npm install
```

如果你受到国内糟糕的网络环境影响，请将ruby源切换至国内镜像[ruby-china](http://gems.ruby-china.org/).

```sh
$ gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
$ bundle config mirror.https://rubygems.org https://gems.ruby-china.org
```

### 构建文档

先跑一下 `grunt` 确保项目已被构建。

使用 Jekyll 在本地运行站点 (默认端口路由为： `http://localhost:4000`):

```sh
$ cd react/docs
$ bundle exec rake
$ bundle exec jekyll serve -w -L
$ open http://localhost:4000/react/index.html
```

### 生成文档

通过如下命令，我们可以在和react存放的统一路径下名为 `react-gh-pages` 的文件夹中生成文档。

```sh
$ bundle exec rake release
```

生成文档操作可能会遇到ssl错误，请根据[SSL CERTIFICATE UPDATES](http://guides.rubygems.org/ssl-certificate-update/#installing-using-update-packages)进行操作。

### 发布文档

切换至本项目的 `gh-pages` 分支下，复制 `react-gh-pages` 文件夹中的所有内容，提交并同步至项目中。

```sh
# 如果是初次在本地创建 gh-pages 分支
$ git checkout --orphan gh-pages
$ git rm --cached -r .
# 复制粘贴 `react-gh-pages` 文件夹中的所有内容
# 切换至文档部署分支
$ git checkout gh-pages
# 复制粘贴 `react-gh-pages` 文件夹中的所有内容
$ git add .
$ git commit -m 'update docs'
$ git push origin gh-pages
```

# Flutter中文官网翻译![Flutter logo][]

本项目为**新版**Flutter官网中文翻译项目；如您想加入并一起翻译，请加微信Demons-du，然后会把你拉入官网翻译群（之前加过但没通过的，抱歉，认证处理的不及时，有很多已经过期了，请重新加一下）。

## 需要翻译的内容

1. 翻译src/docs目录下所有英文html和md文档；

   > 在您准备翻译一篇文档之前，请先对比旧版官网翻译文档，共同的部分可以直接拷贝。
   >
   > 旧版翻译线上地址：https://flutterchina.club/docs/
   >
   > 旧版翻译Github地址：https://github.com/flutterchina/website

2. 网站框架的汉化，这部分主要集中在src目录下的`_includes`和`_layouts`目录下的html文件中

## 本地运行网站

本网站是一个纯静态网站，使用jekyll构建，如果您对网站目录有所疑惑，建议可以了解一下jekyll。

### 1. 运行网站前需先安装下面依赖

- **bash**, the Bourne shell. These instructions assume you're using `bash` -- setup might not work if you use another shell.
- **[nvm][]**, the Node Version Manager.
- **[rvm][]**, the Ruby Version Manager.
- **[Flutter][Flutter install]**
- **[Dart SDK][Dart install]**

> IMPORTANT: Follow the installation instructions for each of the tools
carefully. In particular, configure your shell/environment so
that the tools are available in every terminal/command window you create.

### 2.克隆本项目及相关submodules

> NOTE: This repo has git _submodules_, which affects how you clone it.

To **clone [this repo][]**, follow the instructions given in the
GitHub help on [Cloning a repository][], and _choose one_ of the following
submodule-cloning techniques:

- Clone this repo and its submodule _at the same_, use the
  `--recurse-submodules` option:<br>
  `git clone --recurse-submodules https://github.com/flutter/website.git`
- If you've already cloned this repo without its submodule, then run
  this command from the repo root:<br>
  `git submodule update --init --remote`

> NOTE: At any time during development you can use the submodule command to
> refresh submodules:<br>
> ```
> git pull; git submodule update --init --remote
> ```

### 3. 运行安装脚本

> NOTE: It is safe to (re-)run all of the commands and scripts given below even
if you already have the required packages installed.

依次运行如下命令:

1. <code>cd <i>\<path-to-this-repo></i></code> &nbsp;&nbsp;# change to
   **root of this repo**
1. `source ./tool/env-set.sh` &nbsp;&nbsp;#
   initialize environment variables; install/use required Node & Ruby version
1. `./tool/before-install.sh` &nbsp;&nbsp;#
   install core set of required tools
1. `./tool/install.sh` &nbsp;&nbsp;#
   install everything else needed to build this site

> IMPORTANT:
> - Any time you create a **new terminal/command window** to work on
>   this repo, **repeat steps 1 and 2** above.
> - If you upgrade Dart then rerun all of the steps above.

## 运行网站

 1. Test your changes by serving the site locally.
    Run either **one** of these commands:

    - `./tool/serve.sh` (can also run via `npm run clean`)

    or
    - `bundle exec jekyll serve --incremental --watch --livereload --port 4002`

      **Note**: Unless you're editing files under `site-shared`, you can safely
      ignore `ERROR: directory is already being watched` messages.
      For details, see [#1363](https://github.com/flutter/website/issues/1363).

      **Note**: 第一次启动jekyll会生成网站，需要等待10-20秒，之后就可以在本地访问了。The first time you run either one of these commands,
      jekyll takes anywhere between 10 - 20 seconds to generate static
      content inside the `_sites` directory. If you try to verify the
      site locally but aren't able to see the content right away,
      wait 20 seconds before stopping the 
      server or concluding that something is wrong. 
 1. Prior to submitting, validate site links:<br>
    `./tool/shared/check-links.sh`

> TIP: Sometimes Jekyll gets confused and seems to be out-of-sync. (This might
> happen, for example, when you pull from master and lots of files have moved.)
> To fix Jekyll, stop the `serve.sh` script and remove the generated site files:
> hand, and then restart the `serve.sh` script:

> `npm run clean` 
> OR
> `rm -Rf ./_site/* ./.jekyll*`

> Next, restart the `serve.sh` script: 

> `npm run start`
> OR 
> `./tool/serve.sh`

## Deploying to the official site

Usually, official site deploys are performed by Travis. In the event that you
need to manually deploy, use the deploy script and the `default` project:

```
./tool/shared/deploy.sh --local --robots ok default
```

## Writing for flutter.dev


The [site-shared](https://github.com/dart-lang/site-shared) repo
contains infrastructure shared by most of our Dart and Flutter websites.
As a result, we've moved some of content of this README to the
[docs](https://github.com/dart-lang/site-shared/docs)
directory in the shared repo.

For more information on using/writing for this repo,
refer to the following docs:

* [Infrastructure](https://github.com/dart-lang/site-shared/blob/master/doc/infrastructure.md)
* [Markdown](https://github.com/dart-lang/site-shared/blob/master/doc/markdown.md)
* [Examples (and code excerpts)](https://github.com/dart-lang/site-shared/blob/master/doc/examples.md)
* [Code excerpts](https://github.com/dart-lang/site-shared/blob/master/doc/code-excerpts.md)

Also check out the site-shared
[wiki](https://github.com/dart-lang/site-shared/wiki):

* [Images](https://github.com/dart-lang/site-shared/wiki/Images)
* [Mobile friendly pages: tips & tricks](https://github.com/dart-lang/site-shared/wiki/Mobile-friendly-pages:-tips-&-tricks)
* [Writing for Dart and Flutter websites](https://github.com/dart-lang/site-shared/wiki/Writing-for-Dart-and-Flutter-websites)

[Flutter]: https://flutter.dev
[Build Status]: https://travis-ci.org/flutter/website.svg?branch=master
[Cloning a repository]: https://help.github.com/articles/cloning-a-repository
[Dart install]: https://dart.dev/get-dart
[Flutter install]: /docs/get-started/install
[Flutter logo]: https://github.com/dart-lang/site-shared/blob/master/src/_assets/image/flutter/icon/64.png?raw=1
[Firebase]: https://firebase.google.com/
[first-timers SVG]: https://img.shields.io/badge/first--timers--only-friendly-blue.svg?style=flat-square
[first-timers]: https://www.firsttimersonly.com/
[Jekyll]: https://jekyllrb.com/
[nvm]: https://github.com/creationix/nvm#installation
[Repo on Travis]: https://travis-ci.org/flutter/website
[rvm]: https://rvm.io/rvm/install#installation
[this repo]: https://github.com/flutter/website

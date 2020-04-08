---
tags:
  - posts
date: 2019-04-11
title: 创建vuepress博客，并使用git管理(待完善)
vssue-title: 固定的 Issue 标题
---
按照vuepress给的模板做后，网站更像是一个说明文档，要做一个个人博客，所以我选择了meteorlxy这款主题。
<!-- more -->

>Tip 我在搭建的过程中遇到了一些问题，现我把我搭建的流程，描述一下。

## 开始搭建
在搭建之前，需要自行安装yarn（npm也可以用，但官网推荐使用yarn，是因为'如果你的现有项目依赖了 webpack 3.x，推荐使用 Yarn 而不是 npm 来安装 VuePress。因为在这种情形下，npm 会生成错误的依赖树。'），git。
## 新建文件夹
```sh
mkdir myblog
cd myblog
```
## 安装vuepress,theme
>我安装的是1.xbeta版，你如果想安装0.x稳定版，把@next去掉就行了。不要使用官网推荐的全局安装vuepress，可能会导致问题，我就遇到了。
```sh
npm install vuepress@next  #安装vuepress
npm install vuepress-theme-meteorlxy@next  #安装主题
mkdir docs 
npm init -y  #生成package.json
```
修改下`package.json`，添加以下内容：
```json
"scripts": {
    "dev": "vuepress dev docs",
    "build": "vuepress build docs",
    "deploy": "bash deploy.sh"
}
```
## 我的目录结构
```
|-- docs
|    |-- .vuepress
|         |-- config.js
|    |-- _posts
|-- deploy.sh
|-- package.json
```
`.vuepress`文件夹下，新建`config.js`文件，内容下
```js
// .vuepress/config.js

module.exports = {
    // 网站 Title
    title: 'yang jia\'s blog',
  
    // 网站描述
    description: 'This is my blog',
  
    // 网站语言
    locales: {
      '/': {
        lang: 'zh-CN',
      },
    },
  
    // 使用的主题
    theme: 'meteorlxy',
  
    // 主题配置
    themeConfig: {
      // 主题语言，参考下方 [主题语言] 章节
      lang: require('vuepress-theme-meteorlxy/lib/langs/zh-CN'),

      //侧边栏
      sidebar: 'auto',
  
      // 个人信息（没有或不想设置的，删掉对应字段即可）
      personalInfo: {
        // 昵称
        nickname: 'yang jia',
  
        // 个人简介
        description: 'Normal Life,Happy Life',
  
        // 电子邮箱
        email: 'yangj33@qq.com',
  
        // 所在地
        location: 'hangzhou City, China',
  
        // 组织
        organization: 'PingDingShan University',
  
        // 头像
        // 设置为外部链接
        avatar: 'https://www.meteorlxy.cn/assets/img/avatar.jpg',
        // 或者放置在 .vuepress/public 文件夹，例如 .vuepress/public/img/avatar.jpg
        // avatar: '/img/avatar.jpg',
        
  
        // 社交平台帐号信息
        sns: {
          // Github 帐号和链接
          github: {
            account: 'yangj339',
            link: 'https://github.com/yangj339',
          },
          
  
          // Facebook 帐号和链接
        //   facebook: {
        //     account: 'meteorlxy.cn',
        //     link: 'https://www.facebook.com/meteorlxy.cn',
        //   },
  
          // LinkedIn 帐号和链接
        //   linkedin: {
        //     account: 'meteorlxy',
        //     link: 'http://www.linkedin.com/in/meteorlxy',
        //   },
  
          // Twitter 帐号和链接
        //   twitter: {
        //     account: 'meteorlxy_cn',
        //     link: 'https://twitter.com/meteorlxy_cn',
        //   },
  
          // 新浪微博 帐号和链接
        //   weibo: {
        //     account: '@焦炭君_Meteor',
        //     link: 'https://weibo.com/u/2039655434',
        //   },
  
          // 知乎 帐号和链接
        //   zhihu: {
        //     account: 'meteorlxy.cn',
        //     link: 'https://www.zhihu.com/people/meteorlxy.cn',
        //   },
  
          // 豆瓣 帐号和链接
        //   douban: {
        //     account: '159342708',
        //     link: 'https://www.douban.com/people/159342708',
        //   },
  
          // Reddit 帐号和链接
        //   reddit: {
        //     account: 'meteorlxy',
        //     link: 'https://www.reddit.com/user/meteorlxy',
        //   },
  
          // Medium 帐号和链接
        //   medium: {
        //     account: 'meteorlxy.cn',
        //     link: 'https://medium.com/@meteorlxy.cn',
        //   },
  
          // Instagram 帐号和链接
        //   instagram: {
        //     account: 'meteorlxy.cn',
        //     link: 'https://www.instagram.com/meteorlxy.cn',
        //   },
  
          // GitLab 帐号和链接
        //   gitlab: {
        //     account: 'meteorlxy',
        //     link: 'https://gitlab.com/meteorlxy',
        //   },
  
          // Bitbucket 帐号和链接
        //   bitbucket: {
        //     account: 'meteorlxy',
        //     link: 'https://bitbucket.org/meteorlxy',
        //   },
  
          // Docker Hub 帐号和链接
        //   docker: {
        //     account: 'meteorlxy',
        //     link: 'https://hub.docker.com/u/meteorlxy',
        //   },
        },
      },
  
      // 上方 header 的相关设置
      header: {
        // header 的背景，可以使用图片，或者随机变化的图案（geopattern）
        background: {
          // 使用图片的 URL，如果设置了图片 URL，则不会生成随机变化的图案，下面的 useGeo 将失效
          // url: '/assets/img/bg.jpg',
  
          // 使用随机变化的图案，如果设置为 false，且没有设置图片 URL，将显示为空白背景
          useGeo: true
        },
  
        // 是否在 header 显示标题
        showTitle: true,
      },
  
      // 是否显示文章的最近更新时间
      lastUpdated: true,
  
      // 顶部导航栏内容
      nav: [
        { text: 'home', link: '/', exact: true },
        { text: 'posts', link: '/posts', exact: true },
        // { text: 'houlr', link: 'http://www.houlr.com'}
      ],
  
      // 评论配置，参考下方 [页面评论] 章节
      // comments: {
      //   owner: 'meteorlxy',
      //   repo: 'vuepress-theme-meteorlxy',
      //   clientId: 'MY_CLIENT_ID',
      //   clientSecret: 'MY_CLIENT_SECRET',
      // },
    },
  }
```
新建`deploy.sh`文件，内容如下：  
需要修改`git push ...`那行。
```sh
#!/usr/bin/env sh

# 确保脚本抛出遇到的错误
set -e

# 生成静态文件
npm run build

# 进入生成的文件夹
cd docs/.vuepress/dist

# 如果是发布到自定义域名,比如我现在改的是docs.houlr.com
# echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# 如果发布到 https://<USERNAME>.github.io
git push -f git@github.com:yangj339/yangj339.github.io.git master

# 如果发布到 https://<USERNAME>.github.io/<REPO>
# git push -f git@github.com:<USERNAME>/<REPO>.git master:gh-pages

cd -
```
## 提交到github page，生成页面 

新建gihub仓库，`<USERNAME>.github.io`，`<USERNAME>`是你的gihub账户。
使用`git-bash.exe`,执行`deploy.sh`脚本
```sh
cd e://myblog
npm run deploy
```
---
等3分钟，然后访问
`https://<USERNAME>.github.io/`。即可。

## 配置自己的域名
`ping <USERNAME>.github.io`，得到ip地址，然后把域名解析到这个ip地址。  
再把`deploy.sh`里面设置下自定义域名。


---
title: 使用 FaceBook 的 Docusaurus 搭建 Blog 系统
author: 我拿青春换口饭
authorURL: http://github.com/dotkiro
---

这里简单介绍一下使用 FaceBook 的 Docusaurus 搭建 Blog 系统

## 项目初始化

1. 首先需要使用 `yarn` 或者  `npm` 全局安装  `docusaurus-init` 。
``` shell
yarn global add docusaurus-init
# 或者使用 npm 进行安装
npm install docusaurus-init -g
```

2. 安装完成后，创建你的博客项目文件夹。
``` shell
mkdir my-blog
```
3. 再进入项目文件夹通过 `docusaurus-init` 初始化项目（注意： npx 需要 npm 5.3+ 支持）。
``` shell
cd my-blog
npx docusaurus-init
```

## 项目自定义

1. 初始化后的项目骨架大体如此：
```shell
my-blog
├── docs-examples-from-docusaurus
│   ├── doc1.md
│   ├── doc2.md
│   ├── doc3.md
│   ├── exampledoc4.md
│   └── exampledoc5.md
└── website
    ├── blog-examples-from-docusaurus
    │   ├── 2016-03-11-blog-post.md
    │   ├── 2017-04-10-blog-post-two.md
    │   ├── 2017-09-25-testing-rss.md
    │   ├── 2017-09-26-adding-rss.md
    │   └── 2017-10-24-new-version-1.0.0.md
    ├── core
    │   └── Footer.js
    ├── package.json
    ├── pages
    ├── sidebars.json
    ├── siteConfig.js
    └── static
```

2. 重命名 `docs-examples-from-docusaurus` 为 `docs` ； `blog-examples-from-docusaurus` 为 `blog` 。 并且开启开发预览服务：

``` shell
mv docs-examples-from-docusaurus docs
mv website/blog-examples-from-docusaurus blog
cd website
yarn || npm install 
yarn start # 或者使用 npm start 启动
```
> 本地浏览器打开 http://localhost:3000 预览。

3. 开始自定页面以及配置：
> 修改 `my-blog/website/pages/en/index.js` 来自定义首页；
  修改 `my-blog/website/core/Footer.js` 来自定义页脚；
  修改配置文件 `my-blog/website/siteConfig.js`。

## 使用 GitHub Pages 部署项目
1. 此处使用 `Travis CI` 进行自动化部署，对于 `Travis CI` ，此处不再叙述了。
2. 配置 `Travis CI` 下项目的环境变量 `GH_NAME`, `GH_EMAIL`, `GH_TOKEN`。
3. 项目根目录下创建 `.travis.yml` 文件：
``` yml
# .travis.yml
language: node_js
node_js:
  - '10'
branches:
  only:
    - master
  cache:
    yarn: true
script:
  - git config --global user.name "${GH_NAME}"
  - git config --global user.email "${GH_EMAIL}"
  - echo "machine github.com login ${GH_NAME} password ${GH_TOKEN}" > ~/.netrc
  - curl -o- -L https://yarnpkg.com/install.sh | bash -s --
  - export PATH="$HOME/.yarn/bin:$PATH"
  - cd website
  - yarn install --frozen-lockfile
  - GIT_USER="${GH_NAME}" yarn run publish-gh-pages
```
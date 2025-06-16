<!-- 
这是基于Fuwari的第一版；暂且称为V0 Beta，能用就行的版本。后续还会重新开发基于Astro的船新版本。虽然我知道你很急但是你先别急，先让我先急
——洛寒兮
-->
# Travellings Blog

根据 未公开 的信息，我们将逐渐的将博客内容迁移至此

## 框架
- [fuwari](https://github.com/saicaca/fuwari)
- [Astro](https://astro.build/)

## 环境
- Node.JS
- pnpm

## 使用

### 前期准备

1.安装pnpm

```sh
npm install pnpm
```

2.初始化项目

```sh
pnpm install
pnpm add sharp
```

<a id="newblog"></a>
### 创建新的博文

fuwari原生支持MarkDown格式文本，只需要在终端运行以下命令：

```sh
pnpm new-post <name>
```

命令中的``<name>``请替换为需要创建的博文名，Astro会自动在``src\content\posts\``下创建对应的文件。

## 关键文件结构

```
|- public #非代码资源存放位置
|-- favicon #图标存放位置
|-- image #图片资源存放位置
|
|- scripts #脚本文件，不要动
|-- new-post.js
|
|- src #大部分代码文件存放位置
|-- assets #资源文件存放位置
|--- images #图片资源不建议使用该位置
|-- components #组件
|-- constants #定量
|-- content
|--- posts #博文主要存放位置
|--- spec #独立页面存放位置
|-- i18n #翻译
|-- layouts #布局
|-- config.ts #主配置文件
|- astro.config.mjs #Astro配置文件，与config.ts不同
```

## Frontmatter

在通过[创建新的博文](#newblog)创建的文件中会自带以下内容，如果手动创建了文件则需要将以下模板填进去。
不管是自动创建的还是手动添加，都请根据实际情况修改相应的内容

```yaml
---
title: Blog Post
published: 2024-11-4
description: This is an description to the blog
image: ./cover.jpg
tags: [Foo, Bar]
category: Front-end
draft: false
lang: zh-CN      # 仅当文章语言与 `config.ts` 中的网站语言不同时需要设置，但还是建议写一下
---
```

## Banner

V0 的 20250616 版本当中新增了一个全局的 Banner 小组件，这个小组件有其简单且单独的配置文件来控制 Banner 的样式、显示内容与 Banner的开关
可以在 src 目录下找到名为 banner_config.json 的文件进行修改
以下是这个文件的释义：

```json
{
  "style": "warning",
  // Banner 样式，目前有 info 跟 warning 两种格式
  "message": "网站正在进行维护<br/>部分功能可能受到影响",
  // Banner的信息文件，支持标准的 HTML 语法
  "show": true,
  // Banner 的显示开关
  "close_time": 3600
  // 设定在用户点击关闭后多少秒钟后继续显示 Banner（最低时间限制为60）
  // 会自动换算秒数与分钟、小时的关系
  // 如果配置为 0 则会禁用关闭 Banner 的按键
}
```

## 开发

请参照[Astro官方文档](https://docs.astro.build/zh-cn/getting-started/)

## 版权

2025 © Travellings-link Project. All rights reserved.

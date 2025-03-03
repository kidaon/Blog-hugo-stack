+++
date = '2025-02-25T17:22:51+08:00'
draft = true
title = 'Hugo搭建教程'
description = "这是一个博客搭建教程"
categories = [
    "hugo",
    "教程"
]
tags = [
    "hugo",
]
image = "cover.jpg"
+++

## 前言：为什么选择Hugo？

Hugo是由Go语言编写的静态网站生成器，凭借以下三大核心优势成为技术博客作者的首选工具：

- ⚡ **闪电般的编译速度**  
  1秒生成数千页面，告别传统生成器的漫长等待
- 🎨 **丰富的主题生态**  
  3000+免费主题一键安装，支持高度自定义
- ✍️ **极简的Markdown写作体验**  
  纯文本创作，搭配LiveReload实时预览

无需数据库、无需后端，仅需一个可执行文件即可开启创作之旅，让内容创作者真正实现「专注写作，极致高效」。

## 安装hugo

首先打开[hugo官网](https://gohugo.io/)，点开左上角标签栏的github，然后点tags看历史版本

*或者也可以直接打开网址 (https://github.com/gohugoio/hugo/tags)*

选择你想要下载的版本，这里拿Windows示范，*如果是Linux用户则选择对应架构的 .tar.gz 文件*{{< figure src="hugo安装.png" width="800" >}}

解压后就安装成功了，在这个界面下打开cmd，然后敲入命令`hugo new site your_site_name`就可以搭建你的第一个网站了，可以看到目录下多了一个文件夹{{< figure src="解压后.png" width="800" >}}

最后再配置一下环境变量：
- Win+S搜索「编辑系统环境变量」
- 点击「环境变量」→ 双击「Path」
- 添加新路径：C:\Hugo\bin

这个时候点进你刚刚新创建的文件夹，并打开cmd，输入`hugo server -D`即可运行，并在本地调试你的网页

## 选择主题
可以在(https://themes.gohugo.io/)中挑选你心仪的主题





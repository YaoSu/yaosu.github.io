---
layout: post
title:  "Semantic Versioning!"
date:   2018-03-14 14:02:00 +0800
categories: jekyll update
---


我们接触 `CocoaPods` 的时候，难免会接触到版本号，那具体的版本号都代表什么意思呢？我们自己做 `CocoaPods lib` 的时候要怎么管理版本呢？这里我为大家介绍一个概念 [Semantic Versioning](https://semver.org/)。

`Semantic Versioning` 把版本分为了三个级别，MAJOR.MINOR.PATCH。

1. MAJOR 是一个大版本，当你更新了某些和之前不兼容的API的时候，需要更新 MAJOR 版本号。
2. NINOR 是一个小版本，当你添加向下兼容的功能的时候，需要更新 NINOR 版本号。
3. Patch 当你向下兼容 fixbug 后，需要更新 Patch 版本号。


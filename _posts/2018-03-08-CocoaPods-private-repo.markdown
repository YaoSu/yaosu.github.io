---
layout: post
title:  "CocoaPod私有库的搭建!"
date:   2018-03-08 22:02:00 +0800
categories: jekyll update
---

今天我们谈一谈CocoaPods私有库。

当工程项目到达一定规模的时候，难免会变得臃肿。依赖会变得极其复杂和混乱。在这种情况下，为了使代码减少依赖和方便复用，我们应该把工程里的代码进行拆分。CocoaPods就是我们用来拆分代码和管理代码的利器。

CcocoPods使集成和版本管理变得更简单，把项目模块拆成私有库，既满足了集成的需要，也不会暴露代码，本文主要是说私有库的搭建。

#1. 先明确几个概念

1. Podspec, or Spec。
 
	Podspec, or Spec是什么呢？先看官方的解释
	> A Podspec, or Spec, describes a version of a Pod library. One Pod, over the course of time, will have many Specs. It includes details about where the source should be fetched from, what files to use, the build settings to apply, and other general metadata such as its name, version, and description.
	
	Spec 就是 specification ，顾名思义 spec 是一个描述文件。这个文件记录了  Pod 的名字、版本、描述、源地址 等一系列重要的东西。
	
2. Specs Repo

	Specs Repo 简单点说就是一个 spec 的仓库。
	
创建一个私有库简单来说就是建立一个包含了 spec 的仓库。你在需要用到某个Pod的时候，只需要把 repo 的源地址加到Podfile就可以了。

   	
#2. 具体步骤

首先，你要有个一个 git 仓库的源地址，我是用 gitlab 来做私有仓库的，所以我在gitlab 上新建了一个 project ，拿到了 git 地址。然后执行下面的语句

	$ pod repo add REPO_NAME SOURCE_URL
	
REPO_NAME 是你的 repo 的名字，SOURCE_URL 是一个 git 仓库的地址。

然后执行

	$ cd ~/.cocoapods/repos/REPO_NAME
	$ pod repo lint .
	
检查下是否安装成功。

然后在你包含 SPEC_NAME.podspec 文件的文件夹里执行

	$ pod repo push REPO_NAME SPEC_NAME.podspec
	
SPEC_NAME.podspec 里面的格式必须是符合规范的。

最后，在你需要用到私有库的工程里加入 repo 的源，就可以用 pod 'xxx' 来使用私有库了。例如：

	source 'http://user@gitlab.xxx.com/ios/kit.git'
	
	
	pod 'xxx'


大功告成！
---
title: Xcode报错
date: 2021-12-18 20:33:43
tags:
---
### missing one or more architectures required by this target: arm64
#### 报错：  
The linked framework 'Pods_projectA.framework'is missing one or more architectures required by this target: arm64
#### 解决方案：
Project -> Build Settings -> Excluded Architecture -> Debug -> Any iOS Simulator SDK  添加`arm64`
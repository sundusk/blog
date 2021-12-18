---
title: 关于M1版Mac下无法使用CocoaPods
date: 2021-12-18 17:42:41
tags:
---
### 最近买的Macbook Pro 14寸是M1 Max顶配2T版本，可能由于是新架构，对一些应用的兼容性不是那么稳定，在重新配置和使用CocoaPods时遇到的问题
#### 问题1：终端安装CocoaPods时失败报错
解决办法：
1. 在“应用程序”中找到“终端”，右键打开终端选择"显示简介"
2. 在“显示简介”中勾选“使用Rosetta方式打开”
3. 运行 sudo gem install cocoapods （之前安装过就略过)  
4. 运行 sudo gem install ffi  
5. 最后pod install

#### 问题2：终端使用'pod install'指令时报错
解决办法：
在终端输入如下指令
`sudo arch -x86\_64 gem install ffi `
`arch -x86\_64 pod install`
即可正常

####  问题3：Xcode'pod install'正常后，在项目的无法引入，显示’No such module‘
解决办法：
1. 在“应用程序”中找到“Xcode”，右键打开终端选择"显示简介"
2. 在“显示简介”中勾选“使用Rosetta方式打开”
3. 关闭Xcode后重新打开
4. 清除缓存，运行
##### 备注：搜寻答案时，最多的解决办法是在’podfile‘中加入如下内容才可，但是我没有成功，而是使用了如上方法才解决问题
   `post_install do |installer|
   installer.pods_project.build_configurations.each do |config|
   config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
end`
  
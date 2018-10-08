---
layout: post
title: Androidstudio工具
date: 2018-10-08 21:45:25.000000000 +09:00
---

# AndroidNotes

[TOC]

## 一. 准备工作

### 1. Android程序设计 ##

- 讲究逻辑与视图分离
~~~
一般采用，在布局文件(layoud)里面编写界面，然后在活动(activity)中引入进来
最好每个货都都能对应一个布局
~~~

### 2. 创建Android项目
~~~
由于 Android Studio 在一个工作区间内只允许打开一个项目，在创建新项目时，需先关闭当前项目
    点击导航栏 File->Close Project
然后再新建一个Android项目
~~~
### 3. Android程序的项目结构 ##

> 1、默认结构--Android模式

~~~
一般建立Android项目时，会使用Android的默认结构，该结构适合快速开发
~~~

> 2、Poject模式

~~~
这个模式下，是项目真正的目录结构。该结构下，主要是app目录，它是我们编写程序以及加载资源的目录
~~~

- app具体目录介绍

~~~
1. build
    主要包含一些在编译时自动生成的文件，不需过多关心
2. libs
    用于存放第三方 jar 包，放在这个目录下的jar包都会被自动添加到构建路径里去
3. src->androidTest
    用来编写 Android Test测试用例，可以对项目进行一些自动化测试
4. src->main->java
    用来放置所有 Java代码
5.src->main->res
    项目中使用到的所有图片、布局、字符串等资源都存放在这个目录下。
    1.drawable  存放图片，需要选择分辨率，大多把所有图片放在-xxhdpi文件夹下 
    2.layout    存放布局文件
    3.values    存放字符串、样式、颜色等配置
    4.mipmap    存放应用图标
6.AndroidManifest.xml 
    这是整个 Android项目的配置文件，在程序中定义的所有四大组件都需在这个文件里面注册；
    还可以在这个文件中给应用程序添加权限声明。
7.test
    用来编写 Unit Test 测试用例的，是对项目进行自动化测试的另一种方式
8.build.gradle
    app 模块的 gradle 构建脚本，此文件中会指定很多项目构建相关配置
9.proguard-rules.pro
    用于指定项目代码的混淆规则，当代码完成开发后，打成安装包文件，如不希望代码被人破解，
    通常会将代码进行混淆
~~~

## 二. 开启Android之旅--活动

### 2.1 什么是活动

~~~
活动(Activity)是一种可以包含用户界面的组件，主要用于和用户进行交互。
~~~

### 2.2 活动的基本用法

#### 2.2.1 手动创建活动


```
A:创建项目
    1:新建项目时，名称要恰当，包名使用默认值
    2:在选择添加活动这栏，即 Add an Acitivity to Mobile 这栏，选择 Add No Activity 
    3:点击 Finish，等待Gradle构建完成

B:创建活动
    1.先手动把项目改为 Project 模式
    2.右键点击 com.example.activity包->New->Activity->Empty Activity
    3.弹出创建活动对话框，将活动命名OneActivity，其他默认就行
        1.勾选Generate Layout表示自动为OneActivity创建一个对应的布局文件
        2.勾选Launcher Activity表示会自动将OneActivity设置为当前项目的主活动
        3.勾选BackwardsCompatibility表示会为项目启用向下兼容的模式(勾选)
    4.点击Finish完成创建    
```
- 项目中的任何活动都应该重写 Activity的 onCreate()方法

#### 2.2.2 创建和加载布局

- 创建布局


```
1.右击app/src/main/res目录->New->Direct,先创建一个名为layout的目录
2.在layout目录右键=>New=>Layout resourse filw,命名布局文件one_layout，完成
```
- 加载布局

```
回到OneAcitivity，在onCreate()方法中添加代码:
    setContentView(R.layout.one_layout);
    
这里通过调用setContentView()方法来个当前活动加载一个布局，在该方法中，一般传入一个布局文件的id
```
#### 2.2.3 在AndroidManifest文件中注册

> 所有活动都需要在AndroidManifest中注册才能生效

```
1.活动的声明要放在<application> 标签内
2.通过<activity> 标签来注册活动
    1:使用android:name 来指定具体注册的活动
    2:配置主活动
        在<activity> 标签内部加入<intent-filter，并在标签里添加：
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
    3:使用 android:lable 指定活动中标题的内容(显示在活动最顶部的)
```
#### 2.2.4 在活动中使用 Toast

```
Toast是Android 系统提供的一种很好的提醒方式，在程序
ory
```

# AppWidget
实现一个窗口小组件的功能

# AppWidget 简介
App Widget是应用程序窗口小部件（Widget）是微型的应用程序视图，它可以被嵌入到其它应用程序中（比如桌面）并接收周期性的更新。你可以通过一个App Widget Provider来发布一个Widget。

本文参考[Android官方文本](https://developer.android.com/guide/topics/appwidgets/index.html)，先介绍App Widget的主要组件，然后再以示例来详细说明。

# AppWidgetProvider 介绍
    AppWidgetProvider 是写一个小组件的核心类， 其继承BroadcastReceiver, 具备广播的所有特性。

 **重要的几个回调方法**
 * onUpdate
 * onAppWidgetOptionsChanged
 * onDelete
 * onEnable
 * onDisabled
 * onReceive

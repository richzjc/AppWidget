
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

---
__AppWidgetProvider示例代码,可根据具体的需求复写不同的方法__

    public class AppWidget extends AppWidgetProvider {

    @Override
    public void onUpdate(Context context, AppWidgetManager appWidgetManager, int[] appWidgetIds) {
        super.onUpdate(context, appWidgetManager, appWidgetIds);
    }

    @Override
    public void onAppWidgetOptionsChanged(Context context, AppWidgetManager appWidgetManager, int appWidgetId, Bundle newOptions) {
        super.onAppWidgetOptionsChanged(context, appWidgetManager, appWidgetId, newOptions);
    }

    @Override
    public void onReceive(Context context, Intent intent) {
        super.onReceive(context, intent);
    }

    @Override
    public void onDeleted(Context context, int[] appWidgetIds) {
        super.onDeleted(context, appWidgetIds);
    }

    @Override
    public void onDisabled(Context context) {
        super.onDisabled(context);
    }

    @Override
    public void onEnabled(Context context) {
        super.onEnabled(context);
    }
    }

---

__编写appwidget_provider文件__

1. 在res目录下面创建xml文件
2. 在xml目录下面创建appwidget_provider文件

 示例：

        <?xml version="1.0" encoding="utf-8"?>
        <appwidget-provider xmlns:android="http://schemas.android.com/apk/res/android"
                        android:initialLayout="@layout/activity_main"
                        android:minHeight="180dp"
                        android:minWidth="180dp"
                        android:resizeMode="horizontal|vertical"
                        android:widgetCategory="home_screen|keyguard"
         >
        </appwidget-provider>

---

**在清单文件里面配置信息**

      <receiver android:name=".AppWidget">
         <intent-filter>
              <action android:name="android.appwidget.action.APPWIDGET_UPDATE"/>
         </intent-filter>
          <meta-data
               android:name="android.appwidget.provider"
               android:resource="@xml/appwidget"/>
      </receiver>


在清单文件里面注册这个receiver,并且添加这个action <action android:name="android.appwidget.action.APPWIDGET_UPDATE"/>

只有添加了这个action  程序才默认是appwidget  否则和普通的广播一样的

并且必须要添加meta_data属性  这样一个简单的app_widget就实现了

***

**appWidget注意事项**

appwidget 对使用的控件是有局限性的 只能使用如下的一些控件：

FrameLayout
LinearLayout
RelativeLayout
GridLayout
AnalogClock
Button
Chronometer
ImageButton
ImageView
ProgressBar
TextView
ViewFlipper
ListView
GridView
StackView
AdapterViewFlipper

大家想可以了解RemoteView 就能知道为什么对控件是有局限性了

***

**效果图**

![](WechatIMG23.jpeg)

![](WechatIMG25.jpeg)
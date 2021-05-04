# <font color=#f5a37a>第一行代码</font>
## <font color=#55aa7f>Activity</font>
### <font color=#5000b8>活动的生命周期</font>
1. onCreate()	创建活动时
2. onStart()	不可见变可见时
3. onResume()	活动可交互时
4. onPause()	活动部分不可见时调用，onStop()调用之前也调用
5. onStop()		活动完全不可见时调用
6. onDestroy()	销毁时调用
7. onRestart()	onStop()后重启时调用
---

### <font color=#5000b8>活动的启动模式</font>
活动的启动模式在AndroidManifest.xml的activity的android:theme属性设置，如:
```xml
<activity android:name=".DialogActivity"
	android:lauchMode="singleTop">
</activity>
```

- standard
	进入任何活动都会新建活动包括处于活动栈栈顶的活动在进入在进入自己时也会创建新的自己
- singleTop 
- singTask

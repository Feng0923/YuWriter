Broadcast
===
1.BroadcastReceiver:(接受广播) 全局监听器,方便的实现不同组件之间的通信
- 注册广播:两种方式
$\alpha$.静态注册
```
class MyReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context?, intent: Intent?) {
        Toast.makeText(context,"received action is ${intent?.action},message is ${intent?.getStringExtra("msg")}",Toast.LENGTH_LONG).show()
    }
}
```
在AndroidManifest.xml中
```
        <receiver android:name=".MyReceiver">
            <!--指定该BroadcastReceiver所相应的Intent的Action-->
            <intent-filter>
                <action android:name="com.example.Veng.MyBroadcast"></action>
            </intent-filter>
        </receiver>
```
$\beta$.动态注册
```
        val myReceiver= MyReceiver()
        val intentFilter = IntentFilter()
        intentFilter.addAction("com.example.Veng.MyBroadcast")
        registerReceiver(myReceiver,intentFilter)
```
- 程序启动BroadcastReceiver过程:(发送一条广播)
1.创建需要启动的BroadcastReceiver的Intent.
2.调用Context的sendBroadcast()或sendOrderedBroadcast()方法启动指定的BroadcastReceiver.
tips:OnXxxListener只是在指定程序所在进程中,程序退出时,OnXxxListener监听器也随之关闭,但BroadcastReceiver属于系统级的监听器,它有自己的进程,只要存在与之匹配的Intent被广播出来,BroadcastReceiver就会被激发.
```
            val intent: Intent = Intent()
            intent.action = "com.example.Veng.MyBroadcast" //与接收器设置的一样
            intent.putExtra("msg","Hello")
            sendBroadcast(intent) //发送广播
```
![Snipaste_2018-01-12_22-13-55]($res/Snipaste_2018-01-12_22-13-55.png)






Service
===
Android四大组件之一,后台运行
## 创建,配置Service
1.定义一个继承service的子类
2.在AndroidManifest.xml文件中配置该Service
//如果是在AndroidStudio中,可以直接new一个Service,快速构建.
1.创建:
```

import android.app.Service
import android.content.Intent
import android.os.IBinder
import android.util.Log

class MyService : Service() {
    /*
        必须实现的方法.绑定IBinder对象,应用程序通过该对象与Service通信
     */
    override fun onBind(intent: Intent): IBinder? {
        throw UnsupportedOperationException("Not yet implemented")
        Log.d("myService","onBind")
    }

    /*
    * 在Service第一次被创建后立即回调该方法.
    * */
    override fun onCreate() {
        super.onCreate()
        Log.d("myService","onCreate")

    }

    /*
    * 每次调用StartService(intent)方法是启动该Serviece并回调.
    * */
    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        return super.onStartCommand(intent, flags, startId)
        Log.d("myService","onStartCommand")
    }

    /*
    * 在Service被关闭之前回调该方法
    * */
    override fun onDestroy() {
        super.onDestroy()
        Log.d("myService","onDestroy")
    }
}

```
2.配置:
```
<service android:name=".MyService"></service>
```
## 运行Service
1.通过Context.startService()方法.(与访问者没有关联,访问者退出了,Service然在运行)
2.通过Context.bindService()方法.(访问者与service关联,访问者一旦退出,Service也就终止)
1.start
```
 startService(intent)//启动service
 startService(intent)//启动service
 stopService(intent)//停止service
```
```
01-12 01:11:49.001 2737-2737/? D/myService: onCreate
01-12 01:11:49.001 2737-2737/? D/myService: onStartCommand
01-12 01:11:49.001 2737-2737/? D/myService: onStartCommand
01-12 01:11:49.001 2737-2737/? D/myService: onDestroy
```
2.bind:
```
  bindService(intent,connection,Service.BIND_AUTO_CREATE)
        //1.intent: Service 开启的service 2.connection: ServiceConnetion 监听访问者和Service 3.flag:Boolean 是否自动创建Service 0 则不自动创建,BIND_AUTO_CREATE自动创建
```
Activvity里:
```
    var binder: MyService.MyBinder? = null
    private val connection: ServiceConnection = object : ServiceConnection{
        /**
         * 当Activity与Service断开连接时回调该方法
         */
        override fun onServiceDisconnected(name: ComponentName?) {
            println("--disconnected--")

        }
        /**
         * 当Activity与Service连接成功时回调该方法
         */
        override fun onServiceConnected(name: ComponentName?, service: IBinder?) {
            println("--connected--")
            binder = service as MyService.MyBinder? //获取service的onBind方法所返回的MyBinder对象
        }
    }
```
service里:
```
    private var count: Int = 0
    private val binder = MyBinder()

    inner class MyBinder : Binder() {
        fun getCount(): Int {
            return count
        }
    }
    /*
        必须实现的方法.绑定IBinder对象,应用程序通过该对象与Service通信
     */
    override fun onBind(intent: Intent): IBinder? {
        Log.d("myService", "onBind")
        return binder //返回binder对象
    }
private var quit: Boolean = false 
/* * 在Service第一次被创建后立即回调该方法. * */ 
override fun onCreate() {
    super.onCreate()
    Log.d("myService", "onCreate")
    thread {
  while (!quit) {
            try {
                Thread.sleep(1000)
            } catch (e: Exception) {

            }finally {
                count++
            }
        }
    }
```
然后设置一个按钮获取service里的count值:
```
getState.setOnClickListener { toast("service的count值:${binder?.getCount()}") }

```

![Snipaste_2018-01-12_20-12-44]($res/Snipaste_2018-01-12_20-12-44.png)
![Snipaste_2018-01-12_20-12-54]($res/Snipaste_2018-01-12_20-12-54.png)

当然别忘了解绑:
```
        unbindService(connection)

```







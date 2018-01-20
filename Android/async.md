---
tags:
  - kotlin
---
async
===
1.在build.gradle中添加
	> compile 'org.jetbrains.anko:anko-sdk15:0.8.2'
2.代码书写
```
async {
           val text = URL("https://www.baidu.com").readText()//访问网络
           uiThread { show.text = text }//更新ui
       }
```





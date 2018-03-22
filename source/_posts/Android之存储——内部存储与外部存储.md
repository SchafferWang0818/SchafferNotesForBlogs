---

title: Android存储之 内部存储与外部存储
categories: "android 总结"
tags: 
	- 内部存储
	- 外部存储

---
存储方式如下  : 
![存储方式](https://i.imgur.com/C9ggy4K.jpg)
<!--more-->
---

## 内部存储
### <font color="red"> 内部存储描述&注意事项 </font> ###
- 内部存储是只有当前应用可以访问到的存储方式,SP有能被外部访问的模式;
- 应用卸载后内部存储内容都将被删除;
- 包括`sharedPreferences`,`SQLite`;

### <font color="red"> 内部存储的路径 </font> ###


	- /data/app: 							存放着所有安装的app的apk文件

	- /data/data/包名/shared_prefs 				APP的SP信息
	- /data/data/包名/databases 					APP的数据库信息
	- /data/data/包名/files						APP的文件信息
	- /data/data/包名/cache 						APP的缓存信息



注意: 没有root的手机不能打开内部存储的文件夹;


### <font color="red"> 内部存储使用方式 </font> ###


	内部存储的文件存储位置:	context.getFileDir();
	内部存储的缓存存储位置:	context.getCacheDir();


---

## 外部存储
总结概要:
1. 内部存储和外部存储都存在路径让其他应用读取;
2. 外部存储文件存储都是要精确到文件夹的;
3. 外部存储存储在外部sdCard中,使用上下文得到的是私有的,也是常清理的位置;

<font color="blue">
**外部存储包括私有目录和公有目录.
私有目录有包名存在.
公有目录使用`Environment`获取**</font>

外部存储存储权限如下: 

	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>

---

### <font color="red"> 外部存储存储路径和使用方式 </font> ###

-  公有目录

	```java
		Environment.getRootDirectory()
				->	/system
				//	Android的根目录

		Environment.getDataDirectory()
				->	/data	
				//	用户数据目录

		Environment.getDownloadCacheDirectory()
				->	/data/cache 
				//	下载缓存目录
	
		Environment.getExternalStorageDirectory()
				->	/storage/emulated/0
				//	主要的外部存储目录		需要使用Environment.getExternalStorageState()判断状态.

		Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_ALARMS)			
				->	/storage/emulated/0/Alarms
	```
- 私有目录,<font color="red">**清理数据和缓存的路径,应用被卸载时清理,也可自己手动清理** </font>

	```java
		context.getExternalCacheDir()
			->/storage/emulated/0/Android/data/packageName/cache

		context.getExternalFilesDir(Environment.DIRECTORY_ALARMS)
			->/storage/emulated/0/Android/data/packageName/files/Alarms
	```

---


###  <font color="red">总结:

1. 内部存储和外部存储都存在路径让其他应用读取;
2. 内部存储/data/user/0/包名/ 或 data/data/包名/
3. 外部存储文件存储都是要精确到文件夹的;
4. 外部存储存储在外部sdCard中,使用上下文得到的是私有的,也是常清理的位置;
5. 外部存储路径

	```java
		showLog("Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_ALARMS)->"+ Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_ALARMS).getAbsolutePath());
		showLog("Environment.getDownloadCacheDirectory()->"+Environment.getDownloadCacheDirectory().getAbsolutePath());
		showLog("Environment.getDataDirectory()->"+Environment.getDataDirectory().getAbsolutePath());
		showLog("Environment.getExternalStorageDirectory()->"+Environment.getExternalStorageDirectory().getAbsolutePath());
		showLog("Environment.getRootDirectory()->"+ Environment.getRootDirectory().getAbsolutePath());
		showLog("getExternalCacheDir()->"+getExternalCacheDir().getAbsolutePath());
		showLog("getExternalFilesDir(Environment.DIRECTORY_ALARMS)->"+getExternalFilesDir(Environment.DIRECTORY_ALARMS).getAbsolutePath());
		showLog("内部存储->"+getCacheDir().getAbsolutePath());
		showLog("内部存储->"+getFilesDir().getAbsolutePath());
		Environment.getExternalStorageState();
	        
		//小米6 环境下
	        W: Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_ALARMS)->/storage/emulated/0/Alarms
	        W: Environment.getDownloadCacheDirectory()->/data/cache
	        W: Environment.getDataDirectory()->/data
	        W: Environment.getExternalStorageDirectory()->/storage/emulated/0
	        W: Environment.getRootDirectory()->/system
	        W: getExternalCacheDir()->/storage/emulated/0/Android/data/com.billliao.fentu/cache
	        W: getExternalFilesDir(Environment.DIRECTORY_ALARMS)->/storage/emulated/0/Android/data/com.billliao.fentu/files/Alarms
	        W: 内部存储->/data/user/0/com.billliao.fentu/cache
	        W: 内部存储->/data/user/0/com.billliao.fentu/files
	```
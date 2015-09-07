# 发布lib到jcenter

## 准备
+ 注册账号：https://bintray.com (可以用github账号直接授权).
+ 注册完毕之后，记住用户名.
+ 在 `Edit Your Profile` -> `API Key` 中获取Key.

## 如何使用
+ 创建 `Android Library Project` (注意 `gradle` 的版本不太高，否则可能出错，建议2.2.1)
+ 在 `local.properties` 最后添加：
``` script
bintray.apikey=你的API Key
bintray.user=你的用户名
```
+ 修改 `根目录`build.gradle ,在 dependencies 中添加两句：
``` script
classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.2'
classpath 'com.github.dcendents:android-maven-plugin:1.2'
```
+ 修改Module的build.gradle ，在最后添加：
``` script
ext {
	PUBLISH_GROUP_ID = '你的groupId'	// 填写groupId， 一般是包名，比如：com.android.support
	LIB_NAME = '你的lib名称'	// lib名称，比如：appcompat-v7
	PUBLISH_VERSION = '版本好'	// 版本号，比如：22.2.1
	WEBSITE_URL = '库的网站链接'	// 可以填写github上的库地址.
	ISSUE_TRACKER_URL = '库的issue链接'	// 可以填写github库的issue地址.
	VSC_URL = '库的版本控制地址'	// 可以填写github上库的地址.
}

// 下面这行请勿修改
apply from: 'https://raw.githubusercontent.com/andforce/release-android-lib-to-jcenter/master/bintray.gradle'
```

### 编译发布
``` script
gradle build
gradle bintrayUpload
```
### Add to JCenter
+ 执行完上面的步骤，你只是在bintray中创建了一个Package，要发布到JCenter还需要你手动去网站点一下`Add to JCenter`.之后等待审核就好了.

### 完整使用例子
https://github.com/andforce/Android-DevUtils


## 感谢:
http://theartofdev.com/2015/02/19/publish-android-library-to-bintray-jcenter-aar-vs-jar-and-optional-dependency/

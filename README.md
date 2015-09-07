# 发布lib到jcenter

## 准备
+ 注册账号：https://bintray.com (可以用github账号直接授权).
+ 注册完毕之后，记住用户名.
+ 在Edit Your Profile -> API Key 活取Key.

## 如何使用
+ 创建 Android Library Project (注意 gradle 的版本不太高，否则可能出错，建议2.2.1)
+ 修改`根目录` build.gradle ,在 dependencies 中添加两句：
> classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.2'
> classpath 'com.github.dcendents:android-maven-plugin:1.2'

+ 修改Module的build.gradle ，在最后添加：
> ext {
>	PUBLISH_GROUP_ID = 'org.zarrboogs.devutils'
>	LIB_NAME = 'android-devutils'
>	PUBLISH_VERSION = '0.0.5'
>	WEBSITE_URL = 'https://github.com/andforce/Android-DevUtils'
>	ISSUE_TRACKER_URL = 'https://github.com/andforce/Android-DevUtils/issues'
>	VSC_URL = 'https://github.com/andforce/Android-DevUtils'
> }
> apply from: 'https://raw.githubusercontent.com/andforce/release-android-lib-to-jcenter/master/bintray.gradle'

## 感谢:
http://theartofdev.com/2015/02/19/publish-android-library-to-bintray-jcenter-aar-vs-jar-and-optional-dependency/

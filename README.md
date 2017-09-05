# QQ

QQ是一個可以成功 被 import 成 library 的小專案。 真是太感動了終於可以 import Library 了

使用Library 直接點開看 [![](https://jitpack.io/v/chenFlyingkite/QQ.svg)](https://jitpack.io/#chenFlyingkite/QQ)

Syntax of README  =>     https://guides.github.com/features/mastering-markdown/

用 Android Studio 建一個 project. 然後選擇simple activity or no activity
然後把 名稱換成 library(非必要)

1. **主要請看 QQ的**

* [build.gradle][1] : `classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'`
```gradle
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.3'

        classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
```

* [settings.gradle][2] : 只引進 logs (library name)   =>   `include ':logs'`

```gradle
//include ':app', ':logs'
include ':logs'
```
2. **logs (library name) 的**
* logs/[build.gradle][3] :
 
 ```gradle
 apply plugin: 'com.android.library'
 apply plugin: 'com.github.dcendents.android-maven'
 group='com.github.chenFlyingkite'
  ...
 dependencies {
    //compile fileTree(dir: 'libs', include: ['*.jar'])
    //compile 'com.android.support:appcompat-v7:26.+'
 }
 ```
 3. **跟 QQ library 無關的 app** ([MainActivity.java][4])
 * app/[build.gradle][5] => 加上  `apply plugin: 'android-maven'` 
 ```gradle
 apply plugin: 'com.android.application'
 apply plugin: 'android-maven'
 ```
 如果 app 要用到 logs，記得在  File > Project Structure 
 
 (左邊選 project) > (右邊有 Properties, Build Types, ...) 選 Dependencies > Add > Module Dependency

4. **引用 library 使用的 project : 參考 [jitpack][6]**
* 在 build.gradle 加上
```gradle
allprojects {
    repositories {
        maven { url "https://jitpack.io" }
    }
}
```

* 在 yourLib/build.gradle 加上
```gradle
dependencies { 
    ...
    //compile 'com.github.User:Repo:Tag'
    compile 'com.github.chenFlyingkite:QQ:0.0.1-2'
}
```

[1]: https://github.com/chenFlyingkite/QQ/blob/master/build.gradle
[2]: https://github.com/chenFlyingkite/QQ/blob/master/settings.gradle
[3]: https://github.com/chenFlyingkite/QQ/blob/master/logs/build.gradle
[4]: https://github.com/chenFlyingkite/QQ/blob/master/app/src/main/java/com/flyingkite/qq/MainActivity.java
[5]: https://github.com/chenFlyingkite/QQ/blob/master/app/build.gradle
[6]: https://jitpack.io/

# Incorrect use of ParentDataWidget.
![image](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/43398c44-8dc7-4939-92ce-5ed33dd8f55c)  

## Error Code
~~~
Incorrect use of ParentDataWidget.
~~~

## 해결 방법
Expanded 위젯은 Column,Row,Flex 안에서만 사용 가능하다. 

# Reference
https://jja08111.github.io/flutter/flutter-debuging/  
https://www.fluttercampus.com/guide/229/incorrect-use-of-parentdatawidget-error/  

# Flutter Error(Execution failed for task ':app:mapDebugSourceSetPaths'.)

## Error Code
~~~
xecution failed for task ':app:mapDebugSourceSetPaths'.
> Error while evaluating property 'extraGeneratedResDir' of task ':app:mapDebugSourceSetPaths'
   > Failed to calculate the value of task ':app:mapDebugSourceSetPaths' property 'extraGeneratedResDir'.
      > Querying the mapped value of provider(java.util.Set) before task ':app:processDebugGoogleServices' has completed is not supported
~~~
  
## 해결 방법
- project → android → build.gradle

~~~
classpath 'com.google.gms:google-services:4.3.10'
->
classpath 'com.google.gms:google-services:4.3.14'
~~~

### 수정 전
~~~
buildscript {
    ext.kotlin_version = '1.7.10'
    repositories {
        google()
        mavenCentral()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:7.3.0'
        // START: FlutterFire Configuration
        classpath 'com.google.gms:google-services:4.3.10' // 이부분 수정
        // END: FlutterFire Configuration
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
~~~

### 수정 후
~~~
buildscript {
    ext.kotlin_version = '1.7.10'
    repositories {
        google()
        mavenCentral()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:7.3.0'
        // START: FlutterFire Configuration
        classpath 'com.google.gms:google-services:4.3.14' // 이부분 수정
        // END: FlutterFire Configuration
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
~~~

# PlatformException (PlatformException(sign_in_failed, com.google.android.gms.common.api.ApiException: 12500: , null))  

## Error Code

~~~
PlatformException (PlatformException(sign_in_failed, com.google.android.gms.common.api.ApiException: 12500: , null))
~~~

## 해결 방법
Firebase에 접속 후 **지원 이메일** 추가 하기

# Reference
https://stackoverflow.com/questions/56188338/platformexception-platformexceptionsign-in-failed-com-google-android-gms-comm

# [!] Unable to find a target named `RunnerTests` in project `Runner.xcodeproj`, did find `Runner`.
Runner.xcodeproj에서 RunnerTests라는 타겟을 찾지 못했다는 내용  
## Error Code
~~~
[!] Unable to find a target named `RunnerTests` in project `Runner.xcodeproj`, did find `Runner`.
~~~

## 해결 방법
~~~
target 'Runner' do
  use_frameworks!
  use_modular_headers!

  flutter_install_all_ios_pods File.dirname(File.realpath(__FILE__))
  # target 'RunnerTests' do
  #   inherit! :search_paths
  # end
end
~~~
ios/Podfile로 가서 아래와 같은 부분을 찾아서 RunnerTests 관련 항목을 주석 처리

# Reference
https://blog.dglee.co.kr/34  


# PodInstallError

## Error

### Error Code
~~~
[!] Automatically assigning platform `iOS` with version `11.0` on target `Runner` because no platform was specified.   
Please specify a platform for this target in your Podfile. See `https://guides.cocoapods.org/syntax/podfile.html#platform`.
~~~

### 해결방법
![Untitled](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/e116db65-c234-4a06-8915-a21206b8780d)  


### Error Code
~~~
[!] CocoaPods did not set the base configuration of your project because your project already has a custom config set.   
In order for CocoaPods integration to work at all, please either set the base configurations of the target `Runner` to `Target Support Files/Pods-Runner/Pods-Runner.profile.  xcconfig` or include the `Target Support Files/Pods-Runner/Pods-Runner.profile.xcconfig` in your build configuration (`Flutter/Release.xcconfig`).  
~~~

### 해결방법
Runner → Flutter → Release

~~~
#include "Pods/Target Support Files/Pods-Runner/Pods-Runner.profile.xcconfig"
~~~
위에 코드 추가  
![Untitled](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/7e07fa18-3bca-4c34-a42f-5adf7e298813)   
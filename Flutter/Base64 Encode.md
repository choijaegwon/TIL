# Base64 Encode

## 예시 코드
~~~
import 'dart:convert';
~~~
~~~
final string = base64로 인코딩할 String;
Codec<String, String> stringToBase64 = utf8.fuse(base64);
String token = stringToBase64.encode(string);
~~~
# FlutterJson

## 구조


json 스트링 : json 텍스트 데이터 (자료형 : String)  
json 자료형 : Dart에서 json 데이터를 다루기 위해 사용되는 자료형 (자료형 : Map<String, dynamic>)  
json 객체 : json 데이터를 파싱하여 얻은 객체. 사용자가 직접 정의해야함(자료형 : Object)

~~~
JSON -> Map<String, dynamic> -> Object

JSON -> Map<String, dynamic> => jsonDecode  
Map<String, dynamic> -> Object => fromJson
~~~

~~~
Object -> Map<String, dynamic> -> JSON

Object -> Map<String, dynamic> => toJson
Map<String, dynamic> -> JSON => jsonEncode
~~~


# Reference
https://bebesoft.tistory.com/11  
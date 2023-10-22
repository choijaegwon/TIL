# Singleton 만들기

## 예시 코드
~~~
// file_system.dart
class FileSystem {
  FileSystem._();
  static final instance = FileSystem._();
}

// some_other_file.dart
final fs = FileSystem.instance;
// do something with fs
~~~
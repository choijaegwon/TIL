# Hero로 AppBar 구현시 Text 아래에YellowLines 생성 되는 이슈

## 구현 코드
~~~
Hero(
  tag: 'tag',
  child: Material( // <--- Provide Material
    type: MaterialType.transparency,
    child: YourWidget(),
  ),
);
~~~

# Reference
https://stackoverflow.com/questions/47114639/yellow-lines-under-text-widgets-in-flutter
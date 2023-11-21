# VerticalDivider 안보이는 문제

## 사용법
~~~
VerticalDivider(
  color: Colors.black,
  thickness: 2,
)
~~~

~~~
IntrinsicHeight(
  child: Row(
    children: [
      Text('Hello'),
      VerticalDivider(
        color: Colors.black,
        thickness: 2,
      ),
      Text('World'),
    ],
  ),
)
~~~

# Reference
https://stackoverflow.com/questions/49388281/flutter-vertical-divider-and-horizontal-divider  
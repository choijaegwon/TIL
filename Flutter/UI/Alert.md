# Alert.md

## 예시 코드
![스크린샷 2023-10-04 오후 11 36 11](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/ff1ca857-2d17-4330-a316-24e5fd20a10c)
~~~
showDialog(
    context: context,
    barrierDismissible: false,
    builder: (context) {
        return AlertDialog(
            title: Text('Are you sure?'),
            content: Text('Do you really want to delete?'),
            actions: [
                TextButton(
                    onPressed: () => Navigator.pop(context, false),
                    child: Text('No'),
                ),
                TextButton(
                    onPressed: () => Navigator.pop(context, true),
                    child: Text('YES'),
                ),
            ],
        );
    },
);
~~~
barrierDismissible: false, 속성을 주면 뒤에 터치를 막을 수 있다.
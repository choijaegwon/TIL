# UI 분기 처리 시 좋은 방법

## 예시 코드
### 따로 처리해서 add 해주기
~~~
@override
Widget build(BuildContext context) {
    var children = [
        SizedBox(height: 16.0),
        Avatar(photoUrl: user.photoUrl),
        SizedBox(height: 8.0),
    ];
    if (user.displayName != null) {
        children.add(Text(
            user.displayName,
            style: Theme.of(context).textTheme.title,
        ));
    }
     if (user.username != null) {
        children.add(Text(
            user.username,
            style: Theme.of(context).textTheme.subtitle,
        ));
    }
    return Column(children: children);
}
~~~

### 안에서 한번에 처리
~~~
@override
Widget build(BuildContext context) {
    return Column(
        children = [
            SizedBox(height: 16.0),
            Avatar(photoUrl: user.photoUrl),
            SizedBox(height: 8.0),
            if (user.displayName != null) ...[
                Text(
                    user.displayName,
                    style: Theme.of(context).textTheme.title,
                ),
                SizedBox(height: 8.0),
            ],
            if (user.username != null) ...[
                Text(
                    user.username,
                    style: Theme.of(context).textTheme.subtitle,
                ),
                SizedBox(height: 8.0),
            ],  
        ],
    );
}
~~~

# Reference
https://codewithandrea.com/videos/dart-features-part2-spreads-collectionif-collectionfor/  
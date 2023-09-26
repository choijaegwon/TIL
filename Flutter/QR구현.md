# QR구현
~~~
flutter pub add qr_flutter
~~~

## 예시코드
~~~
QrImageView(
  data: '1234567890',
  version: QrVersions.auto,
  size: 100.0,
),
~~~
data에 원하는 데이터를 넣어주면 그림이 바뀐다.  

에러 상태를 표시할 수도 있다.
~~~
QrImageView(
  data: 'This QR code will show the error state instead',
  version: 1,
  size: 320,
  gapless: false,
  errorStateBuilder: (cxt, err) {
    return Container(
      child: Center(
        child: Text(
          'Uh oh! Something went wrong...',
          textAlign: TextAlign.center,
        ),
      ),
    );
  },
)
~~~

# Reference
https://pub.dev/packages/qr_flutter
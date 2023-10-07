# extension 관련

## 예시 코드

### 타입에서 확장
정의
~~~
extension on double {
	double celsiusToFarhenheit() => this * 1.8 + 32;
  double farhenheitToCelsius() => (this - 32) / 1.8;
}
~~~

사용
~~~
double tempCelsius = 10.0;
double tempFarhenheit = tempCelsius.celsiusToFarhenheit();
print('${tempCelsius}C = ${tempFarhenheit}F');

10C = 50F
~~~

정의
~~~
extension on Widget {
  Widget paddingAll(double padding) => Padding(
    padding: EdgeInsets.all(padding),
    child: this,
  );
}
~~~

사용
~~~
Column(
  crossAxisAlignment: CrossAxisAlignment.stretch,
  children: <Widget>[
    Text('One Line').paddingAll(8),
    Text('Another line').paddingAll(8),
    customRaisedButton(
      context,
      onPressed: () {},
      child: Text('OK'),
      borderRadius: 8,
    ).paddingAll(8),
  ],
)
~~~

### 하나의 클래스로 확장
~~~
class Temperature {  
  Temperature._({this.celsius});
  factory Temperature.celsius(double degrees) => Temperature._(celsius: degrees);
  factory Temperature.farhenheit(double degrees) => Temperature._(celsius: (degrees - 32) / 1.8);

  final double celsius;
  double get farhenheit => celsius * 1.8 + 32;
}

final tempA = Temperature.celsius(10);
final tempB = Temperature.farhenheit(50);
~~~

### 위젯으로 확장
정의
~~~
class VerticalSpacing extends SizedBox {
	VerticalSpacing({double height = 16.0}) : super(height: height);
}
~~~
사용
~~~
VerticalSpacing(),
AirportWidget(
  // parameters
),
VerticalSpacing(),
AirportWidget(
  // parameters
),
VerticalSpacing(),
SegmentedControl<FlightType>(
  // parameters
),
VerticalSpacing(),
SegmentedControl<FlightClass>(
  // parameters
),
VerticalSpacing(),
~~~


# Reference
https://codewithandrea.com/videos/dart-extensions-full-introduction/   
https://codewithandrea.com/videos/dart-extensions-full-introduction/#padding-with-less-boilerplate   
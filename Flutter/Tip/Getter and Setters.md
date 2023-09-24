# Getter and Setters

## 예시 코드
~~~
int get _maxRpm = -100;
set setMaxRpm(int _maxRpm) => _maxRpm = rmp;
~~~

~~~
double speed;
double get _maxRpm => speed * 1.8 + 32;
set setMaxRpm(double rpm) => speed = (rpm - 32) / 1.8;
~~~
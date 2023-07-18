# copyWith()
- 원본 객체를 변경하지 않고 특정 값만 바꾼 새로운 객체를 반환하기 위함

## ExCode
~~~
SliderTheme(
  data: SliderTheme.of(context).copyWith(
  inactiveTrackColor: Color(0xFF8D8E98),
  activeTrackColor: Colors.white,
  thumbColor: Color(0xFFEB1555),
  overlayColor: Color(0x29EB1555),
  thumbShape:
      RoundSliderThumbShape(enabledThumbRadius: 15.0),
  overlayShape:
      RoundSliderOverlayShape(overlayRadius: 30.0),
  ),
);
~~~

# Referencd
https://terry1213.github.io/flutter/flutter-copywith/  
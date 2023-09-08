# BuildContext란?

- 현재 빌드에 대한 정보를 저장하는 객체
- 트리의 각 위젯을 추적하고 트리에서 위젯들의 위치를 찾는 데 사용되는 locator
- Widget의 위치를 찾을 때 사용
- 특정 Widget이 빌드되는 맥락(환경)
- Widget마다 고유하다 현재 빌드의 최소 / 최대 플러터 버전, 화면 크기 등의 정보를 제공한다

# Reference
https://medium.com/flutter-community/widget-state-buildcontext-inheritedwidget-898d671b7956   
https://api.flutter.dev/flutter/widgets/BuildContext-class.html   
https://velog.io/@coding_egg/Flutter-BuildContext-%EB%9E%80  
# extends VS implements VS with(Mixins)

## extends
- 다중 상속 불가
- 클래스의 멤버변수, 함수, 생성자 등을 구현없이 사용할때 사용  
- override를 통해 수정하여 사용가능  
- 슈퍼 클래스의 속성, 변수, 함수를 그대로 사용하거나 수정하여 사용할 수 있게 해준다.

## implements
- 다중 상속 가능
- 클래스의 멤버변수, 함수, 생성자 등의 구현이 필수적  
- 슈퍼 클래스에 정의되어 있는 모든 속성, 변수, 함수를 가져오지만 전부 override하여 구현필요

## with(Mixins)
- 다중 상속 가능
- 다양한 계층의 클래스에서 클래스의 코드를 재사용
- extends처럼 슈퍼 클래스의 속성, 변수, 함수를 전부 가져와서 그대로 사용하거나 수정하여 사용할 수 있게 해준다.

# Reference
https://blog.terry1213.com/dart/dart-extends-vs-implements-vs-with/   
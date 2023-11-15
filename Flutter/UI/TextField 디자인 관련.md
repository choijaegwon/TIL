# TextField 디자인 관련

## 디자인
<img width="574" alt="Untitled" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/8b5bdfc6-a47e-4522-bf29-a1dc5d4283d0">


## 구현 코드
~~~
// obscuringCharacter: 비밀번호 숨김처리시 표시할 Text

import 'package:flutter/material.dart';

class CustomInputTextField extends StatelessWidget {
  /// 컨트롤러
  TextEditingController textEditingController;

  /// 비밀번호 숨김 처리
  bool obscureBool;

  /// x 아이콘 함수 실행
  void Function()? xIconFunction;

  /// onCgange 여부
  void Function(String) onChangeFunction;

  /// 이미지 Str
  String imageStr;

  /// 힌트 text
  String hintText;

  /// 생일 필드 여부
  bool birthDate;

	/// 입력 데코레이터가 활성화되어 있고 오류가 표시되지 않을 때 표시할 테두리 색
  Color enabledBorderColor;

  /// 아이콘 여부
  bool isSuffixIcon;

  /// 숫자만 받기
  bool onlyNumber;

  /// 최대 입력 개수
  bool isMaxLength;

  /// 최대길이
  int? inputMaxLength;

	/// 포커스 노드
  FocusNode? textFieldFocusNode;

  CustomInputTextField({
    required this.textEditingController,
    this.obscureBool = false,
    this.xIconFunction,
    required this.onChangeFunction,
    required this.imageStr,
    required this.hintText,
    this.birthDate = false,
    this.enabledBorderColor = Colors.transparent,
    this.isSuffixIcon = true,
    this.onlyNumber = false,
    this.isMaxLength = false,
    this.inputMaxLength,
    this.textFieldFocusNode,
  });

  @override
  Widget build(BuildContext context) {
    return TextField(
      focusNode: textFieldFocusNode,
      maxLength: isMaxLength ? inputMaxLength : null,
      keyboardType: onlyNumber ? TextInputType.number : null,
      textAlign: birthDate ? TextAlign.center : TextAlign.start,
      controller: textEditingController,
      obscureText: obscureBool,
      obscuringCharacter: '●',
      style: TextStyle(
        color: Colors.white,
        fontSize: 16,
      ),
      decoration: InputDecoration(
        contentPadding: EdgeInsets.symmetric(horizontal: 20, vertical: 18),
        filled: true,
        fillColor: Color.fromRGBO(58, 22, 71, 1),
        counterText: '',
        border: OutlineInputBorder(
          borderRadius: BorderRadius.circular(6),
          borderSide: BorderSide(
            // color: Colors.red,
            width: 1,
          ),
        ),
        // 입력 데코레이터에 포커스가 있고 오류가 표시되지 않을 때 표시할 테두리
        focusedBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(6),
          borderSide: BorderSide(
            // color: Colors.red,
            color: Color.fromRGBO(255, 62, 180, 1),
            width: 1,
          ),
        ),
        // 입력 데코레이터가 활성화되어 있고 오류가 표시되지 않을 때 표시할 테두리
        enabledBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(6),
          borderSide: BorderSide(
            color: enabledBorderColor,
          ),
        ),
        hintText: hintText,
        hintStyle: TextStyle(
          color: Color.fromRGBO(95, 80, 100, 1),
          fontSize: 16,
        ),
        suffixIcon: isSuffixIcon
            ? IconButton(
                onPressed: xIconFunction,
                icon: Image.asset(
                  imageStr,
                  width: 22,
                  height: 22,
                ),
              )
            : null,
      ),
      onChanged: onChangeFunction,
    );
  }
}
~~~

# Reference
https://medium.com/flutter-community/a-visual-guide-to-input-decorations-for-flutter-textfield-706cf1877e25
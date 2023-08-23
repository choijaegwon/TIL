# TextField 문자열 길이 제한 시 카운터 표시 없애는 방법

## 핵심 코드

~~~
counterText:'',
~~~

## 구현 코드

~~~
TextField(                        
  maxLength: 10,       // 문자길이 제한                  
  keyboardType: TextInputType.number,
  inputFormatters: [WhitelistingTextInputFormatter(RegExp('[0-9]')),],
  decoration: InputDecoration(
    labelText: 'Type your Number',
    hintText: '1234',   
    counterText:'',    // counter text를 비움으로 설정
  ),
),
~~~

# Reference
https://blog.naver.com/chandong83/222010129921
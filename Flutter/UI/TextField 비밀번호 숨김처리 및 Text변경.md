# TextField 비밀번호 숨김처리 및 Text변경

## 핵심 코드

~~~
obscureText: true,
obscuringCharacter: '●',
~~~

## 구현 코드

~~~
TextField(
  controller: _passwordController,
  textAlign: TextAlign.center,
  obscureText: true,
  obscuringCharacter: '●',
  style: TextStyle(fontSize: 20)
),
~~~

# Reference
https://stackoverflow.com/questions/55661658/how-to-make-these-password-dots-bigger-in-obscuretext
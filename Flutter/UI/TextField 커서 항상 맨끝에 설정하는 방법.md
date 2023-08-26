# TextField 커서 항상 맨끝에 설정하는 방법

## 핵심 코드

~~~
TextSelection.collapsed(offset: controller.text.length);
~~~

## 구현 코드

~~~
controller.text = someString;
controller.selection = TextSelection.collapsed(offset: controller.text.length);
~~~

# Reference
[https://stcodelab.com/entry/Flutter의-TextField에서-값의-끝에-커서-위치를-설정하는-방법은-무엇인가요](https://stcodelab.com/entry/Flutter%EC%9D%98-TextField%EC%97%90%EC%84%9C-%EA%B0%92%EC%9D%98-%EB%81%9D%EC%97%90-%EC%BB%A4%EC%84%9C-%EC%9C%84%EC%B9%98%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)
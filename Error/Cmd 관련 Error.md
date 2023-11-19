# Cmd E324: ATTENTION Error
환경변수 편집을 하기위해 vi ~/. zshrc 입력시 발생   
vi 비정상 종료후 다시 실행하면 발생하는 Error

## Error code
~~~
E325: ATTENTION
Found a swap file by the name "~/.zshrc.swp"
~~~

## 해결 방법
~~~
rm -f ~/.zshrc.swp
~~~
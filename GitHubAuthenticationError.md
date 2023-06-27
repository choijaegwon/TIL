# GitHubAuthenticationError

## 에러문구
~~~
remote: repository not found.
fatal: authentication failed for
~~~

## 해결방법
~~~
git config --global user.name ‘아이디’
git config --global user.email '이메일'
git config --global user.password ‘복사한 토큰’
git pull
~~~

# Reference
https://wotres.tistory.com/entry/Github-에러-해결법-Authentication-failed-for-use-a-personal-access-token-instead   
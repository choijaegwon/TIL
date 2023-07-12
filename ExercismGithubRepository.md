# ExercismGithubRepository

## 설치

### exercism 설치
~~~
brew install exercism
~~~

### Token 설정
~~~
configure --token='${token}'

ex)

configure --token=11da1e11-1c1f-11b2-b111-c1e1ea11111b
~~~

### GitRepo 생성

~~~
cd ~
git clone <github-repo-url>
~~~

### GitRepo를 폴더로 사용
방금 생성한 git repo폴더 이름을 "Exercism"으로 변경

~~~
mv Exercism-Solutions Exercism
~~~

## 사용하기

### 문제 다운

~~~
exercism download --exercise=hello-world --track=javascript
~~~

### 문제 해결 후 깃에 커밋하기
~~~
git add .
git commit -m "download javascript hello world"
git push origin master
~~~

# Reference
https://www.linkedin.com/pulse/how-setup-exercism-cli-use-your-own-github-repository-jim-lynch/  
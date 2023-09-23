# dart pub global activate flutterfire_cli 입력시 Error

## Error Code
~~~
Warning: Pub installs executables into $HOME/.pub-cache/bin, which is not on your path.
You can fix that by adding this to your shell's config file (.bashrc, .bash_profile, etc.):

export PATH="$PATH":"$HOME/.pub-cache/bin"
~~~

## 해결 방법
~~~
vi ~/. zshrc
~~~
맨 아래에
~~~
export PATH="$PATH":"$HOME/.pub-cache/bin"
~~~
추가

~~~
source ~/.zshrc
~~~

적용

# Firebase projects:list 입력시 Error

## Error Code
~~~
Error: Failed to list Firebase projects. See firebase-debug.log for more info.
~~~

## 해결 방법
~~~
firebase login --reauth
~~~
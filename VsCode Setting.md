# VsCode Setting

<details>
<summary> const 자동으로 붙여주기 </summary>

com + , 누르고  
codeActionsOnSave 검색후  
settings.json   
~~~
"editor.codeActionsOnSave": {
    "source.fixAll": true
}
~~~
true로 설정하면 저장할때 const를 자동으로 붙여준다

</details>

<details>
<summary> 자동 생성된 Dart 파일에 대한 파일 중첩 활성화 </summary>
 
settings.json   
~~~
{
  "explorer.fileNesting.patterns": {
      "*.dart": "${capture}.g.dart, ${capture}.freezed.dart"
  },
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.expand": false,
}
~~~

# Reference
https://codewithandrea.com/articles/vscode-shortcuts-extensions-settings-flutter-development/#6-enable-file-nesting-for-auto-generated-dart-files

</details>
# main에서 비동기 작업을 하고싶을 때

## Excode

~~~
void main() async {

    WidgetsFlutterBinding.ensureInitialized();

    .....비동기작업.....

    runApp(new MyAPP());

}
~~~

# Reference
https://jutole.tistory.com/31
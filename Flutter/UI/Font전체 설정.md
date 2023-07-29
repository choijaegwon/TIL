# Font전체 설정

## ExCode
~~~
@override
Widget build(BuildContext context) {
  return MaterialApp(
    routes: routes,
    navigatorKey: getIt<NavigationService>().key,
    theme: ThemeData(
      fontFamily: 'Pretendard',
    ),
  );
}
~~~

# Referencd
https://dokit.tistory.com/8  
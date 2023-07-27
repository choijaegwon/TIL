# TextField 내부 padding 제거

## ExCode
~~~
@override
Widget build(BuildContext context) {
  return MaterialApp(
    routes: routes,
    navigatorKey: getIt<NavigationService>().key,
    theme: ThemeData(
      inputDecorationTheme: InputDecorationTheme(
          isDense: true,
          contentPadding: EdgeInsets.symmetric(horizontal: 0, vertical: 0)),
    ),
  );
}
~~~

# Referencd
https://yunikim.tistory.com/entry/TextField-%EA%B8%B0%EB%B3%B8-padding-%EC%82%AD%EC%A0%9C-%ED%95%98%EA%B8%B0  
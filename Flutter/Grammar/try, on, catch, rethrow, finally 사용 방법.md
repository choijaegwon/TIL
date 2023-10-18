# try, on, catch, rethrow, finally 사용 방법

- 여러 `on` 을 추가하여 다양한 유형의 예외를 처리할 수 있다.
- `catch` 위의 유형과 일치하지 않는 모든 예외를 처리하는 fallback 절을 가질 수 있다.
- **스택 추적을 유지하면서**`rethrow` 명령문을 사용하여 현재 예외를 호출 스택 위로 던질 수 있다.
- 성공 여부에 관계없이 완료 `finallyFuture` 후 일부 코드를 실행하는 데 사용할 수 있다.

## 예시 코드
~~~
Future<void> printWeather() async {
  try {
    final api = WeatherApiClient();
    final weather = await api.getWeather('London');
    print(weather);
  } on SocketException catch (_) {
    print('Could not fetch data. Check your connection.');
  } on WeatherApiException catch (e) {
    print(e.message);
  } catch (e, st) {
    print('Error: $e\nStack trace: $st');
    rethrow;
  } finally {
    print('Done');
  }
}
~~~

# Reference
https://codewithandrea.com/videos/top-dart-tips-and-tricks-for-flutter-devs/#13-how-to-use-try-on-catch-rethrow-finally   

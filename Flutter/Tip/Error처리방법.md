# Error처리방법

## 예시코드

### 정의
- 각 Error에 대한 타입을 정의한 한다.
http_error_handler.dart
~~~
import 'package:http/http.dart' as http;

String httpErrorHandler(http.Response response) {
  final stateCode = response.statusCode;
  final reasonPhrase = response.reasonPhrase;

  final String errorMessage =
      'Request failed\nStatus Code: $stateCode\nReason: $reasonPhrase';

  return errorMessage;
}
~~~

weather_exception.dart
~~~
class WeatherException implements Exception {
  String message;

  WeatherException([this.message = 'Something went wrong']) {
    message = 'Weather Exception: $message';
  }

  @override
  String toString() => message;
}
~~~

### 사용
~~~
try {
    final http.Response response = await httpClient.get(uri);

    if (response.statusCode != 200) {
        throw httpErrorHandler(response);
    }

    final responseBody = json.decode(response.body);

    if (responseBody.isEmpty) {
        throw WeatherException('Cannot get the location of $city');
    }

    final directGeocoding = DirectGeocoding.fromJson(responseBody);

    return directGeocoding;
} catch (e) {
    rethrow;
}
~~~
rethrow는 이 구문 말고 추후 사용할때(Error를 호출한쪽에) Error를 처리하기 위함
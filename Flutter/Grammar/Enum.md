# Enum

## 예시 코드
~~~
enum AuthException {
  invalidEmail('Invalid email'),
  emailAlreadyInUse('Email already in use'),
  weakPassword('Password is too weak'),
  wrongPassword('Wrong password');

  const AuthException(this.message);
  final String message;
}

const exception = AuthException.wrongPassword;
print(exception.message); // Wrong password
~~~

~~~
enum StatusCode {
  badRequest(401, 'Bad request'),
  unauthorized(401, 'Unauthorized'),
  forbidden(403, 'Forbidden'),
  notFound(404, 'Not found'),
  internalServerError(500, 'Internal server error'),
  notImplemented(501, 'Not implemented');

  const StatusCode(this.code, this.description);
  final int code;
  final String description;

  @override
  String toString() => 'StatusCode($code, $description)';
}
~~~

# Reference
https://codewithandrea.com/tips/dart-2.17-enums-with-members/   
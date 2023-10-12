# if else

## 예시 코드
~~~
void anyFunction() {
    if (wifi) {
        if (login) {
            if (admin) {
                seeAdminPanel();
            } else {
                debugPrint('Must be an administrator');
            } 
        } else {
            debugPrint('Must login in your account');
        }
    } else {
        debugPrint('Must be connected to wifi');
    }
}
~~~
를 
~~~
void anyFunction() {
    if (!wifi) {
        debugPrint('Must be connected to wifi');
        return;
    } 

    if (!login) {
        debugPrint('Must login in your account');
        return;
    }

    if (!admin) {
        debugPrint('Must be an administrator');
        return;
    }

    seeAdminPanel();
}
~~~
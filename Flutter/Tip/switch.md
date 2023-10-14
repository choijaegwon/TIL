# switch

## 예시 코드
~~~
getCaffeine (type) {

    String caffeine;

    switch (type) {
        case 'Cofffee':
            caffeine = '95 mg';
            break;
        case 'Redbull':
            caffeine = '147 mg';
            break;
        case 'Tea':
            caffeine = '11 mg';
            break;
        case 'Soda':
            caffeine = '21 mg';
            break;
    default:
            caffeine = 'Not found';
    }

    return caffeine;
}
~~~
를

~~~
getCaffeine (type) {
    String caffeine;

    const map = {
        'Coffee' : '95 mg',
        'Redbull' : '147 mg,
        'Tea' : '11 mg,
        'Soda' : '21 mg
    };

    caffeine = map[type] ?? 'Not found';

    return caffeine;
}
~~~
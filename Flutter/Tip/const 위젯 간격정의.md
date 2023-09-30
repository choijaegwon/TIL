# const 위젯 간격정의

## 예시 코드
### 정의
~~~
// gaps.dart 
const gapW4 = SizedBox(width: Sizes.p4);
const gapW8 = SizedBox(width: Sizes.p8);
const gapW12 = SizedBox(width: Sizes.p12);
...
const gapW64 = SizedBox(width: Sizes.p64);

const gapH4 = SizedBox(height: Sizes.p4);
const gapH8 = SizedBox(height: Sizes.p8);
const gapH12 = SizedBox(height: Sizes.p12);
...
const gapH64 = SizedBox(height: Sizes.p64);
~~~
### 사용
~~~
Column(
  children: const [
    Text('Spacing is a good idea in UX design.'),
    gapH16,
    Text('It makes your UI less cluttered.'),
  ]
)

Row(
  children: [
    const Text('Image Preview:'),
    gapW16,
    CachedNetworkImage(imageUrl: product.imageUrl),
  ]
)
~~~
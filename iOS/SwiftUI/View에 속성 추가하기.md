# View에 속성 추가하기

## 예시 코드 (워터 마크)
~~~
struct Watermark: ViewModifier {
    var text: String

    func body(content: Content) -> some View {
        ZStack(alignment: .bottomTrailing) {
            content
            Text(text)
                .font(.caption)
                .foregroundColor(.white)
                .padding(5)
                .background(.black)
        }
    }
}

extension View {
    func watermarked(with text: String) -> some View {
        modifier(Watermark(text: text))
    }
}
~~~
이런식으로 다른곳에서 정의를 한후
~~~
VStack(spacing: 10) {
	Color.blue
		.frame(width: 300, height: 200)
		.watermarked(with: "Hacking with Swift")
}
~~~

이런식으로 사용하면 된다.

# Reference
https://taekki-dev.tistory.com/91   
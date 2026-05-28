# Menu버튼
~~~
struct BorderlessButtonMenuView: View {
    var body: some View {
        Menu("PDF") {
            Button("Open in Preview", action: { })
            Button("Save as PDF", action: { })
        }
        .menuStyle(BorderlessButtonMenuStyle())
    }
}
~~~

“PDF”란 Text를 누르면, menu버튼이 나온다.
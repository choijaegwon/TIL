# @Binding 초기화 방법.md

~~~
@Binding var isActivated: Bool
init(isActivated: Binding<Bool> = .constant(true)) {
    _isActivated = isActivated
}
~~~
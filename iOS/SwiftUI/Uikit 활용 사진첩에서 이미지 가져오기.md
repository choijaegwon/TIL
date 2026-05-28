# Uikit 활용 사진첩에서 이미지 가져오기

## 예시 코드

ImagePicker.swift

~~~
import SwiftUI

struct ImagePicker: UIViewControllerRepresentable {
    
    @Binding var image: UIImage?
    @Environment(\.dismiss) var dismiss
    
    // VC가 모든데이터와 통신할수있게하는것
    func makeCoordinator() -> Coordinator {
        Coordinator(self)
    }
    
    // VC 만들기
    func makeUIViewController(context: Context) -> some UIViewController {
        let picker = UIImagePickerController()
        picker.delegate = context.coordinator
        return picker
    }
    
    // 뷰업데이트할때 사용
    func updateUIViewController(_ uiViewController: UIViewControllerType, context: Context) {
        
    }
}

extension ImagePicker {
    class Coordinator: NSObject, UINavigationControllerDelegate, UIImagePickerControllerDelegate {
        let parent: ImagePicker
        
        init(_ parent: ImagePicker) {
            self.parent = parent
        }
        
        // 선택한 이미지로 할 작업
        func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
            guard let image = info[.originalImage] as? UIImage else { return }
            parent.image = image
            parent.dismiss()
        }
    }
}
~~~

작성후, 사용할 곳에서

~~~
@State var selectedUIImage: UIImage? // UIKit에서 사용하는 Image
@State var image: Image? // SwiftUI에서 사용하는 Image
@Environment(\.dismiss) private var dismiss
~~~

이런 변수를 만든후,

~~~
// UIKit에서 사용하는 Image를 SwiftUI에서 사용하기 위해 바꾸는 함수
func loadImage() {
	guard let selectedImage = selectedUIImage else { return }
	image = Image(uiImage: selectedImage)
}
~~~

이런 함수를 만들고

~~~
Button {
    self.showImagePicker.toggle()
} label: {
    ZStack{
        if let image = image {
            image
                .resizable()
                .scaledToFill()
                .frame(width: 140, height: 140)
                .clipped()
                .cornerRadius(70)
                .padding(.top, 88)
                .padding(.bottom, 16)
        } else {
            Image("plus_photo")
                .resizable()
                .renderingMode(.template)
                .scaledToFill()
                .frame(width: 140, height: 140)
                .padding(.top, 88)
                .padding(.bottom, 16)
                .foregroundColor(.white)
        }
    }
}
.sheet(isPresented: $showImagePicker, onDismiss: {
    loadImage()
}) {
    ImagePicker(image: $selectedUIImage)
}
~~~

이렇게 사용하면 된다.
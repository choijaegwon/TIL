# 검증하는 로직(AllSatisfy)
- 약관 모두 동의 할때 필요한 로직
- Array의 모든 요소를 검증하고 싶을 때 사용하는 로직  
- https://github.com/choijaegwon/AllSatisfy  

## 예시 코드

- 뷰 모델
- ContentViewModel.Swift

~~~
import Combine
import Foundation

class ContentViewModel: ObservableObject {

    @Published var allMarketingTermAgreed: Bool = false
    @Published var emailMarketingAgreed: Bool = false
    @Published var phoneMarketingAgreed: Bool = false
    
    var subscriptions = Set<AnyCancellable>()

    init() {
        Publishers.CombineLatest($emailMarketingAgreed, $phoneMarketingAgreed)
            .sink { email, phone in
                self.allMarketingTermAgreed = [email, phone].allSatisfy { $0 == true }
                print(self.allMarketingTermAgreed)
            }
            .store(in: &self.subscriptions)
    }
    
    /// 모두 동의하기
    func allAgree() {
        if self.emailMarketingAgreed && self.phoneMarketingAgreed {
            self.emailMarketingAgreed = false
            self.phoneMarketingAgreed = false
        } else {
            self.emailMarketingAgreed = true
            self.phoneMarketingAgreed = true
        }
    }

}
~~~

- 뷰
- ContentView.Swift

~~~
import SwiftUI

struct ContentView: View {
    
    @StateObject var model = ContentViewModel()
    
    var body: some View {
        VStack {
            
            HStack {
                Text("모두 동의 여부")
                    .foregroundColor(Color.black)
                    .font(Font.custom("Pretendard-SemiBold", fixedSize: 18))
                Text(model.allMarketingTermAgreed.description)
            }
            
            Button {
                self.model.allAgree()
            } label: {
                HStack {
                    Image(self.model.allMarketingTermAgreed ? "icoCheckSelect" : "icoRadio")
                        .resizable()
                        .renderingMode(.original)
                        .frame(width: 15, height: 15)
                    
                    Text("모두 동의 하시겠습니까?")
                        .foregroundColor(Color.black)
                        .font(Font.custom("Pretendard-SemiBold", fixedSize: 14))
                }
            }
            
            Button {
                model.emailMarketingAgreed.toggle()
            } label: {
                HStack {
                    Image(self.model.emailMarketingAgreed ? "icoCheckSelect" : "icoRadio")
                        .resizable()
                        .renderingMode(.original)
                        .frame(width: 15, height: 15)
                    
                    Text("이메일 동의")
                        .foregroundColor(Color.black)
                        .font(Font.custom("Pretendard-SemiBold", fixedSize: 14))
                }
            }
            
            Button {
                model.phoneMarketingAgreed.toggle()
            } label: {
                HStack {
                    Image(self.model.phoneMarketingAgreed ? "icoCheckSelect" : "icoRadio")
                        .resizable()
                        .renderingMode(.original)
                        .frame(width: 15, height: 15)
                    
                    Text("전화번호 동의")
                        .foregroundColor(Color.black)
                        .font(Font.custom("Pretendard-SemiBold", fixedSize: 14))
                }
            }
        }
        .padding()
        .environmentObject(model)
    }
}
~~~

# Reference
https://jinsangjin.tistory.com/150  
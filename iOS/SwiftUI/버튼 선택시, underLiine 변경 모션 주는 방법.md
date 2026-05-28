# 버튼 선택시, underLiine 변경 모션 주는 방법.md

## 예시 코드
~~~
enum TweetFilterOptions: Int, CaseIterable {
    case tweets
    case replies
    case likes
    
    var title: String {
        switch self {
        case .tweets: return "Tweets"
        case .replies: return "Tweets & Replies"
        case .likes: return "Likes"
        }
    }
}

struct FilterButtonView: View {
    
    @Binding var selectedOption: TweetFilterOptions
    
    private let underlineWidth = UIScreen.main.bounds.width /
    CGFloat(TweetFilterOptions.allCases.count)
    
    private var padding: CGFloat {
        let rawValue = CGFloat(selectedOption.rawValue)
        let count = CGFloat(TweetFilterOptions.allCases.count)
        return ((UIScreen.main.bounds.width / count) * rawValue) + 16
    }
    
    var body: some View {
        VStack(alignment: .leading) {
            HStack {
                ForEach(TweetFilterOptions.allCases, id: \.self) { option in
                    Button {
                        self.selectedOption = option
                    } label: {
                        Text(option.title)
                            .frame(width: underlineWidth - 8)
                    }
                }
            }
            
            Rectangle()
                .frame(width: underlineWidth - 32, height: 3, alignment: .center)
                .foregroundColor(.blue)
                .padding(.leading, padding)
                .animation(.spring(), value: selectedOption)
                
        }
    }
}
~~~
사용시
~~~
struct UserProfileView: View {
    
    @State var selectedOption: TweetFilterOptions = .tweets
    
    var body: some View {
        ScrollView {
            VStack {
                ProfileHeaderView()
                    .padding()
                
                FilterButtonView(selectedOption: $selectedOption)
                    .padding()
            } // VStack
            
            .navigationTitle("batman")
        } // ScrollView
    }
}
~~~
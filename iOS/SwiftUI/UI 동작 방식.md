# UI 동작 방식.md

### 1. 컨테이너 뷰(직계 상위 뷰)가 사이즈를 제안한다.
### 2. 하위 뷰가 자신의 사이즈를 결정한다. (하위 뷰는 상위 뷰가 제안한 사이즈를 그대로 사용하거나, 본인이 자신의 사이즈를 결정하기도 한다.)
### 3. 하위 뷰가 컨테이너 뷰에 자신의 사이즈를 알린다. (2단계에서 결정된 사이즈로 컨테이너 뷰의 사이즈가 정해진다.)
### 4. 컨테이너 뷰가 하위 뷰를 가운데 정렬 시킨다. (`alignment`)
### 5. SwiftUI는 반시계로 그림을 그리는 매커니즘이다.

![image](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/22c4da47-54f2-4e38-b380-f9c9c0f5fe33)  

# Reference
https://klioop.tistory.com/28  
https://klioop.tistory.com/30   
https://klioop.tistory.com/29  
https://www.youtube.com/watch?v=GuK6wwX8M0E    
https://protocorn93.github.io/tags/PreferenceKey/  
https://sujinnaljin.medium.com/swiftui-swiftui-%EC%9D%98-layout-3-%EB%8B%A8%EA%B3%84-cf70ba00f88e   

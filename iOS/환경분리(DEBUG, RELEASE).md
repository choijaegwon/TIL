# 환경분리(DEBUG, RELEASE)
- 실제 사용되고 있는앱에서 테스트할 순 없어서 개발하면서 최대한 실제 환경과 비슷하게 만들려고 하는 것
- 무료앱, 유료앱을 나누기 위해 사용  
- DEBUG: 개발자가 개발할때 Xcode를 이용해서 실행시키는 것
- RELEASE: 테스트 플라이트로 받은 앱, 애플스토어에서 받은 앱
- 개발자는 타겟을 사용하여 모든 환경을 볼 수 있다. 

## 하는방법

## 1. 각각의 FB설정 파일 넣어주기


- PROJECT_ID, BUNDLE_ID 확인후 변경
- Target 맞춰서 설정  

<img width="258" alt="image" src="https://user-images.githubusercontent.com/68246962/235298785-0deab00f-0d6b-4183-8580-9ad648542a7f.png">  

## 2. 프로젝트의 Info 확인


<img width="849" alt="image" src="https://user-images.githubusercontent.com/68246962/235298834-e9cceb30-d01a-4a6b-87d0-64a6f58c6c57.png">   

- TARGETS 복사해주기. 

## 3. Bundle Identifier 확인  


- 만약 앱 각각의 앱(ex: Test, TestQa, TestDev)을 설치하고 싶다면, Bundle Identifier에 이름을 수정해주면 된다.   

### App  

 <img width="732" alt="image" src="https://user-images.githubusercontent.com/68246962/235298924-d35151ff-6d25-4a25-851d-19850e80ec27.png">  

### AppQa  

<img width="737" alt="image" src="https://user-images.githubusercontent.com/68246962/235298946-1945e396-28c9-4365-ba16-6704080fca7c.png">  

### AppDev

<img width="734" alt="image" src="https://user-images.githubusercontent.com/68246962/235298962-4508db82-c127-44b7-8c86-5ec088c5f2ed.png">

## 4. Build Settings(Custom Flags) 확인
---

### App

<img width="784" alt="image" src="https://user-images.githubusercontent.com/68246962/235299240-216c6fdf-4905-453a-8318-9da836f7178b.png">  


### AppQa

<img width="787" alt="image" src="https://user-images.githubusercontent.com/68246962/235299288-b52a7e56-9a1a-47c8-9b64-ae89e86f7f71.png">  

### AppDev

<img width="783" alt="image" src="https://user-images.githubusercontent.com/68246962/235299344-5951bc10-1eda-4655-852c-bdc110cc5e08.png">  

## 5. 서버에서 데이터 어떻게 내려주는지 API 확인하기


### 예시 코드
~~~
{
    "app_version_server_list": [
        {
            "app_verison": "1.0.4",
            "app_build_type": "RELEASE",
            "server_endpoint": "RELEASE서버주소",
            "endpoint_type": "RELEASE" // 없어도 된다.
        },
        {
            "app_verison": "1.0.4",
            "app_build_type": "QA",
            "server_endpoint": "QA서버주소",
            "endpoint_type": "QA" // 없어도 된다.
        },
        {
            "app_verison": "1.0.4",
            "app_build_type": "DEBUG",
            "server_endpoint": "Dev서버주소",
            "endpoint_type": "DEBUG" // 없어도 된다.
        }
    ]
}
~~~

## 6. 서버에서 API 받아서 분리

- 전처리기문 사용  
~~~
func lookup() async throws {
    let requestData = LookupServerEndpointByAppVersionRequest.lookup
    let res: Data = try await self.requestManager.initRequest(with: requestData)
    /// 디버그 모드
    #if DEBUG
        #if DEV
            print("현재 타겟: PROD (Debug)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .PROD }[0].serverEndpoint
        #endif

        #if QA
             print("현재 타겟: QA (Debug)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .QA }[0].serverEndpoint
        #endif

        #if PROD
              print("현재 타겟: DEV (Debug)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .DEBUG }[0].serverEndpoint
        #endif
    #else
    /// 릴리즈모드
        #if DEV
            print("현재 타겟: PROD (Release)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .PROD }[0].serverEndpoint
        #endif

        #if QA
             print("현재 타겟: QA (Release)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .QA }[0].serverEndpoint
        #endif

        #if PROD
              print("현재 타겟: DEV (Release)")
            APIAddress.default.serverEndpoint = res.appVersionServerList.filter { $0.appBuildType == .DEBUG }[0].serverEndpoint
        #endif
    #endif
}
~~~
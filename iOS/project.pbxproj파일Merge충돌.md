# project.pbxproj파일Merge충돌

## 문제 상황
- main 브랜치에서 브랜치를 나누어 각각 2개의 기능을 추가하고 Merge할때 project.pbxproj 충돌이 일어났다. 평소와같이 충돌을 잘 해결하고 실행을 시키려 했는데 충돌이 해결이 안됐는지, 프로젝트를 다시 키려고하면 파일이 실행이 안되었다.

## 해결 방법
코드중  

~~~
14B739BC2A14D62C004B542B /* Ad */ = {
	isa = PBXGroup;
	children = (
		14B739BD2A14D642004B542B /* AdView.swift */,
		14B739C32A15C81F004B542B /* AdViewModel.swift */,
	);
	path = Ad;
	sourceTree = "<group>";
};
~~~  

이런식으로 끝에 path와 sourceTree 가 있어야 정상인데,  
코드를 충동났던 부분의(Merge한 부분의) 코드를 다시보니,  

~~~
14B739BC2A14D62C004B542B /* Ad */ = {
	isa = PBXGroup;
	children = (
		14B739BD2A14D642004B542B /* AdView.swift */,
		14B739C32A15C81F004B542B /* AdViewModel.swift */,
	);
	path = Ad;

149F05E72A0883430030A665 /* ScreenSaver */ = {
	isa = PBXGroup;
	children = (
		149F05E82A0883680030A665 /* ScreensaverView.swift */,
		149F05EC2A08853E0030A665 /* AppState.swift */,
	);
	path = ScreenSaver;
	sourceTree = "<group>";
};
14FA16B12A0C93A30081582F /* ScreenSaver */ = {
	isa = PBXGroup;
	children = (
		14FA16B32A0C94060081582F /* LookupScreenSaverRequest.swift */,
	);
	path = ScreenSaver;
	sourceTree = "<group>";
};
~~~  

이런식으로 

~~~
sourceTree = "<group>";
};
~~~
이 부분이 빠져있는걸 볼 수 있었다.  
아마도 마지막 부분은 동일하기 때문에 덧씌여 진 것 같다.  

~~~
14B739BC2A14D62C004B542B /* Ad */ = {
	isa = PBXGroup;
	children = (
		14B739BD2A14D642004B542B /* AdView.swift */,
		14B739C32A15C81F004B542B /* AdViewModel.swift */,
	);
	path = Ad;
    sourceTree = "<group>";
};

149F05E72A0883430030A665 /* ScreenSaver */ = {
	isa = PBXGroup;
	children = (
		149F05E82A0883680030A665 /* ScreensaverView.swift */,
		149F05EC2A08853E0030A665 /* AppState.swift */,
	);
	path = ScreenSaver;
	sourceTree = "<group>";
};
~~~  

따라서 이렇게 해결해 주면 충돌을 해 줄 수 있다.

# Reference
https://stackoverflow.com/questions/361799/unable-to-open-project-cannot-be-opened-because-the-project-file-cannot-be-pa  

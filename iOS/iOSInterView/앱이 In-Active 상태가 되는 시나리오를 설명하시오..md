# 앱이 In-Active 상태가 되는 시나리오를 설명하시오.
- 전화나 메시지 같은 인터럽트가 발생
- 미리알림 같은 특정 알림창이 화면을 덮어서 앱이 실질적으로 event를 받지 못하는 상태 In-Active 상태가 된다. 
- 앱을 처음켜거나, foreground에서 background, background에서 foreground 상태가 될 때도 in-Active 상태를 거쳐간다.
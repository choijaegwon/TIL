# App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.

## Not RunningPermalink
- Not Running은 앱이 아직 실행되지 않았거나, 완전히 종료되어 동작하지 않는 상태.

## Foreground - InactivePermalink
- Inactive는 app이 실행중이지만 사용자로부터 event를 받을 수 없는 상태. multitasking window로 진입하거나 app 실행중 전화, 알림 등에 의해 app을 사용할 수 없게 되는 경우 이 상태로 진입.

## Foreground - ActivePermalink
- Active는 app이 실제 실행중이고 사용자 event를 받아서 상호작용할 수 있는 상태.(바로 Active가 되지 않고 Inactive 상태를 거쳐 Active상태가 된다.)

## Backgound - RunningPermalink
- Background는 홈화면으로 나가거나 다른 app으로 전환되어 현재 app이 실질적인 동작을 하지 않는 상태. 
- 예를 들어 Music app을 닫아도 재생한 음악이 계속 실행되는 경우. 사용자가 app을 사용하지 않는 동안 서버와 데이터를 동기화하거나 타이머가 실행되어야 하는 등의 작업을 이 상태에서 할 수 있습니다.

## Backgound - SuspendedPermalink
- Suspended는 app을 다시 실행했을 때 최근 작업을 빠르게 로드하기 위해 메모리에 관련 데이터만 저장되어있는 상태. 
- app이 background 상태에 진입했을 때 다른 작업을 하지 않으면 Suspended 상태로 진입하게 됩니다.(보통 2~3초 이내) Suspended 상태의 app들은 iOS의 메모리가 부족해지면 가장 먼저 메모리에서 해제됨. 따라서 app을 종료시킨 적이 없더라도 app을 다시 실행하려고 하면 처음부터 다시 실행됩니다.

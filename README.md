# iOSInterviewquestions
iOS개발자들에게 필요한 자료들을 정리하고 있는 중입니다.

면접때 받은 질문이나 공부한내용들

수정해야할 내용이나 추가해야할 내용은 언제든지 PR날려주세요!

```
답이 적혀있지 않은 이유는 해당 내용을 암기식으로 외우기 보다 찾아보고 공부하면서 습득 하시는게 좋기때문입니다.
해당내용을 찾아보면서 관련된 내용들 까지 같이 공부하시면서 해당 내용을 본인의 것으로 얻으시기 바랍니다.
```

모두의 힘을 모아봅시다 👯‍♀️👯‍♂️
감사합니다:)

# Required
아래 내용들은 최대한 많이 공부해놓는것이 좋습니다 📝

+ 면접시기가 wwdc이후 (7월~11월)이라면 해당년도 wwdc세션들을 봐 두시면 매우매우매우 좋습니다.

[Apple All Videos](https://developer.apple.com/videos/all-videos/)

## iOS
### Bounds 와 Frame 의 차이점을 설명하시오.
```
Bound 는 자기자신의 위치를 기준으로 좌표계를 설정합니다 따라서 원점의 좌표는 항상 (0,0) 입니다
Frame 은 SuperView 의 위치를 기준으로 좌표계를 설정합니다. SuperView의 원점과 차이가 나는만큼 원점이 생성됩니다.
```
### 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.

```
 블루투스, 카메라, GPS, 기울기 센서, 지문 인식 등을 사용할수 없으며  
푸쉬 알람기능 또한 사용할수 없습니다.
```
### 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가?
```
CoreData 라고 하며
관계형 데이터베이스를 기반으로 데이터를 저장하는 Sqlite 방식과
비교적 적은 데이터를 저장하는 In Memory 방식
모든 데이터를 한번에 저장하고 한번에 꺼내는 Binary Storage 방식이 있습니다.
```
### 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가?
```
ViewController 라고합니다. 모든앱에는 기본적으로 하나의 뷰컨트롤러를 가지고있습니다.  
뷰컨트롤러의 종류는 ContentViewController 와 ContainerViewController 가있습니다.  
ContenteViewController 는 UIViewController, UITableViewController, UICollectionViewController
등 모든 뷰를 하나의 씬에서 통제합니다.  
ContainerViewController 는 NavigationController, TabbarController, PageViewController
등 부모뷰 밑에 하나이상의 자식뷰를 포함하고 있습니다.
```
### App thinning에 대해서 설명하시오.
```
애플리케이션이 디바이스에 설치될 때 앱스토어와 운영체제가 디바이스의 특성에 맞체 최적화하여 앱을 설치하는 기술입니다. 
앱시닝에는 슬라이싱, 비트코드, 주문형 리소스 가 있습니다.  
슬라이싱은 여러 디바이스에 대해 각각 조각 애플리케이션 번들을 생성하고, 
해당디바이스에 가장 적합한 조각을 전달하는 기술입니다.  
비트코드는 기계어로 번역되기 이전단계의 중간표현으로 비트코드를 사용하여
업로드하면 앱스토어에서 컴파일 단계를 한단계 더 거쳐 디바이스에 최적화 되어 설치됩니다.  
주문형 리소스는 필요할때 다운로드 받는다는 것입니다. 게임을 예로들어 현재보다
상위단계의 데이터는 아직 다운받지 않는 방식입니다.
```
###
### 앱이 시작할 때 main.c 에 있는 UIApplicationMain 함수에 의해서 생성되는 객체는 무엇인가?
```
결론 : UIApplication 싱글턴 객체가 생성됨
모든 iOS 앱에는 정확히 하나의 UIApplication 인스턴스 (또는 매우 드물게 UIApplication의 하위 클래스)가 있습니다.. 
앱이 시작되면 시스템은 UIApplicationMain(_:_:_:_:) 함수를 호출합니다. 
이 함수는 싱글톤 UIApplication 객체를 만들고 공유 클래스 메서드를 호출하여 객체에 액세스합니다.
```
### @Main에 대해서 설명하시오.
```
Swift 5.3 부터는 @main(@UIApplicationMain 대신에)을 사용한다.
UIKit 기반 앱의 main entry point이다.
```
### 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?
```
ForeGround 상태에서는 메모리 및 기타 시스템 리소스 권한에 높은 우선순위를 가지며
시스템은 이러한 우선순위를 만족시키도록 Background 에 있는 앱을 종료시키기도 합니다.
Background 상태에서는 최소한의 메모리 사용을 해야하합니다.

application(didFinishLaunching) -> 앱이 사용자 화면에 보여지기 직전에
willFinishLaunchingWithOptions -> 앱이 최초 실행될때
applicationWillResignActive -> 앱이 Active 에서 InActive 로 전환될때
ApplicationDidEnterBackground -> 앱이 백그라운드 상태일때
applicationWillEnterForeground 앱이 foreground 로 진입할때
applicationDidbacomActive 앱이 active 상태가 되어 실행중일때
applicationWillTerminate 앱이 종료될 
```

### 상태 변화에 따라 다른 동작을 처리하기 위한 앱델리게이트 메서드들을 설명하시오.
```
![image](https://user-images.githubusercontent.com/42457589/143516394-45e78432-1f52-41cb-91bd-5824a1dafe75.png)

application(didFinishLaunching) -> 앱이 사용자 화면에 보여지기 직전에
willFinishLaunchingWithOptions -> 앱이 최초 실행될때
applicationWillResignActive -> 앱이 Active 에서 InActive 로 전환될때
ApplicationDidEnterBackground -> 앱이 백그라운드 상태일때
applicationWillEnterForeground 앱이 foreground 로 진입할때
applicationDidbacomActive 앱이 active 상태가 되어 실행중일때
applicationWillTerminate 앱이 종료될 
```
### 앱이 In-Active 상태가 되는 시나리오를 설명하시오.
```
사용자가 홈버튼은 누르거나 백그라운드로 진입하면 
Appdelegate 에서 applicationWillasign 메소드를 호출하여 Active 상태에서 In-Active 상태로 
전환됩니다. 그후 백그라운드로 진입하면 ApplicationDidEnterBackground 메소드가 호출됩니다.
```
### scene delegate에 대해 설명하시오.
```
ios13 부터 AppDelegate 의 역할이 AppDelegate(App Life Cycle, Session Life Cycle) 와 SceneDelegate(Scene Life Cycle) 로 나뉘어졌습니다.
SceneDegate 는 윈도우에 Scene의 표시를 처리하고 관리합니다.
scene(WillConnectTo) 메소드는 UISceneLifeCycle 의 첫번째 호출되는 메소드로 UIWindow 를 만들고 루트 뷰 컨트롤러를 설정합니다.
willEnterForeground 는 앱이 Foreground 로 전활될때 scene을 설정합니다.
sceneDidBecomeActive 는 sceneWillEnterForeground 직후 호출되며 scene 을 사용할 준비를 마칩니다.
sceneWillResignActive, SceneDidEnterBackground 는 백그라운드로 진입할시 호출됩니다.
sceneDidDisconnect 는 scene 이 백그라운드로 진입할때마다 리소스 확보를위해 scene 을 삭제하는 것을 결정합니다.
```
- UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?
### App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.
```
Not running 앱이 시스템에 의해 종료된 상태입니다.
Inactive - 앱이 Foreground 에서 동작하지만 이벤트를 처리하지 않습니다.
active 상태는 앱이 실행중일때의 상태입니다.
Background 상태는 앱이 백그라운드에 진입 한 상태이며 음악이나 통화같은 백그라운드 작업을 처리합니다.
Suspend 상태는 백그라운드 상태에서 아무런 코드도 실행되지 않는 상태입니다.
```
###
### NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.
```
Multi threading 을 위한 API 에는 C 기반의 GCD 와 object-C 기반의 NSOpreation 이 있습니다.
NSOperation 은 GCD와 비교했을땐 추가적인 오버해드가 있으나, 다양한 작업들 가운데 
의존성을 추가할 수 있고, 재사용, 취소, 중지시킬 수 있다.
```
### GCD API 동작 방식과 필요성에 대해 설명하시오.
```
GCD 는 백그라운드에서 스레드를 관리하면서 동시적으로 작업을 실행시켜주는 저수준 API 입니다.
DispatchQueue
Serial Dispatch Queue
Concurrency Dispatch Queue
Main Dispach Queue 
등에 작업을 등록하여 처리합니다
DispatchQueue 는 FIFO 방식으로 작업을 처리
Serial Dispatch Queue 는 순차적으로 작업처리,
Concurrency DispatchQueue 는 순서에 상관없이 비동기적으로 작업을 처리
Main DispatchQueue 는 앱의 메인스레드에서 작업을 실행할수 있는 시리얼 큐입니다.
```
### Global DispatchQueue 의 Qos 에는 어떤 종류가 있는지, 각각 어떤 의미인지 설명하시오.
```
UserInteractive - 메인스레드에서 작동하며 UI 새로고침 또는 애니메이션 과같이 사용자와 상호작용하는 작업
UserInitiated - 사용자가 시작한 작업이며, 저장된 문서를 열거나 사용자 인터페이스에서 무언가를 클릭할때 상호작용작업을 수행
default - user Initiate 와 utility 사이의 우선순위를 가짐. qos 정보가 할당되지 않으면 defalut 로 설정됨
utility - 데이터 다운로드 등 즉각적인 결과가 필요하지 않은 작업, 시간이 오래걸릴수 있음
background - 백그라운드에서 작용하며 사용자가 볼수없는 작업들을 수행, 에너지효율에 중점을 둠
unspecified - Qos 정보가 없음을 나타냄. environment qos 를 추론해야한다는 단서를 시스템에 
```
###
- iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?
- Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.
- Delegate란 무언인가 설명하고, retain 되는지 안되는지 그 이유를 함께 설명하시오.
- NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.
- UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?
- App Bundle의 구조와 역할에 대해 설명하시오.
- 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?
- 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.
- View 객체에 대해 설명하시오.
- UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.
- UIWindow 객체의 역할은 무엇인가?
- UINavigationController 의 역할이 무엇인지 설명하시오.
- TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.
- 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.
- setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.
###
- NSCache와 딕셔너리로 캐시를 구성했을때의 차이를 설명하시오.
- URLSession에 대해서 설명하시오.
- prepareForReuse에 대해서 설명하시오.
- 다크모드를 지원하는 방법에 대해 설명하시오.

## Autolayout
- 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)
- hugging, resistance에 대해서 설명하시오.
- Intrinsic Size에 대해서 설명하시오.
- 스토리보드를 이용했을때의 장단점을 설명하시오.
- Safearea에 대해서 설명하시오.
- Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.

## Swift
- struct와 class와 enum의 차이를 설명하시오.
- class의 성능을 향상 시킬수 있는 방법들을 나열해보시오.
- Convinience init에 대해 설명하시오.
- Anyobject에 대해 설명하시오.
- Optional 이란 무엇인지 설명하시오.
- Struct 가 무엇이고 어떻게 사용하는지 설명하시오.
- Subscripts에 대해 설명하시오.
- instance 메서드와 class 메서드의 차이점을 설명하시오.
- Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.
- Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.
- KVO 동작 방식에 대해 설명하시오.
- Delegates와 Notification 방식의 차이점에 대해 설명하시오.
- 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.
- MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.
- 프로토콜이란 무엇인지 설명하시오.
- Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.
- mutating 키워드에 대해 설명하시오.
- 탈출 클로저에 대하여 설명하시오.
- Extension에 대해 설명하시오.
- 접근 제어자의 종류엔 어떤게 있는지 설명하시오
- defer란 무엇인지 설명하시오.
- defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.
- property wrapper에 대해서 설명하시오.
- Generic에 대해 설명하시오.
- Result타입에 대해 설명하시오.
- Codable에 대하여 설명하시오.

## ARC
- ARC란 무엇인지 설명하시오.
- Retain Count 방식에 대해 설명하시오.
- Strong 과 Weak 참조 방식에 대해 설명하시오.
- 순환 참조에 대하여 설명하시오.
- 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

## Functional Programming
- 함수형 프로그래밍이 무엇인지 설명하시오.
- 고차 함수가 무엇인지 설명하시오.
- Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

## Architecture
- MVVM, Ribs, VIP 등 자신이 알고있는 아키텍쳐를 설명하시오.
- 의존성 주입에 대하여 설명하시오.

# Optional
아래부터는 추가로 공부를 하면 좋을 내용들입니다.

Objective-c나 rx는 회사, 팀마다 사용하는곳이 차이가있고 신입이나 주니어기준으로 필수라고 여겨지지않기에 옵셔널에 추가하였습니다.

## MRC
- ARC 대신 Manual Reference Count 방식으로 구현할 때 꼭 사용해야 하는 메서드들을 쓰고 역할을 설명하시오.
- retain 과 assign 의 차이점을 설명하시오.
- 특정 객체를 autorelease 하기 위해 필요한 사항과 과정을 설명하시오.
- Autorelease Pool을 사용해야 하는 상황을 두 가지 이상 예로 들어 설명하시오. 
- 다음 코드를 실행하면 어떤 일이 발생할까 추측해서 설명하시오.
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];

## Advanced
- method swizzling이 무엇이고, 어떨 때 사용하는지 설명하시오.
- NSCoder 클래스는 어떤 상황에서 어떻게 써야 하는지 설명하시오.
- Responder Chain 구조에 대해 설명하고, First Responder 역할에 대해 설명하시오.
- NSObject부터 UIButton 까지 상속 과정의 계층과 역할을 설명하시오.
- shallow copy와 deep copy의 차이점을 설명하시오.
- Push Notification 방식에 대해 설명하시오.
- Foundation 과 Core Foundation 프레임워크의 차이점을 설명하시오.
- NSURLConnection 에서 사용하는 Delegate 메서드들에 대해 설명하시오.
- Synchronous 방식과 Asynchronous 방식으로 URL Connection을 처리할 경우의 장단점을 비교하시오.
- Plist 파일 구조와 Plist 파일에 저장된 데이터를 다루기 적합한 클래스를 설명하시오.
- Core Data와 Sqlite 같은 데이터 베이스의 차이점을 설명하시오.
- JSON 데이터를 처리하는 방식과 파서, 객체 변환 방식에 대해 설명하시오.
- 웹 서버와 HTTP 연결을 사용해서 데이터를 주거나 받으려면 사용해야 하는 클래스와 동작을 설명하시오.
- Protocol에서는 왜 var만 되는지 설명하시요.

## Objective-C
- Swift의 클로저와 Objective-C의 블록은 어떤 차이가 있는가?
- Mutable 객체과 Immutable 객체는 어떤것이 있는지 예를 들고, 차이점을 설명하시오.
- dynamic과 property 의미와 차이를 설명하시오.
- @property로 선언한 NSString* title 의 getter/setter 메서드를 구현해보시오.
- @property에서 atomic과 nonatomic 차이점을 설명하고, 어떤것이 안전한지, 어느것이 기본인지 설명하시오.
- @property로 선언한다는 것의 의미를 설명하고, .h에 넣을 경우와 .m에 넣을 경우 차이점을 설명하시오.
- -performSelector:withObject:afterDelay: 메시지를 보내면 인자값의 객체는 retain되는가? 그 이유를 함께 설명하시오.
- Objective-C 에서 캡슐화된 데이터를 접근하기 위한 방법들을 설명하시오.
- Fast Enumeration 이란 무엇인지 설명하시오. 
- unnamed category 방식에 대해 설명하시오.
- Category 확장과 Subclass 확장의 차이점을 설명하시오.
- Category 방식에 대해 설명하시오.
- Objective-C 에서 Protocol 이란 무엇인지 설명하시오.
- Objective-C++ 방식이 무엇인지 설명하고, 어떤 경우 사용해야 하는지 설명하시오.

## Rx
- Reactive Programming이 무엇인지 설명하시오.
- RxSwift에서 Hot Observable과 Cold Observable의 차이를 설명하시오.
- Subject와 drive의 차이를 설명하시오.

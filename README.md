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

willFinishLaunchingWithOptions -> 앱이 최초 실행될때
application(didFinishLaunching) -> 앱이 사용자 화면에 보여지기 직전에
applicationWillResignActive -> 앱이 Active 에서 InActive 로 전환될때
ApplicationDidEnterBackground -> 앱이 백그라운드 상태일때
applicationWillEnterForeground 앱이 foreground 로 진입할때
applicationDidbacomActive 앱이 active 상태가 되어 실행중일때
applicationWillTerminate 앱이 종료될 
```

### 상태 변화에 따라 다른 동작을 처리하기 위한 앱델리게이트 메서드들을 설명하시오.
```
![image](https://user-images.githubusercontent.com/42457589/143516394-45e78432-1f52-41cb-91bd-5824a1dafe75.png)

willFinishLaunchingWithOptions -> 앱이 최초 실행될때
application(didFinishLaunching) -> 앱이 사용자 화면에 보여지기 직전에
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
### UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?
```
```
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
### iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?
```
UIKit - 앱의 기본적인 UI를 만드는데 필요한 툴을 제공해주는 FrameWork 입니다.
앞에 UI가 붙은 클래스들을 사용하려면 UIKit 프레임워크를 import 해야합니다.
제스처, 애니메이션, 그림그리기, 이미지 처리, 텍스트 처리등을 합니다
```
### Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.
```
CocoaTouchFramework 에 포함되어있는 프레임워크중 하나로 String, Int 등 원시데이터 타입과
컬렉션타입 및 운영체제 서비스를 사용해 앱의 기본적인 기능을 관리하는 프레임워크입니다.
String ,date, collection 등을 사용할때 필요합니다.
```
### Delegate란 무언인가 설명하고, retain 되는지 안되는지 그 이유를 함께 설명하시오.
```
클래스의 기능을 다른 클래스에게 구현하도록 권한을 위임하는 것으로 
UITableView 같이 변동성 있는 데이터를 표시하는 경우 
UITableViewController 에서 디테일한 사항 구현을 데이터를 다루는 클래스에게 위임할수 있습니다.
참조변수를 사용하기때문에 retain이 가능합니다.
```
### NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.
```
사용자나 앱 내부적으로 알림을 주고받을때 NotificationCenter에 알림을 등록하여 대상에게 시그널을 보냅니다.
앱 내부적으로 객체간 알림을 주고받을대 NotificationCenter 에 identifier를 등록하고 observe 하여 
객체간 서로 알림을 주고받을 수 있으며
사용자에게 push 알림을 보내기위해 trigger에 request 를 등록하기도 합니다.
내부지역 적으로 LocalNotificationCenter를 이용하며
```
### UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?
```
메인스레드이며 모든 UI변경사항은 메인스레드를 거쳐 수정되어야 합니다.
global 스레드나 기타 백그라운드 스레드를 사용하면 오류가 납니다.
```
### App Bundle의 구조와 역할에 대해 설명하시오.
```
애플리케이션 번들은 애플리케이션의 성공적인 작동에 필요한 모든것을 저장합니다.
ios/mac 플랫폼에 따라 번들의 구조는 다양하지만 사용법은 동일합니다.

구조에는
AppName,
Icon, 
InfoPropertyList, 
Launch image(애플리케이션의 초기 인터페이스를 특정방향으로 표시하는 하나이상의 이미지),
MainWindow(시작시 로드할 기본 인터페이스 객체),
Setting.bundle (애플리케이션에 추가할 애플리케이션 별 기본 설정이 포함된 특별한 유형의 플러그인)
커스텀리소스파일 (nib파일, 이미지, 사운드, 설정파일 )
```
### 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?
```
UIResponder 이며
역할은 
기본데이터의 변경에 대한 응답으로 뷰의 콘텐츠를 업데이트,
뷰와 사용자의 상호작용에 응답,
뷰 크기조정 및 전체 인터페이스 레이아웃 관리,
앱에서 다른 뷰 컨트롤러를 포함한 다른 객체와 조정
```
### 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.
```
UIView 를 상속한 클래스를 생성한 후 xib 파일을 연결합니다.
그리고 bundle.loadNibNameed 에 이름을 등록하고
생성자에 추가하고자 하는 view 객체를 추가합니다.

혹은 클래스 앞에 @IBDesignable 키워드를 추가합니다.
속성값을 변경하려면 속성값 앞에 @IBInspectable 키워드를 추가합니다.
```
### View 객체에 대해 설명하시오.
```
사용자 인터페이스의 기본 구성요소입니다.
화면의 직사각형 영역에 대한 콘텐츠를 관리하는 객체로 
모든 뷰에 공통적인 동작을 정의하며 모든 뷰 클래스의 상위 클래스입니다.
```
### UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.
```
 UIView 는 화면에 그리는 작업과 애니메이션 등의 시각정 행위를 직접 처리하지 않고 
 CoreAnimation 클래스인 CALayer 에게 위임하는데 UIView 는 해당타입의 layer 프로퍼티를 가지고있다.
 그림자, 테두리, 3D 변형, 마스킹, 애니메이션등의 작업을 처리한다
```
### UIWindow 객체의 역할은 무엇인가?
```
사용자 인터페이스에 배경을 제공하고 중요한 이벤트처리행동을 제공하는 객체입니다.
앱 View의 프레젠테이션에 중요하며 스크린에 나타나는 모든 View 는 윈도우로 묶여있습니다.
앱의 콘텐츠를 표시할 기본 영역을 제공해주며 
추가로 표시할 콘텐츠가 생기면 윈도우를 추가합니다.
```
### UINavigationController 의 역할이 무엇인지 설명하시오.
```
여러개의 사용자 뷰를 Stack에 순서대로 저장하여 화면을 이동할수 있도록 관리해주는 객체입니다.
네비게이션 바와 툴바를 표시해주기도 합니다.
navigation item 을 수정하여 버튼과 타이틀 등을 수정할수 있습니다.
```

### TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.
```
TableView 의 UITableView Delegate 는 UITableView Delegate 프로토콜을 채택하여 
테이블 뷰의 시각적인 요소를 관리합니다. 필수 구현 메소드는 없습니다.

TableView 의 TableViewDataSource Delegate 는 TableViewDataSoucreDelegate 프로토콜을 채택하여
테이블의 데이터와 관련된 부분을 관리합니다.
cellRowAt 메소드
numberOfRowInSection 메소드
를 구현해야합니다.
```
### 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.
```
cellForRowAt 메소드에서
switch 문을 사용해 테이블뷰의 종류를 구분하거나
tag 값을 사용해 테이블뷰를 구분합니다.
```

### setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.
```
layoutSubviews는 UIView의 인스턴스 메소드입니다. 이 메소드가 호출되면 해당 view와 subView들이
모두 연달아 호출됩니다. 이는 비용이 많이 들기 때문에 직접 호출하는것은 지양해야 합니다. 
이 메소드는 view의 값이 재계산되어야하는 적절한 시점에 시스템에 의해 자동으로 호출됩니다.

추가로 UIViewController내의 view가 layoutSubviews() 메소드를 호출하게 되면 값이 갱신되고 이후 
UIViewController의 viewDidLayoutSubviews()가 호출됩니다. 
갱신된 view의 값에 의존하는 행위들은 이 메소드 내에 명시해줘야 합니다.

다음과 같은 상황에서는 시스템이 자동으로 size 혹은 position이 변경되야하는 view라고 체크를 하고 
update cycle에서는 layoutSubviews()가 호출되어 체크된 view들의 변경사항을 반영합니다.

- view의 크기를 조절할 때
- Subview를 추가할 때
- 사용자가 UIScrollView를 스크롤할 때
- 기기를 회전할 때
- view의 autolayout constraint값을 변경할 때
위에 나열된 시점에는 자동으로 update cycle에서 layoutSubviews()를 호출하는 행위를 예약하는 것입니다. 

setNeedsLayout()메소드와 setNeedsDisplay() 메소드 모두 호출 즉시 실행되지 않고 
다음 update cycle에 변경사항이 적용됩니다. 
- setNeedsLayout은 layoutSubview메소드를, 
- setNeedsDisplay는 draw메소드를 시스템이 호출하게끔 유도한다. 

- setNeedsLayout()메소드는 모든 핸들러가 종료되고 권한이 main run loop로 돌아오는 시점에 view의 position이나 layout에 관한 변화를 적용시키고 
- setNeedsDisplay()메소드는 다음 드로잉 사이클이 오면 그 때 쌓여있는 그려야할 컨텐츠들을 동시에 적용시킵니다.
```
###
### NSCache와 딕셔너리로 캐시를 구성했을때의 차이를 설명하시오.
```
NSChache 는 메모리 관리가 기본적으로 제공된다
다른 앱에서 메모리를 사용하려고 하면 캐시되어있던 데이터를 지우고 메모리를 해제한다

NSCache 는 Tread-safe 하다
캐시데이터를 읽고 쓰고 지울때마다 lock을 해줄 필요가 없다.
반면 NSDictionary 는 Thrade-safe 하지 않기 때문에 데이터 접근할때 따로 처리해줘야한다.

NSDictionary 는 Key값을 복사하지만 NSCache는 retain 카운트만 증가시킨다. 
복사를 지원하지 않는 객체까지 포용한다.
```
### URLSession에 대해서 설명하시오.
```
URLSesison 은 iOS 에서 제공해주는 HTTP를 이용한 네트워킹을 통해 데이터를 주고받을수 있게
도와주는 API 클래스입니다. URLSession은 thread-safty 하기때문에 어떤 스레드에서든
자유롭게 Session 과 Task 를 생성할수 있습니다.
Session 의 configuration 에는
Default - 기본적인 네트워크 구성
Ephemeral - 쿠키와 캐시를 저장하지 않을때
Background - 앱이 백그라운드에서 컨텐츠를 다운로드하거나 업데이트 할 경우 
가 있으며

Task 에는
dataTask - 데이터를 받는 작업수행시 - background 지원 불가
downloadTask - 데이터다운로드
uploadTask - 데이터 업로드
가있습니다.
success code 는 200~299 까지 입니다.
```
### prepareForReuse에 대해서 설명하시오.
```
dequeueReusableCell 메소드를 통해 셀이 재사용 되면서 기존에 사용되던 투명값이나 체크박스 값이 
원하지 않는 셀에 또다시 나타나는경우 prepareForReuse 메서드를 사용해 셀의 속성을 초기화시켜서
방금 언급한 현상을 방지하기위해 사용합니다.
```
### 다크모드를 지원하는 방법에 대해 설명하시오.
```
Assest 에 색상을 만들 때 any 칼라와 darkmode 칼라를 같이 만들어서 다크모드와 라이트모드에 따른
색상을 구별할 수 있습니다.
또한 코드로 UITraitCollection.userInterfaceStyle == .dark 와같이 케이스를 나누어
색상을 변경할 수 있습니다,
viewdidload 메소드에서 view.overrideUserInterfaceStyle = .dark 와 같이 하여 
다크모드 지원을 안할수도 있습니다.
```

## Autolayout
### 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)
```
Anchor를 이용한 방법과
NsLayoutConstraint를 이용한 방법
Visual Format Language 를 이용한 방법이 있습니다. 
특정 문법에 맞게 스트링을 구성하여 오토레이아웃을 정의하는 방식입니다. 
```
### hugging, resistance에 대해서 설명하시오.
```
어떤 레이아웃에 제약조건이 있을 때 허깅 우선순위가 낮은 뷰가 레이아웃의 빈공간에 맞춰 늘어나게 됩니다.
resistance 우선순위가 낮은 뷰는 레이아웃의 제약조건에 따라 크기가 줄어듭니다.
```
### Intrinsic Size에 대해서 설명하시오.
```
뷰의 컨텐츠의 맞추어 생성된 레이아웃의 기본적인 크기입니다.
버튼이나 레이블은 타이틀과 텍스트의 값에 따라 인트리식사이즈가 결정됩니다.
```
### 스토리보드를 이용했을때의 장단점을 설명하시오.
```
레이아웃을 구성했을때 직접적으로 구성화면을 볼수 있으며 
제공되는 인터페이스를 사용하여 편리하게 뷰를 제작할수 있는 장점이 있습니다.
단점은 레이아웃이 많이 들어가는 화면은 뷰를 수정하기 번거로울수 있으며 
앱이 커질수록 속도가 느려집니다 -> 스토리보드를 분리해서 해결
또한 코드로 생성한 뷰에 비해 재사용이 어려우며
스토리보드로 불가능한 작업이 있습니다 예) 그림자나 경계선 색
```
### Safearea에 대해서 설명하시오.
```
탭바나 네비게이션바, 상태바 등이 있는곳을 앱의 화면과 겹치는 부분을 피하기위해 설정한 구역입니다.
```
### Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.
```
left 는 사용자가 바라보는 왼쪽화면이며
leading 은 글자가 시작하는 방향입니다.
```
## Swift
### struct와 class와 enum의 차이를 설명하시오
```
struct 는 기본적으로 값 타입 입니다. 변수가 생성되고 다른 변수에 deep copy를 합니다.
class 는 기본적으로 참조타입입니다. 객체가 생성되고 다른 변수에 할당하면 모두 같은 주소를 바라봅니다.
enum 은 값타입 이면서 생성을 할필요가 없이 바로 사용할수 있습니다. 각 변수에 고유의 비트값이 할당되기 때문에
switch 문같은 분기문에서 빠른 비교를 할 수 있으며 컴파일시점에 에러를 잡아줍니다.
```

### class의 성능을 향상 시킬수 있는 방법들을 나열해보시오.
```
heap allocation 을 피한다
????
```
### Convinience init에 대해 설명하시오.
```
보조 init 기능으로 class 에 init 에는 designated init 와 convenience init 가 있습니다
designated init 에는 모든 변수가 초기화 되야하며 
convenience init 는 초기화된 변수를 customizing 하기위해 호출됩니다.
내부에는 항상 designated init 가 호출되어야하며 
파라미터로 받지않은 값은 임의의 값으로 초기화 할 수 있습니다.
```
### Anyobject에 대해 설명하시오.
```
swift 는 타입에 민감한 언어이기 때문에 특정하지 않은 타입에 대해서 동작하도록 두가지 특별한 타입을 제공합니다.
Any, AnyObject 타입을 사용하면 상속관계가 아닌 클래스라도 타입 캐스팅이 가능합니다.
Any는 함수타입을 포함하여 모든 타입의 인스턴스르 나타낼수 있습니다.
value타입, 클래스,클로저 타입등 모든 타입에 상관없이 저장이 가능합니다.

AnyObject는 모든 클래스 타입의 인스턴스를 나타낼수 있는 프로토콜입니다. 클래스타입만 저장할수 있습니다.
```

### Optional 이란 무엇인지 설명하시오.
```
값이 있을수도있고 없을수도 있는 변수를 생성할때 사용합니다.
변수 생성시 끝에 ? 를 붙여 생성하며 
언래핑 시 문제가 있으면 nil 이 반환되며 문제가 없으면 바인딩 된 객체값이 반환됩니다.
강제 언래핑을 하려면 끝에 !를 붙이면 되며 언래핑 전 if let 구문이나 guard let 구문을 사용하여
nil 값을 체크합니다. 
```
### Struct 가 무엇이고 어떻게 사용하는지 설명하시오.
```
다양한 변수나 메소드를 가진 객체이며 struct XXX{} 형식으로 선언합니다.
생성자를 호출하여 초기화 하며 값에 의한 호출을 합니다.
```
### Subscripts에 대해 설명하시오.
```
class, struct, enum 에서 collection, 순열, list, sequence 등 집합의 특정 맴버 요소에 쉽게 접근하기위한
방법입니다.
struct 안에 subscript 를 생성하고 반환값 과 set 액선을 설정합니다.
생성한 구조체끝에 대괄호와 번호를 붙여 get에서 반환하는 값을 받습니다.
```
### instance 메서드와 class 메서드의 차이점을 설명하시오.
```
instance 메서드는 객체가 생성된 후 사용할수 있는 메서드이며
class 메서드는 객체가 선언되지 않아도 사용할수 있는 static 메서드입니다.
instance 메서드는 오버라이딩이 가능하나 static 의 경우 서브클래스에서 오버라이딩이 불가능합니다.
```
### Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.
```
테이블 뷰를 대표적으로 예를 들을수 있습니다. 테이블뷰에 사용되는 데이터는 유동적이기 때문에
테이블뷰 클래스 내부에 고정된 형식을 미리 지정하기 어렵습니다.
따라서 테이블뷰를 사용하는 뷰클래스에 델리게이트 를 임명하여 테이블뷰를 설정합니다.
```
### Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.
```
싱글톤 객체는 특정 클래스를 공용으로 사용하고싶을 때 생성합니다.
static let shared = ClassName()
처럼 선언하며
주로 환경설정, 네트워크객체, 로그인 정보등 공용으로 사용하는 정보를 객체에 넣어두고
필요할때마다 사용합니다.
```
### KVO 동작 방식에 대해 설명하시오.
```
KVO 는 A 객체에서 B 객체의 변화됨을 감지할수 있는 패턴입니다.
변수에 코드를 붙여 변수가 변경될때마다 코드가 실행되도록 하는 방법입니다.
will set 과 didset 과 유사하지만 타입 정의 밖에서 옵저버를 추가한다는 점이 다릅니다.
NSObject 클래스를 상속하며
변수 앞에 @objc dynamic 을 붙여서 선언합니다.
.observe()와 핸들러를 통해서 변수의 변화를 관찰합니다.
```
### Delegates와 Notification 방식의 차이점에 대해 설명하시오
```
객체간 소통하기위해 사용하지만 Delegate 패턴은 커뮤니케이션 과정을 유지하는 제3의 
객체가 없어서 좋지만 코드가 비효율적으로 길어지고 많은객체를 컨트롤하기 어렵습니다.
반면에 Notification 은 커뮤니케이션을 객체와 NotificationCenter 간에 이루어져 한단계를 더 거치지만
많은 객체를 관리하기 쉬워집니다.
```
### 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.
```
작업의 속도와 UI업데이트, 다량의 데이터 처리 등에따라 quality of service를 설정해야합니다
userInteractive - 애니메이션, 이벤트, UI 업데이트등 에 사용되는 서비스입니다.
userInitiated - 불러오기 같은 바로 결과를 보여줘야할때 사용되는 서비스입니다.
utilty - 다운로드 등 오래걸리는 작업을 할때 사용되는 서비스입니다.
background - 백그라운드 작업을 할때 사용되는 서비스입니다.
```
### MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.
```
Controller 가 Model 과 View 를 중계하는 구조입니다.
사용자가 View 를 터치하여 이벤트를 발생시키면 컨트롤러는 이벤트를 감지하여 모델 데이터 업데이트를 합니다.
모델의 데이터가 업데이트되면 컨트롤러는 업데이트된 값을 뷰에 갱신합니다.
```

### 프로토콜이란 무엇인지 설명하시오.
```
구현해야할 기능을 명시한 것으로 프로토콜을 상속한 객체는 프로토콜에 명시되어있는
값이나 메소드를 반드시 구현해야합니다.
```
### Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.
```
Hashable
정수 해쉬 값을 제공하기 위해서 Hasher를 통해 해쉬화 될 수 있는 타입, 프로토콜
반드시 하나만 존재해야하는 딕셔너리의 키 값이나 중복된 값은 허용하지 않는 자료구조인 세트에 
들어가는 값을 정수 값으로 변환하여 각각의 인스턴스를 정수 값을 통해 접근할 수 있도록 해준다.
Equatable
값이 같은지 비교할 수 있는 타입 , 프로토콜
Equatable를 따르는 타입은 ==operator 나 != operator를 통해서 인스턴스 값의 동일성을 비교할 수 있음

Hashable은 반드시 유일한 값을 가져야 하기때문에 Equltable 을 상속하여 비교할수 있어야 합니다.
```
### mutating 키워드에 대해 설명하시오.
```
값 타입 속성은 인스턴스 메서드 내에서 수정될수 없지만 메서드 앞에 mutating 을 붙이면
값타입이 let 으로 정의되지 않은 호출된 값이 수정될수 있습니다.
```
### 탈출 클로저에 대하여 설명하시오.
```
함수의 인자로 전달된 클로저가 함수가 반환된 후 실행이 되는 클로저를 의미합니다
보통 비동기 처리를 위하여 많이 구현합니다.
클로저를 매개변수로 갖는 함수를 선언할 때 매개변수 이름 콜론 뒤에 @escaping 키워드를 사용하여 명시합니다.
```
### Extension에 대해 설명하시오.
```
클래스에서 기본적으로 구현된 기능 외에 추가하고싶은 기본 메소드를 생성할때 class 앞에 extension 구문을 붙인후
메소드를 생성합니다. 변수는 생성하지 못합니다.
```
### 접근 제어자의 종류엔 어떤게 있는지 설명하시오
```
open, public - 어디서나 사용이 가능하며 open 이 더 높은 개념입니다.
internal - 모듈 안에서는 어디든지 사용이 가능하지만 외부에서는 불가능합니다.
file private - 정의된 파일 안에서만 사용이 가능합니다.
private - 정의된 클래스 안에서만 사용이 가능합니다.
```
### defer란 무엇인지 설명하시오.
```
메서드 안의 코드가 모두 실행되고 난 후 마지막으로 실행되는 구문입니다.
현재 스코프를 벗어날때 실행된다는 말입니다.
```
### defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.
```
스택형식으로 호출되어 마지막으로 선언된 defer 부터 호출되며 
defer 구문이 호출되기전 try 구문에서 에러를 throw 하면 호출되지않습니다.
```
### property wrapper에 대해서 설명하시오.
```
property 를 가질수 있는 class, struct, enum 앞에 붙이며 중복된 get이나 set 로직을 묶어서 재사용할수 있게 해주는 것입니다.
변수 이름을 wrappedValue 로 선언합니다.
```
### Generic에 대해 설명하시오.
```
타입에 유연하게 대처하기위해 만들어진 기능으로 구현한 기능과 타입은 재사용이 가능합니다. 예를들어 swap 메서드를 작성할 시
String 타입을 swap 하는 메소드
int 타입을 swap 하는 메소드를 작성하는 대신
제너릭 타입을 사용하는 함수하나를 작성하여 코드를 줄일 수 있습니다.
func swap<T:Equatable>(_ a : inout T, _ b: inout T)
```
### Result타입에 대해 설명하시오.
```
에러를 비동기적으로 처리하기 쉽도록 result 타입을 정의하여 사용합니다.
.............
```
### Codable에 대하여 설명하시오.
```
Encodable 과 Decodable 이 합쳐진 것으로 
Encodable 은 데이터를 원하는 프로토콜로 변환해주며
Decodable 은 프로토콜형식의 변수를 원하는 데이터로 변형해줍니다.
```
## ARC
### ARC란 무엇인지 설명하시오.
```
ARC는 Auto Reference Counting의 약자로, 앱의 참조메모리를 자동으로 관리하는 역할을 합니다. 
과거 Obj-c를 사용할때는 release, retain과 같은 코드를 수동으로 삽입해주었지만, 
ARC는 컴파일 타임에 자동으로 retain, release 등을 코드에 삽입하고, 
런타임때 이들을 실행하여 reference count를 증감시킵니다. 
만약 reference count가 0이 되면 deinit을 통해 메모리에서 해제합니다.
```
### Retain Count 방식에 대해 설명하시오.
```
instance 가 할당되면 retain count 가 증가하며 더이상 instance 를 참조하는 객체가 없으면
retain count 가 감소합니다.
```
### Strong 과 Weak 참조 방식에 대해 설명하시오.
```
만약 인스턴스 A가 다른 인스턴스 B를 강한참조하고 있을때
객체 B의 deinitial 은 app 의 크래쉬를 발생시킬 위험이 있기 때문에 
Deinit 이 되지 않습니다
하지만 약한참조로 참조하고있다면 서로의 참조는 끊어지고 객체 B는 Deinit 됩니다. 
```
### 순환 참조에 대하여 설명하시오.
```
인스턴스 A가 인스턴스 B를 참조하고 인스턴스 B가 인스턴스 A 를 참조할때 
순환참조가 발생합니다. 서로 얽혀있기 때문에 메모리의 낭비가 심하게 될수 있는 위험이 있습니다.
```
### 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.
```
인스턴스 A와 인스턴스 B가 서로를 strong reference 할때 발생합니다.
서로가 강하게 참조하고 있기때문에 deinit 이 불가능합니다.
이럴때에는 약한참조를 사용하여 문제를 해결해야 합니다.
```
## Functional Programming
### 함수형 프로그래밍이 무엇인지 설명하시오.
```
변경 가능한 상태를 불변상태로 만들고 모든것을 객체로 다루며 코드의 구독성을 높이고 동시성작업을 보다 쉽게하는 프로그래밍 기법입니다.
함수형 프로그래밍에서는 함수도 객체로 취급하며 함수의 파라미터에 함수를 전달할수 있습니다.
변경 가능한 상태를 불변상태로 만든다는 것은 어떤 로직을 단순히 명령어로 구현하지 않고 함수로 만들어 구현하자는 의미입니다.
```
### 고차 함수가 무엇인지 설명하시오.
```
함수를 인자로 취급하거나 반환하는 함수를 말합니다. 스위프트에서 고차원함수는 map,filter,reduce 등이 있습니다.
```
### Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.
```
map - 맵은 자신을 호출할 때 매개변수로 전달된 함수를 실행하여 그 결과를 다시 반환해주는 함수이다. 
filter - 필터는 말 그대로 컨테이너의 내부의 값을 걸러서 추출하는 역할을 한다.
reduce - 리듀스는 컨테이너 내부의 컨텐츠를 하나로 합하는 기능을 실행한다.
compactmap - 컴팩트 맵은 매개변수로 전달된 클로저가 옵셔널 값을 생산할때(produce) 사용한다. 
시퀀스의 각 요소를 전달받은 클로저에 적용하고 nil이 아닌 값들만 배열 추가한 후 반환한다.
flatMap - 플랫 맵은 시퀀스의 각 요소들에 매개변수로 전달된 클로저을 적용하여 연속적인(concatenated) 값을 가지는 배열을 반환한다.
```
## Architecture
### MVVM, Ribs, VIP 등 자신이 알고있는 아키텍쳐를 설명하시오.
```
MVVM
Model View ViewModel

View 는 ViewModel 을 바라보고
ViewModel 은 Model을 바라봅니다.
View 에 표시되는 값은 ViewModel 이며 
ViewModel 은 Model을 화면에 나타나는 값으로 가공한 데이터입니다.
Model 은 외부 저장소나 내부 데이터 베이스등의 데이터를 
취급하기 쉬운 자료형으로 변환한 데이터입니다.
의존성의 방향이 View -> ViewModel -> Model
이기때문에 변경사항이 생기면 코드수정이 수월해지는 장점이 있지만 
데이터가 많으면 코드가 길어질수 있다는 단점이 있습니다.
```
### 의존성 주입에 대하여 설명하시오.
```
의존성 : Class B 에서 Class A 의 인스턴스를 생성하면 B 는 A 에 의존적인 관계입니다.
주입 : 외부에서 객체를생성하여넣어주는 것입니다.
의존성 주입 : 내부에서 만든 객체를 외부에서 주입하게 만드는 패턴입니다.
```

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

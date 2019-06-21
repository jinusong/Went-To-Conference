# 2019 GDG Android Io Extended

## 소개
2019년 구글 스타트업 캠프에서 열린 019 GDG Android Io Extended 에서 여러 발표들을 보고 들은 것을 메모한 문서입니다.

## 새로운 Android 훑어보기
* Android Dark Theme

* 커스텀뷰

* xml

* ViewBinding

* 새로운 플레이스토어 정책

* Kotlin first


* 정리: 이번에 Google io 에서 Android가 많이 바뀐 내용을 한번에 발표하셨다. View와 관련된 것들이 많이 바뀐 것 같다.
* 느낀점: 늦게와서 제대로 못들었다. ㅠ 


## Kotlin Under the Hood
* Kotlin이 프로퍼티를 사용해서 getter, setter를 사용하지 않는다는 것은 알았는데 코틀린 코드가 바이트코드로 바뀌고 자바코드로 디컴파일 된 결과를 보니까 이제야 완전히 이해가 되었다.

* open class의 기원을 들었는데 언어 디자이너들이 상속에 대한 안좋은 습관을 막기 위해 언어적 차원에서 막았다는 걸 처음 알았다.

* enum은 효과적이고, UsignInt같은 실험적인 기능이 있다.

* class Delegation이 있는데 이걸 사용하면 코드가 엄청 짧아진다. 짱이다.

* Extension function은 내가 제일 좋아하는 Kotlin의 기능이었는데 여기서 한번 더 설명해주었다. Static으로 되어있으니 주의하라고 하였다.


* 정리: Kotlin을 쭉 훑어봤다
* 느낀점: 다 아는 내용이었다. 근데 주의할점을 알려주셔서 좋았다. 짱. 

## Android Accessibility
* Accessibility == 접근성, 또 접근성이다. 저번에 슈퍼 이닛에서도 접근성에 대해서 들었는데 이번에 또 듣게 되었다.

* 요즘 장애인의 수가 많아지면서 개발을 할 때 접근성을 많이 고려해야 한다고 한다.

* Dark Theme도 접근성을 고려해서 나온 것

* 예전에도 Talk back에 대해서 들었는데 이 것도 설명해주셨다. 그리고 Screen Search가 나왔다고 한다.

* 가장 빠르게 접근성을 구현하는 방법은 대체 텍스트를 달아주는 것이다. 대체 텍스트는 contentDescription 태그에 텍스트를 달아주면 된다.

* 색 대비도 고려해야 하고 버튼의 크기도 고려해야 장애인분들이 좀 더 편리하게 서비스를 이용하실 수 있다.

* 정리: 접근성을 무조건 완벽하게 지켜야 된다가 아닌 빠르게 접근성을 지키는 법을 알려주셨다. 그에 따른 중요도도 알려주었다.
* 느낀점: 감동적이다. 내가 개발자로서 사회에 긍정적인 영향을 미칠 수 있다는 것에 큰 매력을 느낀다.

## Privacy Changes in Android Q
* Android Q에서 Backgound App launching 등 보안에 관한 업데이트가 많이 되었다.

* Background에서 사용자에게 중요한 데이터를 전달시키고 싶다면 PendingIntent를 이용하여 전달할 수 있다.

* setFullScreenIntent를 사용하면 해당 notification이 자동으로 나타나고 그 안에 PendingIntent를 넣어 사용할 수 있다.

* PendingIntent는 Intent를 래핑하는 것인데 Notification은 Intent를 건드릴 수 있는 권한이 없기 때문에 PendingIntent를 사용하여 Intent를 간접적으로 사용할 수 있도록한다.

* RemoteView는 Click 이벤트를 사용할 수 없고 PendingIntent로 BroadcastReceiver를 이용하여 이벤트를 전달합니다.

* 한마디로 이제는 Background에서 App을 사용할 수 없고 Notification을 이용하여 데이터를 전달해야 한다.

* 또, 이제 더 이상 하드웨어에 대한 정보를 가져올 수 없고 얻고 싶다면 SSAID를 사용해야 한다.

* SafetyNet Attestaion API를 사용하면 이 기기가 안드로이드기기 인지 아닌지 판별할 수 있지만 절차가 불편하다.


* 정리: 안드로이드의 보안이 강력해지면서 변화에 맞게 어떻게 대응해야하는지 알려주었다.
* 느낀점: 보안이라고 생각하니까 좀 거리가 멀줄 알았는데 듣다 보니까 내가 개발할 때 꼭 알아야 하는 점들이 있어서 재미있었다.

## What's New in Shared Storage
* Shared Storage는 외부 저장소인데 다른 앱들에게 노출이 되는 저장소이다.

* Better attribution(파일 관리를 더 쉽게), Protect app data(앱 데이터 보호), Protect user data(유저 데이터 보호)와 같은 원칙을 기반으로 Shared Storage를 발전시켜나가겠다고 구글은 발표했다.

* Q에서 내부 저장소는 변화가 없고 외부 저장소에서 많은 변화가 발생하였다.

* MediaStore는 추가 권한 없이 사용 가능하고 파일의 구분이 명확해졌다.

* Scoped Storage를 발표로 Scoped mode로 /sdcard 영역에 직접 접근이 불가해졌다. 

* 개별 앱의 공간이 변경되었고 추가 권한 없이 읽고 쓰는 것이 가능 파일 경로로 직접 접근하는 것은 가능하지만 다른 앱이 접근하는 것은 불가능해졌다.

* 공용저장 공간이 변경되었고 Public Files 공간이 모두 사라졌고 MediaStore나 Storage Access Framework를 이용 가능해졌다.

* scoped mode를 적용하는데 시간이 많이 걸린다고 개발자들은 얘기 했고 구글은 앱타겟을 Q로 했을 때 scope mode가 작동하게 하였고 임시로 예전 저장소를 유지할 수 있다고 한다. 내년엔 무조건 scope mode를 써야 됨.

* Audio, Video, Image를 MediaStore에 저장한다. 다른 앱에서 접근이 가능하고 앱이 삭제되어도 데이터는 그대로 있다. 유지가 필요없는 파일들은 MediaStore에 저장하지 않아도 된다.

* Download 컬렉션에서도 변화가 발생했고 MediaStore는 권한이 필요가 없다.

* Media Storage를 구현할 떄 IS_PENDING를 사용하여 다른 앱에 대한 공개 여부를 설정할 수 있고, resolver를 이용하여 파일 전달이 가능하다.

* 기존에는 파일 디렉토리 저장 위치를 설정하여 저장했지만 이제는 Media Storage는 알아서 잘 구분하고 저장을 한다.

* MediaStore의 getExternal~~ 함수를 이용하여 어떤 것을 불러올 것인지 정할 수 있다.

* 이제부터는 ContentResolver를 이용하여 query()를 해야 하고 Pending 파일은 기본적으로 숨김처리 된다.

* MediaStore에서 Uri를 얻은 뒤 그 Uri를 이용하여 query를 진행할 수 있고 데이터를 load 할 수도 있다.

* 권한이 없다면 RecoverableSecurityException가 발생하여 우리는 이 예외를 통해 예외시 처리할 동작을 작성하면 된다.

* 이제 Q에서는 바로 미디어 파일에 있는 location metadata를 얻을 수 없고 ACCESS_MEDIA_LOCATION 퍼미션을 앱에 추가해서 metadata를 얻을 수 있다.

* Storage Access Framework도 이제는 활용하는 것이 좋다. 공통된 시스템 파일 선태기 사용 가능하고 일관된 파일 검색 기능을 가지고 있다. 클라우드도 접근 가능하다.

* OPEN_DOCUMENT, OPEN_DOCUMENT_TREE 권한을 얻는다면 파일 접근 권한을 얻어 파일을 읽고 쓸 수 있다. 물론 파일 추가 삭제도 가능이다.


* 정리: 이번에 가장 많이 변화된 Shared Storage에 대한 많은 이야기를 해주셨다.
* 느낀점: 정말 많은 이야기인데도 불구하고 너무 잘 설명해주셔서 잘 이해할 수 있었다. 이번에 메모장 어플을 만들어볼 생각인데 거기에 scope mode를 적용시켜보고 싶다.

## Flutter X ML Kit
* 듣고 싶었지만 시간 상 못듣고 갔습니다 ㅠㅠ
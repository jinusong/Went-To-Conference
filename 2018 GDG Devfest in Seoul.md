## 소개

2018년 세종대학교에서 열린 GDG Devfest Seoul의 Mobile관련 발표들을 들으면서 제가 이해한 대로 정리한 문서입니다.

## 1. Data Uni-Directional Architecture in Android

**발표자료**: http://bit.ly/DevFest-UDA

**샘플코드**: https://github.com/maryangmin/GDG-Flux-Redux-MVI


여러 액션이 발생하면서 데이터를 비동기로 처리할 때 작업의 끝나는 지점 등을 예측할 수 없기에 State와 View가 서로 엉키는 경우가 발생

* **Flux**: 페이스북에서 만든 것 (웹에서 주로 이용) 데이터를 단방향으로 처리 - Dispatcher가 있음 - Store에서 View를 참조
* **Redux**: Flux에서 고안한 State 관리 라이브러리, 동기적 실행(웹에서 주로 이용) - Dispatcher가 없음 - State를 변경하지 않음 - 함수인 Reducer
* **MVI**: View가 Intent로 Model에 전달하고 Model은 View만 변화 시키고 View는 State를 참조한다. View와 State 분리

MVP에 간단하게 UDA를 적용했을 시 View는 Presenter에 액션을 전달하고 Presenter는 State에 전달 후 View는 State를 구독하여 View를 갱신

* **정리**: 한번 공부해보면 괜찮을 듯한 발표였다. 특히 MVI라는 아키텍쳐를 한번 쯤 프로젝트에 적용해보는 것도 좋을 것 같다.
* **느낀것**: 빨리 Rxjava를 공부해야겠다는 생각이 들었다. 
또한 몇가지의 아키텍쳐 패턴만 아는데에 그치지 않고 매번 새롭게 나오는 패턴도 적용하면 좋을 것 같다는 생각이 들었다.

## 2. 함수형 프로그래밍과 안드로이드 테스팅

이 발표는 UI테스팅이 아닌 Local 테스팅을 다루고 있다.
테스팅을 하기 위해서는 안드로이드에 의존성을 가지고 있는 코드들을 구분할 수 있어야 한다.

MVVM 패턴에 적용시켜 볼 수 있다.
* (1) 테스트 불가능한 코드는 View에 작성한다.
* (2) View는 최대한 passive하게 작성한다.
* (3) 함수내부에서 테스트 외부 변수의 사용을 최대한 줄인다.
* (4) 함수는 리턴값을 가지고 있어야한다.

* **정리**: 함수형 프로그래밍과 안드로이드 테스팅은 많은 관련이 있다. 클래스 내에서 변수를 사용하지 않는 순수함수 형태로 코딩을 해야하며, 입출력관계를 명확히 해야한다.
* **느낀 것**: 아키텍쳐 패턴을 깊게 공부해야겠다. 또, 내가 함수형 프로그래밍에 대한 오해를 가지고 있었다는 것을 알게 되었다. 

## 3. Flutter 101

구글에서 발표한 크로스 플랫폼 SDK로 한번에 코드 작성으로 IOS와 안드로이드 앱을 만들 수 있다.

Flutter는 Dart라는 언어를 사용하여 개발한다. - 자바스크립트와 매우 흡사 하지만 타입이 있다.

UI를 위젯으로 뽑아주기만 해도 사용 가능하며, 디자이너는 IOS와 안드로이드 디자인을 만드데에 어려움이 있지만 이것을 해결해줄 수 있으며,
별도의 도구없이 프로토타입을 만들 수도 있다. 

Dart라는 언어는 Dart2까지 발표되었지만 발전속도도 더디지만 앞으로는 flutter를 통해 발전할 것으로 보임.

Flutter의 아키택쳐는 머티리얼이나 다른 디자인을 함께 제공한다.

상속방식 2가지

* Stateless: 그냥 State를 사용하지 않고 View에 쓰는 방식
* Stateful : 마치 안드로이드에서의 MVVM에서 ViewModel을 사용하는 것과 같이 State에 값을 전달하면 그와 동시에 View도 같이 갱신시켜주는 방식

**Flutter vs React Native**

* 속도면: React Native는 느린데 Flutter는 빠른 편임
* 친근성: Flutter의 Dart라는 언어가 기존에 Java를 공부했던 사람이라면 쉽게 할 수 있을 정도로 친근함. - 스타일을 인라인으로 설정해주어야 함.
* 생산성: Flutter는 어느 곳에서 잘못이 일어났는지 알려주는 Flutter 닥터를 제공해주며 설치속도 면에서는 Flutter가 압승이다.
* API: React Native가 API 측면에서 엄청나게 많이 지원해주지만 Flutter가 나온지 얼마 안됐음에도 불구하고 API 지원속도가 빠른편임
* 문서: Google에서 만들다보니까 문서의 업데이트가 빠르고 많이 된다.
* 퍼포먼스: React Native인지 Flutter인지 구분이 안될 정도로 나쁘지 않다.

* **정리**: Flutter라는 플랫폼의 언어인 Dart를 이 발표에서 처음 들었다. 그리고 Flutter는 React Native에 비해 뒤지지 않은 성능을 지니고 있다.나중에 Dart가 발전된 형태로 많은 라이브러리와 API를 가지게 된다면 배울 의향은 있다.
* **느낀점**: 나는 아직 안드로이드도 제대로 못하는데 Flutter를 배울 시기는 아닌 듯하다. 내 생각에 내가 안드로이드를 어느정도 한다고 생각될 때면 Flutter도
함께 발전되어 있을테니 그 때 배워보고자 한다.

## 4. Android DataBinding for Modularization, ViewModel and Testing

DataBinding은
~~~gradle
Databinding{
    Enabled = true
}
~~~
이런 식으로 gradle에 간단하게 추가하면 쉽게 사용할 수 있고 이런 데이터바인딩은 아주 유용하다.

만약 MVP 패턴에 이를 적용한다면 Presenter와 Activity의 xml 코드가 직접적인 관계를 형성하게 되는데

예를 들면
~~~xml
android:text="@{@string/title{presenter.yea}}"
~~~
이런 식으로 사용할 수 있다. 

이외에도  visibility 등에도 @={title != null} 등으로 사용이 가능하다.

**@BindingAdapter**

BindingAdapter는 앞과 같이 어노테이션을 사용하여 Adapter를 만들 수 있다.

이런 데이터 바인딩을 사용하게 되면 양방향 바인딩이 가능하여 실시간으로 쉡게 View 변화에 맞게 대응할 수 있게 된다.

이렇게 Databing을 사용하게 되면 Presenter가 재사용이 가능하게 되면서 MVVM 패턴의 ViewModel로써 사용할 수 있게  된다.

RecyclerView 사용시에도 ViewHolder 클래스를 Header, item, progressive 나눌 것 없이 DataBinding을 통해 관리를 할 수 있게 된다.

Testing에서도 모든 로직인 Business 로직에서 실행되니까 @Test 어노테이션으로 테스팅도 어렵지 않게 할 수 있다.

* **정리**: DataBinding은 쉽게 gradle에 추가할 수 있으며, 아키텍쳐 패턴에 적용시키면 xml의 레이아웃을 바인딩하는 것에 그치지 않고 MVP에 경우 Presenter에, MVVM에 경우에는 ViewModel에 직접적으로 사용할 수 있게 된다. 또한 이번 발표에서 나온 Dirtyflag와 사용하는 예제를 보면 알 수 있듯이 입력과 같이 처리가 가능하고 RecyclerView에 적용할 시에는 관리가 훨씬 편리해진다는 장점이 있다. 추가적으로 테스팅까지 편리해진다.
* **느낀점**: 내가 아직 많이 부족해 발표 내용을 완전히 흡수하지 못한 것 같아 아쉽다. 이번이 내가 더 성장할 수 있게 하는 계기가 되었으면 좋겠다. 또, DataBinding에 대해서는 내가 따로 좀 더 공부 해야겠다.

## 5. Android Oreo & Pie 업데이트하기

* **정리**: 오레오, 파이의 업데이트 사항에 대해서 발표가 진행되었다. 워낙 많은 양의 정보를 한 발표에 담으시다보니 발표가 빠른편이었다. 
아무튼 백그라운드 서비스 센서, Notification의 우선순위, 포그라운드 서비스, 자동 폰트 조절 등 여러 기능들이 추가되었음을 알려주고 몇개는 코드까지 살펴볼 수 있었다.
* **느낀점**: 내가 다 메모하기에는 너무나 많은 내용이었따....
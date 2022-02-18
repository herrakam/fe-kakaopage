# fe-kakaopage

## 크롱 피드백

<hr>

```
  color: white;
```

### <li> 다음엔 색상표현시 실무에서 많이 사용하는 16진수 표기법을 해보세요.

### 16진수표기법(#000000)과 색 이름을 혼합해서 사용했는데, 16진수로 통합해야겠다.

### => 만약 내가 사용하고 싶은 색의 이름은 알지만 16진수표기법을 모를 때, 어떻게 정보를 찾지?

```
.genreHome {
  width: 52.8px;
```

### <li> calc 사용해서 길이 조절하기

### 좀더 페이지를 완벽하게 클론해보기 위해 개발자도구에 찍힌 값을 사용했는데, 좋은 방법이 아니였던 것 같다.

### 아마 다른 `flex`, `grid`, `margin`, `padding` 등으로 나눠지거나 합쳐지는 과정을 거치면서 과 최종적인 길이가 나온걸로 예상되는데, 다음에는 완벽한 클론코딩보다는 실제 사용할만할 값을 기준으로 구현해야겠다.

### 바닐라 css에서도 `calc()`를 사용할 수 있을 지 몰랐다. `calc()`를더 직관적인 계산으로 길이를 구현할 수 있을 것 같다.

```
  width: 142px;
  height: 96px;
```

### <li> css도 중복이 보이면 제거하려고 노력하면 더 좋죠.class를 추가로 만들어서 같이 사용한다던가~

### 이건 이미지 테그의 크기를 조절 하기 위해 부모와 자식에 같은 값을 줬던 것으로 기억하는데, 쉽게 새선할 수 있는 사항인 것 같다.

### 어제 그룹에서 이야기를 나눠보면서 바닐라 css에서도 변수처럼 사용할 수 있다는 걸 알았는데, 이를 응용하는 것도 좋은 방법이 될 것 같다.

```
width:100%. height:100%;
```

### <li> 기본 부모의 100%를 먹을테니 혹시 제거할 수 있으면 제거하세요.

### 해당 코드를 지워봤지만, 지우는 순간 해당 테그의 크기가 꺠졌다. `div`로 감싸지 않고 img 단일로 사용해서 그런 가 하는 생각이 드는데, 부모와 자식의 크기가 동일할 때, 습관적으로 크기를 정해주는걸 지양하고 블록 테그로 감싸서 문제를 해결해야겠다.

<br>

## 크롱에게 물어보기

<hr>

### <li> 클래스 네이밍 문제

### 클래스 네이밍에 대해 3가지 규칙을 찾을 수 있었는데, 리액트를 사용한다면 컴포넌트로 네이밍을 처리하기 때문에 실무에서 이에 대한 중요성이 떨어 질 것 같다는 생각이 들었다.

### <li> 정렬만을 위해 사용하는 flex

### 블록 테그를 인라인 테그처럼 사용하기 위해 사용하는게 아니라 단순히 테그 내부를 정렬하는데 flex를 사용했는데, 이게 성능상에서 비효율적이지 않을까?

### 만약 비효율적이라면, 어떤 방법으로 정렬하는게 효율적인가?

### 성능 차이는 거의 없고, 그냥 편하게 사용해도 된다는 답변을 받았다. 개꿀

## 공부해볼 개념들

### css 변수

### hide ??

### 디자인 페턴을 그대로 사용하지 마라!! 장단점, 사용하고 나서 개선된 점 등을 파악해야 된다.(ex: bem을 사용했을 때의 장단점? 개선된 점? 호환은 잘 되나?)

### 클래스가 많아지는건 아주 좋은 현상이다!!

### 가상 엘리먼트: 간단한 작업 스크립트 없이 사용!

### 커밋 굳이 영어로 할 필요 없음!

### 가장 가까운 요소를 찾아주는..

# step2

## 구현해야 할 기능

<br>
- [x] navBar 텝 클릭시 해당 텝만 노란색 밑줄, 다른 테그는 밑줄 빼기

### 1. onclick 이벤트로 해당 객체 접근하기

#### 클릭한 테그에 접근할 수 있다면, 하나의 함수 만으로 navbar의 모든 텝에 필요한 함수를 구현할 수 있다고 생각했다

#### 구글링을 해봤지만 만족할 답이 나오지 않았고, 이전 코드들을 살펴보다가 event.target이 생각나서 응용해보았다.

#### 비록 e.target이 아닌 e 만으로 해당 테그에 접근해 event.target 개념을 사용한 게 맞는지 확신을 할 수는 없었지만, 클릭한 텝 밑에 노란색 밑줄을 넣는 것은 성공했다.

### 2.nodelist는 배열인데 고차함수를 쓸 수 없다.

### `e.parentNode.childNodes`로 자신을 포함한 모든 형제 테그들을 선택 후, 테그의 밑줄을 없애려 했다

### 배열을 리턴하니 map 함수를 사용하려 했는데, map을 사용할 수 없었다.

### 구글링해 보니, DOM은 특정 언어에 의존하지 않도록 설계되었고, DOM API가 반환하는 모든 유형은 기본 유형이 아닌 호스트 유형이 된다는 걸 알았다.

https://stackoverflow.com/questions/21768551/javascript-why-use-nodelist-instead-of-using-array

### 그러니 js 고유의 고차함수인 map은 사용할 수 없었다. 기본 for 문으로 대체해서 해결했다.

- [x] 요일 클릭시 요일에 노란 색 밑줄, 아래 웹툰은 요일별 웹툰으로 교체하기

1. 함수 재활용 하기

### 앞에서 구현한 함수를 기능별로 잘 쪼개면 함수를 재활용 할 수 있을 것 같았다.

### 그래서 구현한 함수를 2가지 함수로 나누고, 2가지중 하나에서 나머지 하나를 불러오는 형식으로 리팩토링을 했다.

### 함수를 좀 더 넓게 활용할 수 있었다.

- [x] 장르 텝 클릭시 맞는 정보 가져오기

1. 함수 재활용

### 이 역시도 함수를 재활용 할 수 있을 것 같았지만, html 구조가 달라 그대로 사용할 수 없었다.

### 함수를 리팩토링하는 것 보다는 테그를 리팩토링 하는게 좋은 것 같아 테그를 리팩토링해 함수를 재활용 할 수 있엇다.

2. backgroundImage 변경 안됨

### 처음에 변경되지 않았을 때에는 함수에서 따옴표를 잘 못 쓴 줄 알았다. 그래서 여러가지 경우의 수로 따옴표를 변경해 봤지만, 적용되지 않았다.

### 문제는 배열로 선언한 데이터로 있엇다. 이미지의 url 주소를 템플릿 리터럴을 이용해서 문자열로 선언해 넣어놨는데, 이게 함수의 템플릿 리터럴과 충돌한 것으로 생각된다.

### 다행히 데이터의 템플릿 리터럴을 큰따옴표로 바꾸니 해결되었다.

- [x] navbar 클릭할 때 맞는 데이터 가져오기

1. 이미지로 대체한 결과

### 최대한 본 사이트와 비슷하게 만들기 위해 사이트처럼 nav텝을 이미지로 구현했는데, 텍스트가 없어 원하는 값을 텝에서 찾을 수 없었다.

### navTab에 원하는 텍스트를 삽입 후, `font-size:0`을 통해 안보이게 만들어 정렬에 영향을 주지 않게 해서 해결했다.

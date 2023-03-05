[결과물 페이지](https://posco-test-world.netlify.app/)

## 프로젝트 개요

- 프로젝트 명: Test-World
- 팀 구성: 장경은, 김계환, 박지원, 김민정
- 4가지 테스트를 경험해볼 수 있는 모바일 기준 웹사이트

## 각 페이지별 사용법

### 경력 유형 검사

  - 메인 페이지

    - 좌측 상단 홈 버튼을 누르면 메인 페이지로 갈 수 있습니다.
    - 햄버거 메뉴를 누르면 다른 테스트로 바로 이동할 수 있습니다.
    - 스타트 버튼을 눌러 시작합니다.

  - 테스트 페이지

    - 왼쪽 버튼부터 전혀 그렇지 않다, 그렇지 않다, 보통이다, 그렇다, 매우 그렇다입니다.
    - 본인이 생각하기에 알맞은 정도를 선택합니다.
    - 잘못 대답한 경우 좌측 상단 이전버튼을 누르면 이전 질문에 다시 대답할 수 있습니다.
    - 40개의 질문에 대답하면 결과 페이지가 나옵니다.

  - 결과 페이지

    - 결과 페이지에서는 검사 결과 어떤 경력 유형을 가지고 있는지 알려줍니다.
    - 아래에서는 해당 경력 유형에 대해 설명하고, 관련 직업들이 나열됩니다.
    - 각 유형별 점수가 그래프로 나타납니다.
    - 버튼을 눌러 각 유형에 대한 정보를 볼 수 있습니다.
    - 버튼을 눌러 다시 한 번 검사해볼 수 있습니다.
    - 카톡으로 결과공유, 이미지로 결과 저장, URL 복사를 할 수 있습니다.

### 반응속도 테스트

  -

### Big5 성격 검사

  -

### 색상 구분 테스트

  -

## 기능 설명

### 공통 기능

  - Canvas를 이용한 애니메이션

    - 전체적인 디자인이 픽셀 디자인이기 때문에 이러한 분위기에 맞는 트랜지션 효과가 있습니다.
    - Canvas의 z-index 값이 1이 되면서 width와 height가 num인 사각형을 랜덤 좌표에 반복해서 그립니다.
    - 해당 좌표를 배열에 담아두었다가, setTimeOut을 이용하여 사각형 그리기가 끝났을 시간 쯤에 해당 좌표에 clearRect를 이용하여 다시 사각형을 지워줍니다.
    - Canvas를 리셋하고 배열을 비워줍니다. Canvas의 z-index도 -1로 바꿔줍니다.

  - 이미지로 결과 저장

    - "HTML2CANVAS" 라는 라이브러리를 이용했습니다.
    - 해당 라이브러리를 이용하여 결과 부분에 해당하는 HTML 태그를 캡쳐합니다.
    - 이미지 다운로드를 위해 createElement로 a태그를 만들고 a태그의 href 속성에 해당 이미지 URL를 삽입합니다.
    - 해당 태그를 클릭하여 이미지를 다운로드합니다.
    - 이 기능이 아이폰에서는 작동하지 않기 때문에 Boolean 타입의 전역변수 isIphone을 선언하여 isIphone이 true일 경우 해당 기능은 작동하지 않고 화면 캡쳐를 사용하라는 문구를 띄웁니다.

  - 카톡으로 결과 공유

    - 각 테스트의 결과창에서는 테스트 결과를 카톡으로 공유할 수 있게 했습니다.
    - Kakao SDK를 각 HTML 파일에서 script 태그로 가져왔습니다.
    - kakaoShare() 함수를 선언하여 공유 시 보여질 이미지와 설명 등을 정의해주었습니다.

  - URL 복사

    - url을 변수로 선언합니다. url 변수는 사이트의 주소입니다.
    - navigator.clipboard 요소에 접근하여 writeText() 메소드를 사용하여 url을 넣어주었습니다.
    - 복사가 되면 "복사되었습니다!"를 띄웁니다.

### 경력 유형 검사

  - 메인 페이지

    - Start 버튼을 누르면 Canvas 애니메이션이 나오면서 테스트 페이지로 이동합니다.
    - 각 요소들이 보여지거나 숨겨지는 것은 hide 클래스를 추가했다 지웠다 하는 것으로 구현했습니다. hide 클래스의 CSS 속성은 display: none; 입니다.

  - 테스트 페이지

    - 1개의 질문이 하나의 section 태그로 묶어져 있으며, test 클래스를 가지고 있습니다.
    - 애초에는 모두 hide 클래스를 가지고 있으나, 메인 페이지에서 Start 버튼을 누르면 첫 번째 질문에는 on 클래스가, 두 번째 질문에는 next 클래스가 생성됩니다.
    - 질문에 답을 하면 goNextPage()가 실행됩니다.
    - 다음 페이지로 넘기는 함수 goNextPage()에서는 prev 클래스를 가진 태그가 hide 클래스를 갖게 되고, on 클래스를 가진 태그가 prev를 갖게 되며, next 클래스를 가진 태그가 on을 갖게 되고, next 태그의 인접 형제가 next 클래스를 갖게 됩니다.
    - 이전 페이지로 돌아가는 함수 goPrevPage()도 이와 같은 로직으로 작동합니다.
    - prev 클래스를 가진 태그는 CSS로 translateX(-150%), next 클래스를 가진 태그는 CSS로 translateX(150%)가 적용됩니다.
    - 마지막 질문지일 때 goNextPage()가 실행되면 getResult() 함수를 실행합니다.

  - 결과 페이지

    - 결과는 각 유형 별 점수를 합산하여 100점 만점으로 환산합니다.
    - 다른 유형에 대한 질문이라도 특정 문항은 해당 유형의 점수에서 보너스 점수를 추가하거나 감점시킵니다.
    - 가장 높은 점수를 가진 유형이 userType 변수에 할당되고 이에 따라 summary와 explain 클래스를 가진 태그 안에 요약과 설명이 입력됩니다.
    - 그래프는 애니메이션 시간을 고려하여 setTimeOut을 이용하여 1초 후부터 그려지기 시작합니다.
    - 다시 시작하는 버튼을 누르면 페이지가 새로고침되면서 첫 화면으로 돌아가게 됩니다.
    - 카톡으로 결과 공유는 userType을 매개변수로 전달하여 kakaoShare() 함수에서 해당 유저의 타입에 따른 이미지와 설명을 띄우도록 합니다.

  - 그 외 고민했던 점들

    - [노션 페이지](https://synonymous-island-173.notion.site/Test-World-Front-end-Team-Project-15c51b1b952e4d209a402dc32c98f460)

### 반응속도 테스트

  -

### Big5 성격 검사

  -

### 색상 구분 테스트

  - 

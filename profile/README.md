# 박차고 (Park-Charge-Go)

<img src="https://github.com/SPACE-AXE/pcg-app-front/blob/main/lib/assets/images/logo.png" width="300" height="300">

## 프로젝트 소개

<p align="justify">
프로젝트 개요/동기
</p>

친환경에 대한 사람들의 관심이 높아짐에 따라, 전기차의 수요 또한 가파르게 증가하고 있다. 하지만 전기차의 수요 증가에 비하여 충전 인프라의 부족으로 전기차 사용자의 불편을 초래한다는 것을 알 수 있다. 

우리 'SPACE AXE'팀은 그 중 전기차 충전 요금과 주차 정산 요금을 따로 결제해야 하는 불편함에서 착안하여, 전기차 충전 요금과 주차 정산 요금을 한 번에 결제할 수 있는 시스템, 박차고(Park-Charge-Go)를 제안한다.

### 차별점

기존의 경우 주차 정산 요금과 전기차 충전 요금을 따로 결제해야 하는 시스템이며, 이러한 부분이 전기차 사용자들로 하여금 불편함을 유발하는 원인이 되었다. 박차고의 경우, 별도로 결제하던 요금들을 한 번에 정산할 수 있도록 하여 이러한 불편함을 해소하는 것에 집중하였다.

<br>

## 기술 스택 - 프론트엔드

| Flutter | dart |
| :--------: | :--------: |
| <img src="https://engineering.linecorp.com/wp-content/uploads/2019/08/flutter1.png" width="80px"> | <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Dart_programming_language_logo_icon.svg/2048px-Dart_programming_language_logo_icon.svg.png" width="80px"> |

## 기술 스택 - 백엔드

| NestJS | TypeORM |
| :--------: | :--------: |
| <img src="https://i.namu.wiki/i/X7RPRZJiL_bDk-b5yfaeCqEaINp3iwm7ngVhzN9LDg4hNjz0Bs3QTo7pgbCfGW3xp_sQZxMGUfnxBAXGNFwGKw.svg" width="80px"> | <img src="https://images.velog.io/images/ko1586/post/3ec3b39b-d04b-4bfb-abaf-e4418ecbe4c8/typeorm_logo%20(1).png" width="80px"> |

<br>

## 애플리케이션

## 구현 기능

### 메인 화면

사용자가 애플리케이션을 실행하면 메인 화면으로 이동한다. 메인 화면에서는 로그인, 인근 주차장 조회, 이용 내역 조회, 카드 관리 페이지, 차량 관리 페이지, QR 결제 페이지, 사전 결제 페이지로 이동할 수 있다.

### 자체 로그인

사용자가 로그인 버튼을 터치하면 로그인 페이지로 리다이렉트된다. 사용자는 회원가입 버튼을 터치하여 회원가입을 진행할 수 있고, 아이디 / 비밀번호 찾기 버튼을 터치하여 분실한 아이디를 찾거나 비밀번호를 재설정할 수 있다. 로그인 기능은 회원 결제 및 내역 조회 등의 기능을 제공할 때 사용된다.

### 주차장 조회

'주차장 위치 확인하기' 버튼을 터치하면 네이버 지도 API를 사용하여 공공데이터에 저장되어 있는 주차장 목록을 시 단위로 필터링하여 보여주며, 사용자의 위치 5km 이내에 있는 박차고의 자체 데이터베이스에 내장되어 있는 주차장 목록을 보여준다.

### 카드 관리 / 차량 관리

'카드 관리' 버튼을 터치하여 카드 관리 페이지로, '차량 관리' 버튼을 터치하여 차량 관리 페이지로 이동할 수 있다. 각각의 페이지에서 등록되어 있는 카드 / 차량의 조회, 등록 및 삭제를 수행할 수 있다.

### QR 결제

애플리케이션 하단에 위치한 플로팅 액션 버튼^[1]을 왼쪽으로 슬라이드하면 QR 결제 페이지로 이동할 수 있다. 해당 페이지를 최초로 구동한 유저의 경우 카메라의 권한을 요청하는 팝업 메시지가 발생하며, 권한을 취득하면 카메라를 통해 QR 코드를 인식할 수 있는 상태가 된다. POS에서 발급한 QR 코드를 인식하면 백엔드에서 결제의 유효성 검사를 실행하며, 유효하다고 판단될 경우 기존에 등록되어 있던 카드의 정보를 활용하여 결제를 진행하게 된다.

### 사전 결제

애플리케이션 하단에 위치한 플로팅 액션 버튼을 오른쪽으로 슬라이드하면 사전 결제 페이지로 이동할 수 있다. 해당 페이지에 진입할 시, 사전 결제가 필요한 차량이 입차되어 있는 경우 결제 정보를 화면에 표시한다. 결제 버튼을 터치할 경우, 기존에 등록되어 있던 카드의 정보를 활용하여 사전 결제를 진행하게 된다.

## 전체 시스템 구조

<img src="https://file.notion.so/f/f/ba6f1cad-b823-49e4-9035-0e2c432fab99/d7983893-4497-434a-a85a-fede9dae6b63/%EB%B0%B1%EC%97%94%EB%93%9C_%EC%8B%9C%EC%8A%A4%ED%85%9C_%EA%B5%AC%EC%A1%B0%EB%8F%84.png?id=19b415d5-a239-4fbc-91df-7d45b296d585&table=block&spaceId=ba6f1cad-b823-49e4-9035-0e2c432fab99&expirationTimestamp=1703232000000&signature=xhGhXHyp3Z-ngq8lIo3Rxg10hv57kIq5vT4LFE3pFeU&downloadName=%EB%B0%B1%EC%97%94%EB%93%9C+%EC%8B%9C%EC%8A%A4%ED%85%9C+%EA%B5%AC%EC%A1%B0%EB%8F%84.png">

<img src="https://file.notion.so/f/f/ba6f1cad-b823-49e4-9035-0e2c432fab99/051742e3-87a4-4f27-8bae-1ba6f5ad395f/%EB%B0%B1%EC%97%94%EB%93%9C_%EC%8B%9C%EC%8A%A4%ED%85%9C_%EA%B5%AC%EC%A1%B0%EB%8F%842.png?id=aa870370-8a59-41d8-be2e-b6b3253a173f&table=block&spaceId=ba6f1cad-b823-49e4-9035-0e2c432fab99&expirationTimestamp=1703232000000&signature=jkDA-iXhIcztdgEmHzkvapY_1IKnKLcBAOu2p9lD2LM&downloadName=%EB%B0%B1%EC%97%94%EB%93%9C+%EC%8B%9C%EC%8A%A4%ED%85%9C+%EA%B5%AC%EC%A1%B0%EB%8F%842.png">

## 문제 및 해결 방안

## 한계점 및 보완 계획

## 향후 활용방안 및 기대효과

## 각주

[^1]: 플로팅 액션 버튼: UI 내에 특정 위치에 고정되어 떠있는 요소로 사용자에게 중요한 행동을 언제든지 클릭할 수 있도록 제공한다. 본 애플리케이션에서는 좌우로 슬라이드하여 QR 결제와 사전 결제 페이지로의 이동을 구현하였다.

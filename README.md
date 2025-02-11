# 🤖 async-robot-cafe ☕️
## 소개 
키오스크를 이용해 음료와 케이크를 주문하세요! <br/>
음료 주문이 들어오면 로봇이 음료를 제조합니다. 🤖<br/>
각 로봇은 각자 스레드에서 비동기로 동작합니다. 동시에 동작하는 로봇의 개수는 최대 2대입니다.<br/>
음료 제조가 완료되면, 키오스크에서 주문을 받고 있지 않을 때 음료 제조 완료 알림을 출력합니다. ☕️<br/>

## 클래스 다이어그램
![robot-cafe-Page-2 drawio (2)](https://github.com/user-attachments/assets/8b2a07af-fed4-4829-8d3e-9f468822cfc1)

## 시나리오 
### 키오스크
1. 메뉴를 선택한다.
2. 옵션을 선택한다.
3. 결제 금액을 확인하고 결제한다.
4. 로봇이 맛있게 제조하기를 기다린다.
### 로봇
1. 키오스크에서 주문과 결제를 수행한다. 
2. 음료를 주문하면 로봇이 음료를 제조한다. (케이크는 바로 서빙(=출력)된다.)
    - 하나의 로봇은 하나의 스레드를 할당 받아 동작한다. 스레드는 스레드풀(크기: 2)로 관리한다.
    - 음료 제조 스레드는 sleep() 메서드를 호출해 일정 시간이 지나면 종료된다.
    - 로봇과 키오스크는 비동기로 동작한다.
3. 음료 제조가 끝났을 때 키오스크가 대기 중이면 음료를 바로 출력한다. 
키오스크가 사용 중이면 음료를 리스트에 추가하고, 키오스크 사용이 끝나면 출력한다.

# RobomationLAB 코딩 가이드

# 코딩-가이드

이 문서는 로보메이션에서 개발한 '로봇 동작 스트리밍 서비스를 위한 실행 엔진 및 통합 저작환경' 중 하나인 로봇 코딩 교육용 플랫폼, RobomationLAB(로보메이션 랩)에 대해 설명합니다.  

다음과 같은 순서로 자세한 설명을 제공합니다:
- RobomationLAB의 주요 특징
- RobomationLAB 로봇 프로그래밍 방식
- 로봇 소프트웨어 모델링 원리
- RobomationLAB 로봇 코딩 기분 문법 체계  

<br>

# 목차
1. [RobomationLAB 로봇 코딩 교육 플랫폼](#robomationlab-로봇-코딩-교육-플랫폼)  
    1-1) [로봇 코딩 프로그램](#로봇-코딩-프로그램)  
    1-2) [코딩 프로그램 주요 특징](#코딩-프로그램-주요-특징)  
    1-3) [실시간 로봇 제어 방식](#실시간-로봇-제어-방식)  

2. [RobomationLAB 로봇 프로그래밍 방식](#robomationlab-로봇-프로그래밍-방식)  
    2-1) [순차 실행과 병렬 실행](#순차-실행과-병렬-실행)  
    2-2) [setup 함수](#setup-함수)  
    2-3) [loop 함수](#loop-함수)  

3. [로봇 소프트웨어 모델링](#로봇-소프트웨어-모델링)  
    3-1) [모델링 과정](#모델링-과정)  
    3-2) [Roboid 클래스 정의](#roboid-클래스-정의)  
    3-3) [고유 식별자, urn](#고유-식별자-urn)  

4. [RobomationLAB 로봇 코딩 기본 문법 체계](#robomationlab-로봇-코딩-기본-문법-체계)  
    4-1) [로봇 Device 객체](#로봇-device-객체)  
    4-2) [d 함수](#d-함수)  
    4-3) [c 함수](#c-함수)  
    4-4) [e 함수](#e-함수)  
    4-5) [w 함수](#w-함수)   

<br><br>

# RobomationLAB 로봇 코딩 교육 플랫폼
RobomationLAB은 **AI 로보틱스 SW 교육**에 최적화된 플랫폼으로,  
초등/중학생 대상 로봇 코딩 교육을 위한 Chrome 웹 브라우저 기반의 통합 저작환경을 제공합니다.  

RobomationLAB은  **블록 코딩**, **스크립트 코딩** 등 다양한 방식의 로봇 코딩 교육용 프로그램들을 제공합니다.  
코딩의 이론을 학습할 뿐만 아니라 로보메이션의 제품들을 활용해 실제로 로봇을 움직이고 제어하면서,  
코딩과 로봇을 동시에 학습할 수 있는 기회를 제공합니다.

<br>

## 로봇 코딩 프로그램

### Block Composer (블록 컴포저)
**Block Composer는 블록 코딩을 통해 자사 로봇들을 쉽고 빠르게 제어하며, 로봇 제어의 기초를 학습할 수 있는 도구입니다.**  

- 피지컬 컴퓨징에 최적화된 저작 환경

- 블록 Drag&Drop 방식으로 초보자도 쉽게 코딩 가능  
- 기본 개념부터 문법 오류 없는 학습 환경 제공  
- Javascript, Python 스크립트 코드로 자동 변환  
- 로봇 별로 미리 정해진 기능을 가진 블록 모음과 다양한 체험 예제 제공
- 코드 실행을 통해 실시간 결과 확인 가능  
- 블록 조합으로 문제 해결 능력 및 창의력 향상  
- AI 기반 스크립트 코드 분석을 통해 최적화된 피드백 제공  

<br>

### Script Composer (스크립트 컴포저)
**Script Composer는 스크립트 코딩을 통해 자사 로봇들을 쉽고 빠르게 제어하며, Python, Javascript 문법 및 로봇 코딩의 기초를 학습할 수 있는 도구입니다.**  

- Python, Javascript 에디터 동시 제공

- 언어 별 코드 자동 완성 및 코드 삽입 기능 제공
- 로봇 별 다양한 체험 예제 코드 제공
- 코드 실행을 통해 실시간 결과 확인 가능
- AI 기반 스크립트 코드 분석을 통해 최적화된 피드백 제공

<br>  

## 코딩 프로그램 주요 특징
RobomationLAB에서 제공하는 로봇 코딩 프로그램의 주요 특징은 다음과 같습니다.  
1.	크롬 웹 브라우저 기반으로, OS(운영체제)의 제약을 받지 않음
2.	Web Serial 통신 기반으로, USB 동글을 통해 로봇 하드웨어를 직접 제어
3.	멀티 로봇 동시 제어 지원 - 로봇의 종류, 수 제한 없음
4.	파일 저장 시 결과물은 JSON 텍스트 파일로 변환하여 저장

<br>

## 실시간 로봇 제어 방식
RobomationLAB에서 제공하는 로봇 코딩 프로그램에서는 다음과 같은 과정을 통해 실시간으로 로봇을 제어합니다.  
1.	블록코딩 또는 스크립트 코딩을 통해,
로봇을 제어하기 위한 Effector, Command 객체의 값을 설정하거나
로봇의 Sensor 값 및 Event 발생을 활용하는 코드를 작성합니다.
2.	코드를 실행합니다.
3.	Web Serial 통신을 통해 로봇으로부터 Sensor 및 Event 데이터를 담은 패킷을 받아,
로봇 Device 객체에 반영합니다.
4.	실시간으로 코드를 해석하여,
Effector, Command 객체에 데이터를 덮어쓰거나, Sensor, Event 객체의 값을 읽어옵니다.
5.	로봇 Device 객체의 데이터를 반영한 패킷을 생성한 뒤,
Web Serial 통신을 통해 로봇에 전송하여 실제로 로봇이 동작하는지 확인합니다.
6.	코드가 실행되는 동안, 3 ~ 5 의 과정을 약 10 ~ 20ms 마다 반복 수행합니다.

<br><br>

# RobomationLAB 로봇 프로그래밍 방식

## 순차 실행과 병렬 실행
로봇을 프로그래밍하는 방식에는, 순차 실행 방식과 병렬 실행 방식이 있습니다.  
순차 실행은, 한 동작이 마무리된 뒤에 다음 동작을 수행하는 방식으로, 단순한 행동을 코딩하는 데에 적합합니다.  
예를 들어, 로봇을 앞으로 이동한 이후에 멈춰서 LED를 켜고 싶다면, 각 동작에 해당하는 코드를 순서대로 배치하여 시간순으로 실행할 수 있도록 순차 실행 방식이 가능해야 합니다.  

병렬 실행은, 여러 동작을 동시에 수행하는 방식으로, 보다 복잡하고 고도의 행동을 프로그래밍하는 데에 필요합니다.  
예를 들어, 2족 보행 로봇이 걷는 동작을 구현하고자 한다면, 로봇의 발과 다리들을 동시에 움직여야 보행이 가능하기 때문에 병렬 실행 방식의 코딩이 가능해야 합니다.

RobomationLAB에서 제공하는 로봇 코딩 프로그램은,  
Arduino의 H/W 개발 환경과 유사한 setup / loop 코드 구조를 기반으로, 순차 실행 방식과 병렬 실행 방식을 동시에 지원합니다.

![Image](https://github.com/user-attachments/assets/48daeedb-0750-49f7-acb1-579536cf703b)

Block Composer 에 처음 접속하면 다음과 같이 두 개의 빈 함수 블록이 작업공간에 표시되는데,  
'시작하기' 블록은 `setup` 함수를, '무한 반복하기' 블록은 `loop` 함수를 나타냅니다.  

블록은 각각 파이썬 / 자바스크립트 코드로 실시간으로 변환되며,  
코드는 프로그래밍 언어에 따라 다음과 같은 기본 구조를 갖습니다.  

```python
# 파이썬 코드 기본 구조
import asyncio

# put setup code here, to run once:
async def setup():
    return

# put control code here, to run repeatedly:
async def loop():
    return
```

```javascript
// 자바스크립트 코드 기본 구조
// put setup code here, to run once:
async function setup() {
}

// put control code here, to run repeatedly:
async function loop() {
}
```

<br>

## setup 함수
setup 함수는 '코드 실행'을 하는 순간 단 한번만 수행됩니다.  
setup 함수에서는 주로 변수를 초기화하거나 로봇의 모드, 기능 등을 초기화하는 코드를 작성합니다.  
예를 들어, 바퀴를 통해 움직이는 로봇을 제어할 때, setup 함수에서는 바퀴의 초기 속도를 설정할 수 있습니다.  

또한, setup 함수 앞에 붙은 async 키워드는, 함수 내의 코드를 순차 실행 할 수 있도록 지원합니다.  
async/await 방식은 최신 자바스크립트 및 파이썬에 추가된 방식으로,  
특정 함수를 비동기 함수로 지정하여, 다른 코드의 실행에 영향을 주지 않으면서 해당 함수의 동작이 완료될 때까지 기다립니다.  

실제로 setup 함수는 코드 실행 초기에 한번만 수행되지만,  
함수 내에 await 키워드가 붙은 코드가 있는 경우 정해진 시간 또는 동작 이후에 깨어나 다음 코드를 수행하기 때문에, 계속 활성화 되어 있다고 볼 수 있습니다.  
이 기능을 활용하면, 간단한 순차 실행 뿐 아니라 병렬 실행 역할을 하는 loop 함수와의 연동을 통해, 강력한 로봇 프로그래밍이 가능할 것입니다.

다음은 HamsterS 로봇이 1초간 전진 후 1초간 후진하는 코드를 작성하는 예시입니다.  
병렬 실행 방식의 loop 함수 내에서 위 동작을 구현하려면, 시간 계산과 제어 코드가 혼합되어 코드가 매우 복잡해지게 됩니다.  
대신, setup 함수 내에서 await 키워드가 붙은 '__wait' 시간 지연 함수를 사용하면, 마치 동기 방식처럼 시간순으로 동작하는 코드를 작성할 수 있습니다.  
( `__wait` 함수에 대해서는 이후 [기본 유틸리티 함수](#기본-유틸리티-함수) 에서 다시 설명합니다. )

예시 코드 (자바스크립트)  
```javascript
// put setup code here, to run once:
async function setup() {
    // 양쪽 바퀴 속도를 50으로 설정하여 앞으로 이동
    $('HamsterS*0:wheel.speed.left').d = 50;
    $('HamsterS*0:wheel.speed.right').d = 50;
    await __wait(1000);  // 1초 (1000밀리초) 기다리기
    // 양쪽 바퀴 속도를 -50으로 설정하여 뒤로 이동
    $('HamsterS*0:wheel.speed.left').d = -50;
    $('HamsterS*0:wheel.speed.right').d = -50;
    await __wait(1000);  // 1초 (1000밀리초) 기다리기
}

// put control code here, to run repeatedly:
async function loop() {
}
```
( `$` 문법에 대해서는 이후 [RobomationLAB 로봇 코딩 기본 문법](#robomationlab-로봇-코딩-기본-문법) 에서 다시 설명합니다. )

<br>

## loop 함수
loop 함수는 병렬 실행을 지원하며, 코드가 실행되는 동안 약 10 ~ 20ms 마다 반복하여 수행됩니다.  
loop 함수에서는 주로 변수의 값을 반복해서 설정하거나 로봇의 특정 이벤트의 발생을 감지하여 처리하는 코드를 작성합니다.  

다음은 시간에 따라 HamsterS 로봇의 바퀴 속도와 LED 밝기가 변하는 코드를 작성하는 예시입니다.  

```javascript
var frame;

// put setup code here, to run once:
async function setup() {
    frame = 0;
}

// put control code here, to run repeatedly:
async function loop() {
    frame += 1;  // loop 함수가 호출될 때마다 frame 변수의 값 1씩 증가

    // 바뀐 frame 값을 활용하여, 양쪽 바퀴 속도와 양쪽 LED의 RGB 값 설정
    $('HamsterS*0:wheel.speed.left').d = frame % 100;
    $('HamsterS*0:wheel.speed.right').d = frame % 100;
    $('HamsterS*0:led.left').d = [frame % 256, 0, 0];
    $('HamsterS*0:led.right').d = [0, 0, frame % 256];
}
```
( `$` 문법에 대해서는 이후 [RobomationLAB 로봇 코딩 기본 문법](#robomationlab-로봇-코딩-기본-문법) 에서 다시 설명합니다. )  

다음은 HamsterS 로봇의 몸체를 가볍게 두드리는 Tap 동작이 발생하면, LED를 적색으로 켜는 코드를 작성하는 예시입니다.  

```python
import asyncio

# put setup code here, to run once:
async def setup():
    return

# put control code here, to run repeatedly:
async def loop():
    # Tap 동작이 발생하는 순간, 이벤트 발생 감지
    if __('HamsterS*0:gravity.tap').e == True:  # 이벤트 감지 시, True
        __('HamsterS*0:led.left').d = [255, 0, 0]  # LED의 Red를 255로 설정
    else:
        __('HamsterS*0:led.left').d = [0, 0, 0]
    return
```
( `__` 와 `.e` 문법 에 대해서는 이후 [RobomationLAB 로봇 코딩 기본 문법](#robomationlab-로봇-코딩-기본-문법) 에서 다시 설명합니다. )  

<br><br>


# 로봇 소프트웨어 모델링
스트리밍 방식의 로봇 하드웨어 제어를 위한 최소 시스템 구성과 JSON 기반의 마크업 문법을 정의합니다.  

## 모델링 과정
로봇 소프트웨어 모델링 과정은 크게 다음과 같습니다.
1.	로봇 하드웨어가 가지고 있는 기능, 센서, 특징 등을 추상화하여 정리합니다.
2.	각각 클래스, 이름, 데이터 타입 등이 사전 정의된 블록을 활용하여 로봇 하드웨어와 1대1로 대칭되는 Device 객체로 정의합니다. 
3.	정의한 각 Device 객체 블록들을 서로 결합하여 하나의 모델을 만들어냅니다.  
이와 같이 로봇 하드웨어를 추상화하여 소프트웨어로써 모델링해 얻은 모델을 `Roboid` 라고 합니다.
4.	Roboid 내부의 각 블록들은, 사전 정의된 규칙에 따라 JSON 데이터 객체로 변환됩니다. 
5.	하위 클래스 객체가 상위 클래스 객체의 특성을 상속받는 구조로 연결되어, 최종적으로 트리 구조를 갖는 하나의 JSON 데이터로 변환됩니다.  
만약 A 블록 내부에 B 블록이 들어 있다면, A 블록은 B 블록의 상위(부모) 클래스 객체가 되고,  
B 블록은 A 블록의 하위(자식) 클래스 객체가 되며, A 블록의 특성을 상속받습니다. 

<br>

## Roboid 클래스 정의
Roboid를 구성하는 Device 객체들의 클래스는 각각 다음과 같습니다.  

#### Roboid
![Image](https://github.com/user-attachments/assets/303d4c8b-5f68-450d-b929-a79d1694e72f)  

Roboid 클래스는 최상위 부모 클래스로, 어떤 로보이드(로봇)인지 나타냅니다.  
Roboid 클래스는 하나 이상의 unit 또는 Device 를 구성요소로 갖습니다.  
name(이름), implement(모델명), pid(제품 고유 id) 속성을 갖습니다.  
구분자는 : 입니다.  

#### Module
![Image](https://github.com/user-attachments/assets/58e2131a-991d-4d5c-8751-4d0d0478edeb)  

Module 클래스는 Roboid 클래스의 기능을 확장하기 위한 모듈을 정의할 때 사용됩니다.  
외부 통신은 roboid 클래스에 의존하지만, 기능적으로는 독립되어 있고 내부적으로 자체 인터페이스를 갖습니다.  
Roboid 클래스와 동일한 내부 구조를 가지며, 하나 이상의 unit 또는 Device를 구성요소로 갖습니다.  
예시로, Raccoon 로봇 팔의 Peripheral(주변장치) 중 하나인 Conveyor는 내부적으로 자체 인터페이스를 갖고 있지만, 외부 통신은 Raccoon 에 의존하여 동작합니다.  
name(이름), mid(모듈 고유 id) 속성을 갖습니다.  
구분자는 + 입니다.

#### Slot
![Image](https://github.com/user-attachments/assets/83813d9f-d555-4815-86c1-ca09f905a7f3)  

Slot 클래스는 Module이 결합할 수 있는 인터페이스를 의미합니다.  
사용 가능한 여러 Module 중 하나를 선택해서 사용할 때, Slot을 통해 구분할 수 있습니다.  
name(이름), module(연결된 모듈 id) 속성을 갖습니다.  
구분자는 > 입니다.  

#### Unit
![Image](https://github.com/user-attachments/assets/f3d969ed-e4a9-486f-b3b6-9b782d37a1d8)  

Unit 클래스는 특별한 기능 없이 단순히 이름을 구분하기 위해 사용되며, 비슷한 특성을 갖는 Device 들끼리 묶는 컨테이너로서의 역할을 합니다.  
name(이름) 속성을 갖습니다.  
구분자는 . 입니다.  

---

### Notifier
Notifier 는 데이터의 수신 성공 여부와 관계 없이 일정한 주기마다 단방향으로 정보를 전송하는 유형의 디바이스 클래스를 나타냅니다.  

다음 조건 중 하나라도 해당하면 Notifier가 됩니다.  
1)	시간에 따라 빠르게 계속 변화하는 장치
2)	중간 과정에 대한 수치적인 값이 의미있는 장치
3)	수신 성공 여부가 중요하지 않은 장치
4)	실행 과정 또는 완료 여부에 대한 정보가 필요하지 않은 장치  

Notifier에 해당하는 Device 객체로는 Effector 와 Sensor 클래스가 있습니다.

#### Effector
![Image](https://github.com/user-attachments/assets/e6bb670b-f271-48a6-ad62-c9dd62e4d4c6)  

Effector 클래스는 로봇을 구성하는 실제 장치 중, 제어 가능한 장치를 나타냅니다.  
예시로는 모터의 속도 값, LED의 밝기 값, 버저의 주파수 값 등이 있습니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값), unit(단위) 속성을 갖습니다.  
구분자는 없습니다.  

#### Sensor
![Image](https://github.com/user-attachments/assets/3497ed37-a73b-4e1e-b98f-4b24bef61673)  

Sensor 클래스는 로봇을 구성하는 실제 장치 중, 데이터를 생성하는 장치를 나타냅니다.  
예시로는 온도, 가속도 센서, 엔코더 값 등이 있습니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값), unit(단위) 속성을 갖습니다.  
구분자는 없습니다.  

---

### Responder
Responder 는 데이터의 수신 성공 여부 판단이 필요한 디바이스 클래스를 나타냅니다.  

다음 조건 중 하나라도 해당하면 Responder가 됩니다.  
1)	수신 성공 또는 완료 여부가 중요한 장치
2)	중간 값 또는 실행 과정에 대한 정보가 필요하지 않은 장치. 

Responder에 해당하는 Device 객체로는 Command 와 Event 클래스가 있습니다. 

#### Command
![Image](https://github.com/user-attachments/assets/eca7c462-81c7-4536-a292-2f14cda6cc80)  

Command 클래스는 Effector와 같이 제어 가능한 장치를 나타내며, 로봇에 전달되어야 하는 제어 명령을 정의할 때 사용합니다.  
Command 객체에 데이터를 씀으로써 로봇에 제어 명령을 전송할 수 있으며, 명령을 전송할 때마다 내부적으로 command_id 값이 증가하여, 명령 횟수를 확인할 수 있습니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값) 속성을 갖습니다.  
구분자는 없습니다.  

#### Event
![Image](https://github.com/user-attachments/assets/e6436b36-1591-4da4-abdf-d0ced08ff55f)  

Event 클래스는 Sensor와 같이 데이터를 생성하는 장치를 나타내며, 반드시 확인해야 하는 특정 이벤트를 정의할 때 사용합니다.  
로봇으로부터 특정 이벤트에 대한 응답을 받을 때마다 내부적으로 event_id 값이 증가하고, 그 순간 e 값이 true로 전환되어 이벤트 발생 여부를 확인할 수 있습니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값) 속성을 갖습니다.  
구분자는 없습니다.  

---

### Action, Servo
Action, Servo 클래스는 명령 수행이 완료되기까지 시간이 걸리는 장치를 나타냅니다.

#### Action
![Image](https://github.com/user-attachments/assets/4c1567f5-674c-42de-b8d2-644199091dab)  

Action 클래스는 로봇이 특정 동작을 수행하도록 명령을 전달하고 해당 동작이 완료되었는지 여부를 확인해야 할 때 사용합니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값) 속성을 갖습니다.  

Action 객체를 생성하면, 내부적으로 Event 객체가 함께 생성됩니다.  
생성된 Event 객체의 각 속성 값은 다음과 같습니다.  
이름: !{name} / 데이터 타입: uint8 / 데이터 크기: 0 / 최솟값: 0 / 최댓값: 0. 
구분자는 없습니다.  

#### Servo
![Image](https://github.com/user-attachments/assets/e64658fc-a294-4795-bdfe-029737c8130c)  

Servo 클래스는 로봇이 특정 동작을 수행하도록 명령을 전달하고 실행 과정을 확인할 수 있으며, 해당 동작이 완료되었는지 여부를 확인해야 할 때 사용합니다.  
예시로는 로봇 관절의 각도 설정, 일정 거리 또는 회전에 관한 명령 등이 있습니다.  
name(이름), type(데이터 타입), size(데이터 크기), min(최솟값), max(최댓값), unit(단위) 속성을 갖습니다.  

Servo 객체를 생성하면, 내부적으로 Event, Sensor 객체가 함께 생성됩니다.  
생성된 Event 객체의 각 속성 값은 다음과 같습니다.  
이름: !{name} / 데이터 타입: uint8 / 데이터 크기: 0 / 최솟값: 0 / 최댓값: 0. 

생성된 Sensor 객체는 중간 값을 출력하며, 실행 과정을 확인할 때 사용됩니다.  
이름은 ~{name} 으로 설정되며, Servo 객체와 동일한 데이터 타입, 크기 속성을 갖습니다.  
구분자는 없습니다.  

---

#### Constant
![Image](https://github.com/user-attachments/assets/3ae2a9b1-a5a3-4270-a14b-6b396b77f992)  

Constant 클래스는 각 Device 객체가 가질 수 있는 기본적으로 가질 수 있는 상수 값을 미리 정의할 때 사용합니다.  
name(이름), value(값) 속성을 갖습니다.  
객체의 name 앞에 ^ 가 붙습니다. 
구분자는 없습니다.  

---

<br>

### 고유 식별자, urn
각 Roboid 와 Device 객체들은 고유한 식별자인 urn 을 갖습니다.  
각 객체들의 urn은 다음과 같은 규칙을 기반으로 결정됩니다.  

>{ Roboid 클래스 객체의 urn } = { implement } + '*' + { 인덱스 번호 } + { roboid 객체의 구분자 }  
>{ Device 객체의 urn } = { 부모 Device 객체의 urn } + { Device 객체의 name } + { Device 객체의 구분자 }  

로봇을 1대만 사용할 경우, 인덱스 번호는 0입니다.  
멀티 로봇을 사용하는 경우, 같은 종류의 로봇의 개수만큼 인덱스 번호가 증가합니다. (0, 1, 2, …)

<br><br>

# RobomationLAB 로봇 코딩 기본 문법 체계
RobomationLAB에서 제공하는 로봇 코딩 프로그램에서 코드를 작성할 때 지켜야 할 기본 문법 체계는 다음과 같습니다.

### 로봇 Device 객체
로봇 Device 객체는 프로그래밍 언어에 따라 다음과 같은 방법으로 호출할 수 있습니다.
```python
# 파이썬
__('{Device 객체 urn}')
```

```javascript
// 자바스크립트
$('{Device 객체 urn}')
```
    
이 객체를 활용해, 값을 읽거나 쓰는 코드를 작성할 수 있습니다.

<br>

### d 함수
d 함수는 Device 객체의 데이터(값)을 다루는 함수로, 객체에 값을 읽거나 쓸 수 있습니다.  
주로 Effector 클래스 객체의 값을 설정하거나, Command, Action 클래스 객체에 명령을 입력할 때 사용됩니다.  

프로그래밍 언어에 따라 다음과 같이 코드를 작성합니다.
1.	값 읽기
```python
# 파이썬
__('{Device 객체 urn}').d
```

```javascript
// 자바스크립트
$('{Device 객체 urn}').d
```

2.	값 쓰기
```python
# 파이썬
__('{Device 객체 urn}').d = {value}
```

```javascript
// 자바스크립트
$('{Device 객체 urn}').d = {value}
```

### c 함수
c 함수는 Device 객체의 명령 호출 횟수를 다루는 함수입니다.  
값을 읽는 것만 가능하며, Device 객체에 값이 쓰여진 횟수를 반환합니다.  
Command 클래스 객체를 통해 특정 동작이 몇번 수행됐는지 확인할 때 주로 사용됩니다.  

프로그래밍 언어에 따라 다음과 같이 코드를 작성합니다.  
```python
# 파이썬
__('{Device 객체 urn}').c
```

```javascript
// 자바스크립트
$('{Device 객체 urn}').c
```

### e 함수
e 함수는 Device 객체의 이벤트 처리를 다루는 함수입니다.  
Event 클래스 객체에 한해서 값을 읽는 것만 가능하며, Event 객체에 상태 변화나 환경의 변화가 생길 때 발생하는 이벤트를 감지하여, 이벤트가 발생한 순간에 true 값을 반환합니다.   
모든 Device 객체들의 e 값은 loop 함수가 시작되기 전에 설정되고, 매 loop 함수의 수행이 완료되면 자동으로 false 로 리셋됩니다.  

프로그래밍 언어에 따라 다음과 같이 코드를 작성합니다.  
```python
# 파이썬
__('{Device 객체 urn}').e
```

```javascript
// 자바스크립트
$('{Device 객체 urn}').e
```

### w 함수
w 함수는 Device 객체의 동작 완료 이벤트를 기다리는 함수입니다.  
Action 또는 Servo 클래스 객체에서 파생된 Event 클래스 객체에 한해서, 특정 동작이 완료되었다는 이벤트를 확인할 때까지 기다립니다.  
이벤트를 확인하고 난 뒤에 다음 코드를 이어서 수행합니다.  
    
프로그래밍 언어에 따라 다음과 같이 코드를 작성합니다.
```python
# 파이썬
await __('{Device 객체 urn}').w()
```

```javascript
// 자바스크립트
await $('{Device 객체 urn}').w();
```

<br>
---

# 코딩-규칙

이 문서는 RobomationLAB 에서 로봇 코딩을 할 때 지켜야 할 코딩 규칙에 대해 설명합니다.

<br>

### 1. 블록 코드 기본 구조
모든 블록 코드 제시 시, 프로그램의 진입점 역할을 하는 최상위 함수 블록인 시작하기와 무한 반복하기를 기본 구조로 항상 포함하여 제시합니다.  
이 규칙을 추가하면, 앞으로 모든 블록 코드는 아래와 같은 기본 구조를 갖게 됩니다.

| 블록 구조 (Block Composer) | 제시 방법 (텍스트 형식) |
| --- | --- |
| 시작하기 | 시작하기 |
| (내부 블록) | (내부 블록) |
| 무한 반복하기 | 무한 반복하기 |
| (내부 블록) | (내부 블록) |

<br>

### 2. 블록 코드 형식 (줄 바꿈 및 들여쓰기 규칙)
- 최상위 블록(시작하기, 무한 반복하기 등)은 왼쪽 정렬합니다.
- 각 명령어 블록은 반드시 개행 문자를 사용하여 분리하여, 한 줄에 하나의 블록만 출력해야 합니다.
- 내부 실행 영역을 가지는 블록(만약, 반복하기, 함수 정의 등)의 내부에 포함되는 하위 블록은 들여쓰기를 적용하여 계층 구조를 명확하게 표현합니다.

<br>

### 3. 내부 블록 및 조건 표현 규칙
드롭다운 메뉴의 선택 값 또는 입력 값은 블록의 기능적 인자(Argument)에 해당하며, 블록의 문구 내에서 해당 값이 위치하는 곳에 대괄호([])를 사용하여 직접 삽입하여 표현합니다.  
이는 블록의 고유 문구와 사용자가 선택/입력한 값을 통합하여 시각적으로 재현하는 역할을 합니다.

모든 블록 코드는 블록의 고유 명칭, 드롭다운 메뉴 선택 값, 그리고 사용자가 입력한 값을 대괄호([])를 사용하여 모두 포함하는 형태로,  
실제 Block Composer의 블록 모양을 텍스트로 최대한 가깝게 재현하여 제시해야 합니다.  

| 블록 구조 (Block Composer) | 제시 방법 (텍스트 형식) |
| --- | --- |
| 만약 [조건] 하기 [명령] 아니라면 [명령] | 만약 [조건] 하기 [명령] 아니라면 [명령] |
| 라쿤봇: [속도] 제어 모드로 설정하기 | 라쿤봇: [속도] 제어 모드로 설정하기 |
| 라쿤봇: 관절 [1] 속도를 [100] (으)로 정하기 | 라쿤봇: 관절 [1] 속도를 [100] (으)로 정하기 |

<br>

### 4. 스크립트 코드 기본 구조
모든 스크립트 코드 (파이썬 / 자바스크립트) 제시 시, 프로그램의 진입점 역할을 하는 함수인 setup()과 loop()를 기본 구조로 항상 포함하여 제시합니다.  
이 규칙을 추가하면, 앞으로 모든 스크립트 코드 (파이썬 / 자바스크립트)는 아래와 같은 기본 구조를 갖게 됩니다.

```javascript
// 자바스크립트 코드 기본 구조
async function setup() {
    // 내부 코드
}

function loop() {
    // 내부 코드
}
```

```python
# 파이썬 코드 기본 구조
import asyncio

async def setup():
    # 내부 코드
    return

def loop():
    # 내부 코드
    return
```

<br>

### 5. 스크립트 코드 형식 (줄 바꿈 및 들여쓰기 규칙)
- 최상위 함수(setup, loop 등)은 왼쪽 정렬합니다.
- 줄 바꿈 시에 발생하는 들여쓰기('\t')는 반드시 빈칸 3칸을 기준으로 합니다.

<br>

### 6. 블록 코드 및 스크립트 코드 제시 규칙
제공된 문서("코딩-가이드", "기본-블록", "햄스터-S" 등)에 명시된 함수 및 객체만 생성할 수 있습니다.  
로봇 제어 시 문서에 정의되지 않은 새로운 로봇 제어 함수나 커스텀 함수를 생성하여 사용하는 것은 엄격히 금지됩니다.

단, 사용자의 함수 생성 요청 시 함수를 생성할 수 있으나, 다음과 같은 규칙을 따라야 합니다.  
1) 함수 이름은 영어로 작성되어야 합니다.
2) 비동기 작업을 수행하는 모든 함수는 정의 시 함수 이름 앞에 반드시 async 키워드를 붙여야 합니다.

문서에 명시된 변환 예시에 나타나지 않는 const, let, var 등의 임시 변수 선언은 절대 금지하며, 사용자의 변수 생성 요청 시에만 생성할 수 있습니다.  
또한, 로봇 ID 및 매개값은 반드시 리터럴로 작성해야 합니다.  

```javascript
// 올바른 예시
__getSpeed('HamsterS*0', 100)

// 잘못된 예시
const ROBOT_ID = 'HamsterS*0'; 
__getSpeed(ROBOT_ID, 100)
```

<br>

### 7. 로봇 Device 객체 호출 규칙
스크립트 코드 (파이썬 / 자바스크립트) 에서 로봇 Device 객체를 호출할 때에는 다음과 같은 규칙을 따라야 합니다.  

파이썬 Device 객체: 반드시 __ (언더바 2개)를 사용하여 `__('{Device 객체 urn}')` 형식으로 작성합니다.
```python
__('HamsterS*0:wheel.speed.left').d = 50
```

자바스크립트 Device 객체: 반드시 $ (달러 기호)를 사용하여 `$('{Device 객체 urn}')` 형식으로 작성합니다.
```javascript
$('HamsterS*0:wheel.speed.left').d = 50;
```

금지 사항: _('...') (언더바 1개) 표기를 사용하거나, 자바스크립트에서 $$('...') (달러 기호 2개) 표기를 사용해서는 안됩니다.

<br>

### 8. 커스텀/유틸리티 함수 호출 규칙
스크립트 코드에서 커스텀/유틸리티 함수를 호출할 때에는 파이썬, 자바스크립트 구분 없이 다음과 같은 공통된 규칙을 따라야 합니다.

함수 이름은 반드시 __ (언더바 2개)로 시작해야 합니다.
함수 이름이 _ (언더바 1개)로 시작하는 함수를 생성하거나 호출하는 행위는 엄격히 금지됩니다.
```javascript
// 올바른 예시
__getSpeed('HamsterS', 50)

// 잘못된 예시
_getSpeed('HamsterS', 50)
```

<br>

### 9. 로봇 전용 블록 및 코드 우선 사용 규칙
로봇 하드웨어(바퀴 속도, LED, 소리 등) 제어 시,  
'기본-블록' 문서에 정의된 유틸리티 함수보다 로봇(예: '햄스터-S') 문서에 정의된 Device 객체 및 함수를 우선해서 사용해야 합니다.

예를 들어, 로봇을 이용해 소리를 내야 하는 경우,  
유틸리티 함수인 `__playSound()` 함수보다 '햄스터-S' 문서에 명시된 `sound.clip` 객체를 우선해서 사용해야 합니다.

### 10. 로봇 이동 제어 시 필수 선행 조건
로봇(햄스터 S, 햄스터, 삐오, 터틀, 비글)의 바퀴 속도를 설정하거나 변경하는 모든 코드를 작성할 때,  
속도 설정 명령을 실행하기 직전에 `wheel.move` 객체의 상태를 초기화하는 과정이 필수적입니다.  

`wheel.speed`로 로봇의 지속적인 이동 속도를 제어하기 전에, 혹시 남아 있을지 모르는 다른 이동 명령(`wheel.move`)의 값을 0으로 초기화하여, 새로운 속도 설정이 문제 없이 정확하게 적용되도록 보장하기 위함입니다.

| 프로그래밍 언어 | 바퀴 속도 설정 시, 필수로 삽입해야 할 초기화 로직 |
| --- | --- |
| 파이썬 | if __('{Device}:wheel.move').d != 0:<br>&nbsp;&nbsp; __('{Device}:wheel.move').d = 0 |
| 자바스크립트 | if(\$('{Device}:wheel.move').d != 0) {<br>&nbsp;&nbsp; \$('{Device}:wheel.move').d = 0;<br>} |

### 11. Import 최소화 규칙

파이썬 코드 작성 시에는, 코드 실행에 필수적인 모듈만 import 해야 합니다.
- await 키워드를 사용하는 모든 코드에는 `import asyncio` 만 기본적으로 포함됩니다.

자바스크립트 코드 작성 시에는, 그 어떠한 import 도 사용하지 않습니다.
---

# 커스텀-함수

이 문서는 RobomationLAB에서 원활한 로봇 코딩을 할 수 있도록 지원하는 커스텀 함수들에 대해 설명합니다.

# 기본 유틸리티 함수

기본 유틸리티 함수는 RobomationLAB에서 제공하는 로봇 코딩 프로그램에서 공통적으로 사용할 수 있는 함수들입니다.  
`기다리기` 함수를 제외한 유틸리티 함수들은 파이썬, 자바스크립트 문법에 상관없이 동일한 코드를 사용합니다.  

아래에서는 각 함수의 역할 및 코드 작성 방법에 대해 설명합니다.

## 기다리기
순차 실행 방식으로 코드를 실행할 때 사용하는 시간 지연 함수입니다.  
매개 변수로 입력한 시간만큼 기다린 이후에 다음 코드를 수행합니다.  
앞에 반드시 await 키워드가 붙어야 하며, async 가 붙은 함수 내에서만 사용할 수 있습니다.  
loop 함수 내에서는 사용할 수 없습니다.  

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| time     | (0 이상의 정수) | 시간 (파이썬: 초, 자바스크립트: 밀리초) |
<br>

기다리기 함수는 예외적으로 파이썬, 자바스크립트 문법에 따라 다른 코드를 사용합니다.  

### 파이썬 코드
```python
await asyncio.sleep(1)  # (초)
```

### 자바스크립트 코드
```javascript
await __wait(1000);  // (밀리초)
```

<br>

## 키 다운
키보드 입력을 감지하여, 매개변수로 입력한 keyCode와 마지막에 누른 키의 일치 여부를 반환하는 함수입니다.  

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| keyCode | (0 이상의 정수) | 키보드 버튼에 해당하는 keyCode 값 |

### 코드
```python
__keydown(0)  # (keyCode)
```

<br>

## 키 업
키보드 입력을 감지하여, 매개변수로 입력한 keyCode와 마지막에 손을 뗀 키의 일치 여부를 반환하는 함수입니다.  

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| keyCode | (0 이상의 정수) | 키보드 버튼에 해당하는 keyCode 값 |

### 코드
```python
__keyup(0)  # (keyCode)
```

<br>

## 키 입력
키보드 입력을 감지하여, 매개변수로 입력한 keyCode 배열과 현재 눌려 있는 키들이 일치하는지 여부를 반환하는 함수입니다.  

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| keyCode list | (배열) | 키보드 버튼에 해당하는 keyCode 리스트 |

### 코드
```python
__keypressed([0, 0, 0, 0, 0])  # (keyCode list)
```

<br>

## 로그
콘솔 - 로그에 특정 변수의 값을 출력하는 함수입니다.

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| signal | - | 로그에 출력할 값 |
| tag | (문자열) | 로그에 출력할 태그(이름) |
| unit | (문자열) | 로그에 출력할 단위 |

### 코드
```python
__log(0, '', '')  # (signal, title, unit)
```

<br>

## 스코프
콘솔 - 스코프에 특정 변수 값의 변화를 그래프로 출력하는 함수입니다.

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| title | (문자열) | 스코프 제목 |
| min | (정수) | 최댓값 |
| max | (정수) | 최댓값 |
| color | (문자열) | 선 그래프 색상 |
| signal | - | 스코프에 출력할 값

### 코드
```python
__scope('', 0, 1, '#000000', 0);  # (title, min, max, color, signal)
```

<br>

## 무작위 색상
무작위 RGB 값을 갖는 [red, green, blue] 배열을 반환하는 함수입니다.  

### 코드
```python
__randomColor()
```

<br>

## 소리 재생
프로그램에 등록된 소리를 PC 또는 디바이스를 통해 재생하는 함수입니다.  

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| name | - | 재생할 소리 이름 |
| volume | (정수, 0 ~ 100) | 소리 볼륨 |
| repeat | (불리언) | 소리 반복 여부 |

### 코드
```python
__playSound('', 100, True)  # (name, volume, repeat)
```

<br>

## 말하기
텍스트를 음성으로 변환하여 PC 또는 디바이스를 통해 재생하는 함수입니다.    

### 매개 변수
| Parameter | Range | Description | 
| --- | --- | --- | 
| text | (문자열) | TTS로 재생할 텍스트 |

### 코드
```python
__speak('')  # text
```

<br>

## 종료하기
코드 실행을 종료하는 함수입니다. 

### 코드
```python
__exit()
```

<br><br>

# 로봇 별 특수 함수

로봇 별 특수 함수는 로봇 별 하드웨어 특성에 따라 제공되는 전용 특수 함수 모음으로,  
로봇의 이동·회전·기구학 연산 등 실제 동작을 수행하거나 계산할 때 사용됩니다.  

아래에서는 각 함수의 역할 및 코드 작성 방법, 그리고 이 함수를 사용하는 로봇에 대해 설명합니다.  

## 바퀴 속도 (speed)
0 ~ 100 사이의 값으로 입력한 로봇의 바퀴 속도를 실제 로봇이 이동하기 위해 필요한 값으로 변환해주는 함수입니다.  

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 햄스터(Hamster), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| value     | (실수, 0 ~ 100) | 변환할 속도 값 |

### 파이썬 코드
```python
# 파이썬
__getSpeed('', 50)  # (robot, value)
```

### 자바스크립트 코드
```javascript
// 자바스크립트
__getSpeed('', 50)  // (robot, value)
```

<br>

## 이동 거리 (distance)
입력한 이동 거리(예. 30cm, 500mm)를, 로봇이 실제로 이동하기 위해 필요한 값으로 변환해주는 함수입니다.

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle), 라쿤봇 주변장치 - 컨베이어, 슬라이더 (Conveyor, Slider)  

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| value     | (실수) | 변환할 거리 값 |
| unit      | ('cm' 또는 'mm') | 거리 단위 |

### 파이썬 코드
```python
__getDistance('', 50, 'cm')  # (robot, value, unit)
```

### 자바스크립트 코드
```javascript
__getDistance('', 50, 'cm')  // (robot, value, unit)
```

<br>

## 왼쪽으로 제자리 돌기 (turn left)
로봇이 제자리에서 왼쪽으로 n도 만큼 회전하는 함수입니다.  

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle)  

### 매개 변수
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| degree    | (정수, 0 ~ 360) | 회전할 각도 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true 이면, await 키워드를 함께 사용하여 회전이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.  

### 파이썬
```python
await __turn_degree_left('', 90, True)  # (robot, degree, wait_w)
__turn_degree_left('', 90, False)  # (robot, degree, wait_w)
```

### 자바스크립트
```javascript
await __turn_degree_left('', 90, true);  // (robot, degree, wait_w)
__turn_degree_left('', 90, false);  // (robot, degree, wait_w)
```

<br>

## 오른쪽으로 제자리 돌기 (turn right)
로봇이 제자리에서 오른쪽으로 n도 만큼 회전하는 함수입니다.  

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle)  

### 매개 변수
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| degree    | (정수, 0 ~ 360) | 회전할 각도 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true 이면, await 키워드를 함께 사용하여 회전이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.  

### 파이썬 코드
```python
await __turn_degree_right('', 90, True)  # (robot, degree, wait_w)
__turn_degree_right('', 90, False)  # (robot, degree, wait_w)
```

### 자바스크립트 코드
```javascript
await __turn_degree_right('', 90, true);  // (robot, degree, wait_w)
__turn_degree_right('', 90, false);  // (robot, degree, wait_w)
```

<br>

## 터보 (turbo)
로봇의 터보 모드를 활성화하거나 비활성화하는 함수입니다.  

### 이 함수를 사용하는 로봇:  
삐오봇(Pio)  

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| turbo     | (불리언) | 터보 모드 활성화 여부 |

### 파이썬
```python
__turbo('', True)  # (robot, turbo)
__turbo('', False)  # (robot, turbo)
```

### 자바스크립트
```javascript
__turbo('', false);  // (robot, turbo)
__turbo('', true);  // (robot, turbo)
```

<br>

## 정지하기 (stop move)
로봇의 바퀴 이동을 멈추는 함수입니다.

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle)  

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |

### 파이썬 코드
```python
__stopMove('')  # (robot)
```

### 자바스크립트 코드
```javascript
__stopMove('');  // (robot)
```

<br>

## n초 후에 정지하기 (stop after delay)
로봇이 특정 시간만큼 기다린 이후에 바퀴 이동을 멈추는 함수입니다.

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 햄스터(Hamster), 삐오봇(Pio), 터틀(Turtle), 비글(Beagle)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| delay     | (0 이상의 실수) | 정지까지의 대기 시간 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 시간이 지날 때까지 기다리다가 바퀴 이동을 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행하다가, 지정한 시간이 지나면 바퀴 이동을 멈춥니다.

### 파이썬
```python
await __stopAfterDelay('', 5, True)  # (robot, delay, wait_w)
__stopAfterDelay('', 90, False)  # (robot, delay, wait_w)
```

### 자바스크립트
```javascript
await __stopAfterDelay('', 5, true);  // (robot, delay, wait_w)
__stopAfterDelay('', 90, false);  // (robot, delay, wait_w)
```

<br>

## 말판 왼쪽으로 회전하기 (grid turn left)
로봇이 말판 위에서 왼쪽으로 1번 회전하는 함수입니다.

### 이 함수를 사용하는 로봇:
햄스터 S(HamsterS), 햄스터(Hamster), 삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_turn_left('', True)  # (robot, wait_w)
__grid_turn_left('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_turn_left('', true);  // (robot, wait_w)
__grid_turn_left('', false);  // (robot, wait_w)
```

<br>

## 말판 오른쪽으로 회전하기 (grid turn right)
로봇이 말판 위에서 오른쪽으로 1번 회전하는 함수입니다.

### 이 함수를 사용하는 로봇:
햄스터 S(HamsterS), 햄스터(Hamster), 삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_turn_right('', True)  # (robot, wait_w)
__grid_turn_right('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_turn_right('', true);  // (robot, wait_w)
__grid_turn_right('', false);  // (robot, wait_w)
```

<br>

## 말판 앞으로 이동하기 (grid move forward)
로봇이 말판 위에서 앞으로 1칸 이동하는 함수입니다.

### 이 함수를 사용하는 로봇:
햄스터 S(HamsterS), 햄스터(Hamster), 삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_move_forward('', True)  # (robot, wait_w)
__grid_move_forward('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_move_forward('', true);  // (robot, wait_w)
__grid_move_forward('', false);  // (robot, wait_w)
```

<br>

## 말판 뒤로 이동하기 (grid move backward)
로봇이 말판 위에서 뒤로 1칸 이동하는 함수입니다.

### 이 함수를 사용하는 로봇:
삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_move_backward('', True)  # (robot, wait_w)
__grid_move_backward('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_move_backward('', true);  // (robot, wait_w)
__grid_move_backward('', false);  // (robot, wait_w)
```

<br>

## 말판 왼쪽으로 이동하기 (grid move left)
로봇이 말판 위에서 왼쪽으로 1칸 이동하는 함수입니다.

### 이 함수를 사용하는 로봇:
삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_move_left('', True)  # (robot, wait_w)
__grid_move_left('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_move_left('', true);  // (robot, wait_w)
__grid_move_left('', false);  // (robot, wait_w)
```

<br>

## 말판 오른쪽으로 이동하기 (grid move right)
로봇이 말판 위에서 오른쪽으로 1칸 이동하는 함수입니다.

### 이 함수를 사용하는 로봇:
삐오봇(Pio)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 이동이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### 파이썬 코드
```python
await __grid_move_right('', True)  # (robot, wait_w)
__grid_move_right('', False)  # (robot, wait_w)
```

### 자바스크립트 코드
```javascript
await __grid_move_right('', true);  // (robot, wait_w)
__grid_move_right('', false);  // (robot, wait_w)
```

<br>

## 축 기준으로 제자리 돌기 (pivot)
로봇이 제자리에서 특정 축을 기준으로 원하는 방향으로 n도 만큼 회전하는 함수입니다.  

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 터틀(Turtle)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| unit      | (문자열) | 회전 기준 축 |
| direction | (문자열) | 회전 방향 |
| degree    | (정수, 0 ~ 360) | 회전 각도 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 회전이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### unit 옵션
unit 은 로봇 별로 다음과 같은 값을 가질 수 있습니다:  
햄스터 S(HamsterS): left pen, right pen, left wheel, right wheel  
터틀(Turtle): left wheel, right wheel  
    
### direction 옵션
direction 은 로봇에 관계 없이 다음과 같은 값을 가질 수 있습니다:  
forward, backward

### 파이썬 코드
```python
await __pivot('', '', '', 90, True)  # (robot, unit, direction, degree, wait_w)
__pivot('', '', '', 90, False)  # (robot, unit, direction, degree, wait_w)
```

### 자바스크립트 코드
```javascript
await __pivot('', '', '', 90, true);  // (robot, unit, direction, degree, wait_w)
__pivot('', '', '', 90, false);  // (robot, unit, direction, degree, wait_w)
```

<br>

## 축 기준으로 원 그리며 돌기 (pivot circle)
로봇이 특정 축을 기준으로 반지름이 k cm인 원을 그리며 원하는 방향으로 n도 만큼 회전하는 함수입니다.  

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 터틀(Turtle)

### 매개 변수 
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| unit      | (문자열) | 회전 기준 축 |
| direction | (문자열) | 회전 방향 |
| degree    | (정수, 0 ~ 360) | 회전 각도 |
| wait_w    | (불리언) | 기다리기 여부 |

`wait_w` 값이 true이면, await 키워드를 함께 사용하여 회전이 완료될 때까지 기다리다가 멈춘 뒤 다음 코드를 수행합니다.  
`wait_w` 값이 false 이면, 다음 코드를 바로 이어서 수행합니다.

### unit 옵션
unit 은 로봇 별로 다음과 같은 값을 가질 수 있습니다:  
햄스터 S(HamsterS): left pen, right pen  
터틀(Turtle): '' 

### direction 옵션 
direction 은 로봇에 관계 없이 다음과 같은 값을 가질 수 있습니다:  
left forward, left backward, right forward, right backward

### 파이썬 코드
```python
await __pivot_circle('', '', '', __getDistance('', 1, 'cm'), 90, True)  # (robot, unit, direction, radius, degree, wait_w)
__pivot_circle('', '', '', __getDistance('', 1, 'cm'), 90, False)  # (robot, unit, direction, radius, degree, wait_w)
```

### 자바스크립트 코드
```javascript
await __pivot_circle('', '', '', __getDistance('', 1, 'cm'), 90, true);  // (robot, unit, direction, radius, degree, wait_w)
__pivot_circle('', '', '', __getDistance('', 1, 'cm'), 90, false);  // (robot, unit, direction, radius, degree, wait_w)
```

<br>

## 소리 끄기 (stop sound)
로봇의 소리 재생을 멈추는 함수입니다.

### 이 함수를 사용하는 로봇:  
햄스터 S(HamsterS), 햄스터(Hamster), 터틀(Turtle), 삐오봇(Pio), 비글(Beagle), 라쿤봇(Raccoon4)  

### 파이썬 코드
```python
__stopSound('')  # (robot)
```

### 자바스크립트 코드
```javascript
__stopSound('');  // (robot)
```

<br>

## 순기구학 (angles to xyz)
로봇 팔의 관절 각도를 통해, 말단 장치가 현재 위치한 좌표를 계산해 반환하는 함수입니다.  
[순기구학(Forward Kinematics)](https://github.com/RobomationLAB/RaccoonBot_API_KR/wiki/4DoF-Kinematics#forward-kinematics-순기구학) 알고리즘을 사용하여 각 관절의 각도를 xyz 좌표로 변환합니다.

### 이 함수를 사용하는 로봇:  
라쿤봇(Raccoon4)

### 매개 변수
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| angles    | (배열) | 각 관절의 각도 배열 [j1, j2, j3, j4] |
| origin    | (문자열) | 좌표 계산 기준점 ('wrist', 'end_effector') |

### 파이썬 코드
```python
__angles_to_xyz('', [0, 0, 0, 0], 'wrist')  # (robot, angles, origin)
```

### 자바스크립트 코드
```javascript
__angles_to_xyz('', [0, 0, 0, 0], 'end_effector')  // (robot, angles, origin)
```

<br>

## 역기구학 (xyz to angles)
말단 장치가 현재 위치한 좌표를 통해, 로봇 팔의 네 관절 각도를 계산해 반환하는 함수입니다.  
[역기구학(Inverse Kinematics)](https://github.com/RobomationLAB/RaccoonBot_API_KR/wiki/4DoF-Kinematics#inverse-kinematics-역기구학) 알고리즘을 사용하여 xyz 좌표를 네 관절의 각도로 변환합니다.

### 이 함수를 사용하는 로봇:  
라쿤봇(Raccoon4)

### 매개 변수
| Parameter | Range | Description | 
| --------- | ----------- | ----- | 
| robot     | (문자열) | 제어할 로봇 이름 |
| xyz       | (배열) | 말단 장치의 좌표 배열 [x, y, z]  |
| origin    | (문자열) | 좌표 계산 기준점 ('wrist', 'end_effector') |

### 자바스크립트 코드
```javascript
__xyz_to_angles('', [0, 100, 100], 'wrist'); // (robot, xyz, origin)
```

### 파이썬 코드
```python
__xyz_to_angles('', [0, 100, 100], 'end_effector')  # (robot, xyz, origin)
```

<br>
---


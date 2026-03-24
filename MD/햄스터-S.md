# 블록
## 바퀴 속도 설정하기
햄스터 S의 바퀴 속도를 설정합니다.  
바퀴 속도가 양수이면 앞쪽 방향으로 회전하고, 바퀴 속도가 음수이면 뒤쪽 방향으로 회전합니다.  
예를 들어, 바퀴 속도가 100 이라면, 앞쪽 방향으로 100의 속도로 회전하고,  
바퀴 속도가 -100 이라면, 뒤쪽 방향으로 100의 속도로 회전합니다.  
한번 바퀴 속도를 설정하면, 다시 바퀴 속도를 설정하기 전까지 해당 속도로 햄스터 S가 이동합니다.

![](https://github.com/user-attachments/assets/61cadedb-40dd-4d83-8606-a2665c4d0d03)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| wheel | 드롭다운 옵션 | 바퀴 종류 | 왼쪽(left), 오른쪽(right), 양쪽(left, right) |
| velocity | 입력값 | 바퀴 속도 | -100 ~ 100 정수, 0: 정지 | 
 
### 자바스크립트 코드
```javascript
// 왼쪽 바퀴 속도를 50 (으)로 정하기
if($('HamsterS*0:wheel.move').d != 0) {
    $('HamsterS*0:wheel.move').d = 0;
}
$('HamsterS*0:wheel.speed.left').d = __getSpeed('HamsterS*0', 50);

// 오른쪽 바퀴 속도를 50 (으)로 정하기
if($('HamsterS*0:wheel.move').d != 0) {
    $('HamsterS*0:wheel.move').d = 0;
}
$('HamsterS*0:wheel.speed.right').d = __getSpeed('HamsterS*0', 50);
```

### 파이썬 코드
```python
# 양쪽 바퀴 속도를 50 (으)로 정하기
if __('HamsterS*0:wheel.move').d != 0:
    __('HamsterS*0:wheel.move').d = 0
__('HamsterS*0:wheel.speed.left').d = __getSpeed('HamsterS*0', 50)
__('HamsterS*0:wheel.speed.right').d = __getSpeed('HamsterS*0', 50)
```

## 거리 이동하기
햄스터 S가 이동할 거리를 설정합니다.  
바퀴 속도가 설정되어 있지 않은 경우, 이동하지 않습니다.  
거리 값이 0일 경우에는, 현재 설정되어 있는 바퀴 속도대로 멈추지 않고 이동합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.

![](https://github.com/user-attachments/assets/ee7ca894-fa71-4ae0-b458-d0ce6239b8e5)

### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| distance | 입력값 | 거리 값 | 0 이상 실수 |
| unit | 드롭다운 옵션 | 거리 단위 | cm, mm, 인치(inch) | 

### 자바스크립트 코드
```javascript
// 5 cm 이동하기 | 기다리기 O
$('HamsterS*0:wheel.move').d = __getDistance('HamsterS*0', 5, 'cm');  // (robot, distance, unit)
await $('HamsterS*0:wheel.!move').w();

// 1000 mm 이동하기 | 기다리기 X
$('HamsterS*0:wheel.move').d = __getDistance('HamsterS*0', 1000, 'mm');  // (robot, distance, unit)
```

### 파이썬 코드
```python
# 5 cm 이동하기 | 기다리기 O
__('HamsterS*0:wheel.move').d = __getDistance('HamsterS*0', 5, 'cm')  # (robot, distance, unit)
await __('HamsterS*0:wheel.!move').w()

# 1000 mm 이동하기 | 기다리기 X
__('HamsterS*0:wheel.move').d = __getDistance('HamsterS*0', 1000, 'mm')  # (robot, distance, unit)
```

## 시간 이동하기
햄스터 S가 이동할 시간을 설정합니다.  
바퀴 속도가 설정되어 있지 않은 경우, 이동하지 않습니다.    
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  
  
![](https://github.com/user-attachments/assets/eefc6840-4a63-45ba-839e-32f3b6431096)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| time | 입력값 | 시간 값 | 0 이상 실수 |
| unit | 드롭다운 옵션 | 시간 단위 | 초(seconds), 밀리초(milliseconds) | 

옵션을 밀리초(milliseconds)로 설정한 경우에는, time 값을 1000으로 나눈 값이 입력됩니다.

### 자바스크립트 코드
```javascript
// 5 초 이동하기 | 기다리기 O
await __stopAfterDelay('HamsterS*0', 5, true);  // (robot, time, wait_w)

// 5000 밀리초 이동하기 | 기다리기 X
__stopAfterDelay('HamsterS*0', 5, false);  // (robot, time, wait_w)
```

### 파이썬 코드
```python
# 5 초 이동하기 | 기다리기 O
await __stopAfterDelay('HamsterS*0', 5, True)  # (robot, time, wait_w)

# 5000 밀리초 이동하기 | 기다리기 X
__stopAfterDelay('HamsterS*0', 5, False)  # (robot, time, wait_w)
```

## 제자리 돌기
햄스터 S가 제자리에서 회전할 방향과 각도를 설정합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  
  
![](https://github.com/user-attachments/assets/459bc694-001b-4b3e-b127-5b9b05d948c3)

### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 회전 방향 | 왼쪽(left), 오른쪽(right) |
| degree | 입력값 | 회전 각도 | 0 이상 정수 | 

### 자바스크립트 코드
```javascript
// 왼쪽으로 90도 제자리 돌기 | 기다리기 O
await __turn_degree_left('HamsterS*0', 90, true);  // (robot, degree, wait_w)

// 오른쪽으로 270도 제자리 돌기 | 기다리기 X
__turn_degree_right('HamsterS*0', 270, false);  // (robot, degree, wait_w)
```

### 파이썬 코드
```python
# 왼쪽으로 90도 제자리 돌기 | 기다리기 O
await __turn_degree_left('HamsterS*0', 90, True)  # (robot, degree, wait_w)

# 오른쪽으로 270도 제자리 돌기 | 기다리기 X
__turn_degree_right('HamsterS*0', 270, False)  # (robot, degree, wait_w)
```

## 바퀴 속도 변경하기
햄스터 S의 바퀴 속도를 변경합니다.  
현재의 바퀴 속도에 입력한 속도를 더한 값이 새로운 바퀴 속도가 됩니다.  
새롭게 설정된 바퀴 속도의 범위는 -100 ~ 100으로 설정됩니다.

![](https://github.com/user-attachments/assets/617f64dc-772b-459e-9785-8fdf0394669c)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| wheel | 드롭다운 옵션 | 바퀴 종류 | 왼쪽(left), 오른쪽(right), 양쪽(left, right) |
| velocity | 입력값 | 현재 바퀴 속도에 더할 속도 값 | -200 ~ 200 정수, 0: 정지 | 
 
### 자바스크립트 코드
```javascript
// 왼쪽 바퀴 속도를 50 만큼 바꾸기
if($('HamsterS*0:wheel.move').d != 0) {
    $('HamsterS*0:wheel.move').d = 0;
}
$('HamsterS*0:wheel.speed.left').d = $('HamsterS*0:wheel.speed.left').d + __getSpeed('HamsterS*0', 50);

// 오른쪽 바퀴를 50 만큼 바꾸기
if($('HamsterS*0:wheel.move').d != 0) {
    $('HamsterS*0:wheel.move').d = 0;
}
$('HamsterS*0:wheel.speed.right').d = $('HamsterS*0:wheel.speed.right').d + __getSpeed('HamsterS*0', 50);

// 양쪽 바퀴를 50 만큼 바꾸기
if($('HamsterS*0:wheel.move').d != 0) {
    $('HamsterS*0:wheel.move').d = 0;
}
$('HamsterS*0:wheel.speed.left').d = $('HamsterS*0:wheel.speed.left').d + __getSpeed('HamsterS*0', 50);
$('HamsterS*0:wheel.speed.right').d = $('HamsterS*0:wheel.speed.right').d + __getSpeed('HamsterS*0', 50);
```

### 파이썬 코드
```python
# 왼쪽 바퀴 속도를 50 만큼 바꾸기
if __('HamsterS*0:wheel.move').d != 0:
    __('HamsterS*0:wheel.move').d = 0
__('HamsterS*0:wheel.speed.left').d = __('HamsterS*0:wheel.speed.left').d + __getSpeed('HamsterS*0', 50)

# 오른쪽 바퀴 속도를 50 만큼 바꾸기
if __('HamsterS*0:wheel.move').d != 0:
    __('HamsterS*0:wheel.move').d = 0
__('HamsterS*0:wheel.speed.right').d = __('HamsterS*0:wheel.speed.right').d + __getSpeed('HamsterS*0', 50)

# 양쪽 바퀴 속도를 50 만큼 바꾸기
if __('HamsterS*0:wheel.move').d != 0:
    __('HamsterS*0:wheel.move').d = 0
__('HamsterS*0:wheel.speed.left').d = __('HamsterS*0:wheel.speed.left').d + __getSpeed('HamsterS*0', 50)
__('HamsterS*0:wheel.speed.right').d = __('HamsterS*0:wheel.speed.right').d + __getSpeed('HamsterS*0', 50)
```

## 정지하기
햄스터 S의 이동을 멈춥니다.  
햄스터 S의 양쪽 바퀴 속도가 모두 0으로 초기화됩니다.

![](https://github.com/user-attachments/assets/85a24bfe-4c5e-479c-a4fd-3d6bf3d4d990)
 

### 자바스크립트 코드
```javascript
__stopMove('HamsterS*0');
```

### 파이썬 코드
```python
__stopMove('HamsterS*0')
```

## 바퀴가 움직이는 중인가?
햄스터 S의 바퀴가 움직이고 있는지 아닌지 여부를 **참(1) / 거짓(0)** (으)로 반환합니다.

![](https://github.com/user-attachments/assets/1aed96fd-1809-4d2d-b65a-d3e227170872)
 

### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.moving').d
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.moving').d
```

## 말판 앞으로 한 칸 이동하기
햄스터 S가 말판 위에서 한 칸 이동합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  
  
![](https://github.com/user-attachments/assets/be46ad58-7a85-42f2-9dac-1fa7614f9274)


### 자바스크립트 코드
```javascript
// 말판 앞으로 한 칸 이동하기 | 기다리기 O
await __grid_move_forward('HamsterS*0', true);  // (robot, wait_w)

// 말판 앞으로 한 칸 이동하기 | 기다리기 X
__grid_move_forward('HamsterS*0', false);  // (robot, wait_w)
```

### 파이썬 코드
```python
# 말판 앞으로 한 칸 이동하기 | 기다리기 O
await __grid_move_forward('HamsterS*0', True) # (robot, wait_w)

# 말판 앞으로 한 칸 이동하기 | 기다리기 X
__grid_move_forward('HamsterS*0', False) # (robot, wait_w)
```

## 말판에서 한번 돌기
말판 위 햄스터 S가 입력받은 방향으로 90도 회전합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  
  
![](https://github.com/user-attachments/assets/f5b2d91f-3ea1-4552-8776-1229f4cf96d0)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 회전 방향 | 왼쪽(left), 오른쪽(right)|

### 자바스크립트 코드
```javascript
// 말판 위에서 왼쪽으로 한번 돌기 | 기다리기 O
await __grid_turn_left('HamsterS*0', true); // (robot, wait_w)

// 말판 위에서 왼쪽으로 한번 돌기 | 기다리기 X
__grid_turn_left('HamsterS*0', false); // (robot, wait_w)

// 말판 위에서 오른쪽으로 한번 돌기 | 기다리기 O
await __grid_turn_right('HamsterS*0', true); // (robot, wait_w)

// 말판 위에서 오른쪽으로 한번 돌기 | 기다리기 X
__grid_turn_right('HamsterS*0', false); // (robot, wait_w)
```

### 파이썬 코드
```python
# 말판 위에서 왼쪽으로 한번 돌기 | 기다리기 O
await __grid_turn_left('HamsterS*0', True) # (robot, wait_w)

# 말판 위에서 왼쪽으로 한번 돌기 | 기다리기 X
__grid_turn_left('HamsterS*0', False) # (robot, wait_w)

# 말판 위에서 오른쪽으로 한번 돌기 | 기다리기 O
await __grid_turn_right('HamsterS*0', True) # (robot, wait_w)

# 말판 위에서 오른쪽으로 한번 돌기 | 기다리기 X
__grid_turn_right('HamsterS*0', False) # (robot, wait_w)
```

## 펜 홀더 기준 회전하기

펜 홀더 사용 중에, 햄스터 S가 제자리에서 회전할 방향과 각도를 설정합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  


![](https://github.com/user-attachments/assets/eca3533f-e751-4a5d-9841-176b5bfafc08)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| pivot | 드롭다운 옵션 | 회전 기준 | 왼쪽 펜(left pen), 오른쪽 펜(right pen), 왼쪽 바퀴(left wheel), 오른쪽 바퀴(right wheel)|
| direction |드롭다운 옵션 | 방향 | 앞쪽(forward), 뒤쪽(backward) |
| degree | 입력값 | 회전 각도 | 0 이상 정수 | 


### 자바스크립트 코드
```javascript
//왼쪽 펜 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'left pen', 'forward', 90, true); //(robot, pivot, direction, degree, wait_w)

//왼쪽 펜 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'left pen', 'backward', 90, false); //(robot, pivot, direction, degree, wait_w)

//오른쪽 펜 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'right pen', 'forward', 90, true); //(robot, pivot, direction, degree, wait_w)

//오른쪽 펜 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'right pen', 'backward', 90, false); //(robot, pivot, direction, degree, wait_w)

//왼쪽 바퀴 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'left wheel', 'forward', 90, true); //(robot, pivot, direction, degree, wait_w)

//왼쪽 바퀴 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'left wheel', 'backward', 90, false); //(robot, pivot, direction, degree, wait_w)

//오른쪽 바퀴 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'right wheel', 'forward', 90, true); //(robot, pivot, direction, degree, wait_w)

//오른쪽 바퀴 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'right wheel', 'backward', 90, false); //(robot, pivot, direction, degree, wait_w)
```

### 파이썬 코드
```python
# 왼쪽 펜 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'left pen', 'forward', 90, True) # (robot, pivot, direction, degree, wait_w)

# 왼쪽 펜 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'left pen', 'backward', 90, False) # (robot, pivot, direction, degree, wait_w)

# 오른쪽 펜 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'right pen', 'forward', 90, True) # (robot, pivot, direction, degree, wait_w)

# 오른쪽 펜 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'right pen', 'backward', 90, False) # (robot, pivot, direction, degree, wait_w)

# 왼쪽 바퀴 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'left wheel', 'forward', 90, True) # (robot, pivot, direction, degree, wait_w)

# 왼쪽 바퀴 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'left wheel', 'backward', 90, False) # (robot, pivot, direction, degree, wait_w)

# 오른쪽 바퀴 기준 앞쪽 방향으로 90도 돌기 | 기다리기 O
await __pivot('HamsterS*0', 'right wheel', 'forward', 90, True) # (robot, pivot, direction, degree, wait_w)

# 오른쪽 바퀴 기준 뒤쪽 방향으로 90도 돌기 | 기다리기 X
__pivot('HamsterS*0', 'right wheel', 'backward', 90, False) # (robot, pivot, direction, degree, wait_w)
```

## 펜 홀더 기준 원 그리며 돌기

펜 홀더 사용 중에, 햄스터 S가 원을 그릴 때 회전할 기준, 각도, 방향 그리고 원의 반지름 크기를 설정합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  


![](https://github.com/user-attachments/assets/75870fcc-92c1-4fa6-9915-094aa58affdf)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| pivot | 드롭다운 옵션 | 회전 기준 | 왼쪽 펜(left pen), 오른쪽 펜(right pen)|
| direction | 드롭다운 옵션 | 방향 | 왼쪽 앞(left forward), 왼쪽 뒤(left backward), 오른쪽 앞(right forward), 오른쪽 뒤(right backward) |
| radius | 입력값 | 원의 반지름 | 0 이상 실수 |
| unit | 드롭다운 옵션 | 거리 단위 | cm, mm, 인치(inch) |
| degree | 입력값 | 회전 각도 | 0 이상 실수 |


### 자바스크립트 코드
```javascript
// 왼쪽 펜 기준 왼쪽 앞으로 1cm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'left pen', 'left forward', __getDistance('HamsterS*0', 1, 'cm'), 90, false); // (robot, pivot, direction, circle_info, degree, wait_w)

// 왼쪽 펜 기준 왼쪽 뒤로 1cm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'left pen', 'left backward', __getDistance('HamsterS*0', 1, 'cm'), 90, true); // (robot, pivot, direction, circle_info, degree, wait_w)

// 왼쪽 펜 기준 오른쪽 앞으로 1cm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'left pen', 'right forward', __getDistance('HamsterS*0', 1, 'cm'), 90, false); // (robot, pivot, direction, circle_info, degree, wait_w)

// 왼쪽 펜 기준 오른쪽 뒤로 1cm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'left pen', 'right backward', __getDistance('HamsterS*0', 1, 'cm'), 90, true); // (robot, pivot, direction, circle_info, degree, wait_w)

// 오른쪽 펜 기준 왼쪽 앞으로 1mm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'right pen', 'left forward', __getDistance('HamsterS*0', 1, 'mm'), 90, false); // (robot, pivot, direction, circle_info, degree, wait_w)

// 오른쪽 펜 기준 왼쪽 뒤로 1mm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'right pen', 'left backward', __getDistance('HamsterS*0', 1, 'mm'), 90, true); // (robot, pivot, direction, circle_info, degree, wait_w)

// 오른쪽 펜 기준 오른쪽 앞으로 1mm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'right pen', 'right forward', __getDistance('HamsterS*0', 1, 'mm'), 90, false); // (robot, pivot, direction, circle_info, degree, wait_w)

// 오른쪽 펜 기준 오른쪽 뒤로 1mm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'right pen', 'right backward', __getDistance('HamsterS*0', 1, 'mm'), 90, true); // (robot, pivot, direction, circle_info, degree, wait_w)
```

### 파이썬 코드
```python
# 왼쪽 펜 기준 왼쪽 앞으로 1cm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'left pen', 'left forward', __getDistance('HamsterS*0', 1, 'cm'), 90, False) # (robot, pivot, direction, circle_info, degree, wait_w)

# 왼쪽 펜 기준 왼쪽 뒤로 1cm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'left pen', 'left backward', __getDistance('HamsterS*0', 1, 'cm'), 90, True) # (robot, pivot, direction, circle_info, degree, wait_w)

# 왼쪽 펜 기준 오른쪽 앞으로 1cm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'left pen', 'right forward', __getDistance('HamsterS*0', 1, 'cm'), 90, False) # (robot, pivot, direction, circle_info, degree, wait_w)

# 왼쪽 펜 기준 오른쪽 뒤로 1cm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'left pen', 'right backward', __getDistance('HamsterS*0', 1, 'cm'), 90, True) # (robot, pivot, direction, circle_info, degree, wait_w)

# 오른쪽 펜 기준 왼쪽 앞으로 1mm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'right pen', 'left forward', __getDistance('HamsterS*0', 1, 'mm'), 90, False) # (robot, pivot, direction, circle_info, degree, wait_w)

# 오른쪽 펜 기준 왼쪽 뒤로 1mm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'right pen', 'left backward', __getDistance('HamsterS*0', 1, 'mm'), 90, True) # (robot, pivot, direction, circle_info, degree, wait_w)

# 오른쪽 펜 기준 오른쪽 앞으로 1mm 원을 그리며 90도 돌기 | 기다리기 X
__pivot_circle('HamsterS*0', 'right pen', 'right forward', __getDistance('HamsterS*0', 1, 'mm'), 90, False) # (robot, pivot, direction, circle_info, degree, wait_w)

# 오른쪽 펜 기준 오른쪽 뒤로 1mm 원을 그리며 90도 돌기 | 기다리기 O
await __pivot_circle('HamsterS*0', 'right pen', 'right backward', __getDistance('HamsterS*0', 1, 'mm'), 90, True) # (robot, pivot, direction, circle_info, degree, wait_w)
```

## 센서로 선 따라가기

햄스터 S가 바닥 센서를 이용하여 특정한 선을 따라갑니다.


![](https://github.com/user-attachments/assets/40ec6db2-46f2-4ba7-8317-44a8e8263b5e)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 바닥 센서 방향 | 왼쪽(left), 오른쪽(right), 가운데(middle) |
| color | 드롭다운 옵션 | 선의 색 | 검정색(black), 흰색(white) |

### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.trace.mode').d = 1; // 왼쪽 바닥 센서로 검정색 선을 따라가기
$('HamsterS*0:wheel.trace.mode').d = 2; // 오른쪽 바닥 센서로 검정색 선을 따라가기
$('HamsterS*0:wheel.trace.mode').d = 3; // 가운데 바닥 센서로 검정색 선을 따라가기
$('HamsterS*0:wheel.trace.mode').d = 8; // 왼쪽 바닥 센서로 흰색 선을 따라가기
$('HamsterS*0:wheel.trace.mode').d = 9; // 오른쪽 바닥 센서로 흰색 선을 따라가기
$('HamsterS*0:wheel.trace.mode').d = 10; // 가운데 바닥 센서로 흰색 선을 따라가기
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.trace.mode').d = 1 # 왼쪽 바닥 센서로 검정색 선을 따라가기
__('HamsterS*0:wheel.trace.mode').d = 2 # 오른쪽 바닥 센서로 검정색 선을 따라가기
__('HamsterS*0:wheel.trace.mode').d = 3 # 가운데 바닥 센서로 검정색 선을 따라가기
__('HamsterS*0:wheel.trace.mode').d = 8 # 왼쪽 바닥 센서로 흰색 선을 따라가기
__('HamsterS*0:wheel.trace.mode').d = 9 # 오른쪽 바닥 센서로 흰색 선을 따라가기
__('HamsterS*0:wheel.trace.mode').d = 10 # 가운데 바닥 센서로 흰색 선을 따라가기
```

## 회전 후 선 따라가기 & 교차로에서 멈추기
햄스터 S가 지정한 방향으로 회전한 뒤, 다음 교차로를 만날 때까지 이동합니다.  
기다리기를 체크하면, 이동이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  


![](https://github.com/user-attachments/assets/18abed99-d96e-4776-ab15-b52850b1f586)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 이동 방향 | 좌회전(left), 우회전(right), 전진(forward), 유턴(uturn) |
| color | 드롭다운 옵션 | 선의 색 | 검정색(black), 흰색(white) |
### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.trace.mode').d = 4; // 좌회전 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await $('HamsterS*0:wheel.trace.!mode').w();
$('HamsterS*0:wheel.trace.mode').d = 5; // 우회전 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
$('HamsterS*0:wheel.trace.mode').d = 6; // 전진 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await $('HamsterS*0:wheel.trace.!mode').w();
$('HamsterS*0:wheel.trace.mode').d = 7; // 유턴 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
$('HamsterS*0:wheel.trace.mode').d = 11; // 좌회전 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await $('HamsterS*0:wheel.trace.!mode').w();
$('HamsterS*0:wheel.trace.mode').d = 12; // 우회전 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
$('HamsterS*0:wheel.trace.mode').d = 13; // 전진 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await $('HamsterS*0:wheel.trace.!mode').w();
$('HamsterS*0:wheel.trace.mode').d = 14; // 유턴 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.trace.mode').d = 4 # 좌회전 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await __('HamsterS*0:wheel.trace.!mode').w()
__('HamsterS*0:wheel.trace.mode').d = 5 # 우회전 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
__('HamsterS*0:wheel.trace.mode').d = 6 # 전진 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await __('HamsterS*0:wheel.trace.!mode').w()
__('HamsterS*0:wheel.trace.mode').d = 7 # 유턴 한 뒤에 검정색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
__('HamsterS*0:wheel.trace.mode').d = 11 # 좌회전 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await __('HamsterS*0:wheel.trace.!mode').w()
__('HamsterS*0:wheel.trace.mode').d = 12 # 우회전 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
__('HamsterS*0:wheel.trace.mode').d = 13 # 전진 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 O
await __('HamsterS*0:wheel.trace.!mode').w()
__('HamsterS*0:wheel.trace.mode').d = 14 # 유턴 한 뒤에 흰색 선을 따라가다가 다음 교차로에서 멈추기 | 기다리기 X
```

## 선 따라가기 속도 설정
햄스터 S의 선 따라가기 속도를 설정합니다.  
속도의 범위는 1 ~ 10 입니다.


![](https://github.com/user-attachments/assets/ba4073a0-b922-46fb-8134-0ed65b086a75)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| velocity | 입력값 | 선 따라가기 속도 값 | 1 ~ 10 사이 정수| 
### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.trace.speed').d = 1; // 선 따라가기 속도 1로 설정하기
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.trace.speed').d = 1 # 선 따라가기 속도 1로 설정하기
```

## 선 따라가기 방향 변화량 설정
햄스터 S의 선 따라가기 방향 변화량을 설정합니다.  
변화량의 범위는 1 ~ 10 입니다.


![](https://github.com/user-attachments/assets/430c5d52-beab-4be8-a252-9f7f59ef1f1c)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| differential | 입력값 | 선 따라가기 방향 변화량 값 | 1 ~ 10 사이 정수| 
### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.trace.gain').d = 5; // 선 따라가기 방향 변화량 5로 설정하기
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.trace.gain').d = 5 # 선 따라가기 방향 변화량 5로 설정하기
```

## 선 따라가기 멈추기
햄스터 S의 선 따라가기 기능을 종료합니다.


![](https://github.com/user-attachments/assets/6e8f8405-1efd-4d59-81a0-58b6a1dcbcb4)


### 자바스크립트 코드
```javascript
$('HamsterS*0:wheel.trace.mode').d = 0; // 선 따라가기 멈추기
```

### 파이썬 코드
```python
__('HamsterS*0:wheel.trace.mode').d = 0 # 선 따라가기 멈추기
```


## LED 색 설정하기
햄스터 S의 LED 색을 설정합니다.  
왼쪽, 오른쪽 또는 양쪽의 색을 설정할 수 있습니다.


![](https://github.com/user-attachments/assets/26ae2a4b-d052-49f2-bcf1-53ec4b4ac3ae)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 적용 LED 방향 | 왼쪽(left), 오른쪽(right), 양쪽(left, right)|
| color | 드롭다운 옵션 | 색상 | 검정색([0, 0, 0]), 빨간색([255, 0, 0]), 노란색([255, 255, 0]), 초록색([0, 255, 0]), 청록색([0, 255, 255]), 파란색([0, 0, 255]), 자홍색([255, 0, 255]), 흰색([255, 255, 255]) | 

### 자바스크립트 코드
```javascript
// 왼쪽 LED 색을 빨간색으로 정하기
$('HamsterS*0:led.left').d = [255, 0, 0];

// 오른쪽 LED 색을 초록색으로 정하기
$('HamsterS*0:led.right').d = [0, 255, 0];

// 양쪽 LED 색을 파란색으로 정하기
$('HamsterS*0:led.left').d = [0, 0, 255]; 
$('HamsterS*0:led.right').d = [0, 0, 255];
```

### 파이썬 코드
```python
# 왼쪽 LED 색을 빨간색으로 정하기
__('HamsterS*0:led.left').d = [255, 0, 0]

# 오른쪽 LED 색을 초록색으로 정하기
__('HamsterS*0:led.right').d = [0, 255, 0]

# 양쪽 LED 색을 파란색으로 정하기
__('HamsterS*0:led.left').d = [0, 0, 255]
__('HamsterS*0:led.right').d = [0, 0, 255]
```

## LED 색 색상 카테고리 블록으로 설정하기
색상 카테고리에 있는 블록들로 햄스터 S의 LED 색을 설정합니다.  
왼쪽, 오른쪽 또는 양쪽의 색을 설정할 수 있습니다.


![](https://github.com/user-attachments/assets/e7ce75aa-5f94-4f26-b9ce-4f23c37cff55)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 적용 LED 방향 | 왼쪽(left), 오른쪽(right), 양쪽(left, right)|
| color | 입력값 | LED 색상 | RGB 배열([255,255,255]) | 

### 자바스크립트 코드
```javascript
// 왼쪽 LED 색상을 R:255, G:255, B:255 색상으로 정하기
$('HamsterS*0:led.left').d = [255, 255, 255];

// 오른쪽 LED 색상을 R:255, G:255, B:255 색상으로 정하기 
$('HamsterS*0:led.right').d = [255, 255, 255];

// 양쪽 LED 색상을 무작위 색상으로 정하기
$('HamsterS*0:led.left').d = __randomColor();
$('HamsterS*0:led.right').d = __randomColor();
```

### 파이썬 코드
```python
# 왼쪽 LED 색상을 R:255, G:255, B:255 색상으로 정하기 
__('HamsterS*0:led.left').d = [255, 255, 255]

# 오른쪽 LED 색상을 R:255, G:255, B:255 색상으로 정하기 
__('HamsterS*0:led.right').d = [255, 255, 255]

# 양쪽 LED 색상을 무작위 색상으로 정하기
__('HamsterS*0:led.left').d = __randomColor()
__('HamsterS*0:led.right').d = __randomColor()
```

## LED 색 색상 지정 RGB만큼 변경하기
지정한 R,G,B 값만큼  햄스터 S의 LED 색을 변경합니다.  
왼쪽, 오른쪽 또는 양쪽의 색을 설정할 수 있습니다.


![](https://github.com/user-attachments/assets/07afdb1c-0b2e-4eb7-9358-4bce2c6c5047)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 적용 LED 방향 | 왼쪽(left), 오른쪽(right), 양쪽(left, right)|
| color | 입력값 | 변경 R,G,B 값 | R,G,B 각각 -255~255 사이 정수 | 

### 자바스크립트 코드
```javascript
// 왼쪽 LED 색을 R : 10, G : 10, B : 10 만큼 바꾸기
$('HamsterS*0:led.left').d = [$('HamsterS*0:led.left').d[0] + 10, $('HamsterS*0:led.left').d[1] + 10, $('HamsterS*0:led.left').d[2] + 10];

// 오른쪽 LED 색을 R : 100, G : 100, B : 100 만큼 바꾸기
$('HamsterS*0:led.right').d = [$('HamsterS*0:led.right').d[0] + 100, $('HamsterS*0:led.right').d[1] + 100, $('HamsterS*0:led.right').d[2] + 100];

// 양쪽 LED 색을 R : -50, G : -50, B : -50 만큼 바꾸기
$('HamsterS*0:led.left').d = [$('HamsterS*0:led.left').d[0] + -50, $('HamsterS*0:led.left').d[1] + -50, $('HamsterS*0:led.left').d[2] + -50];
$('HamsterS*0:led.right').d = [$('HamsterS*0:led.right').d[0] + -50, $('HamsterS*0:led.right').d[1] + -50, $('HamsterS*0:led.right').d[2] + -50];

```

### 파이썬 코드
```python
# 왼쪽 LED 색을 R : 10, G : 10, B : 10 만큼 바꾸기
__('HamsterS*0:led.left').d = [__('HamsterS*0:led.left').d[0] + 10, __('HamsterS*0:led.left').d[1] + 10, __('HamsterS*0:led.left').d[2] + 10]

# 오른쪽 LED 색을 R : 100, G : 100, B : 100 만큼 바꾸기
__('HamsterS*0:led.right').d = [__('HamsterS*0:led.right').d[0] + 100, __('HamsterS*0:led.right').d[1] + 100, __('HamsterS*0:led.right').d[2] + 100]

# 양쪽 LED 색을 R : -50, G : -50, B : -50 만큼 바꾸기
__('HamsterS*0:led.left').d = [__('HamsterS*0:led.left').d[0] + -50, __('HamsterS*0:led.left').d[1] + -50, __('HamsterS*0:led.left').d[2] + -50]
__('HamsterS*0:led.right').d = [__('HamsterS*0:led.right').d[0] + -50, __('HamsterS*0:led.right').d[1] + -50, __('HamsterS*0:led.right').d[2] + -50]
	
```

## LED 끄기
햄스터 S의 LED 색을 없앱니다.  
왼쪽, 오른쪽 또는 양쪽의 LED를 끌 수 있습니다.

![](https://github.com/user-attachments/assets/b0b93ba3-2cc1-4e96-a891-9fd24962539b)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 적용 LED 방향 | 왼쪽(left), 오른쪽(right), 양쪽(left, right)|

### 자바스크립트 코드
```javascript
// 왼쪽 LED 끄기
$('HamsterS*0:led.left').d = [0, 0, 0];

// 오른쪽 LED 끄기
$('HamsterS*0:led.right').d = [0, 0, 0];

// 양쪽 LED 끄기
$('HamsterS*0:led.left').d = [0, 0, 0];
$('HamsterS*0:led.right').d = [0, 0, 0];
```

### 파이썬 코드
```python
# 왼쪽 LED 끄기
__('HamsterS*0:led.left').d = [0, 0, 0]

# 오른쪽 LED 끄기
__('HamsterS*0:led.right').d = [0, 0, 0]

# 양쪽 LED 끄기
__('HamsterS*0:led.left').d = [0, 0, 0]
__('HamsterS*0:led.right').d = [0, 0, 0]
```

## 버저음 설정하기
지정된 주파수로 햄스터 S의 버저음을 설정합니다.  
소리낼 수 있는 주파수의 범위는 122.1hz ~ 4186.0hz 입니다.  
이 외의 값을 입력하면 버저음이 발생하지 않습니다.

![](https://github.com/user-attachments/assets/249e6daf-226e-4fda-84a8-1df11b67a42d)



### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| sound | 입력값 | 버저음 주파수 | 122.1 ~ 4186.0(hz)|

### 자바스크립트 코드
```javascript
// 버저음 주파수 1000hz로 설정하기
$('HamsterS*0:sound.buzz').d = 1000;
```

### 파이썬 코드
```python
# 버저음 주파수 1000hz로 설정하기
__('HamsterS*0:sound.buzz').d = 1000
```

## 음계 연주하기
햄스터 S가 지정된 음계를 재생합니다.

![](https://github.com/user-attachments/assets/4847363d-0af4-464b-a5a6-91bce8739a61)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| note | 드롭다운 옵션 | 음계 | 도(Do), 도#(Do#), 레(Re), 레#(Re#), 미(Mi), 파(Fa), 파#(Fa#), 솔(So), 솔#(So#), 라(La), 라#(La#), 시(Ti)|
| octave | 드롭다운 옵션 | 옥타브 | 3 ~ 7 |

### 자바스크립트 코드
```javascript
// 4 옥타브 도(Do) 음을 연주하기
$('HamsterS*0:sound.note').d = 40;

// 7 옥타브 시(Ti) 음을 연주하기
$('HamsterS*0:sound.note').d = 87;
```

### 파이썬 코드
```python
# 4 옥타브 도(Do) 음을 연주하기
__('HamsterS*0:sound.note').d = 40

# 7 옥타브 시(Ti) 음을 연주하기
__('HamsterS*0:sound.note').d = 87
```

## 소리 재생하기
햄스터 S가 특정 사운드 클립을 재생합니다.  
기다리기를 체크하면, 재생이 완료될 때까지 기다립니다.  
단, 기다리기를 체크한 경우에는 async 함수 내에서만 사용할 수 있습니다.  

![](https://github.com/user-attachments/assets/6a168f1b-2ee7-4720-a400-c00a5e20a36b)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| sound_clip | 드롭다운 옵션 | 사운드 클립 | beep(1), beep2(2), beep3(3), beep_repeat(4), beep_random(5), beep_random_repeat(6), snore(7), snore_repeat(8), siren(9), siren_repeat(10), engine(11), engine_repeat(12), fart_a(13), fart_b(14), noise(15), noise_repeat(16), whistle(17), chop_chop(18), chop_chop_repeat(19), robot(32), dibidibidip(33), melody(34), mission_complete(35), happy(48), angry(49), sad(50), sleep(51), toy_march(52), birthday(53)|

### 자바스크립트 코드
```javascript
// beep 소리 재생하기 | 기다리기 O
$('HamsterS*0:sound.clip').d = 1;
await $('HamsterS*0:sound.!clip').w();

// birthday 소리 재생하기 | 기다리기 X
$('HamsterS*0:sound.clip').d = 53;
```

### 파이썬 코드
```python
# beep 소리 재생하기 | 기다리기 O
__('HamsterS*0:sound.clip').d = 1
await __('HamsterS*0:sound.!clip').w()

# birthday 소리 재생하기 | 기다리기 X
__('HamsterS*0:sound.clip').d = 53
```


## 소리 끄기
햄스터 S의 소리를 끕니다.

![](https://github.com/user-attachments/assets/38a570e4-f9b2-4645-81c9-b2e67d8b88a1)

### 자바스크립트 코드
```javascript
// 햄스터 S 소리 끄기
__stopSound('HamsterS*0');
```

### 파이썬 코드
```python
# 햄스터 S 소리 끄기
__stopSound('HamsterS*0')
```

## 소리가 재생 중인가?
햄스터 S의 소리가 재생중인지 아닌지 여부를 **참(1) / 거짓(0)** (으)로 반환합니다.

![](https://github.com/user-attachments/assets/63bb3360-a1c5-4642-a4e7-404181f2ef18)

### 자바스크립트 코드
```javascript
// 햄스터 S의 소리가 재생 중인가? - 재생시 true, 아닐시 false
$('HamsterS*0:sound.playing').d;
```

### 파이썬 코드
```python
# 햄스터 S의 소리가 재생 중인가? - 재생시 True, 아닐시 False
__('HamsterS*0:sound.playing').d
```


## 바퀴 속도 값
햄스터 S의 지정한 바퀴 속도 값을 반환합니다.

![](https://github.com/user-attachments/assets/3c402e19-42df-4763-a990-e1a9929494fb)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 방향 | 왼쪽(left), 오른쪽(right) |
### 자바스크립트 코드
```javascript
//왼쪽 바퀴 속도
__getSpeedInput('HamsterS*0', $('HamsterS*0:wheel.speed.left').d);

//오른쪽 바퀴 속도
__getSpeedInput('HamsterS*0', $('HamsterS*0:wheel.speed.right').d);

```

### 파이썬 코드
```python
# 왼쪽 바퀴 속도
__getSpeedInput('HamsterS*0', __('HamsterS*0:wheel.speed.left').d)

# 오른쪽 바퀴 속도
__getSpeedInput('HamsterS*0', __('HamsterS*0:wheel.speed.right').d)
```

## 근접 센서 값
햄스터 S의 특정 근접 센서 값을 반환합니다.  
물체가 가까울수록 값이 커집니다. 측정 범위는 0 ~ 100입니다.

![](https://github.com/user-attachments/assets/1943d54a-53ca-4172-ae59-6c30983c0ab2)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 방향 | 왼쪽(left), 오른쪽(right) |
### 자바스크립트 코드
```javascript
//왼쪽 근접 센서 값
$('HamsterS*0:proximity.left').d;

//오른쪽 근접 센서 값
$('HamsterS*0:proximity.right').d;

```

### 파이썬 코드
```python
# 왼쪽 근접 센서 값
__('HamsterS*0:proximity.left').d

# 오른쪽 근접 센서 값
__('HamsterS*0:proximity.right').d
```

## 바닥 센서 값
햄스터 S의 특정 바닥 센서 값을 반환합니다.  
검정색이 최소값, 흰색이 최대값을 가집니다. 측정 범위는 0 ~ 100입니다.  

![](https://github.com/user-attachments/assets/ee002b87-9f81-4fbc-aa65-2b215464a054)

* 흰색은 프린터용 A4 용지 기준 100으로 설정되어 있습니다.  

![](https://github.com/user-attachments/assets/56fcbb33-b00b-439d-9b5a-6fd003310157)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| direction | 드롭다운 옵션 | 방향 | 왼쪽(left), 오른쪽(right) |
### 자바스크립트 코드
```javascript
//왼쪽 바닥 센서 값
$('HamsterS*0:floor.left').d;

//오른쪽 바닥 센서 값
$('HamsterS*0:floor.right').d;
```

### 파이썬 코드
```python
# 왼쪽 바닥 센서 값
__('HamsterS*0:floor.left').d

# 오른쪽 바닥 센서 값
__('HamsterS*0:floor.right').d
```

## 중력 가속도 값
햄스터 S의 특정 축의 중력 가속도 값을 반환합니다.  
가속도 센서는 햄스터/햄스터S가 얼마나 빠르게 움직이거나 기울어지는지를 측정하는 센서입니다.  
측정 범위는 -32768 ~ 32767입니다.  
지구의 중력(1g)은 아래쪽으로 작용하므로 지구 중력 값은 Z = -16384가 됩니다.  
* X축: 로봇을 앞, 뒤 방향으로 기울이는 동작을 할 때 변화합니다.
* Y축: 로봇을 왼쪽, 오른쪽 방향으로 기울이는 동작을 할 때 변화합니다.
* Z축: 로봇을 위, 아래 방향으로 뒤집을 때 변화합니다.  


![](https://github.com/user-attachments/assets/5afb3a34-ea36-455b-bb9d-d6880a4dc564)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| axis | 드롭다운 옵션 | 축 기준 | x축, y축, z축|
### 자바스크립트 코드
```javascript
// x축 기준 중력 가속도 값
$('HamsterS*0:acceleration.x').d;

//y축 기준 중력 가속도 값
$('HamsterS*0:acceleration.y').d;

//z축 기준 중력 가속도 값
$('HamsterS*0:acceleration.z').d;
```

### 파이썬 코드
```python
# x축 기준 중력 가속도 값
__('HamsterS*0:acceleration.x').d

# y축 기준 중력 가속도 값
__('HamsterS*0:acceleration.y').d

# z축 기준 중력 가속도 값
__('HamsterS*0:acceleration.z').d

```


## 밝기 센서 값
햄스터 S의 밝기 센서 값을 반환합니다.  
주변이 밝으면 값이 커지고, 어두우면 작아집니다. 측정 범위는 0 ~ 600입니다.  

![](https://github.com/user-attachments/assets/d7291f6d-452f-4324-bff1-ed181423728f)

### 자바스크립트 코드
```javascript
// 밝기 센서 값
$('HamsterS*0:light').d; 
```

### 파이썬 코드
```python
# 밝기 센서 값
__('HamsterS*0:light').d
```

## 온도 센서 값
햄스터 S의 온도 센서 값을 반환합니다.  
실내 온도가 아닌 로봇의 내부 온도를 나타내며, 측정 범위는 -40.0 ~ +87.5 도(°C)입니다. 


![](https://github.com/user-attachments/assets/1887d32c-c3e2-4a64-b261-c655f79bf149)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
| unit | 드롭다운 옵션 | 온도 단위 | 섭씨(°C), 화씨(°F)|
### 자바스크립트 코드
```javascript
// 섭씨 기준 온도센서 값
__getTemperature($('HamsterS*0:temperature').d, '°C');

// 화씨 기준 온도센서 값
__getTemperature($('HamsterS*0:temperature').d, '°F');

```

### 파이썬 코드
```python
# 섭씨 기준 온도센서 값
__getTemperature(__('HamsterS*0:temperature').d, '°C')

# 화씨 기준 온도센서 값
__getTemperature(__('HamsterS*0:temperature').d, '°F')

```

## 신호 세기 값
햄스터 S의 신호 세기 값을 반환합니다.  
로봇과 동글 사이의 신호 세기를 나타내며, 거리가 가까울수록 값이 커집니다.  
안정적인 동작을 위해 `-50dBm ~ -80dBm` 범위 내에서 사용 권장합니다.  
신호 세기 값은 0에 가까울수록(예: -40 > -90) 신호가 강한 상태입니다. 

![](https://github.com/user-attachments/assets/74d2f2ae-b10f-4770-802a-01ec99f4e2be)


### 자바스크립트 코드
```javascript
// 신호 세기 값
$('HamsterS*0:signal_strength').d;
```

### 파이썬 코드
```python
# 신호 세기 값
__('HamsterS*0:signal_strength').d
```

## 배터리 전압
햄스터 S의 배터리 전압 값을 반환합니다.  
배터리 완충 시 전압은 약 `4.0V`이며, 보통 `3.7V` 이상에서 안정적으로 동작합니다.  
전압이 `3.25V` 이하로 떨어지면 동작 오류가 발생할 수 있으므로 반드시 충전을 권장합니다.  

![](https://github.com/user-attachments/assets/2536ccaf-1cd6-4bc9-8fb0-d1f111cd2971)


### 자바스크립트 코드
```javascript
// 배터리 전압 값
$('HamsterS*0:battery.level').d;
```

### 파이썬 코드
```python
# 배터리 전압 값
__('HamsterS*0:battery.level').d
```

## 상태 변경 여부
햄스터 S의 상태 변경 여부를 **참(1) / 거짓(0)** (으)로 반환합니다.

![](https://github.com/user-attachments/assets/fdf53ac4-aef5-4f77-a114-f36612d7ff8f)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|condition|드롭다운 옵션|위치 조건|앞으로 기울였는가, 뒤로 기울였는가, 왼쪽으로 기울였는가, 오른쪽으로 기울였는가, 거꾸로 뒤집어졌는가, 뒤집어지지 않았는가, 장애물/손을 감지했는가, 두드렸는가|
### 자바스크립트 코드
```javascript
// 햄스터 S가 앞으로 기울였는가?
$('HamsterS*0:acceleration.x').d > 5000;

// 햄스터 S가 뒤로 기울였는가?
$('HamsterS*0:acceleration.x').d < -5000;

// 햄스터 S가 왼쪽으로 기울였는가?
$('HamsterS*0:acceleration.y').d > 5000;

// 햄스터 S가 오른쪽으로 기울였는가?
$('HamsterS*0:acceleration.y').d < -5000;

// 햄스터 S가 거꾸로 뒤집어졌는가?
$('HamsterS*0:acceleration.z').d > 0;

// 햄스터 S가 뒤집어지지 않았는가?
$('HamsterS*0:acceleration.z').d < -3000;

// 햄스터 S가 장애물/손을 감지했는가?
$('HamsterS*0:proximity.left').d > 50 || $('HamsterS*0:proximity.right').d > 50;

// 햄스터 S를 두드렸는가?
$('HamsterS*0:acceleration.tap').e;

```

### 파이썬 코드
```python
# 햄스터 S가 앞으로 기울였는가?
__('HamsterS*0:acceleration.x').d > 5000

# 햄스터 S가 뒤로 기울였는가?
__('HamsterS*0:acceleration.x').d < -5000

# 햄스터 S가 왼쪽으로 기울였는가?
__('HamsterS*0:acceleration.y').d > 5000

# 햄스터 S가 오른쪽으로 기울였는가?
__('HamsterS*0:acceleration.y').d < -5000

# 햄스터 S가 거꾸로 뒤집어졌는가?
__('HamsterS*0:acceleration.z').d > 0

# 햄스터 S가 뒤집어지지 않았는가?
__('HamsterS*0:acceleration.z').d < -3000

# 햄스터 S가 장애물/손을 감지했는가?
__('HamsterS*0:proximity.left').d > 50 or __('HamsterS*0:proximity.right').d > 50

# 햄스터 S를 두드렸는가?
__('HamsterS*0:acceleration.tap').e
```

## 입출력 포트 입력 모드 설정하기
햄스터 S 입출력 포트의 입력 모드를 설정합니다.  
A포트, B포트 또는 A와 B 포트의 입력 모드를 설정할 수 있습니다.

![](https://github.com/user-attachments/assets/0a0d1dbe-c2d9-434f-9496-29e0602bffd8)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|port|드롭다운 옵션|설정 입출력 포트|A(a), B(b), A와 B(a,b)|
|mode|드롭다운 옵션|포트 동작 모드|아날로그 입력, 디지털 입력, 디지털 입력(풀업), 디지털 입력(풀다운), 전압 입력, 서보 출력, pwm 출력, 디지털 출력|
### 자바스크립트 코드
```javascript
// 햄스터 S 포트 A를 아날로그 입력으로 정하기
$('HamsterS*0:io.a.mode').d = 0;

// 햄스터 S 포트 A를 디지털 입력으로 정하기
$('HamsterS*0:io.a.mode').d = 1;

// 햄스터 S 포트 B를 디지털 입력(풀업)으로 정하기
$('HamsterS*0:io.b.mode').d = 2;

// 햄스터 S 포트 B를 디지털 입력(풀다운)으로 정하기
$('HamsterS*0:io.b.mode').d = 3;

// 햄스터 S 포트 A와 B를 전압 입력으로 정하기
$('HamsterS*0:io.a.mode').d = 4;
$('HamsterS*0:io.b.mode').d = 4;

// 햄스터 S 포트 A와 B를 서보 출력으로 정하기
$('HamsterS*0:io.a.mode').d = 8;
$('HamsterS*0:io.b.mode').d = 8;

// 햄스터 S 포트 A와 B를 pwm 출력으로 정하기
$('HamsterS*0:io.a.mode').d = 9;
$('HamsterS*0:io.b.mode').d = 9;

// 햄스터 S 포트 A와 B를 디지털 출력으로 정하기
$('HamsterS*0:io.a.mode').d = 10;
$('HamsterS*0:io.b.mode').d = 10;
```

### 파이썬 코드
```python
# 햄스터 S 포트 A를 아날로그 입력으로 정하기 
__('HamsterS*0:io.a.mode').d = 0

# 햄스터 S 포트 A를 디지털 입력으로 정하기
__('HamsterS*0:io.a.mode').d = 1

# 햄스터 S 포트 B를 디지털 입력(풀업)으로 정하기
__('HamsterS*0:io.b.mode').d = 2

# 햄스터 S 포트 B를 디지털 입력(풀다운)으로 정하기
__('HamsterS*0:io.b.mode').d = 3

# 햄스터 S 포트 A와 B를 전압 입력으로 정하기
__('HamsterS*0:io.a.mode').d = 4
__('HamsterS*0:io.b.mode').d = 4

# 햄스터 S 포트 A와 B를 서보 출력으로 정하기
__('HamsterS*0:io.a.mode').d = 8
__('HamsterS*0:io.b.mode').d = 8

# 햄스터 S 포트 A와 B를 pwm 출력으로 정하기
__('HamsterS*0:io.a.mode').d = 9
__('HamsterS*0:io.b.mode').d = 9

# 햄스터 S 포트 A와 B를 디지털 출력으로 정하기
__('HamsterS*0:io.a.mode').d = 10
__('HamsterS*0:io.b.mode').d = 10
```

## 입출력 포트 출력값 설정하기
햄스터 S 입출력 포트의 출력값을 설정합니다.  
A포트, B포트 또는 A와 B 포트의 입력 모드를 설정할 수 있습니다.


![](https://github.com/user-attachments/assets/c7cd277c-b08e-4ddd-b863-997b3a060810)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|port| 드롭다운 옵션|설정 입출력 포트|A(a), B(b), A와 B(a,b)|
|output|입력값|입출력 포트 출력값| 0 ~ 180 |
### 자바스크립트 코드
```javascript
// 햄스터 S 포트 A 출력값을 180으로 정하기
$('HamsterS*0:io.a.out').d = 180;

// 햄스터 S 포트 B 출력값을 0으로 정하기
$('HamsterS*0:io.b.out').d = 0;

// 햄스터 S 포트 A,B 출력값을 100으로 정하기
$('HamsterS*0:io.a.out').d = 100;
$('HamsterS*0:io.b.out').d = 100;
```

### 파이썬 코드
```python
# 햄스터 S 포트 A 출력값을 180으로 정하기
__('HamsterS*0:io.a.out').d = 180

# 햄스터 S 포트 B 출력값을 0으로 정하기
__('HamsterS*0:io.b.out').d = 0

# 햄스터 S 포트 A,B 출력값을 100으로 정하기
__('HamsterS*0:io.a.out').d = 100
__('HamsterS*0:io.b.out').d = 100
```

## 입출력 포트 출력값 변경하기
햄스터 S 입출력 포트의 출력값을 변경합니다.  
현재의 포트 출력값에 입력한 출력값을 더한 값이 새로운 포트 출력값이 됩니다.  
새롭게 설정된 포트 출력값 범위는 0 ~ 180으로 설정됩니다.  
A포트, B포트 또는 A와 B 포트의 입력 모드를 설정할 수 있습니다.

![](https://github.com/user-attachments/assets/4d898564-88c6-4c20-b318-b7eebbc2b365)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|port| 드롭다운 옵션|설정 입출력 포트|A(a), B(b), A와 B(a,b)|
|value|입력값|입출력 포트 변경값| 정수 |
### 자바스크립트 코드
```javascript
// 햄스터 S 포트 A 출력값을 10만큼 변경하기
$('HamsterS*0:io.a.out').d = $('HamsterS*0:io.a.out').d + 10;

// 햄스터 S 포트 B 출력값을 20만큼 변경하기
$('HamsterS*0:io.b.out').d = $('HamsterS*0:io.b.out').d + 20;

// 햄스터 S 포트 A,B 출력값을 30만큼 변경하기
$('HamsterS*0:io.a.out').d = $('HamsterS*0:io.a.out').d + 30;
$('HamsterS*0:io.b.out').d = $('HamsterS*0:io.b.out').d + 30;
```

### 파이썬 코드
```python
# 햄스터 S 포트 A 출력값을 10만큼 변경하기
__('HamsterS*0:io.a.out').d = __('HamsterS*0:io.a.out').d + 10

# 햄스터 S 포트 B 출력값을 20만큼 변경하기
__('HamsterS*0:io.b.out').d = __('HamsterS*0:io.b.out').d + 20

# 햄스터 S 포트 A,B 출력값을 30만큼 변경하기
__('HamsterS*0:io.a.out').d = __('HamsterS*0:io.a.out').d + 30
__('HamsterS*0:io.b.out').d = __('HamsterS*0:io.b.out').d + 30

```

## 집게 열기 / 닫기
햄스터 S의 집게를 열거나 닫습니다.


![](https://github.com/user-attachments/assets/a929ee44-d10d-46bc-a2a0-f7a298d5af5e)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|toggle|드롭다운 옵션|집게 토글|열기(1), 닫기(2)|
### 자바스크립트 코드
```javascript
// 햄스터 S 집게 열기
$('HamsterS*0:io.gripper').d = 1;

// 햄스터 S 집게 닫기
$('HamsterS*0:io.gripper').d = 2;
```

### 파이썬 코드
```python
# 햄스터 S 집게 열기
__('HamsterS*0:io.gripper').d = 1

# 햄스터 S 집게 닫기
__('HamsterS*0:io.gripper').d = 2
```

## 슈터 각도 설정하기
햄스터 S의 슈터 각도를 설정하여 제어합니다.  
각도의 범위는 0 ~ 180 입니다.


![](https://github.com/user-attachments/assets/d7d62658-0af1-494b-bcdf-188e9426f71f)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|angle|입력값|슈터 각도|0 ~ 180 사이 정수|
### 자바스크립트 코드
```javascript
// 햄스터 S 슈터 각도 180도로 정하기
$('HamsterS*0:io.shooter').d = 180;

// 햄스터 S 슈터 각도 0도로 정하기
$('HamsterS*0:io.shooter').d = 0;
```

### 파이썬 코드
```python
# 햄스터 S 슈터 각도 180도로 정하기
__('HamsterS*0:io.shooter').d = 180

# 햄스터 S 슈터 각도 0도로 정하기
__('HamsterS*0:io.shooter').d = 0
```

## 입출력 포트 입력 값
햄스터 S의 입출력 포트 입력 값을 반환합니다.


![](https://github.com/user-attachments/assets/49226c62-3bb9-4408-9e90-817190e9c4ec)


### 드롭다운 옵션 및 입력값
| 이름 | 구분 | 설명 | 범위 / 종류 |  
| ------ | ------ | ------ | ------ |
|port| 드롭다운 옵션|입출력 포트|A(a), B(b)|

### 자바스크립트 코드
```javascript
// 햄스터 S A포트 입출력 포트 값
$('HamsterS*0:io.a.in').d;

// 햄스터 S B포트 입출력 포트 값
$('HamsterS*0:io.b.in').d;
```

### 파이썬 코드
```python
# 햄스터 S A포트 입출력 포트 값
__('HamsterS*0:io.a.in').d

# 햄스터 S B포트 입출력 포트 값
__('HamsterS*0:io.b.in').d
```
# 그래프 시각화 
## 곡선 그래프 

### 곡선 그래프는 어떤식으로 구하는 게 좋을까?

#### 사인 함수? 
##### 단조로운 곡선은 좋지만 값이 일정하지 않음 


#### 베지어 함수 
##### 점과 점 사이에 있는 값 곡선으로 나타냄 

###### 채택 


### 함수 계산


#### 2차 베지에 곡선으로 
#### 각 지점을 Point 화 시켜 계산 
### 곡선률 계산 

##### pow() = 제곱 수 구하는 함수 

###### - [**cubicTo()**](https://developer.android.com/reference/kotlin/androidx/compose/ui/graphics/Path?authuser=1#cubicTo(kotlin.Float,kotlin.Float,kotlin.Float,kotlin.Float,kotlin.Float,kotlin.Float)) — Adds a cubic bezier segment that curves from the current point to the given point (x3, y3), using the control points (x1, y1) and (x2, y2).
###### 지정된 전용 함수가 존재 cubicTo 를 통해 계산의 필요가 없어짐 

#### 지점을 선으로 연결 후 일직선의 거리를 점과의 점 사이 거리를 나눔 

### 추가적으로 더 들어가는 함수는?
##### 사용자 계산으로 인하여 변화를 실시간 시각화 


### 계산해야 될 것은?

#### 입력 당 시간 이 얼마나 걸리는지 확인 

### 개선점  



#### 색깔을 좀 더 보기 편하게 
#### 포인트의 형태를 변화 - 시각화를 하지 않음

####  사용자 기기에 틀을 맞추지만 형태를 변화 시킬 수 있어야 하기에 그래프는 값을 포인트 값으로 수정
#### 색상에 alpha를 주어 자연스럽게 연결  

### 의문점 
#### 왜 미리보기 렌더링에서는  형태가 이상할까

##### 추측 1. Preview에서 Native Canvas의 시각화를 기기의 크기로 받아서  

##### 추측 2. Preview 에서 사용 시 SetContent로 잡고 있지 않기 때문 

### 에러 가능성
#### 사용자 기기에 따른 형태가 달라질 수 있음
##### 보완 O 

### 추가 작업 

#### 사용자가 입력에 따라 보이는 칸 갯 수를 0~ 10 등등 그래프 조작이 가능해야함 

## 직선 그래프 
### 함수 계산 
#### 곡선 그래프와 같이 Point화 



































# 오류 

##  java.lang.IllegalArgumentException: CreationExtras must have a value by `SAVED_STATE_REGISTRY_OWNER_KEY`

### 오류 원인 

#### `androidx.hilt:hilt-navigation-compose`만 연결되어 있었다

### 해결 방법  
#### androidx.navigation:navigation-compose:2.5.3 dependency




## java.lang.IllegalStateException: Vertically scrollable component was measured with an infinity maximum height constraints, which is disallowed.

### 오류 원인

#### rememberScrollState 의 vertical 용량을 초과 
#### 해결 방법 

##### 기존 문제 발생 원인이 LazyColumn의 Items 에 들어간 VerticalState 와 remember로 설정한 verticalscroll 이 충돌

##### Vertical scroll 을 제거
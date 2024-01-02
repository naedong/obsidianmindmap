

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



---
## Method e in android.util.Log not mocked 

```
Method e in android.util.Log not mocked
```

Mockk 를 통한 Log 문제 해결


--- 
## CLEARTEXT communication to aiopen.etri.re.kr not permitted by network security policy

userTraffic X 
Network security policy 파일 추가 

---
## kotlinx.coroutines.test.UncompletedCoroutinesError: After waiting for 10s, the test coroutine is not completing



runTest  환경에서 10초 이상 걸렸을 경우 생기는 에러 

--- 

## Exception thrown during onAfterAll invocation of plugin com.android.tools.utp.plugins.host.apkinstaller.AndroidTestApkInstallerPlugin.


device offline


com.android.ddmlib.AdbCommandRejectedException: device offline

### device 전원을 키지 않고 테스트를 진행 했을 경우 

---
## java.lang.IllegalArgumentException: Unexpected char 0x20 at 12 in header name:

### 헤더에 공백이 있으면 안된다.

--- 

FATAL EXCEPTION: main
Process: kr.io.etri, PID: 24157
    java.lang.ExceptionInInitializerError
		at kr.io.etri.common.item.LocalDateTimeKt.getNowDate(LocalDateTime.kt:36)
at kr.io.etri.common.item.ChatItemKt.ChatItem(ChatItem.kt:50)
at kr.io.etri.presentation.view.chat.ChatScreenKt$ChatScreen$1$1$invoke$$inlined$items$default$4.invoke(LazyDsl.kt:424)	at kr.io.etri.presentation.view.chat.ChatScreenKt$ChatScreen$1$1$invoke$$inlined$items$default$4.invoke(LazyDsl.kt:145)
at androidx.compose.runtime.internal.ComposableLambdaImpl.invoke(ComposableLambda.jvm.kt:138)


---


##  java.io.FileNotFoundException: android.resource:  ~~~ (No such file or directory)


--- 
## Failed to open APK '/data/app/kr.io.etri-SUd8qxny3oddCTsb4-TFOw==/base.apk' I/O error 

---
## failed to add asset path /data/app/kr.io.etri-SUd8qxny3oddCTsb4-TFOw==/base.apk


--- 
## Cannot invoke "android.content.res.Resources.openRawResource(int)" because the return value of "android.content.Context.getResources()" is null

---
Unable to get current module info in ModuleManager created with non-module Context
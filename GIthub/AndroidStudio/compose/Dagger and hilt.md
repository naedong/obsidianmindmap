# [dagger](https://developer.android.com/training/dependency-injection/hilt-android?hl=ko)

## @Inject 
### 어노테이션은 주로 의존성을 주입 받을 클래스의 생성자, 필드 또는 메서드에 사용됩니다. 

### 의존성 주입 프레임워크가 해당 클래스의 인스턴스를 생성하고 필요한 의존성을 주입합니다.

### 주로 class에 사용

#### class @Inject constructor( " 생성 받을 객채") 이러한 형태로 생성


## @Module 

### 주로 kotlin Object로 사용 
#### 이유 object는 자동 싱글톤 이기에 한 번만 생성하고 스캔하기에 의존성 제공이 용이

#### 코드 가독성이 향상 

### 어노테이션은 의존성 주입 프레임워크에게 의존성을 어떻게 생성하고 제공할지 알려주는 클래스 

### 모듈 클래스 내부에선 의존성 객체를 생성 메서드를 정의

### 모듈 클래스는 주로 의존성을 생성하는 곳이며 프레임워크가 해당 모듈을 스캔하여 의존성을 제공 

## @Singleton
### javax.inject.Singleton 
### Injector가 한 번만 Instance 하는 유형을 식별합니다.
###  상속되지 않았습니다.

### 애플리케이션 전체에서 하나의 공유 인스턴스를 생성하기 위함


## @installIn
### `@InstallIn` 주석에 참조할 수 있는 관련 Hilt 구성요소가 있습니다. 각 Hilt 구성요소는 해당 Android 클래스에 결합을 삽입해야 합니다.

이전 예에서는 Hilt 모듈에서 `ActivityComponent`를 사용하는 방법을 보여주었습니다.

Hilt는 다음 구성요소를 제공합니다.

|Hilt 구성요소|인젝터 대상|
|---|---|
|`SingletonComponent`|`Application`|
|`ActivityRetainedComponent`|N/A|
|`ViewModelComponent`|`ViewModel`|
|`ActivityComponent`|`Activity`|
|`FragmentComponent`|`Fragment`|
|`ViewComponent`|`View`|
|`ViewWithFragmentComponent`|`@WithFragmentBindings` 주석이 지정된 `View`|
|`ServiceComponent`|`Service`|

# Hilt

## Hilt는 해당 Android 클래스의 수명 주기에 따라 생성된 구성요소 클래스의 인스턴스를 자동으로 만들고 제거합니다.

|생성된 구성요소|생성 위치|소멸 위치|
|---|---|---|
|`SingletonComponent`|`Application#onCreate()`|`Application` 소멸됨|
|`ActivityRetainedComponent`|`Activity#onCreate()`|`Activity#onDestroy()`|
|`ViewModelComponent`|`ViewModel` 생성됨|`ViewModel` 소멸됨|
|`ActivityComponent`|`Activity#onCreate()`|`Activity#onDestroy()`|
|`FragmentComponent`|`Fragment#onAttach()`|`Fragment#onDestroy()`|
|`ViewComponent`|`View#super()`|`View` 소멸됨|
|`ViewWithFragmentComponent`|`View#super()`|`View` 소멸됨|
|`ServiceComponent`|`Service#onCreate()`|`Service#onDestroy()`|



# Hilt 적용 순서 
## 1. Project 단위 build.gradle의 Plugins에 적용 

```kotlin
buildscript {  
    dependencies {  
        classpath(libs.hilt.gradle)  
    }  
} 

plugins {  
    alias(libs.plugins.hiltAndroid) apply false  
    alias(libs.plugins.kspAndroid) apply false 
}

```

> 플러그인을 적용 시키지 않아도 작동은 되지만 플러그인을 적용 하면 HIlt에서 생성된 클래스를 수동으로 참조하지 않아도 된다. 
   아래는 수동 참조 예시이다
```kotlin 
@HiltAndroidApp(MultiDexApplication::class)
class MyApplication : Hilt_MyApplication()
```
> 위와 같이 수동으로 참조를 해야 한다.



## 2. Module 단위 build.gradle 에 plugins , Dependencies에 설정 

```kotlin
plugins{
    alias(libs.plugins.hiltAndroid) apply false  
    alias(libs.plugins.kspAndroid) apply false 
}
```

> hilt 설정 시 에러가 날 수 있다. 에러가 날 경우 아래와 같이 Dependencies 에 먼저 import 하고 plugins 에 설정을 한다.  
```kotlin

dependencies {
	implementation(libs.hilt)  
	ksp(libs.hilt.android.compiler)
}

```

## 3.  Application class 작동 확인 및 사용 
```kotlin 
@HiltAndroidApp  
class HiltTestApplcation : Application()
```
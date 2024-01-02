
# Android Testing 

## 1. Hilt Test

### 1. dependency 추가
#### testImplementation dependency 추가
##### hilt-android-testing
#### androidTestImplementation dependency 추가
##### hilt-android-testing
#### kspTest dependency 추가

##### hilt-android-compiler
#### kspAndroidTest dependency 추가

##### hilt-android-compiler

### 2. build.gradle project 단위 수정 
#### 추가
```
  
testOptions {  
    emulatorSnapshots {  
  
        enableForTestFailures = true  
        maxSnapshotsForTestFailures = 3  
        compressSnapshots = false  
    }    
}

defaultConfig {    
    testInstrumentationRunner = "수정을 인자값으로 커스텀할 Runner 추가 .CustomTestRunner" // `AndroidJUnitRunner()` 를 확장하여 수정, 사용하기 위해
}
```


### 3. CustomTestApp 추가

#### 추가
```kotlin

class CustomTestRunner : AndroidJUnitRunner() {  
  
    override fun newApplication(cl: ClassLoader?, name: String?, context: Context?): Application {  
        return super.newApplication(cl, HiltTestApplication::class.java.name, context)  
    }  
}

```

### 4. Test Module 추가

#### 테스트시 사용할 모듈을 사용하기 위해 제작
```kotlin 
@Module  // 모듈 Injection 
//@TestInstallIn(  
//    components = [SingletonComponent::class],  
//    replaces = [DataStoreModule::class]  
//)  
@InstallIn(SingletonComponent::class)  // 사용할 Component 추가 
object TestModule {  
  
    private val SET_TEST_KEY = "SET_TEST_KEY"  
  
    @Provides   // **Provides** 의존성을 제공하겠다 표시
    fun providePreferencesDataStore(  
        @ApplicationContext context : Context  
    ) : DataStore<Preferences> = PreferenceDataStoreFactory.create {  
        context.preferencesDataStoreFile(SET_TEST_KEY)  
    }  
}


```

### 5. Test 추가 
#### 추가 
```kotlin 

@UninstallModules(DataStoreModule::class)  
@HiltAndroidTest  
class AndroidTest  {
@get:Rule(order = 0)   // @get:Rule 룰을 지정 테스트슈트 전체에 Rule 적용
var hiltTestRule = HiltAndroidRule(this) 

@get:Rule(order = 2)  
var composeTestRule = createAndroidComposeRule<MainActivity>()

    @Before  
    fun setup() {  
        hiltTestRule.inject()   // 룰을 적용하기 위해 사전에 Inject 해줘야함 
        composeTestRule.setContent {  
            composeTestRule.activity.viewModels<MainViewModel>().value  
        }  
    }
}
```

### 6. 테스트 코드 작성

#### 추가 
```kotlin 
@Test  
fun testWriteAndReadData() {  
    runBlocking {  
        val key = stringPreferencesKey("example_key")  
        dataStore.edit { preferences ->  
            preferences[key] = "example_value"  
        }  
        val result = dataStore.data.first()[key]  
  
        assertEquals("example_value", result)  
    }  
}

```
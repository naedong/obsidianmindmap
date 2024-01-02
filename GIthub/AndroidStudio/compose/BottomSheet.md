
## 개념
 > Modal Bottom Sheet 는 Dialog  처럼 열고 닫을 수 있는 Sheet
 > Persistent Bottom Sheet 사용자의 화면에 지속적으로 남아있으며 swipe 및 호출 시 나타남 예로 naver map 
 

### Modal Bottom Sheet 
```kotlin 

val sheetState = rememberModalBottomSheetState(  
    skipPartiallyExpanded = true  // Bottom Sheet가 화면을 채울지 말지 True/ False로 정함 
  confirmValueChange = 
   // 값에 따른 변경 값을 정함 


```

밑에는 Sheet 호출 
```kotlin

ModalBottomSheet(  
    onDismissRequest = {  },  
    sheetState = sheetState,  
    modifier = Modifier,  
    dragHandle = {  
  
    },  
  
    tonalElevation = 15.dp,  
    containerColor = Color.Cyan,  
    windowInsets = WindowInsets(  
        left = 0.dp,  
        right = 0.dp,  
        top = configuration.screenHeightDp.dp,  
        bottom = 0.dp,  
    ) // 사용 예시 
	// 밑에는 함수 ModalBottomSheet 
	fun ModalBottomSheet(  
    onDismissRequest: () -> Unit,  // Dismiss (hidden 함수)
    modifier: Modifier = Modifier,  // modifier (객체 수정 함수)
    sheetState: SheetState = rememberModalBottomSheetState(),  // sheetState 기본적으로 State를 불러오지만 값을 수정하기 위해서 재 호출 필요 있음 
    shape: Shape = BottomSheetDefaults.ExpandedShape,  // Shape 함수   
    containerColor: Color = BottomSheetDefaults.ContainerColor,  // 바탕이 되는 container 색상 적용
    contentColor: Color = contentColorFor(containerColor),  // 안의 Content 색상 정하기
    tonalElevation: Dp = BottomSheetDefaults.Elevation,   // TonalElevation 그림자를 통한 높낮이 효과 
    scrimColor: Color = BottomSheetDefaults.ScrimColor,   // Dialog 가 아닌 기존의 UI 컬러
    dragHandle: @Composable (() -> Unit)? = { BottomSheetDefaults.DragHandle() },  // Handler를 수정 할 수 있도록 수정 None 설정하면 기존의 모양이 보이지 않음 
    windowInsets: WindowInsets = BottomSheetDefaults.windowInsets,  // WindowInsets를 통해 BottomSheet를 조절할 수 있도록 설정  
    content: @Composable ColumnScope.() -> Unit,  // 안의 Content 를 설정 
)
```
*  SnapShotFlow를 사용하여 State 객체를 콜드 Flow로 변환합니다. `snapshotFlow`는 수집 될 때 블록을 실행하고 읽은 `State` 객체의 결과를 내보냅니다. `snapshotFlow` 블록 내에서 읽은 `State` 객체의 하나가 변경되면 새 값이 이전에 내보낸 값과 같지 않은 경우 Flow에서 새 값을 수집기에 내보냅니다(이 동작은 `Flow.distinctUntilChanged` 의 동작과 비슷함).


*  다음 예는 사용자가 목록에서 첫 번째 항목을 지나 분석까지 스크롤 할 때 기록되는 부작용을 보여줍니다.

```kotlin 
val listState = rememberLazyListState()LazyColumn(state = listState) {  
// ...
}
LaunchedEffect(listState) {    
	snapshotFlow { listState.firstVisibleItemIndex }        
	.map { index -> index > 0 }        
	.distinctUntilChanged()        
	.filter { it == true }        
	.collect {          
	  MyAnalyticsService.sendScrolledPastFirstItemEvent()   
	       }
	   }
```

```kotlin
Modifier
.onGloballyPositioned { layoutCoordinates ->  
    infomationBtnOffset = layoutCoordinates.boundsInRoot().bottomCenter  
    Log.e("LayoutCoordinates", "boundsInParent : ${layoutCoordinates.boundsInParent()}")  
    Log.e("LayoutCoordinates", "boundsInWindow : ${layoutCoordinates.boundsInWindow()}")  
    Log.e("LayoutCoordinates", "boundsInRoot : ${layoutCoordinates.boundsInRoot()}")  
  
    Log.e("LayoutCoordinates", "parentLayoutCoordinates : ${layoutCoordinates.parentLayoutCoordinates}")  
    Log.e("LayoutCoordinates", "parentCoordinates : ${layoutCoordinates.parentCoordinates}")  
    Log.e("LayoutCoordinates", "size : ${layoutCoordinates.size}")  
    Log.e("LayoutCoordinates", "isAttached : ${layoutCoordinates.isAttached}") 

	Log.e("LayoutCoordinates", "BottomCenter : ${layoutCoordinates.boundsInRoot().bottomCenter}") 

	layoutCoordinates.boundsInRoot().topCenter : Offset(540.0, 0.0)
}  
.graphicsLayer {  
    //         translationY = -it.calculateTopPadding().value  
},

```

* 위의 결과값 
```kotlin
  boundsInParent : Rect.fromLTRB(0.0, 0.0, 1080.0, 346.0)
  boundsInWindow : Rect.fromLTRB(0.0, 63.0, 1080.0, 409.0)
  boundsInRoot : Rect.fromLTRB(0.0, 0.0, 1080.0, 346.0)
	
  
  parentLayoutCoordinates : androidx.compose.ui.node.InnerNodeCoordinator@71d404c
  parentCoordinates : androidx.compose.ui.node.LayoutModifierNodeCoordinator@7d3b895
  size : 1080 x 346
  isAttached : true

  bottomCenter : Offset(540.0, 346.0)
layoutCoordinates.boundsInRoot().topCenter : Offset(540.0, 0.0)
layoutCoordinates.boundsInRoot().center : Offset(540.0, 173.0)
```

* 위와 같이 UI의 현재 위치를 반환함 

센터에서 위를 위치하고 싶으면 Window 의 UI를 가져와서 

Rc
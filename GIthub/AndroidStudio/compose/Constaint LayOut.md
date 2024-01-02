
```kotlin
Modifier.constrainAs(text) { 
						linkTo(start = guideline, 
								end = parent.end) 
									width = Dimension.preferredWrapContent }
```

- preferredWrapContent : constraints의 내부 공간에 맞춰 wrap content를 합니다.
    - contaraint 내부 공간에 맞추면서 기본 크기도 적용할 수 있습니다. e.g. Dimemsion.preferredWrapContent.atLeast(100.dp)
- wrapContent: 첫 번째 예제처럼 constraints 내부 공간과는 상관없이 item을 감쌀 수 있을 만큼을 크기로 갖습니다.
- fillToConstraints: constraint에 선언된 값만큼 constraint 내부를 확장해서 채웁니다.
- preferredValue: constraint내부 공간에서 preferredValue에 선언된 dp 값만큼을 크기로 갖습니다.
- value: constraint와 상관없이 선언된 dp값만큼을 크기로 갖습니다.
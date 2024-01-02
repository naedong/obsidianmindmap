### flatten()

다음 코드에서처럼 List 안에 여러개의 List가 존재하는 경우 flatten() 함수를 사용하면 하나의 List로 변환해 줍니다.

1. `val numbers = listOf(listOf(1,2,3), listOf(5,6,7), listOf(8,9,0))`
2. `val result = numbers.flatten()`

4. `println(result)`

> 출력결과 :  
> [1, 2, 3, 5, 6, 7, 8, 9, 0]

### flatMap()

비슷한 형태로 flatMap 이 있는데, flatten 이 그냥 펼치는 것에 반해서 flatMap은 다양한 효과를 줄 수 있습니다.  
예를 들어 다음코드에서는 숫자를 가진 컬렉션들을 펼치면서 “num” 이라는 문자열과 합친 후 문자열 컬렉션으로 변환합니다.

1. `val numbers = listOf(listOf(1,2,3), listOf(5,6,7), listOf(8,9,0))`
2. `val result = numbers.flatMap { it.map { "num $it"} }`

4. `println(result)`

> 출력결과 :  
> [num 1, num 2, num 3, num 5, num 6, num 7, num 8, num 9, num 0]


`groupBy`와 `groupingBy` 함수는 비슷한 기능을 제공하지만 사용 방법과 반환값이 다르다.

### GroupBy

`groupBy` 함수는 `Map<K, List<V>>` 형태의 결과를 반환한다. 즉, 키와 키에 해당하는 요소들을 리스트로 묶은 맵을 반환한다. 이 함수는 컬렉션의 각 요소에 대해 키를 추출하여 그룹화하고, 각 그룹은 해당 키와 일치하는 요소들의 리스트로 표현된다.

```kotlin
val words = listOf("apple", "banana", "cherry", "date", "elderberry")

val groups = words.groupBy { it.length }

println(groups) // 출력 : {5=[apple], 6=[banana, cherry], 4=[date], 10=[elderberry]}
```

위 코드에서 **`groupBy`** 함수는 문자열의 길이에 따라 그룹화하여 맵으로 반환한다.

### GroupingBy

`groupingBy` 함수는 `Grouping<T, K>` 객체를 반환한다. 이 객체는 그룹화된 요소를 나타내는 `eachCount` 및 `fold`와 같은 함수를 제공한다. `Grouping` 객체는 각 그룹에서 요소를 추출하고 계산하는 데 사용된다.

```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6)

val groups = numbers.groupingBy { if (it % 2 == 0) "even" else "odd" }
val counts = groups.eachCount()

println(counts) // 출력: {odd=3, even=3}
```

위 코드에서 `groupingBy` 함수는 정수를 2로 나누어 떨어지는 수와 그렇지 않은 수로 그룹화한다. 그리고 `eachCount` 함수를 호출하여 각 그룹의 요소 수를 계산한다.

따라서 `groupBy` 함수는 각 그룹의 요소를 리스트로 묶은 맵을 반환하며, `groupingBy` 함수는 `Grouping` 객체를 반환하여 각 그룹의 요소를 조작할 수 있도록 한다.

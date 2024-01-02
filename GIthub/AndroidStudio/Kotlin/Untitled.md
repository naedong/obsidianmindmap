
간단한 계산을 할때 재귀 함수로 호출하는 것보다 변수와 For문을 사용하는 것이 더 빠를 수 있다 

ex ) 약수 찾기 등 
```kotlin

fun recursive(n : Int, start : Int ) : Int {  
	return if(n % start == 1){ start }  
	else recursive(n, start + 1)  
}
// 밑에 것이 더욱 빠르게 연산이 된다. 
    fun solution(n: Int): Int {
        var check = 0
        for ( i in 1..n){
            if(n % i == 1){
                check = i 
                break 
            }   
        }
        return check 
    }


```



> [!example] Title
	 Contents


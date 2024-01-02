

```kotlin

/**  
     * Returns the array element at the specified [index]. This method can be called using the  
     * index operator.     * ```     * value = arr[index]     * ```     *     * If the [index] is out of bounds of this array, throws an [IndexOutOfBoundsException] except in Kotlin/JS     * where the behavior is unspecified.     */  
    // public operator fun get(index: Int): T  
  
    @Test  
    fun SportArray(){  
        var sport = arrayOf("Soccer", "Cricket", "Rugby")  
  
        assertEquals("Soccer", sport[0])  
        assertEquals("Cricket", sport[1])  
        assertEquals("Rugby", sport[2])  
  
//       이름이 다를 시 에러가 발생  
//        assertEquals("Sccer", sport[0])  
  
        assertThrows(IndexOutOfBoundsException::class.java){  
            sport[100]  
        }  
        assertThrows(IndexOutOfBoundsException::class.java){  
            sport[-1]  
        }  
  
        // Throws 하지 못해 에러가 발생  
//        assertThrows(IndexOutOfBoundsException::class.java){  
//            sport[1]  
//        }  
        // 뒤집기 0~ 2 순서 변경  
        sport.reverse()  
  
//      assertEquals("Soccer", sport[0])  
//      에러가 발생  
        assertEquals("Rugby", sport[0])  
        assertEquals("Cricket", sport[1])  
        assertEquals("Soccer", sport[2])  
  
        /**  
         * Reverses elements in the array in-place.         */
     public fun CharArray.reverse(): Unit {  
        val midPoint = (size / 2) - 1  
        if (midPoint < 0) return  
        var reverseIndex = lastIndex  
        for (index in 0..midPoint) {  
            val tmp = this[index]  
            this[index] = this[reverseIndex]  
            this[reverseIndex] = tmp  
            reverseIndex--  
        }  
    }  
  
        /**  
         * Reverses elements of the array in the specified range in-place.         *         * @param fromIndex the start of the range (inclusive) to reverse.  
         * @param toIndex the end of the range (exclusive) to reverse.  
         *         * @throws IndexOutOfBoundsException if [fromIndex] is less than zero or [toIndex] is greater than the size of this array.         * @throws IllegalArgumentException if [fromIndex] is greater than [toIndex].  
         */
    @SinceKotlin("1.4")  
    public fun <T> Array<T>.reverse(fromIndex: Int, toIndex: Int): Unit {  
        AbstractList.checkRangeIndexes(fromIndex, toIndex, size)  
        val midPoint = (fromIndex + toIndex) / 2  
        if (fromIndex == midPoint) return  
        var reverseIndex = toIndex - 1  
        for (index in fromIndex until midPoint) {  
            val tmp = this[index]  
            this[index] = this[reverseIndex]  
            this[reverseIndex] = tmp  
            reverseIndex--  
        }  
    }  
  
  
        // 만약 1, 0 일 경우 fromIndex가 toIndex보다 크기 때문에 에러가 발생  
        // sport.reverse(1, 0)  
        // 1, 0 번의 순서 변경  
        sport.reverse(0, 2)  
        // 0번과 1번의 순서를 변경  
  
        assertEquals("Cricket", sport[0])  
        assertEquals("Rugby", sport[1])  
        assertEquals("Soccer", sport[2])  
  
        var sports = arrayOf("Soccer", "Cricket", "Rugby", "Baseball")  
  
        sports.reverse(0, 3)  
  
        assertEquals("Rugby", sports[0])  
  
       // assertEquals("Baseball", sports[0])  
        assertEquals("Soccer", sports[2])  
        assertEquals("Baseball", sports[3])  
  
        sports.sortedArray()  
  
        assertEquals("Rugby", sports[0])  
  
        // assertEquals("Baseball", sports[0])  
        assertEquals("Soccer", sports[2])  
        assertEquals("Baseball", sports[3])  
  
// 섞기  
        // kotlin의 shuffle은 Fisher–Yates shuffle에 의거해서 사용 중이며  
        // 피셔 에이트 셔플 - 셔플 알고리즘   Knuth shuffle 이라고도 함  
        /**  
         * -- To shuffle an array a of n elements (indices 0..n-1):         * for i from n−1 down to 1 do         *      j ← random integer such that 0 ≤ j ≤ i         *      exchange a[j] and a[i]         *         *-- To shuffle an array a of n elements (indices 0..n-1):         * for i from 0 to n−2 do         *      j ← random integer such that i ≤ j < n         *      exchange a[i] and a[j]         *         */  
        sports.shuffle()  
  
        @SinceKotlin("1.4")  
        public fun <T> Array<T>.shuffle(random: Random): Unit {  
            for (i in lastIndex downTo 1) {  
                val j = random.nextInt(i + 1)  
                val copy = this[i]  
                this[i] = this[j]  
                this[j] = copy  
            }  
        }  
  
  
       
    ```

# Array to Map<Key, Value> 
```kotlin 

 /**  
 *  Array to Map<key, Value>        
 * */  
    

  /**  
  * Returns a [Map] containing key-value pairs provided by [transform] function  * applied to elements of the given array.  *  * If any of two pairs would have the same key the last one gets added to the map.  *  * The returned map preserves the entry iteration order of the original array.  *  * @sample samples.collections.Arrays.Transformations.associateArrayOfPrimitives  
  */  
/**  
 * public inline fun <T, K, V> Array<out T>.associate(transform: (T) -> Pair<K, V>): Map<K, V> { *     val capacity = mapCapacity(size).coerceAtLeast(16) *     return associateTo(LinkedHashMap<K, V>(capacity), transform) * } */  
/**  
 * @SinceKotlin("1.4")  
 * public inline fun <K, V> Array<out K>.associateWith(valueSelector: (K) -> V): Map<K, V> { *     val result = LinkedHashMap<K, V>(mapCapacity(size).coerceAtLeast(16)) *     return associateWithTo(result, valueSelector) * } */
    val fruits = arrayOf("Pear", "Apple", "Papaya", "Banana")  
        fruits.associateWith { it.length  }  
        // fruits를 lenght에 따라 키를 설정 
        // Pear = 4 
        // Apple = 5 
  
  
    }

```

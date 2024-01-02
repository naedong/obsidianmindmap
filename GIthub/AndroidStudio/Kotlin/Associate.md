## 기본 개념
> Associate의 기본은 Data를 Map의 형태로  key, value를 만드는 것에 있다. 



```kotlin

  
/**  
 * * associate * Pair의 형태로 key와 value를 만든다.  
 * associateBy(class::propertie1,class::propertie2) * 파라미터에 프로퍼티를 넣어 (key,value)로 만든다.  
 * associateBy{ key로 만들 propertie} * key 값을 기준으로 value값에는 배열의 객체가 들어간다.  
 * associateWith{value로 만들 propertie} * value를 기준으로 key에는 배열의 객체가 들어간다.  
 * */  
  /**  * Returns a [Map] containing key-value pairs provided by [transform] function  * applied to elements of the given array.  *  * If any of two pairs would have the same key the last one gets added to the map.  *  * The returned map preserves the entry iteration order of the original array.  *  * @sample samples.collections.Arrays.Transformations.associateArrayOfPrimitives  
  */  

public inline fun <T, K, V> Array<out T>.associate(transform: (T) -> Pair<K, V>): Map<K, V> { 
		val capacity = mapCapacity(size).coerceAtLeast(16) *     
	return associateTo(LinkedHashMap<K, V>(capacity), transform) 
} 

  
/**  
 * Populates and returns the [destination] mutable map with key-value pairs * provided by [transform] function applied to each element of the given collection. * * If any of two pairs would have the same key the last one gets added to the map.  
 ** @sample samples.collections.Collections.Transformations.associateTo  
 */  
public inline fun <T, K, V, M : MutableMap<in K, in V>> Iterable<T>.associateTo(destination: M, transform: (T) -> Pair<K, V>): M {  
    for (element in this) {  
        destination += transform(element)  
    }  
    return destination  
}



  
  
/**  
 * Returns a [Map] where keys are elements from the given collection and values are * produced by the [valueSelector] function applied to each element. * * If any two elements are equal, the last one gets added to the map.  
 * * The returned map preserves the entry iteration order of the original collection.  
 ** @sample samples.collections.Collections.Transformations.associateWith  
 */  
@SinceKotlin("1.3")  
public inline fun <K, V> Iterable<K>.associateWith(valueSelector: (K) -> V): Map<K, V> {  
    val result = LinkedHashMap<K, V>(mapCapacity(collectionSizeOrDefault(10)).coerceAtLeast(16))  
    return associateWithTo(result, valueSelector)  
}


/**  
 * Populates and returns the [destination] mutable map with key-value pairs for each element of the given collection, * where key is the element itself and value is provided by the [valueSelector] function applied to that key. * * If any two elements are equal, the last one overwrites the former value in the map.  
 ** @sample samples.collections.Collections.Transformations.associateWithTo  
 */  
@SinceKotlin("1.3")  
public inline fun <K, V, M : MutableMap<in K, in V>> Iterable<K>.associateWithTo(destination: M, valueSelector: (K) -> V): M {  
    for (element in this) {  
        destination.put(element, valueSelector(element))  
    }  
    return destination  
}

/**  
 * Returns a [Map] containing the elements from the given collection indexed by the key * returned from [keySelector] function applied to each element. ** If any two elements would have the same key returned by [keySelector] the last one gets added to the map. * * The returned map preserves the entry iteration order of the original collection.  
 ** @sample samples.collections.Collections.Transformations.associateBy  
 */  
public inline fun <T, K> Iterable<T>.associateBy(keySelector: (T) -> K): Map<K, T> {  
    val capacity = mapCapacity(collectionSizeOrDefault(10)).coerceAtLeast(16)  
    return associateByTo(LinkedHashMap<K, T>(capacity), keySelector)  
}


/**  
 * Populates and returns the [destination] mutable map with key-value pairs, * where key is provided by the [keySelector] function and * and value is provided by the [valueTransform] function applied to elements of the given collection. ** If any two elements would have the same key returned by [keySelector] the last one gets added to the map. ** @sample samples.collections.Collections.Transformations.associateByToWithValueTransform  
 */  
public inline fun <T, K, V, M : MutableMap<in K, in V>> Iterable<T>.associateByTo(destination: M, keySelector: (T) -> K, valueTransform: (T) -> V): M {  
    for (element in this) {  
        destination.put(keySelector(element), valueTransform(element))  
    }  
    return destination  
}

```


```kotlin

@Test  
fun `Accsociate List, Array to Map, Pair (key,value) 테스트 `() {
	val arrays = listOf(  
	    "Arrays",  
	    "baemins",  
	    "platform"  
	)  
	// array 동일  
  
val associateArray = arrays.associate {  
    it.let {  
        it to it.length  
    }  
}  
// 글자 수 대로 key = value 형태로 저장  
// 결과물  { Arrays=6, baemins=7, platform=8 }  
val arrayAssociateBy = arrays.associateBy { it.length }  
// 글자 수 대로 key = value 형태로 저장  
// 결과물  { 6 = Arrays, 7 = baemins, 8 = platform }  
val arrayAssociateWith = arrays.associateWith { it.length }  
// 글자 수 대로 key = value 형태로 저장  
// 결과물  { Arrays=6, baemins=7, platform=8 }  
//        assertEquals("", withConvenience)  
  
  
/**  
 *  Class to Map<key, Value> */
 
 val storeGoods = listOf(  
    Goods("Candy",  
        "SSG",  
        1500),  
    Goods("Snack",  
        "HomePlus",  
        2500),  
    Goods("Chocolate",  
        "Coupang",  
        3500),  
    )  
// Default  
// [Goods(name=Candy, platform=SSG, price=1500), Goods(name=Snack, platform=HomePlus, price=2500), Goods(name=Chocolate, platform=Coupang, price=3500)]  
  
val asscioentNamePrice = storeGoods.associate {  
    it.let {  
        (name, platform, price) -> name to price  
    }  
}  
// 이름과 가격을 key = value 형태로 저장  
// { Candy = 1500, Snack = 2500, Chocolate = 3500 }  
  
  
val asscioentNamePull = storeGoods.associate {  
    it.let {  
            (name, platform, price) -> platform to name  
    }  
}  
// Platform 과 과자를 key = value 형태로 저장  
// { SSG=Candy, HomePlus=Snack, Coupang=Chocolate }  
  
  
  
val asscioentByPrice = storeGoods.associateBy(Goods::price)  
// 가격, Class의 정보를 key = value 형태로 저장  
// { 1500=Goods(name=Candy, platform=SSG, price=1500), 2500=Goods(name=Snack, platform=HomePlus, price=2500), 3500=Goods(name=Chocolate, platform=Coupang, price=3500) }  
  
val defferent = storeGoods.associateBy {  
    it.run {  
        this.name  
    }  
}  
// 가격, Class의 정보를 key = value 형태로 저장 위와 다르게 참조 형태의 변경  
// { Candy=Goods(name=Candy, platform=SSG, price=1500), Snack=Goods(name=Snack, platform=HomePlus, price=2500), Chocolate=Goods(name=Chocolate, platform=Coupang, price=3500) }

```


* To는 Data A를  인자로 B를 받아 Pair의 형태로 만든다.

* 기본 구조 
```kotlin

  
        /**  
         * Creates a tuple of type [Pair] from this and [that].  
         * This can be useful for creating [Map] literals with less noise, for example:    
         * @sample samples.collections.Maps.Instantiation.mapFromPairs  
         */  
        public infix fun <A, B> A.to(that: B): Pair<A, B> = Pair(this, that)  

```

* 예시
```kotlin 


        val defferentTwo = storeGoods.associateBy {  
            it.run {  
                this.name to this  
            }  
        }

		// 가격, Class의 정보를 key = value 형태로 저장 위와 다르게 참조 형태의 변경  
// {  
// (Candy, Goods(name=Candy, platform=SSG, price=1500))=Goods(name=Candy, platform=SSG, price=1500),  
// (Snack, Goods(name=Snack, platform=HomePlus, price=2500))=Goods(name=Snack, platform=HomePlus, price=2500),  
// (Chocolate, Goods(name=Chocolate, platform=Coupang, price=3500))=Goods(name=Chocolate, platform=Coupang, price=3500)  
// }  
// 위와 다른 이유는 to의 형태를 위에 예시와 함께 직관적으로 풀이하면 (String, Class) 형식의 Pair가 된다. 이것을 Map<key, value>로 묶은 것이다.  
// 다른 형태로  
//


val withClass = storeGoods.associateWith {  
    it.name  
}  
// {  
// Goods( name=Candy, platform=SSG, price=1500 ) = Candy,  
// Goods(name=Snack, platform=HomePlus, price=2500) = Snack,  
// Goods(name=Chocolate, platform=Coupang, price=3500)= Chocolate  
// }

```
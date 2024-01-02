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

  
val toTest = storeGoods.run {  
    this.map {  
        it.name to it  
    }}  
  
// [  
// (Candy, Goods(name=Candy, platform=SSG, price=1500)),  
// (Snack, Goods(name=Snack, platform=HomePlus, price=2500)),  
// (Chocolate, Goods(name=Chocolate, platform=Coupang, price=3500))  
// ]  
// (String, Class) 형태의 Pair로 저장이 된 모습  
  
val dissolutionToList = toTest.map {  
    it.let {  
        it.toList()  
    }  
}  
// Pair 형태를 리스트로 변경  
// [  
// [Candy, Goods(name=Candy, platform=SSG, price=1500)],  
// [Snack, Goods(name=Snack, platform=HomePlus, price=2500)],  
// [Chocolate, Goods(name=Chocolate, platform=Coupang, price=3500) ]  
// ]  
// Pair의 형태가 각각 List로 저장되는 모습  
  
  
val dissolution = toTest.associate {  
    it.run {  
        this.first to this.second  
    }  
}  
// Pair 형태를 Map <Key, Value>로 저장한 형태  
// {  
// Candy=Goods(name=Candy, platform=SSG, price=1500),  
// Snack=Goods(name=Snack, platform=HomePlus, price=2500),  
// Chocolate=Goods(name=Chocolate, platform=Coupang, price=3500)  
// }


```
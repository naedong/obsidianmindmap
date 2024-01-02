

Lazy Evaluation이란 요소가 실제로 필요할 때까지 평가되지 않는 것을 의미합니다. 컬렉션은 반면에 요소가 요청될 때마다 전체 컬렉션이 평가됩니다.

### 📌 **sequence의 장점**

1. 앞서 말했듯이 중간 결과를 저장할 임시 컬렉션을 생성하지 않는다. 
2. 원소에 연산을 차례대로 적용하다가 결과가 얻어지면 그 이후 원소에 대해서는 연산을 하지 않는다.

```
println(listOf(1, 2, 3, 4, 5, 6).map { it * it }.find { it > 10 })
```

위와 같은 계산이 있을 때, 우리가 기대하는 결과는 4이다. (find는 람다로 지정한 연산에 해당하는 **첫번째 원소**를 반환함)

#### **✅ sequence를 사용하지 않을 때**

![](https://blog.kakaocdn.net/dn/JEEiB/btrBKvWERrP/xk5g20r1HaKUpO4K2v7RwK/img.png)

일반적인 컬렉션 연산 연쇄 동작 과정

1. 전체 컬렉션 원소들에 대하여 map연산 실행
2. map연산 결과에 대하여 find실행 ( > 10 인 첫 번째 원소 찾기)

#### ****✅** sequence를 사용할 때**

![](https://blog.kakaocdn.net/dn/mqXiF/btrBKpvrxiR/DQ2Vk0N52KVwlttrNeBGB0/img.png)

sequence를 사용할 때 동작 과정

1. 각 원소에 대하여 순차적으로 map 연산을 실행한 다음 -> find 연산을 실행한다. 
2. 4번째 원소가 원하는 결과이기 때문에 뒤 원소 5, 6에 대해서는 아무 연산도 실행하지 않는다. 

## 🤔 **그럼 항상 sequence를 사용해야 하는 것 아닌가?** 

이 질문에 대한 답은 NO!

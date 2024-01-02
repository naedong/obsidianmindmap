
CoroutineScope.lauch  {
 반환값이 없는 job 객체 
}

CoroutineScope.anysc  {
 반환값이 있는 job 객체 
}



GlobalScope = 프로그램 어디서나 제어 동작 가능
CoroutineScope = 특정 Dispatch 에서 동작 제어 가능 


RunBlocking 은 coroutine 동작이 끝날 때 까지 메인 스레드를 중지 시키지만 
RunBlocking 을 사용 시 ANR(Application Not Response ) 가 발생될 수 있음 

그 외에 스코프내에서 

Job.join = Job 이 끝날때 까지 대기 
Defferred.await() = Defferred 가 끝날때 까지 대기 

중단은 isActive 가 false 가 될 때 
cancle() 을 사용 
The screen was changing after clicking `Finish` button, because the flow in `SplashViewModel` never stopped collecting values. Whenever i changed "onBoardingCompleted"(Boolean) value in Data Store by calling `saveOnBoardingState` function then that value was automatically emitted.

To fix that we have to use `.first()` flow operator which collecting only first emitted value and cancels the flow instead of `.collect()` operator.


Data Store 등을 사용할 시 스트림의 값이 넘어오질 않는다면 .collect 를 사용하여 방출된 값을 전달해야함 
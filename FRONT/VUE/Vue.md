#Vue with Ts

##@Watch
 Vue 공식 문서에서 아래와 같이 설명하고 있습니다.

"Vue는 루트 수준의 반응성 속성을 동적으로 추가 할 수 없으므로 모든 루트 수준의 반응성 데이터 속성을 빈 값으로라도 초기에 선언하여 Vue 인스턴스를 초기화해야합니다."
> 1. data { name: "" };  
> 2. data { name: null }  
> 3. data { name: undefined }

@Watch('name')  
onChangeName(){  
    // 1  
    console.log(name)           // ""  
    -> 위처럼 빈값으로 선언을 했으니 @Watch가 동작함  
    // 2  
    console.log(name)           // ""  
    -> 위처럼 빈값으로 선언을 했으니 @Watch가 동작함  
    // 3  
    console.log(name)           // ""  
    -> 위처럼 빈값으로 선언을 했으나 @Watch가 동작하지 않음.  
}
#여기서 Null, Undefined 의 차이를 알 수 있다.  
>Null은 변수를 선언하고 빈 값을 할당한 상태(빈 객체)이다   -> 자료형이 있는 상태  
>Undefined은 변수를 선언하고 값을 할당하지 않은 상태이다   -> 자료형이 없는 상태

또한 ``빌드시 컴파일러에 따라 달라진다.``  
>그 이유는, vue-cli로 코드를 빌드하면,  
webpack과 ts-loader로 타입스크립트 문법을 자바스크립트로 컴파일을 하게 됩니다.  
이 때 프로퍼티를 확인해서 값이 할당된 프로퍼티만 객체의 속성으로 추가하기 때문입니다.

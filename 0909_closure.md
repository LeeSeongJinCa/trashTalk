# 클로저

### 클로저란?
- 함수 내에서 함수를 정의하고 사용하면 클로저라고 한다.
- 대개는 정의한 함수를 리턴하고 사용은 바깥에서 하게된다.

``` javascript
function getClosure() {
    var text = 'variable 1';
    return function() {
        return text;
    };
}
var closure = getClosure();
closure();
> 'variable 1'
```
위에서 정의한 getClosure()는 함수를 반환하고, 반환된 함수는 getClosure()내부에서 선언된 변수를 참조하고 있다. 또한 이렇게 참조된 변수는 함수 실행이 끝났다고 해서 사라지지 않았고, 여전히 제대로 된 값을 반환하고 있는 걸 알 수 있다.

여기서 반환된 함수가 클로저인데, MDN에서 정의된 내용에서도 말했듯 환경을 기억하고 있는 것처럼 보인다.
``` javascript
var base = 'Hello, ';
function sayHelloTo(name) {
  var text = base + name;
  return function() {
    console.log(text);
  };
}

var hello1 = sayHelloTo('승민');
var hello2 = sayHelloTo('현섭');
var hello3 = sayHelloTo('유근');
hello1();
hello2();
hello3();
> 'Hello, 승민'
> 'Hello, 현섭'
> 'Hello, 유근'
```

### 은닉화
- Javascript 네이밍 컨벤션에서는 변수 앞에 underscore(_)를 사용하면 Private variable으로 쓰고 싶다는 의도이다.
``` javascript
function hello(name) {
    var _name = name;
    return function() {
        console.log('Hello, '+name);
    };
}

var hello1 = hello('성진');
var hello2 = hello('나');
var hello3 = hello('Dunkun');

hello1();
hello2();
hello3();
> 'Hello, 성진'
> 'Hello, 나'
> 'Hello, Dunkun'
```













# JSX


<br>

```
💡 JSX란 자바스크립트의 문법을 확장한 것으로 JavaScript와 XML/HTML을 합친 것이다.
```

<br>

## JSX 코드 예제

```
const element = <h1>Hello World!</h1>;
```

대입 연산자 =의 왼쪽은 ```자바스크립트``` 문법, 대입 연산자 =의 오른쪽은 ```HTML``` 문법이다.

```const element``` 까지는 자바스크립트 문법, ```<h1>Hello World!</h1>``` 는 HTML 문법이다.

→ ```<h1>```태그로 둘러싸인 문자열을 element라는 변수에 선언

JSX는 내부적으로 XML/HTML 코드를 자바스크립트로 변환하는 과정을 거친다. 따라서 실제로 JSX 코드를 작성해도 최종적으로는 자바스크립트 코드가 나오게된다.

<br>

JSX 코드를 자바스크립트 코드로 변환하는 역할을 하는 것이 리액트의 ```createElement()``` 함수이다.

```jsx
class Hello extends React.Component {
	render() {
		return <div> Hello {this.props.toWhat} </div>;
	}
}

ReactDOM.render (
	<Hello toWhat="World" />,
	document.getElementById('root')
);
```

Hello라는 리액트 컴포넌트이다.

이 컴포넌트 내부에서는 자바스크립트 코드와 HTML 코드가 결합된 JSX를 사용하고 있는 것을 볼 수 있다.

그리고 이 컴포넌트를 ReactDOM의 ```render()``` 함수를 사용하여 실제 화면에 렌더링하고 있다.


<br>


```jsx
class Hello extends React.Component {
	render() {
		return React.createElement('div', null, `Hello ${this.props.toWhat}`);
	}
}

ReactDOM.render (
	React.createElement(Hello, { toWhat: 'World' }, null),
	document.getElementById('root')
);
```

이 코드는 JSX를 사용하지 않고 자바스크립트 코드만 사용한 코드로 위 코드와 동일한 기능이다.

위에서 JSX를 사용했던 부분이 이 코드에서는 ```React.createElement()``` 함수로 대체되었다.


<br>


```createElement()``` 함수의 파라미터는

```jsx
React.createElement(
	type,
	[props],
	[...children]
)
```

* type : element의 유형
  * ex) ```<div>, <span>``` 등 HTML 태그 또는 다른 리액트 컴포넌트
* props : element의 속성
* children : 현재 element가 포함하고 있는 자식 element


<br>
<br>

## JSX 장점

### 1️⃣  코드가 간결해진다.

- **JSX 사용한 경우**
```<div>Hello, {name} </div>```


- **JSX 사용 안 한 경우**
```React.createElement('div', null, `Hello, ${name}`);```


<br>


### 2️⃣  가독성이 향상된다.

JSX를 사용한 경우가 안한 경우보다 코드의 의미가 더 빠르게 와닿는다.


<br>



### 3️⃣  Injection Attact 이라는 해킹을 방어하여 보안성이 올라간다.

Injection Attack : 입력창에 문자나 숫자 같은 일반적인 값이 아닌 소스코드를 입력하여 해당 코드가 실행되도록 만드는 해킹 방법



<br>
<br>


## JSX 사용법

```jsx
const name = "js";
const element = <h1>안녕, {name}</h1>;

ReactDOM.render (
	element,
	document.getElementById('root')
);
```

XML/HTML 코드를 사용하다가 중간에 자바스크립트 코드를 사요할 경우 중괄호{}를 사용해서 묶어주면 된다.


<br>

```jsx
function formatName(user) {
	return user.firstName + ' ' + user.lastNamse;
}

const user = {
	firstName: 'Inje',
	lastName: 'Lee'
};

const element = (
	<h1>
			Hello, {formatName(user)}
	</h1>
);

ReactDOM.render (
	element,
	document.getElementById('root')
);
```

위 코드에서 중괄호{}를 사용하여 자바스크립트 함수를 호출하여 사용했다.


<br>


### HTML 태그의 속성에 값을 넣고 싶을 때

- 큰 따옴표 사이에 문자열을 넣거나

```const element = <div tabIndex=”0”></div>;```

- 중괄호 사이에 자바스크립트 코드를 넣는다.

```const element = <img src={user.avatarUrl}></img>;```


<br>


### children 정의하기

```jsx
const element = (
	<div>
		<h1>안녕하세요</h1>
		<h2>열심히 리액트를 공부해 봅시다! </h2>
	</div>
);
```

위 코드에서 ```<div>``` 태그의 children은 ```<h1>과 <h2>``` 태그이다.

👉[컴포넌트](https://github.com/kimjaehee18/STUDY/edit/main/React/Component.md)

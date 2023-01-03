# 컴포넌트


<br>

## Component

리액트는 컴포넌트 기반의 구조이다.

리액트의 모든 페이지는 컴포넌트로 구성되어 있고, 하나의 컴포넌트는 여러 개의 컴포넌트 조합으로 구성되어 있다.

→ 전체 코드의 양이 줄어 개발 시간과 유지 보수 비용을 줄일 수 있다.

자바스크립트의 함수와 비슷하다.


<br>

## Props

### 1️⃣  Props의 개념

→ 리액트 컴포넌트의 속성

컴포넌트에 전달할 다양한 정보를 담고 있는 자바스크립트 객체


<br>


### 2️⃣  Props의 특징

리액트 컴포넌트의 props는 바꿀 수 없고, 같은 props가 들어오면 항상 같은 엘리먼트를 리턴해야 한다.


<br>


### 3️⃣  Props 사용

JSX를 사용하는 경우는 아래 코드와 같이 `키-값` 쌍의 형태로 컴포넌트에 props를 넣을 수 있다.

```jsx
function App(props) {
	return (
		<Profile
			name="js"
			introduction="안녕하세요, js입니다."
			viewCount={1500}
		/>
	);
}
```

 → Profile이라는 컴포넌트에 name, introduction, viewCount 라는 3개의 속성을 넣었고, 이 속성들은 Profile 컴포넌트에 props로 전달된다.


<br>


JSX를 사용하지 않는 경우

```jsx
React.createElement(
	Profile,
	{
		name:"js",
		introduction:"안녕하세요, js입니다.",
		viewCount: 1500
	},
	null
);
```

type은 Profile

props는 자바스크립트 객체

children은 없기 때문에 null


<br>


# 컴포넌트 만들기

### 1️⃣  컴포넌트 종류

* 클래스 컴포넌트
* 함수 컴포넌트

초기에는 클래스 컴포넌트 많이 사용 → 사용기 불편 → 함수 컴포넌트를 개선해서 주로 사용

함수 컴포넌트를 개선하는 과정에서 개발된 것이 훅(Hook)


<br>


### 2️⃣  함수 컴포넌트

```jsx
function Welcome(props) {
	return <h1>안녕, {props.name} </h1>;
}
```

Welcome 함수, props객체를 입력으로 받는다.

리액트 엘리먼트를 리턴하기 때문에 리액트 컴포넌트라 한다.


<br>


### 3️⃣  클래스 컴포넌트

```jsx
class Welcome extens React.Component {
	render() {
		return <h1>안녕, {this.props.name} </h1>;
	}
}
```

리액트의 모든 클래스 컴포넌트는 React.Component를 상속 받는다.

React.Component 를 상속받았기 때문에 리액트 컴포넌트이다.


<br>


### 4️⃣  컴포넌트 특징

- 컴포넌트의 이름은 항상 대문자

소문자로 시작하면 DOM 태그로 인식하기 때문이다.

```jsx
//HTML div 태그로 이닉
const element = <div />;

//Welcome이라는 리액트 컴포넌트로 인식
const element = <Welcome name="인제" />;
```

- 컴포넌트 렌더링

```jsx
function Welcome(props) {
	return <h1>안녕, {props.name} </h1>;
}

const element = <Welcome name="인제" />;

ReactDOM.render (
	element,
	document.getElementById('root');
);
```

# 컴포넌트 합성

<aside>
💡 여러 개의 컴포넌트를 합쳐서 하나의 컴포넌트를 만드는 것

</aside>

```jsx
function Welcome(props) {
	return <h1>Hello, {props.name} </h1>;
}

function App(props) {
	return (
		<div>
			<Welcome name="Mike" />
			<Welcome name="Steve" />
			<Welcome name="Jane" />
		</div>
	)
}

ReactDOM.render(
	<App />,
	document.getElementById('root')
);
```


<br>


# 컴포넌트 추출

```
💡 큰 컴포넌트를 쪼개서 여러 개의 컴포넌트로 만든다.
```

<br>


Comment 컴포넌트

```jsx
function Comment(props) {
	return (
		<div className="comment">
			<div className="user-info">
				<img className="avatar"
					src={props.author.avatarUrl}
					alt={props.author.name}
				/>
				<div className="user-info-name">
					{props.author.name}
				</div>
			</div>
			<div className="comment-text">
				{props.text}
			</div>
			<div className="comment-date">
				{formatDate(props.date)}
			</div>
		</div>
	);
}
```


<br>


img 태그 부분을 따로 빼서 컴포넌트로 만든다.

```jsx
function Avatar(props) {
	return (
		<img className="avatar"
				src={props.user.avatarUrl}
				alt={props.user.name}
		/>
	);
}
```


<br>



위에서 만든 Avatar 컴포넌트를 Comment 컴포넌트에서 기존 코드와 대체한다. 코드가 한결 짧아졌다.

```jsx
function Comment(props) {
	return (
		<div className="comment">
			<div className="user-info">
					<Avatar user={props.author} />
				<div className="user-info-name">
					{props.author.name}
				</div>
			</div>
			<div className="comment-text">
				{props.text}
			</div>
			<div className="comment-date">
				{formatDate(props.date)}
			</div>
		</div>
	);
}
```


<br>



user-info 부분도 빼서 컴포넌트로 만든다.

```jsx
function UserInfo(props) {
	return (
		<div className="user-info">
			<Avatar user={props.user} />
			<div className="user-info-name">
				{props.user.name}
			</div>			
		</div>
	);
}
```

<br>



위에서 만든 컴포넌트들을 기존 코드에서 대체했다. 맨 처음 코드보다 간결해졌다.

```jsx
function Comment(props){
	return (
		<div className="comment">
			<UserInfo user={props.author} />
			<div className="comment-text">
				{props.text}
			</div>
			<div className="comment-date">
				{formatDate(props.date)}
			</div>
		</div>
	);
}
```


<br>


[State와 생명주기](https://www.notion.so/State-d649b2111cc84261b5b38b923d56a89e)

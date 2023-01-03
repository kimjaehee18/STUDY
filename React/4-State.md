# State와 생명주기


<br>


## 🔘 State

### 1️⃣  State란

```
💡 리액트 컴포넌트의 변경 가능한 데이터
```


<br>


### 2️⃣  State의 특징

→ 자바스크립트 객체

```jsx
class LikeButton extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			liked: false
		};
	}

	...
}
```

this.state 부분이 컴포넌트의 state를 정의하는 부분이다.


<br>

**state를 직접 수정 (잘못된 방법 🚫 )**

```jsx
this.state = {
	name: 'js'
};
```


<br>


**setState 함수를 통한 수정 (정상적인 방법 ⭕ )**

```jsx
this.setState({
	name: 'js'
});
```

→ state는 직접적인 변경이 불가능 하다.



<br>

## 🔘 생명주기

* **마운트(Mount)** : 컴포넌트가 생성되는 시점, 컴포넌트의 생성자가 실행된다. 생성자에서 state를 정의한다. 컴포넌트가 렌더링 된다.

* **업데이트(Update)** : 컴포넌트가 여러번 렌더링 되는 과정, props가 변경되거나 setState()에 의해 state가 변경된다.

* **언마운드(Unmount)** : 상의 컴포넌트에서 현재 컴포넌트를 더 이상 화면에 표시하지 않게 되는 과정



👉[훅(Hook)](https://github.com/kimjaehee18/STUDY/blob/main/React/5-Hook.md)

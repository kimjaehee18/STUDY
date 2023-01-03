# 훅(Hook)


<br>


### 훅이란?
```
💡 리액트의 state와 생명주기 기능에 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만든 것 
```

훅의 이름은 모두 ```use```로 시작한다


<br>

### 1️⃣  useState()
```
💡 state를 사용하기 위한 훅
```

함수 컴포넌트에서는 기본적으로 state라는 것을 제공하지 않기 때문에 클래스 컴포넌트처럼 state를 사용하고 싶으면 useState() 훅을 사용해야 한다.


<br>

**useState() 사용하지 않은 코드**

```jsx
import React, { useState } from "react";

function Counter(props) {
	var count = 0;

	return (
		<div>
			<p>총 {count}번 클릭했습니다.</p>
			<button onClick={() => count++}>
				클릭
			</button>
		</div>
	);
}
```

Counter 함수 컴포넌트는 버튼을 클릭하면 카운트를 하나씩 증가시키고 현재 카운트를 보여준다.


<br>

하지만 위의 코드는 버튼 클릭 시 카운트 값을 증가시키지만 재렌더링이 일어나지 않아 새로운 카운트 값이 화면에 표시되지 않게 된다.

따라서 state를 사용해서 값이 바뀔때마다 재렌터링이 되도록 해야하는데 함수 컴포넌트는 state가 없으므로 useState()를 사용하여 업데이트 한다.

`const [변수명, set함수명] = useState(초깃값);`


<br>


**useState() 사용한 코드**

```jsx
import React, { useState } from "react";

function Counter(props) {
	const [count, setCount] = useState(0);

	return (
		<div>
			<p>총 {count}번 클릭했습니다.</p>
			<button onClick={() => setCount(count + 1)}>
				클릭
			</button>
		</div>
	);
}
```


<br>



### 2️⃣  useEffect()
```
💡 사이드 이펙트(side effect)를 수행하기 위한 훅
```

*사이드 이펙트 : 서버에서 데이터를 받아오거나 수동으로 DOM을 변경하는 등의 작업*

`useEffect(이펙트 함수, 의존성 배열);`

*의존성 배열 : 배열 안에 있는 변수 중에 하나라도 값이 변경되었을 때 이펙트 함수 실행*


<br>


**useEffect() 사용한 코드**

```jsx
import React, { useState } from "react";

function Counter(props) {
	const [count, setCount] = useState(0);

	useEffect(() => {
		document.title = `총 ${count}번 클릭했습니다.`;
	});

	return (
		<div>
			<p>총 {count}번 클릭했습니다.</p>
			<button onClick={() => setCount(count + 1)}>
				클릭
			</button>
		</div>
	);
}
```

*useEffect() 를 사용해서 클래스 컴포넌트에서 제공하는 componentDidMount(), componentDidUpdate() 와 같은 생명주기 함수의 기능을 동일하게 수행한다.*

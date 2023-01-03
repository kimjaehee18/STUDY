## 훅을 사용한 컴포넌트 개발

> **프로젝트 구성도**
>
>src 
> 
>    - index.js 
>    - component
> 
>        - css
>        - js
> 
>      - useCounter.jsx
> 
>      - Accommodate.jsx
> 


<br>

**useCounter.jsx**

```jsx
import React, { useState } from "react";

function useCounter(initialValue) {
    const [count, setCount] = useState(initialValue);

    const increaseCount = () => setCount((count) => count + 1);
    const decreaseCount = () => setCount((count) => Math.max(count - 1, 0));

    return [count, increaseCount, decreaseCount];
}

export default useCounter;
```

<br>



**Accommodate.jsx**

```jsx
import React, { useEffect, useState } from "react";
import useCounter from "./useCounter";

const MAX_CAPACITY = 10;

function Accommodate(props) {
    const [isFull, setIsFull] = useState(false);
    const [count, increaseCount, decreaseCount] = useCounter(0);

    useEffect(() => {
        console.log("=======================");
        console.log("useEffect() is called.");
        console.log(`isFull: ${isFull}`);
    });

    useEffect(() => {
        setIsFull(count >= MAX_CAPACITY);
        console.log(`Current count value: ${count}`);
    }, [count]);

    return (
        <div style={{padding: 16}}>
            <p>{`총 ${count}명 수용했습니다.`}</p>

            <button onClick={increaseCount} disabled={isFull}>
                입장
            </button>
            <button onClick={decreaseCount}>퇴장</button>

            {isFull && <p style={{color: "red"}}>정원이 가득찼습니다. </p>}
        </div>
    );
}

export default Accommodate;
```


<br>


**index.js**

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import reportWebVitals from './reportWebVitals';
import Accommodate from './component/js/Accommodate';

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
  <React.StrictMode>
    <Accommodate />
  </React.StrictMode>,
);

reportWebVitals();
```


<br>


**결과창**

입장 버튼 누른 후


<img src="https://user-images.githubusercontent.com/72512101/210359965-1f29c434-c726-407f-9b6d-1373c4e5f457.png" style="width:50%; height:50%">

<img src="https://user-images.githubusercontent.com/72512101/210359968-c832040d-63e7-458b-be4e-36536c97f06a.png" style="width:50%; height:50%">



<br>


퇴장 버튼 누른 후

<img src="https://user-images.githubusercontent.com/72512101/210359969-cf2477b9-4042-4d3d-8601-48cd88943cd7.png" style="width:50%; height:50%">

## 댓글 컴포넌트 만들기

> **프로젝트 구성도**
> 
> src
> 
> 
>    - index.js 
>    - component
> 
>        - css
>            - Comment.css
>        - js
> 
>      - Comment.jsx
> 
>      - CommentList.jsx
> 


<br>


**Comment.jsx**

```jsx
import React from "react"; 
import '../css/Comment.css';         //css 파일 불러오기
import imageA from './user.png';     //imageA로 이미지 경로 불러오기

function Comment(props) {
    return (
        <div className="wrapper">
            <div className="image">
                <img src={imageA} />     //앞에서 불러온 이미지 경로를 대입
            </div>
        
            <div className="user">
                <span><b>{props.name}</b></span>    //
            </div>
            <div className="comment"><span>{props.comment}</span></div>
        </div>
    );
}

export default Comment;
```


<br>


**CommentList.jsx**

```jsx
import React from "react";
import Comment from "./Comment";     //Comment 컴포넌트 사용

function CommentList(props) {
    return(
        <div>
            <Comment  name="홍길동" comment="리액트 공부" />  //name, comment 전달
            <Comment  name="서동현" comment="리액트 공부2" />
        </div>
    );
}

export default CommentList;
```


<br>



**Comment.css**

```css
.wrapper {
    display: flex;
    border: 1px solid gray;
    border-radius: 16px;
    margin: 10px;
    padding: 10px;
}

img {
    width: 50px;
}

.user {
    margin-left: 20px;
    margin-top:5px;
}

.comment {
    position: relative;
    margin-top: 30px;
    left: -42px;
}
```


<br>


**index.js**

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import reportWebVitals from './reportWebVitals';
import CommentList from './component/js/CommentList';

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
  <React.StrictMode>
    <CommentList />
  </React.StrictMode>,
);

reportWebVitals();
```



<br>




**결과창**

<img src="https://user-images.githubusercontent.com/72512101/210359095-c1c92b39-f55f-4b26-9e5e-181267a85e38.png" style="width:50%; height:50%">

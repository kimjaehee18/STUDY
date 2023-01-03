## **State와 생명주기 함수 사용하기**

> **프로젝트 구성도**
> 
> src
> 
>    - index.js 
>    - component
> 
>        - css
>            - Notification.css
>        - js
> 
>      - Notification.jsx
> 
>      - NotificationList.jsx


<br>


**Notification.jsx**

```jsx
import React from "react";
import '../css/Notification.css'

class Notification extends React.Component {
    constructor(props){
        super(props);
        this.state = {};
    }

    render() {
        return (
            <div className="wrapper">
                <span className="messageText">
                    {this.props.message}
                </span>
            </div>
        );
    }
}

export default Notification;
```


<br>


**NotificationList.jsx**

```jsx
import React from "react";
import Notification from "./Notification";

const reservedNotifications = [
    {
        message: "안녕하세요, 오늘 일정을 알려드립니다.",
    },
    {
        message: "점심 식사 시간입니다.",
    },
    {
        message: "이제 곧 미팅이 시작됩니다.",
    },
];

var timer;

class NotificationList extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            notification: [],
        };
    }

    componentDidMount() {
        const { notification } = this.state;
        timer = setInterval(() => {
            if(notification.length < reservedNotifications.length) {
                const index = notification.length;
                notification.push(reservedNotifications[index]);
                this.setState({
                    notification: notification,
                });
            }else {
                clearInterval(timer);
            }
        }, 3000);
    }

    render() {
        return (
            <div>
                {this.state.notification.map((notification) => {
                    return <Notification message={notification.message} />;
                })}
            </div>
        );
    }
}

export default NotificationList;
```


<br>


**Notification.css**

```css
.wrapper {
    margin: 8;
    padding: 8;
    display: flex;
    flex-direction: row;
    border: 1px solid gray;
    border-radius: 16;
}

.messageText {
    color:black;
    font-size: 16;
}
```


<br>


**index.js**

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import reportWebVitals from './reportWebVitals';
import NotificationList from './component/js/NotificationList';

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
  <React.StrictMode>
    <NotificationList />
  </React.StrictMode>,
);

reportWebVitals();
```

<br>


**결과창**

<img src="https://user-images.githubusercontent.com/72512101/210359500-c71724e7-172f-4893-b130-f7054dbda3c9.png" style="width:50%; height:50%">

<br>


3초 후

<img src="https://user-images.githubusercontent.com/72512101/210359504-afe60dc6-55bc-499d-abf3-16446a416943.png" style="width:50%; height:50%">

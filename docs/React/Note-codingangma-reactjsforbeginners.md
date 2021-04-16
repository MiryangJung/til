---
layout: default
title: Note.codingangma-reactjsforbeginners
parent: React
---

# 코딩앙마 초보자를 위한 ReactJS 강의노트
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

>  [코딩앙마 초보자를 위한 ReactJS](https://youtube.com/playlist?list=PLZKTXPmaJk8J_fHAzPLH8CJ_HO_M33e7-)


## 설치해야할 것들

- node.js


## react 앱 만들기

create-react-app : React 웹 개발용 Boilerplate

```
npx create-react-app my-app
npm start
```


# 컴포넌트

__component/Hello.js__

```
export default function Hello(){
    return <p>Hello</p>;
}
```

__App.js__

```
import './App.css';
import Hello from './component/Hello'
import Welcome from './component/Welcome'

function App() {
  const name = "TOM"
  return (
    <div className="App">
      <Hello />
      <Welcome />
      <Welcome />
    </div>
  );
}

export default App;
```

__component/Hello.js__

```
import World from "./World"


export default function Hello(){
    return (
        <>
        <p>Hello</p>
        <World />
        </>
    )
}
```

__component/Welcome.js__

```
export default function Welcome(){
    return <h1>Welcome</h1>;
}
```

__component/World.js__

```
export default function World(){
    return <h1>World</h1>;
}
```

# CSS

- 인라인 스타일

```
<p style={{
            color:"#aaa",
            borderRight:"2ppx solid #000"
        }}>
```

- css 모듈
   - Hello.css 로 만든다고해서 Hello 컴포넌트에만 css가 적용되는 것이 아님
   - 모듈을 이용하면 컴포넌트 별로 css 따로 작성 가능

__hello.module.css__

```
.box{
    width: 100px;
    height: 100px;
    background-color: aqua;
}
```

__Hello.js__

```
import World from "./World"
import styles from "./Hello.module.css"

export default function Hello(){
    return (
        <>
        <p className={styles.box}>
            Hello
        </p>
        <World />
        </>
    )
}
```


# 이벤트 처리


__Hello.js__

```

function showName(name){
    console.log(name);
}

export default function Hello(){
    return (
        <div>
            <h1>hello</h1>
            <button onClick={()=>showName("tom")}>Show name</button>
        </div>
    )
}
```

# state, useState

```
const [상태 값 저장 변수, 상태 값 갱신 함수] = useState(초기값);
```

__Hello.js__

```
import { useState } from "react";

export default function Hello(){
    const [name, setName] = useState('Mike');

    function changeName(){
        setName(name === "Mike" ? "Jane" : "Mike");
    }

    return (
        <div>
            <h1>state</h1>
            <h2>{name}</h2>
            <button onClick={changeName}>Change</button>
        </div>
    )
}
```

반복해서 컴포넌트를 사용해도 state는 각각 관리된다.

__App.js__

```
<Hello />
<Hello />
<Hello />
```


# props

__App.js__

```
 <Hello age={10}/>
      <Hello age={20}/>
      <Hello age={30}/>
```

__Hello.js__

```
export default function Hello(props){
   ...
    return (
        <div>
            <h2>{name}({props.age}세)</h2>
        </div>
    )
}
```

전달받은 값은 변경 불가능

```
props.age = 1; // error
```

`useState` 를 이용해 해당 변수의 state를 변경 가능

```
import { useState } from "react";

export default function Hello(props){
    const [name, setName] = useState('Mike');
    const [age, setAge] = useState(props.age);

    function changeAge(){
        setAge(age+1);
    }

    return (
        <div>
            <h2>{name}({age}세)</h2>
            <button onClick={changeAge}>Change</button>
        </div>
    )
}
```

# 더미 데이터

__db/data.json__

```
{
    "days": [
      {
        "id": 1,
        "day": 1
      },
      ...
    ],
    "words": [
      {
        "id": 1,
        "day": 1,
        "eng": "book",
        "kor": "책",
        "isDone": false
      },
      ...
    ]
  }
```

__DayList.js__

```
import dummy from "../db/data.json"

export default function DayList(){
    console.log(dummy);
    return <>day list</>;
}
```

# map

```
import dummy from "../db/data.json"

export default function DayList(){
    console.log(dummy);
    return (
        <ul>
            {dummy.days.map(day=>(
                <li key={day.id}>Day  {day.day}</li>
            ))}
        </ul>
    );
}
```

# react-router-dom

```
npm install  react-router-dom
```

__App.js__

```
import Header from './component/Header'
import DayList from './component/DayList'
import Day from './component/Day'
import EmptyPage from './component/EmptyPage'
import {BrowserRouter, Route, Switch} from 'react-router-dom'

function App() {
  return (
    <BrowserRouter>
      <div className="App">
        <Header />
        <Switch>
          <Route exact path="/">
            <DayList />
          </Route>
          <Route path="/day/:day">
            <Day />
          </Route>
          <Route>
            <EmptyPage />
          </Route>
        </Switch>
      </div>
    </BrowserRouter>
  );
}

export default App;
```

__component/Day.js__

```
import dummy from "../db/data.json"
import {useParams} from "react-router-dom"

export default function Day(){
    const day = useParams().day;
    const wordList = dummy.words.filter(word=>word.day===day);
    return (
        <>
        <h2>Day {day}</h2>
        <table>
            <tbody>
                {wordList.map(word=>(
                    <tr key={word.id}>
                        <td>{word.eng}</td>
                        <td>{word.kor}</td>
                    </tr>
                ))}
            </tbody>
        </table>
        </>
    )
}
```

__component/DayList.js__

```
import {Link} from "react-router-dom";
import dummy from "../db/data.json";

export default function DayList(){
    return (
        <ul>
            {dummy.days.map(day=>(
                <li key={day.id}>
                    <Link to={`/day/${day.day}`}>Day  {day.day}</Link>
                </li>
            ))}
        </ul>
    );
}
```

__component/Header.js__

```
import {Link} from "react-router-dom";

export default function Header(){
    return (
        <div className="header">
            <h1>
                <Link to="/">토익 영단어(고급)</Link>
            </h1>
            <div className="menu">
                <a href="#x" className="link">
                    단어 추가
                </a>
                <a href="#x" className="link">
                    Day 추가
                </a>
            </div>
        </div>
    );
}
```

__component/EmptyPage.js__

```
import {Link} from "react-router-dom";

export default function Header(){
    return (
        <div>
            <Link to="/">돌아가기</Link>
        </div>
    );
}
```


# Json-server

```
npm install -g json-server
json-server --watch ./src/db/data.json --port 3001
```

# useEffect

컴포넌트 렌더링 이후에 일을 수행

한 번만 실행하고자 할 땐 빈배열 전달

```
useEffect(()=>{...}, []);
```

# useRef

ref 객체 반환

```
const inputEl = useRef(null);
<input ref={inputEl} type="text" />
```

# useHistory

페이지 이동

# ts 적용

```
npm install typescript @types/node @types/react @types/react-dom @types/jest
```
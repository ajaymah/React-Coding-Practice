### 1 - Data Table with pagination features. ###
<a href="https://flems.io/#0=N4IgZglgNgpgziAXAbVAOwIYFsZJAOgAsAXLKEAGhAGMB7NYmBvEAXwvW10QICsEqdBk2J4hcYgAIArnBgAnOJIC8k5AB00kycE3bt6kBAAmhxJICMFPfsOYcZyYYCiWaAE9JAYUJND1rVsQDABzGEcAJgAOAP0nEFpqamkABwxiCHpHQwBlWjBiAHcMeRhJZzQQiDQYBUMbdhtdQIMjUyRJCNig+3COwwAldwwtABVCWiwUuCzKG1bQvvMAZi75+MTktIzZ80MAWRKAaxgMyslDzDD5esDGwOa4wxNHZe7W3uyQPJTCCAxJAAFdIwKD+daGRaRACs7w2SVS6UyaC+ABF0gCAIKYKDuCS3bT3bSPIIvDoAFjhdi4X32EGohAwoMkABlauCWvEoRSrBCEgjtsivl5nAB5AmSIk6Plk8ywvmffogUVQCAAN3+kgAQvJaIUUXNOZCwpEAJxU-lbJG7eIAcXkGF+9MkqPgEBCNRuIAa3RJrVlkgAbBbFXsQJjYAAPEbGBSSAASGCgYMNT2CJo6yxifM2iJ2BrDOST8EkAxgKVKcgYSLVfR9TRl7XMAHYQzSlQBJOAYABGoKgAPRGrgHLT3PMEWDOYF1oL8VGMAwDLq3ruvsbjmzRpAofizmIjK0AHU-oxR0Fx5JlvLt7nBTbDCyMIV3Cv6w8Nx1zQr22GWR5JFGB0DQtS9lgABgtO9Zy+AA5aRFDrNcG23AMLEgn8HCVAApaRVRGSQizQZcAC9zwWDMVm-W8Z3zL4KiqGo32Qj9UKbSxeW3XdDExNUAUOeQznIrlKM6VtpytOicNoBCcQgfFV0Jdc2McCw1i4394i1JheGwapJCPJMTi9UDRPJdS02gqSw1RRJiFoL132JT9zAsN5MKWeIfBKKBaGIRhtV1WgjhHVML1E5ZOMs2ihSVeMBguEZFkcljnJUjoLEpDyvltXt5AgZlE3kfLQtMzzlinGjJNisMO1Gbx6DgPDiBGYgJSlP14jQm8024kBEzQTBCEAjB3F8ky+UvCIsqqvMaviHJiGkWMGHa5S0zQyres0wxsKXEL6ECvUQMmsyMNm+850MLVZGqeAlFFfVmKUlCNvYixxI0rCwwAaVGgdWRgQp5OE41yvci6YKVZxawYIEB0G57JXW0l3q3bbvviFlaBCAi6WIZdk1B9Nys+6LqofcN5AZCBGGoNrFOR17UdU6iMc8g5NVy6n-mJqa2aCKz5p4wT5IZpzpXSidzvZuCMVVMpEyJsKKPKmbybmymFyXXwUpe1i3siKKeh25VVVreQgRBFMytedHBZiym8gKYpShdGBa18lIkY6lzOgsk3McMQEmFBWhvcS0WTu3KatodimrpAI98sYPWmYNlmOgiCHZaVABFaRqi0Nk+ltzMevjzXE4qYhSgrUOELW5n-XY6a2yDkABh15kfogLA+YimXK8utERDFpuM5bmF24575sGkZk9uoA7o7HMyA9aIXKafF8fZRqes7jj5TYXOBuwTJMbdOzzoigx3E-tR0-mod24HdT0J7Sw2s7JwPZ4AVSwACYEjAr4xwigLTe99aTHFONUEIiUrh72bl1Vu9tj4dwAGrVGoCII6wVSrX1eEfeECcvh1QamgJqUAWqrUZr7KWnRIHxD6oZGhcYTy01LkQnkd8yHQ0qHdZBk9UGvCHhg2eAANDAGo4xEVIgPcGfCq5fCLLAJQZZ65VhahkWsn9JbfxWMbCRXwACaap6A1EjkJFWIkb7MMMFvRO2tlxpwYYYq8G8WGmwAFq0DKCXRRkRf5QP4TZDEkhsRJjxOLVKBjM4rBzn-L4mIezugwNAI6+ogmZnVsPKGYZ4KIX0Z1Z47Flh5JMUqLwxYewX2KiDWxYM7bKJHkqG6b8ahn0kI9D+9D96iPLjPNE-xMAjTGg5HJRjWkFL3LDKQgIEZ9IlqUtoxDhnQ1gCMByBkjIrjLuYck4jSEqOqWKdqmgAC6mhNAwEjCkByUhYxgAwM1GQchFAAG5KAgDkLAemyIEA8AiBYU0iAQVsA4DuLgeB8DUDPj8oQjBmA8DYJc1gQA" target="_blank">Copy Data</a>
```
import { useState, useEffect } from "react";
import users from "./data/users";

export default function DataTable() {
  const [message, setMessage] = useState("Data Table");
  const [showPL, setPL] = useState([5, 10, 20]);
  const [data, setData] = useState(users);
  const [startPage, setSP] = useState(1);
  const [endpage, setEP] = useState(0);
  const [startNEXt, setNS] = useState(0);
  const handleSelect = (e) => {
    let num = e.target.value;
    let orignalData = [...users];
    let sliceData = orignalData.slice(0, num);
    setData(sliceData);
    const s = orignalData.length / num;
    setEP(Math.ceil(s));
    setNS(parseInt(num));
    setSP(1);
  };
  const pageAction = (e, val) => {
    e.preventDefault();
    if (val == "next") {
      let oData = [...users];
      let x = startNEXt * startPage;
      let y = parseInt(x+startNEXt)
      const sl = oData.slice(x, y);
      setData(sl);
      setSP((p) => p + 1);
    }
    if (val == "prev") {
      let oData = [...users];
      setSP((p) => p - 1);
      let x1 = startNEXt * (startPage - 1);
      const sl = oData.slice(x1 - startNEXt, x1);
      setData(sl);
    }
  };
  useEffect(() => {
    let orignalData1 = [...users];
    let sliceData1 = orignalData1.slice(0, 5);
    setData(sliceData1);
    const s = orignalData1.length / 5;
    setEP(Math.ceil(s));
    setNS(5);
  }, []);
  return (
    <div>
      <h1>
        {message} - {users.length} {startNEXt}
      </h1>
      <table>
        <thead>
          <tr>
            {[
              { label: "ID", key: "id" },
              { label: "Name", key: "name" },
              { label: "Age", key: "age" },
              { label: "Occupation", key: "occupation" },
            ].map(({ label, key }) => (
              <th key={key}>{label}</th>
            ))}
          </tr>
        </thead>
        <tbody>
          {data.map(({ id, name, age, occupation }) => (
            <tr key={id}>
              <td>{id}</td>
              <td>{name}</td>
              <td>{age}</td>
              <td>{occupation}</td>
            </tr>
          ))}
        </tbody>
      </table>
      <div>
        <div className="pp">
          <select onChange={handleSelect}>
            {showPL.map((p) => (
              <option value={p}>Show {p}</option>
            ))}
          </select>
          <button
            onClick={(e) => pageAction(e, "prev")}
            disabled={startPage == 1 ? true : false}
          >
            Prev
          </button>
          <span>
            {" "}
            Page {startPage} of {endpage}{" "}
          </span>
          <button
            onClick={(e) => pageAction(e, "next")}
            disabled={endpage == startPage ? true : false}
          >
            {" "}
            Next
          </button>
        </div>
        <div></div>
        <div></div>
        <div></div>
      </div>
    </div>
  );
}

```
### 2- dice roller app that simulates the results of rolling 6-sided dice ###
```
import { useState } from 'react';

export default function App() {
  const [message, setMessage] = useState('Hello World!');
  const [count, setCount] = useState(0);
  const [dise, setDise] = useState([])
  const changeHandler = (e)=>{
    const {value} = e.target
    setCount(value)    
  }
  const addHandler = (e)=>{
    //e.preventDefault();
    let arr = []
    for(let i=0; i < count; i++){
      let x = {
        c:i,
        n:RNumber(),
      }
      arr.push(x)
    }
    setDise(arr)
  }
  const RNumber = ()=>{
    let arr = []
    let x = (Math.floor(Math.random() * 6) + 1)
    for(let i=0; i < x; i++){
      arr.push(i)
    }
    return arr;
  }
  return (
    <div>
    <p><input type="text" onChange={changeHandler} />
    <button onClick={addHandler}>Add</button></p>
    <div className="w">
       {dise.map((a)=>{
        return (
          <div className={`d a-${(a.n.length)}`}>
            {a.n.map((b)=>{
              return(
                <div className="i">{b}</div>
              )
            })}
          </div>
        )
       })}
    </div>
    </div>
  );
}

```
### 3- Trafic light ###
```
import React, {useState, useEffect} from 'react';
export default function TrafficLight() {
  const [hightlight, setHightLight] = useState("red");
  useEffect(()=>{
    let timer;
    if(hightlight == 'red'){
       timer = setTimeout(()=>{
                  setHightLight('yellow');
                  clearTimeout(timer)
                }, 2000)
    } else if(hightlight == 'yellow'){
       timer = setTimeout(()=>{
                  setHightLight('green');
                  clearTimeout(timer)
                }, 1000)
    } else {
      timer = setTimeout(()=>{
                  setHightLight('red');
                  clearTimeout(timer)
                }, 3000)
    }
   
  },[hightlight])
  return (
    <>
    <div className="traficLight">
      <div className={`light red ${hightlight == "red" ? 'hightlight' : ""}`}></div>
      <div className={`light yellow ${hightlight == "yellow" ? 'hightlight' : ""}`}></div>
      <div className={`light green ${hightlight == "green" ? 'hightlight' : ""}`}></div>
    </div>
    </>
  );
}
```
```
body {
  font-family: sans-serif;
}
.traficLight {
  width: 80px;
  height: 240px;
  border: 5px solid #000;
  border-radius: 100px;
  background-color: #bbb;
  position: relative;
}
.traficLight:before{
  border:2px solid #000;
  content:"";
  height: 100px;
  width:5px;
  position: absolute;
  top:100%;
  left:45%;
  background: #000;

}
.traficLight > div {
  width: 80px;
  height: 80px;
  border: 0px solid #eee;
  border-radius: 100px;
  background: #aaa;
  box-shadow:1px 1px 10px 2px #000000
}
.traficLight > div.red.hightlight {
  background: #ff0000;
}
.traficLight > div.yellow.hightlight {
  background: #ff0;
}
.traficLight > div.green.hightlight {
  background: green;
}

```
### 4- Loazy Load ###
```
import { useState, useEffect } from "react";

export default function App() {
  const [orignaldata, setOrignalData] = useState([]);
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [visiableCount, setVCount] = useState(2)
  const fetchData = async () => {
    try {
      const res = await fetch("https://jsonplaceholder.typicode.com/users");
      if (!res.ok) throw new Error("failed");
      const data = await res.json();
      setOrignalData(data);
      setData(data);
    } catch (err) {
      setError("failing..");
    } finally {
      setLoading(false);
    }
  };
  const loadmore = ()=>{
    setLoading(true)
    setTimeout(()=>{
      setVCount((preCount)=>preCount+2)
      setLoading(false)
    }, 3000)
    
  }
  useEffect(() => {
    fetchData();
  }, []);
  return (
    <>
      <h2>{"Hacker News Jobs Board"}</h2>
      {loading && "Loading..."}
      <ul className="dataList">
        {data.slice(0,visiableCount).map((item, i) => {
          return (
            <li key={i}>
              <h4>
                {item.name} - {item.username}
              </h4>
              <p>{item.company.catchPhrase}</p>
              <p>Email:- {item.email}</p>
              <address> 
              <strong>Street</strong> : {item.address.street} 
              <br/><strong>City</strong> :{item.address.city} 
              <br/> <strong>Zip</strong> : {item.address.zipcode}
              </address>
            </li>
          );
        })}
      </ul>
      <div><button onClick={loadmore}>{ !loading ? "Load more.." : "Loading..."}</button></div>
    </>
  );
}

```


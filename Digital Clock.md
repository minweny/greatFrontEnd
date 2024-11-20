Clock.js
```
import {useState, useEffect} from 'react';

export default function Clock() {
  const [time, setTime] = useState(new Date());

  const hours = time.getHours(); // Get the current hour
  const h1 = Math.floor(hours / 10);
  const h2 = hours % 10;

  const minutes = time.getMinutes(); // Get the current minute
  const m1 = Math.floor(minutes / 10);
  const m2 = minutes % 10;

  const seconds = time.getSeconds(); // Get the current second
  const s1 = Math.floor(seconds / 10);
  const s2 = seconds % 10;

  useEffect(() => {
    const interval = setInterval(() => {
      setTime(new Date());
    }, 1000);

    return () => clearInterval(interval);
  }, []);
  

  return (
    <div className="clock-outer">
      <div className="clock">
        <Digit digit={h1} />
        <Digit digit={h2} />
        <Digit digit={':'} />
        <Digit digit={m1} />
        <Digit digit={m2} />
        <Digit digit={':'} />
        <Digit digit={s1} />
        <Digit digit={s2} />
      </div>
    </div>
  );
}

function Digit({digit}) {
  return (
    <span className="digit">{digit}</span>
  );
}

```

styles.css
```
body {
  font-family: sans-serif;
  
}

.clock-outer {
  width: 300px;
  height: 100px;
  background-color: grey;
  padding: 10px;
  display: flex;
}

.clock {
  flex-grow: 1;
  background-color: black;
  
  display: flex;
  flex-direction: row;
  /* gap: 20px; */
  align-items: center;
  justify-content: center;
}

.digit {
  color: white;
  font-size: xxx-large;
}

```
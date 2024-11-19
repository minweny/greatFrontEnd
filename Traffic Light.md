TrafficLight.js
```
import React, {useState, useEffect} from 'react';

export default function TrafficLight() {
  const [currentLight, setCurrentLight] = useState('red');

  useEffect(() => {
    const interval = setInterval(() => {
      if (currentLight === 'red') {
        setCurrentLight('yellow');
      } else if (currentLight === 'yellow') {
        setCurrentLight('green');
      } else {
        setCurrentLight('red');
      }
    }, currentLight === 'red' ? 4000: currentLight === 'yellow'? 500: 3000);

    return () => clearInterval(interval);
  }, [currentLight]);
  return (
    <div className="traffic-light">
      <div className={`light ${currentLight === 'red' ? 'red': 'inactive'}`} />
      <div className={`light ${currentLight === 'yellow' ? 'yellow': 'inactive'}`} />
      <div className={`light ${currentLight === 'green' ? 'green': 'inactive'}`} />
    </div>
  );
}

```

styles.css
```
body {
  font-family: sans-serif;
}

.traffic-light {
  width: 100px;
  height: 250px;
  background-color: black;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
}

.light {
  width: 70px;
  height: 50px;
  border-radius: 50%;
  background-color: white;
}

.light.red {
  background-color: red;
}

.light.yellow {
  background-color: yellow;
}

.light.green {
  background-color: green;
}

```
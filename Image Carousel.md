ImageCarousel.js
```
import { useState } from 'react';
import './styles.css';

export default function ImageCarousel({ images }) {
  const [idx, setIdx] = useState(0);
  const image = images[idx];
  const buttons = [];
  for (let i = 0; i < images.length; i++) {
    buttons.push(
      <button className={`bottom-button ${i === idx? "active":""}`} onClick={() =>
        setIdx(i)
      }></button>
    );
  }

  return (
    <div className="container">
      <div className="carousel">
        <img key={image.src} alt={image.alt} src={image.src} />
        <button className="side-button left" onClick={() =>{
          setIdx((pre) => {
            return pre === 0 ? images.length - 1: pre - 1;
          });
        }
        }>{"<"}</button>
        <button className="side-button right" onClick={() =>{
          setIdx((pre) => {
            return pre === images.length - 1 ? 0: pre + 1;
          });
        }
        }
        >{">"}</button>
        <div className="bottom-buttons">{buttons}</div>
      </div>
    </div>
  )
}


```

styles.css
```
body {
  font-family: sans-serif;
}

img {
  object-fit: contain;
  width: 100%;
  height: 100%;
  /* position: absolute; */
}

.carousel {
  width: min(600px, 100vw);
  height: min(400px, 100vh);
  position: relative;
  background-color: black;
}

.side-button {
  top: 50%;
  width: 40px;
  height: 40px;
  border-radius: 100%;
  position: absolute;
}

.left {
  left: 20px;
}

.right {
  right: 20px;
}

.bottom-buttons {
  left: 50%;
  transform: translateX(-50%);
  bottom: 80px;
  position: absolute;
  display: flex;
  gap: 8px;
}

.bottom-button {
  width: 10px;
  height: 10px;
  border-radius: 100%;
  /* display: inline-block; */
  background-color: white;
}

.active {
  background-color: black;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  
  width: 100vw;
  height: 100vh;
}


```
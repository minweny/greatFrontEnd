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
      <button onClick={() =>
        setIdx(i)
      }>{i}</button>
    );
  }

  return (
    <div className="container">
      <div className="carousel">
        <img key={image.src} alt={image.alt} src={image.src} width="100%" />
        <button onClick={() =>{
          setIdx((pre) => {
            return pre === 0 ? images.length - 1: pre - 1;
          });
        }
        }>Left</button>
        <button onClick={() =>{
          setIdx((pre) => {
            return pre === images.length - 1 ? 0: pre + 1;
          });
        }
        }
        >Right</button>
      </div>
      <div>{buttons}</div>
    </div>
  )
}

```

styles.css
```
body {
  font-family: sans-serif;
}

.carousel {
  max-width: 600px;
  max-height: 400px;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

```
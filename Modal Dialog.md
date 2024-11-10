App.js
```
import { useState } from 'react';

import ModalDialog from './ModalDialog';

export default function App() {
  const [title, setTitle] = useState('Modal Dialog');
  const [visible, setVisible] = useState(false);
  const open = () => setVisible(true);
  const close = () => setVisible(false);

  return (
    <div>
      <button onClick={open}>Open Modal</button>
      {visible && 
      <ModalDialog title={title} close={close}>
        One morning, when Gregor Samsa woke from troubled
        dreams, he found himself transformed in his bed into
        a horrible vermin. He lay on his armour-like back,
        and if he lifted his head a little he could see his
        brown belly, slightly domed and divided by arches
        into stiff sections.
      </ModalDialog>}
    </div>
  );
}

```

ModalDialog.js
```
import './styles.css';

export default function ModalDialog({ children, title, close }) {
  return (
    <div className="modal-overlay">
      <div className="modal">
        <h1>{title}</h1>
        {children}
        <div>
          <button onClick={close}>Close</button>
        </div>
      </div>
    </div>
  );
}

```

styles.css
```
body {
  font-family: sans-serif;
}

.modal-overlay {
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  inset: 0;
  padding: 40px;
}

.modal {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  gap: 20px;
  background-color: white;
}

```
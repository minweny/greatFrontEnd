App.js
```
import {useState} from 'react';

export default function App() {
  const [todos, setTodos] = useState(["Walk the dog", "Water the plants", "Wash the dishes"]);
  const deleteTodo = (index) => {
    todos.splice(index, 1);
    setTodos([...todos]);
  };
  const [todo, setTodo] = useState("");
  const handleChange = (e) => {
    setTodo(e.target.value);
  }
  const handleSubmit = (e) => {
    e.preventDefault();
    setTodos([...todos, todo]);
    setTodo('');
  }
  return (
    <div>
      <h1>Todo List</h1>
      <div>
        <input type="text" placeholder="Add your task"
          value={todo} 
          onChange={handleChange}
        />
        <div>
          <button onClick={handleSubmit}>Submit</button>
        </div>
      </div>
      <ul>
        {todos.map((item, index) => 
          <li key={index}>
            <span>{item}</span>
            <button onClick={() => deleteTodo(index)}>Delete</button>
          </li>
        )}
      </ul>
    </div>
  );
}

```
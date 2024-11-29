App.js
```
import { useState, useEffect } from 'react';

function Job({job}) {
  const {title, by, time} = job;
  const date = new Date(time * 1000);
  return <div className="job">
    <p>{title}</p>
    <p>By {by} - {date.toLocaleString()}</p>
  </div>;
}

export default function App() {
  const [ids, setIds] = useState([]);
  const [jobs, setJobs] = useState([]);

  const fetchMultiple = (ids) => {
    const start = jobs.length;
    const end = Math.min(start + 6, ids.length + 1);
    const newIds = ids.slice(start, end);
    Promise.all(newIds.map(id => fetch(`https://hacker-news.firebaseio.com/v0/item/${id}.json`)))
    .then(responses => Promise.all(responses.map(response => response.json())))
    .then(newJobs => {
      const jobs2 = [...jobs, ...newJobs];
      setJobs(jobs2);
    });
  };

  useEffect(() => {
    const fetchIds = async () => {
      const ids2 = await fetch('https://hacker-news.firebaseio.com/v0/jobstories.json')
      .then(response => response.json());
      setIds(ids2);

      if (jobs.length === 0) {
        fetchMultiple(ids2);
      }
    }
    fetchIds();
  }, []);

  return <div className="board">
    <h1>Hacker News Jobs Board</h1>
    {jobs.map((job, idx) => <Job job={job} id={job.id}/>) }
    <button onClick={() => fetchMultiple(ids)}>Load more jobs</button>
  </div>;
}

```

styles.css
```
body {
  font-family: sans-serif;
}

.board {
  background-color:antiquewhite;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.job {
  background-color: white;
  border-radius: 5px;
  padding: 10px;
}
```
# EXP 14 – Fetch Student Details Using an API in React

## NAME: Monisha L

## REG NO: 2305001019

---

## Aim

To develop a React application that fetches student details from a public REST API using the `fetch()` method and displays the details dynamically.

## Objectives

- To understand API integration in React.
- To use the `fetch()` method to retrieve data from an API.
- To implement asynchronous operations using `async` and `await`.
- To manage data using the `useState` hook.
- To display student details dynamically.

## Program

### Step 1: Create a React Project

```bash
npm create vite@latest student-api
cd student-api
npm install
npm run dev
```

Select React as the framework and JavaScript as the variant.

### Step 2: App.jsx

```jsx
import { useState } from "react";
import "./App.css";

function App() {
  const [student, setStudent] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  async function getStudentDetails() {
    setLoading(true);
    setError("");
    setStudent(null);

    try {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users/1"
      );

      if (!response.ok) {
        throw new Error("Failed to fetch student details");
      }

      const data = await response.json();

      data.name = "Monisha";
      setStudent(data);

    } catch (err) {
      setError("Unable to load details. Please try again.");

    } finally {
      setLoading(false);
    }
  }

  return (
    <div className="container">
      <h1>Monisha's Student Management System</h1>

      <p>Click the button to fetch student details from an API.</p>

      <button onClick={getStudentDetails} disabled={loading}>
        {loading ? "Loading..." : "View Details"}
      </button>

      {loading && <p>Fetching data from the API...</p>}

      {error && <p className="error">{error}</p>}

      {student && (
        <div className="student-card">
          <h2>Student Details</h2>
          <p><b>ID:</b> {student.id}</p>
          <p><b>Name:</b> {student.name}</p>
          <p><b>Email:</b> {student.email}</p>
          <p><b>City:</b> {student.address.city}</p>
        </div>
      )}
    </div>
  );
}

export default App;
```

### Step 3: App.css

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f1f5f9;
}

.container {
  max-width: 600px;
  margin: 60px auto;
  padding: 25px;
  text-align: center;
  background: white;
  border-radius: 12px;
}

h1 {
  color: #1d4ed8;
}

button {
  background: #2563eb;
  color: white;
  border: none;
  padding: 12px 22px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.student-card {
  margin-top: 25px;
  padding: 20px;
  background: #dbeafe;
  border-radius: 8px;
  text-align: left;
}

.error {
  color: #dc2626;
}
```

### Step 4: index.css

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
```

### Step 5: main.jsx

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## Output

<img width="1530" height="780" alt="image" src="https://github.com/user-attachments/assets/6fe437db-1aab-4e6a-a9af-d6e1d491aea9" />


## Result

Thus, a React application was successfully developed to fetch student details from a public REST API using the `fetch()` method and display the customized student information dynamically.

---


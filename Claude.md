# SHNOOR Assessment — Full Syllabus Reference
### Detailed notes: JavaScript · React · Node.js · Express.js · REST APIs · SQL/PostgreSQL · Deployment

---

## 1. JavaScript Core

### 1.1 Variables: `var`, `let`, `const`

**Definition:** Three ways to declare a variable in JavaScript, differing in scope, reassignment rules, and hoisting behavior.

- `var` — function-scoped, can be redeclared and reassigned, hoisted and initialized as `undefined`
- `let` — block-scoped (`{}`), can be reassigned but not redeclared in the same scope
- `const` — block-scoped, cannot be reassigned — but if it holds an object/array, the *contents* can still change

**Example:**
```js
function example() {
  if (true) {
    var a = 1;   // function-scoped — leaks outside the if block
    let b = 2;   // block-scoped — only exists inside {}
  }
  console.log(a); // 1 (accessible)
  console.log(b); // ReferenceError: b is not defined
}

const arr = [1, 2, 3];
arr.push(4);       // legal — mutating contents
arr = [5, 6];       // TypeError — cannot reassign a const
```

**Why it matters:** Modern JS (and every code review) expects `let`/`const`, never `var`. Interviewers test this to see if you understand *scope*, not just syntax.

---

### 1.2 Data Types

**Definition:** JavaScript has 7 primitive types (`string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`) and one composite type (`object`, which includes arrays and functions).

**Example:**
```js
typeof "hello"     // "string"
typeof 42          // "number"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object"  <-- famous JS quirk/bug, memorize this
typeof {}           // "object"
typeof []           // "object"  <-- arrays are objects
typeof function(){} // "function"
```

**Why it matters:** `typeof null === "object"` is a long-standing JavaScript bug that's now permanent for backward compatibility. It's a classic trick question.

---

### 1.3 Equality: `==` vs `===`

**Definition:** `==` (loose equality) converts operand types before comparing. `===` (strict equality) compares both value and type with no conversion.

**Example:**
```js
"5" == 5    // true  — string "5" is coerced to number 5
"5" === 5   // false — different types, no coercion

null == undefined   // true
null === undefined  // false

0 == false  // true
0 === false // false
```

**Why it matters:** Always use `===` in real code and in this assessment's mental model. `==` produces surprising results that are a classic MCQ trap.

---

### 1.4 Functions: Regular vs Arrow

**Definition:** Regular functions (`function() {}`) have their own `this` binding determined by how they're called. Arrow functions (`() => {}`) do **not** have their own `this` — they inherit it from the enclosing scope.

**Example:**
```js
const obj = {
  name: "Deepak",
  regularFn: function() {
    console.log(this.name); // "Deepak" — this = obj
  },
  arrowFn: () => {
    console.log(this.name); // undefined — this = outer scope, not obj
  }
};

obj.regularFn(); // "Deepak"
obj.arrowFn();   // undefined
```

**Why it matters:** This `this`-binding difference is one of the most commonly tested JS concepts, especially inside callbacks and React class methods.

---

### 1.5 Array Methods: `map()`, `filter()`, `reduce()`

**Definition:**
- `map()` — transforms every element, returns a **new array of the same length**
- `filter()` — returns a **new array** with only elements that pass a test function
- `reduce()` — collapses the array into a **single accumulated value**

**Example:**
```js
const nums = [1, 2, 3, 4, 5];

nums.map(n => n * 2);           // [2, 4, 6, 8, 10]
nums.filter(n => n % 2 === 0);  // [2, 4]
nums.reduce((sum, n) => sum + n, 0); // 15 (0 is the starting value)

// reduce building an object — a common advanced use
const counts = ['a', 'b', 'a'].reduce((acc, letter) => {
  acc[letter] = (acc[letter] || 0) + 1;
  return acc;
}, {});
// { a: 2, b: 1 }
```

**Why it matters:** These three methods are used constantly in real code (especially React rendering) and are a near-guaranteed MCQ topic.

---

### 1.6 Destructuring & Spread/Rest

**Definition:** Destructuring extracts values from arrays/objects into variables. Spread (`...`) expands an iterable; rest (`...`) collects remaining items into an array.

**Example:**
```js
// Object destructuring
const user = { name: "Deepak", age: 21 };
const { name, age } = user;

// Array destructuring
const [first, second] = [10, 20];

// Spread — copying/merging
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]
const merged = { ...user, city: "Nandyal" }; // adds a new field

// Rest — collecting arguments
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3); // 6
```

**Why it matters:** This syntax appears everywhere in React (`{...props}`, state updates) and in Express (`req.body` destructuring).

---

### 1.7 Promises & `async/await`

**Definition:** A **Promise** represents a value that will be available later (e.g., after a network request). It has three states: pending, fulfilled, rejected. `async/await` is syntax that lets you write promise-based code in a sequential, readable style.

**Example:**
```js
// Promise-based
function getUser() {
  return fetch('/api/user').then(res => res.json());
}

// async/await — same logic, cleaner syntax
async function getUser() {
  const res = await fetch('/api/user');
  const data = await res.json();
  return data;
}

// Error handling with async/await
async function getUserSafe() {
  try {
    const res = await fetch('/api/user');
    return await res.json();
  } catch (err) {
    console.error('Failed to fetch user:', err);
  }
}
```

**Common trap:** `async/await` inside `.forEach()` does NOT wait for each iteration — `forEach` ignores returned promises.
```js
// WRONG — does not run sequentially, all fire at once
[1, 2, 3].forEach(async (n) => {
  await doSomething(n);
});

// CORRECT — use a for...of loop instead
for (const n of [1, 2, 3]) {
  await doSomething(n);
}
```

**Why it matters:** Async handling is central to both Node.js backend work and React data fetching — expect multiple questions here.

---

## 2. React

### 2.1 Components & JSX

**Definition:** A component is a reusable function that returns UI described in JSX (JavaScript XML — HTML-like syntax inside JS).

**Example:**
```jsx
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// Usage
<Welcome name="Deepak" />
```

**Why it matters:** JSX compiles to `React.createElement()` calls under the hood — understanding this helps explain why JSX has rules like "must return a single root element."

---

### 2.2 Props vs State

**Definition:**
- **Props** — data passed **into** a component from its parent. Read-only from the child's perspective.
- **State** — data a component **owns and manages internally**, which can change and triggers a re-render when updated.

**Example:**
```jsx
// Props: passed from parent, read-only
function TaskItem({ title, onDelete }) {
  return (
    <li>
      {title}
      <button onClick={onDelete}>Delete</button>
    </li>
  );
}

// State: owned internally
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

**Why it matters:** This distinction — "props flow down, state is owned" — is the single most foundational React concept and gets tested from multiple angles.

---

### 2.3 `useState` Hook

**Definition:** Gives a functional component memory across re-renders. Returns a pair: the current value and a setter function.

**Example:**
```jsx
const [count, setCount] = useState(0);

// Direct update
setCount(count + 1);

// Functional update (safer — avoids stale state issues)
setCount(prev => prev + 1);
```

**Common trap:** State updates are asynchronous and batched — calling `setCount(count + 1)` twice in the same event handler does NOT add 2, because both calls reference the same stale `count`.
```jsx
function handleClick() {
  setCount(count + 1); // uses old count
  setCount(count + 1); // still uses the SAME old count
  // Result: count increases by only 1, not 2
}

// Fix: use the functional form
function handleClickFixed() {
  setCount(prev => prev + 1); // uses latest value
  setCount(prev => prev + 1); // uses latest value again
  // Result: count increases by 2
}
```

**Why it matters:** This exact "stale state" trap is one of the most commonly asked React gotchas in interviews.

---

### 2.4 `useEffect` Hook

**Definition:** Runs side effects (data fetching, subscriptions, timers, manual DOM changes) after the component renders. The dependency array controls when it re-runs.

**Example:**
```jsx
useEffect(() => {
  console.log('Runs after every render');
});

useEffect(() => {
  console.log('Runs once, after first render only');
}, []);

useEffect(() => {
  console.log('Runs when userId changes');
}, [userId]);

// Cleanup function (runs before the next effect, or on unmount)
useEffect(() => {
  const timer = setInterval(() => console.log('tick'), 1000);
  return () => clearInterval(timer); // cleanup
}, []);
```

**Common trap:** Forgetting to include a variable the effect depends on in the dependency array leads to stale closures (the effect keeps using an old value) or, in other cases, missing re-runs entirely.

**Why it matters:** `useEffect` dependency array behavior is one of the top 3 most-tested React topics in any technical screening.

---

### 2.5 Lists and Keys

**Definition:** When rendering a list with `.map()`, React needs a unique `key` prop on each item to track which DOM elements correspond to which data, especially across re-renders.

**Example:**
```jsx
// GOOD — using a stable unique ID
{tasks.map(task => (
  <li key={task.id}>{task.title}</li>
))}

// RISKY — using array index as key
{tasks.map((task, index) => (
  <li key={index}>{task.title}</li>
))}
```

**Why it matters:** Using index as a key breaks when items are reordered, inserted, or deleted — React can misattribute state/DOM nodes to the wrong item. Always prefer a stable ID from your data (like a database `id`).

---

### 2.6 Controlled Components (Forms)

**Definition:** A form input whose value is driven by React state (not the DOM itself). Every keystroke updates state, and the input's `value` reflects that state.

**Example:**
```jsx
function SearchBox() {
  const [query, setQuery] = useState('');

  return (
    <input
      value={query}
      onChange={(e) => setQuery(e.target.value)}
    />
  );
}
```

**Why it matters:** Controlled inputs are the standard React pattern for forms — you'll be expected to recognize and write this pattern.

---

### 2.7 Lifting State Up / Parent-Child Communication

**Definition:** Since props are read-only, a child component cannot directly modify data owned by its parent. Instead, the parent passes down a **callback function** as a prop, and the child calls that function to request a change.

**Example:**
```jsx
function Parent() {
  const [tasks, setTasks] = useState([]);

  function deleteTask(id) {
    setTasks(prev => prev.filter(t => t.id !== id));
  }

  return <TaskList tasks={tasks} onDelete={deleteTask} />;
}

function TaskList({ tasks, onDelete }) {
  return tasks.map(task => (
    <TaskItem key={task.id} task={task} onDelete={() => onDelete(task.id)} />
  ));
}
```

**Why it matters:** This is React's core "one-way data flow" principle. Expect a question phrased like "how does a child notify a parent of a change."

---

## 3. Node.js

### 3.1 The Event Loop

**Definition:** Node.js runs JavaScript on a **single thread**, but achieves concurrency through **non-blocking I/O**. Instead of waiting for slow operations (file reads, database queries, network requests) to finish, Node hands them off to the system and continues processing other work, then comes back via a callback/promise when the result is ready.

**Example (conceptual):**
```js
console.log('1: Start');

setTimeout(() => {
  console.log('3: Timeout callback (runs later)');
}, 0);

console.log('2: End');

// Output order: 1, 2, 3
// Even with 0ms delay, the timeout callback runs AFTER synchronous code finishes
```

**Common trap:** "Node handles concurrency because it's multi-threaded" — **WRONG.** JavaScript execution in Node is single-threaded; the *illusion* of concurrency comes from non-blocking I/O (handled by `libuv` under the hood), not multiple threads running your JS code simultaneously.

**Why it matters:** This is *the* signature Node.js interview question. Understanding "non-blocking ≠ multi-threaded" separates real understanding from memorized buzzwords.

---

### 3.2 Modules: `require`/`module.exports`

**Definition:** Node uses the CommonJS module system to split code across files. `module.exports` defines what a file shares; `require()` imports it elsewhere.

**Example:**
```js
// math.js
function add(a, b) { return a + b; }
module.exports = { add };

// app.js
const { add } = require('./math');
console.log(add(2, 3)); // 5
```

**Why it matters:** Basic but foundational — expect at least one question testing whether you know how files share code in Node.

---

### 3.3 Environment Variables

**Definition:** Configuration values (API keys, database URLs, secrets) kept out of source code and injected at runtime via `process.env`.

**Example:**
```js
require('dotenv').config(); // loads variables from a .env file

const dbUrl = process.env.DATABASE_URL;
const port = process.env.PORT || 3000;
```

**Why it matters:** Security best practice — `.env` files should never be committed to version control (should be in `.gitignore`). This is a common practical question.

---

## 4. Express.js

### 4.1 Basic Server & Routing

**Definition:** Express is a minimal web framework built on Node.js for handling HTTP requests via **routes** — combinations of an HTTP method and a URL path, each mapped to a handler function.

**Example:**
```js
const express = require('express');
const app = express();

app.get('/tasks', (req, res) => {
  res.status(200).json({ tasks: [] });
});

app.post('/tasks', (req, res) => {
  res.status(201).json({ message: 'Task created' });
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

**Why it matters:** This is the backbone of backend work in the assessment's stated stack (Node/Express).

---

### 4.2 Middleware

**Definition:** Functions that run **between** the incoming request and the final route handler. Used for logging, authentication, parsing request bodies, etc. Middleware must call `next()` to pass control forward, or the request hangs.

**Example:**
```js
app.use(express.json()); // built-in middleware — parses JSON request bodies

// Custom middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next(); // REQUIRED — without this, the request never proceeds
});

// Middleware for a specific route (e.g., auth check)
function requireAuth(req, res, next) {
  if (!req.headers.authorization) {
    return res.status(401).json({ error: 'Unauthorized' });
  }
  next();
}

app.get('/protected', requireAuth, (req, res) => {
  res.json({ secret: 'data' });
});
```

**Common trap:** Forgetting `next()` — the request silently hangs with no error, which is a classic live-coding gotcha.

**Why it matters:** Middleware is one of the most heavily tested Express concepts, both in MCQs and in the technical interview.

---

### 4.3 `req.params` vs `req.query` vs `req.body`

**Definition:**
- `req.params` — values from the URL path (e.g., `/tasks/:id`)
- `req.query` — values from the URL query string (e.g., `?sort=asc`)
- `req.body` — data sent in the request payload (e.g., JSON from a POST)

**Example:**
```js
// Route: GET /tasks/:id?verbose=true
app.get('/tasks/:id', (req, res) => {
  console.log(req.params.id);    // from the URL path, e.g. "42"
  console.log(req.query.verbose); // from the query string, e.g. "true"
});

// Route: POST /tasks with JSON body { "title": "Learn Express" }
app.post('/tasks', (req, res) => {
  console.log(req.body.title); // "Learn Express"
});
```

**Why it matters:** Confusing these three is a very common beginner mistake and a frequent MCQ target.

---

## 5. RESTful APIs

### 5.1 REST Principles & HTTP Methods

**Definition:** REST (Representational State Transfer) is a convention for structuring APIs around **resources**, using standard HTTP methods to represent actions on them.

| Method | Purpose | Example |
|---|---|---|
| GET | Read data | `GET /tasks` — list all tasks |
| POST | Create new data | `POST /tasks` — create a task |
| PUT | Replace an entire resource | `PUT /tasks/5` — replace task 5 completely |
| PATCH | Partially update a resource | `PATCH /tasks/5` — update just one field |
| DELETE | Remove a resource | `DELETE /tasks/5` — delete task 5 |

**Common trap — PUT vs PATCH:** `PUT` expects you to send the *entire* resource (missing fields may be wiped or set to null). `PATCH` only updates the fields you actually send.
```js
// PUT — must send the full object
PUT /tasks/5
{ "title": "New title", "is_done": false } // must include ALL fields

// PATCH — send only what changes
PATCH /tasks/5
{ "is_done": true } // only updates this one field
```

**Why it matters:** PUT vs PATCH is one of the most consistently tested REST concepts.

---

### 5.2 HTTP Status Codes

**Definition:** Three-digit codes returned by the server indicating the result of a request.

| Code | Meaning | When to use |
|---|---|---|
| 200 | OK | General success (GET, PATCH, PUT) |
| 201 | Created | After successfully creating a resource (POST) |
| 204 | No Content | Success, but nothing to return (DELETE) |
| 400 | Bad Request | Client sent malformed/invalid data |
| 401 | Unauthorized | Missing or invalid credentials — "I don't know who you are" |
| 403 | Forbidden | Valid credentials, but insufficient permission — "I know you, but you can't do this" |
| 404 | Not Found | Resource doesn't exist |
| 500 | Internal Server Error | Something broke on the server |

**Common trap — 401 vs 403:** Both feel like "access denied" but are semantically different. 401 = authentication problem. 403 = authorization problem.

**Why it matters:** Pure memorization, high point-value, and very likely to appear as direct MCQs.

---

### 5.3 Statelessness & Idempotency

**Definition:**
- **Stateless**: each request must contain everything the server needs to process it (e.g., an auth token) — the server doesn't remember previous requests.
- **Idempotent**: calling the same request multiple times produces the same result as calling it once. `GET`, `PUT`, and `DELETE` are idempotent; `POST` is not.

**Example:**
```js
// Idempotent — calling this 5 times still results in is_done = true
PUT /tasks/5 { "is_done": true }

// NOT idempotent — calling this 5 times creates 5 separate tasks
POST /tasks { "title": "New task" }
```

**Why it matters:** Less commonly tested at the MCQ level but a strong signal of deeper understanding if it comes up in the technical interview.

---

## 6. SQL / PostgreSQL

### 6.1 Basic Queries: SELECT, WHERE, ORDER BY

**Definition:** The core commands for reading data from a table.

**Example:**
```sql
-- Get all columns from all rows
SELECT * FROM tasks;

-- Get specific columns
SELECT title, is_done FROM tasks;

-- Filter rows
SELECT * FROM tasks WHERE is_done = FALSE;

-- Sort results
SELECT * FROM tasks ORDER BY created_at DESC;

-- Limit results
SELECT * FROM tasks LIMIT 10;
```

---

### 6.2 INSERT, UPDATE, DELETE

**Definition:** Commands for modifying data.

**Example:**
```sql
-- Add a new row
INSERT INTO tasks (title, is_done) VALUES ('Learn SQL', FALSE);

-- Modify existing rows
UPDATE tasks SET is_done = TRUE WHERE id = 1;

-- Remove rows
DELETE FROM tasks WHERE id = 1;
```

---

### 6.3 GROUP BY & Aggregate Functions

**Definition:** `GROUP BY` groups rows sharing a value, typically combined with aggregate functions like `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`.

**Example:**
```sql
SELECT is_done, COUNT(*) 
FROM tasks 
GROUP BY is_done;
-- Result: is_done=false -> 7, is_done=true -> 3
```

---

### 6.4 WHERE vs HAVING

**Definition:** `WHERE` filters individual rows **before** grouping happens. `HAVING` filters **groups** after `GROUP BY` has run — and is the only way to filter on an aggregate result like `COUNT(*)`.

**Example:**
```sql
-- WRONG — cannot use WHERE on an aggregate function
SELECT department, COUNT(*) 
FROM employees 
WHERE COUNT(*) > 5   -- ERROR
GROUP BY department;

-- CORRECT
SELECT department, COUNT(*) 
FROM employees 
GROUP BY department 
HAVING COUNT(*) > 5;
```

**Why it matters:** This is one of the single most commonly tested SQL traps in any technical assessment.

---

### 6.5 JOINs

**Definition:** Combines rows from two or more tables based on a related column.
- **INNER JOIN**: returns only rows that have matches in both tables
- **LEFT JOIN**: returns all rows from the left table, plus matched rows from the right (unmatched = NULL)

**Example:**
```sql
-- INNER JOIN — only tasks that have a matching category
SELECT tasks.title, categories.name
FROM tasks
INNER JOIN categories ON tasks.category_id = categories.id;

-- LEFT JOIN — all tasks, even those with no category
SELECT tasks.title, categories.name
FROM tasks
LEFT JOIN categories ON tasks.category_id = categories.id;
```

**Common trap:** Defaulting to INNER JOIN when you actually need to find *unmatched* rows (e.g., "find users with zero orders") — that requires a LEFT JOIN combined with `WHERE ... IS NULL`.

---

### 6.6 Primary Key & Foreign Key

**Definition:**
- **Primary Key**: uniquely identifies each row in a table (e.g., `id`)
- **Foreign Key**: a column in one table that references the primary key of another, creating a relationship between them

**Example:**
```sql
CREATE TABLE categories (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL
);

CREATE TABLE tasks (
  id SERIAL PRIMARY KEY,
  title TEXT NOT NULL,
  category_id INTEGER REFERENCES categories(id) -- foreign key
);
```

---

### 6.7 NULL Handling

**Definition:** `NULL` represents "no value." You cannot compare it using `=` — you must use `IS NULL` or `IS NOT NULL`.

**Example:**
```sql
-- WRONG — this never matches, even for NULL rows
SELECT * FROM tasks WHERE category_id = NULL;

-- CORRECT
SELECT * FROM tasks WHERE category_id IS NULL;
```

---

### 6.8 Indexing (Concept Level)

**Definition:** An index is a data structure that speeds up read queries (like a book's index) by avoiding a full table scan. Trade-off: indexes speed up `SELECT` but slow down `INSERT`/`UPDATE`/`DELETE`, because the index itself must be updated too.

**Example:**
```sql
CREATE INDEX idx_tasks_category ON tasks(category_id);
```

**Common trap:** Assuming "more indexes = always better." Panelists ask this specifically to see if you understand the write-speed trade-off.

---

## 7. Deployment / Cloud Basics (Lighter Weight)

### 7.1 Environment Variables in Production

**Definition:** Same concept as in Node.js locally, but critically important in deployment: secrets should be set via your hosting platform's dashboard (Render, AWS, etc.), never hardcoded or committed to Git.

---

### 7.2 CI/CD (Conceptual)

**Definition:** Continuous Integration/Continuous Deployment — automatically testing and deploying code whenever changes are pushed, instead of manually uploading files to a server.

**Why it matters:** You're not expected to configure a pipeline for this assessment — just understand what the term means and why it's used (faster, more reliable deployments).

---

## Quick-Reference Summary Table

| Topic | Most Likely Trap |
|---|---|
| `const` | People think it means immutable — it only blocks reassignment |
| `let`/`var` | Block scope vs function scope |
| `==`/`===` | Type coercion surprises |
| `useState` | Batched/stale updates — use functional form |
| `useEffect` | Missing/incorrect dependency array |
| List keys | Using index instead of a stable ID |
| Node event loop | "Multi-threaded" is the wrong answer — it's non-blocking I/O |
| Express middleware | Forgetting `next()` |
| PUT vs PATCH | Full replace vs partial update |
| 401 vs 403 | Authentication vs authorization |
| WHERE vs HAVING | Can't filter aggregates with WHERE |
| JOIN types | INNER drops unmatched rows; LEFT keeps them |
| NULL comparison | Must use `IS NULL`, not `= NULL` |

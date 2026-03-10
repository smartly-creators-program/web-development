# Backend Development with Node.js & Express

- In web development (client <--> server) where client is the frontend interface which user interacts with; our *server aka Backend* is the arena that handles API requests, database queries and storage ensurng in keeping our website dynamic and responsive to user requests and specifics.

Think of a website like a restaurant:

- **Frontend** = The dining area (what customers see and interact with)
- **Backend** = The kitchen (where the magic happens behind the scenes)
- **API** = The waiter (takes orders from frontend, delivers from backend)
- **Database** = The pantry (stores all our ingredients/data)

<div align="center">
  <img src="https://ddi-dev.com/uploads/backend-is.png" alt="Backend-Introduction" width="600" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" />
</div>

---

## So, What is Backend "Development"?

Backend is the **brain** of our application. It:

- Processes requests from users
- Talks to databases
- Handles business logic
- Manages authentication & security
- Serves data to the frontend

**or simply:** When you click "Login" on Instagram, the backend checks if our password is correct, fetches our feed, and sends it back to display our profile. [Multiverse stance: if your password is incorrect, you are still stuck on the login page with 'Invalid Email/Password' message. 🙂]

<div align="center">
  <img src="https://media.licdn.com/dms/image/v2/D4D12AQHRHrNbwP14iQ/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1656174905705?e=2147483647&v=beta&t=zX_zWMMLgty2NK4qYzLSoSFCcBBE7dditaGeQ_jL0Vc" alt="backend" width="600" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" />
</div>

---

## Why Node.js?

**Node.js** = JavaScript... but for servers! [Remember js is language for both worlds]

- Before Node.js, JavaScript only lived in browsers. Now it can run on servers too.

### The Superpower:
**Non-blocking I/O** (Asynchronous)

```js
☕ Traditional Server (Synchronous):
Customer 1 orders coffee → [Wait 5 min] → Serve
Customer 2 orders tea → [Wait 3 min] → Serve
Customer 3 orders juice → [Wait 2 min] → Serve

Total time: 10 minutes (everyone waiting in line)

⚡ Node.js Server (Asynchronous):
Customer 1 orders coffee → Start brewing
Customer 2 orders tea → Start brewing (while coffee brews)
Customer 3 orders juice → Start pouring (while both brew)

Total time: 5 minutes (all happening simultaneously!)
```

---

## Express.js: The Framework

**Express** is to Node.js what a **recipe book** is to cooking. Thats it, to put it in simpler terms.

Sure, one *could* cook without recipes, but Express gives you:
- ✅Pre-built tools
- ✅Organized structure
- ✅Less code to write(Modularity + Efficiency)
- ✅Faster development

---

## Lets put our Builder's Cap and glance through our (First) Backend setup 👷🏻‍♀️👷‍♂️

### Pre-requisites
- Before starting ahead, Ignite your Adrenaline and open your vscode
- [Nodejs](https://nodejs.org/en/download) & Npm Package Manager [Recommended: Download LTS (Long Term Support) version for stability.]

### **Step 1: The Foundation**

```bash
# Create project folder
mkdir my-backend
cd my-backend

# check versions
node -v
npm -v

# Initialize Node project
npm init -y

# Install Express
npm install express
```

*Hint: `npm` is like an app store/google playstore for JavaScript packages* 🌟

---

### **Step 2: Create our Server**

**File: `server.js`**

```javascript
// Import Express (like calling a chef into our kitchen)
const express = require('express');

// Create an Express application (our restaurant is now open!)
const app = express();

// Middleware: Allows server to understand JSON data
// (Teaching our waiter to read the menu)
app.use(express.json());

// ROUTE 1: Basic GET request
// When someone visits the homepage
app.get('/', (req, res) => {
  res.send('🏠 Welcome to the Backend Kitchen!');
});

// ROUTE 2: GET request with data
// Like asking "What's on the menu?"
app.get('/menu', (req, res) => {
  const menu = {
    appetizers: ['Spring Rolls', 'Soup'],
    mains: ['Pasta', 'Pizza', 'Burger'],
    desserts: ['Ice Cream', 'Cake']
  };
  res.json(menu);
});

// ROUTE 3: POST request (sending data)
// Like placing an order
app.post('/order', (req, res) => {
  const order = req.body; // Get data sent from frontend
  
  console.log('📋 New order received:', order);
  
  res.json({
    message: '✅ Order confirmed!',
    ourOrder: order,
    estimatedTime: '20 minutes'
  });
});

// ROUTE 4: Dynamic route with parameters
// Like asking for a specific dish
app.get('/dish/:dishName', (req, res) => {
  const dish = req.params.dishName;
  
  res.json({
    dish: dish,
    price: '$12.99',
    status: 'Available'
  });
});

// Start the server (open for business!)
const PORT = 3000;
app.listen(PORT, () => {
  console.log(`🚀 Server is running on http://localhost:${PORT}`);
});
```

---

## Lets understand what our server.js is doing

### **1. Routes (The Menu)**

- In Backend world, they are recognized as **'CRUD'--> Create::Read::Update::Delete**
- All web applications has these CRUD operations undergoing.

```javascript
app.get('/route', handler)    // Read/Retrieve data
app.post('/route', handler)   // Create/Send data
app.put('/route', handler)    // Update data
app.delete('/route', handler) // Delete data
```

**Real-world analogy:**
- `GET` = "Show me the menu"
- `POST` = "Here's my order"
- `PUT` = "Change my order from pizza to pasta"
- `DELETE` = "Cancel my order"

---

### **2. Request & Response**

```javascript
app.get('/example', (req, res) => {
  // req = What the customer sent you
  // res = What you send back to the customer
});
```

**The waiter's job:**
- **req** (request) = Customer's order slip
- **res** (response) = Food you serve back

---

### **3. Middleware (The Prep Cook)**

```javascript
app.use(express.json()); // Parses JSON data
```

Middleware runs **before** our routes. It prepares/processes requests.

```
Request Flow:
[Browser] → [Middleware] → [Route Handler] → [Response]
           ↓
       (cleans, validates, authenticates)
```

---

## Testing our Backend

### **Method 1: Browser (GET only)**
```
Visit: http://localhost:3000/menu
```

### **Method 2: Postman / Thunder Client**
 Visual tools to test all request types. 

> Testing is a crucial part of backend development -- Bind it to your heart.

- [Postman](https://www.postman.com/)
- [Hoppscotch](https://hoppscotch.io/)
- [VS Code Extension: Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)

### **Method 3: Code (using fetch)**
```javascript
// Frontend JavaScript
fetch('http://localhost:3000/order', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    item: 'Burger',
    quantity: 2
  })
})
.then(res => res.json())
.then(data => console.log(data));
```

---

## Project Structure

>  Structure, Modularity, and Clean Coding will take you a long way.

```
my-backend/
│
├── server.js           # Main entry point
├── package.json        # Project metadata
│
├── routes/             # All our routes
│   ├── userRoutes.js
│   └── productRoutes.js
│
├── controllers/        # Business logic
│   └── userController.js
│
├── models/             # Database schemas
│   └── User.js
│
└── middleware/         # Custom middleware
    └── auth.js
```

---

## Todo API

- **Lets have a Mini-Project cuz Learning strengthens the Cognitive grip over Concepts.**

```javascript
const express = require('express');
const app = express();

app.use(express.json());

// In-memory database (just an array)
let todos = [
  { id: 1, task: 'Learn Node.js', done: false },
  { id: 2, task: 'Build an API', done: false }
];

// GET all todos
app.get('/todos', (req, res) => {
  res.json(todos);
});

// POST new todo
app.post('/todos', (req, res) => {
  const newTodo = {
    id: todos.length + 1,
    task: req.body.task,
    done: false
  };
  todos.push(newTodo);
  res.status(201).json(newTodo);
});

// PUT update todo
app.put('/todos/:id', (req, res) => {
  const id = parseInt(req.params.id);
  const todo = todos.find(t => t.id === id);
  
  if (!todo) {
    return res.status(404).json({ error: 'Todo not found' });
  }
  
  todo.done = req.body.done;
  res.json(todo);
});

// DELETE todo
app.delete('/todos/:id', (req, res) => {
  const id = parseInt(req.params.id);
  todos = todos.filter(t => t.id !== id);
  res.json({ message: 'Todo deleted' });
});

app.listen(3000, () => console.log('📝 Todo API running on port 3000'));
```

---

## HTTP Status Codes (The Restaurant Signals)

- [HTTP STATUS CODES](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)

```
200 ✅ OK - "Here's our food!"
201 ✅ Created - "New dish added to menu!"
400 ❌ Bad Request - "Sorry, I don't understand our order"
401 ❌ Unauthorized - "You need to login first"
404 ❌ Not Found - "That dish doesn't exist"
500 ❌ Server Error - "Kitchen's on fire! 🔥"
```

---

## Key Takeaways

1. **Node.js** = JavaScript for servers
2. **Express** = Framework to build backends faster
3. **Routes** = Different endpoints for different actions
4. **Middleware** = Functions that run before route handlers
5. **REST API** = Standardized way to build web services

---

## Next Steps

✅ Add a **real database** ([MongoDB](https://www.mongodb.com/), [PostgreSQL](https://www.postgresql.org/))  
✅ Implement **authentication** [JWT tokens](https://jwt.io/) 
✅ Handle **file uploads**  [Multer Package](https://www.npmjs.com/package/multer)
✅ Add **error handling** middleware  
✅ Deploy to **cloud** (Netflix, Heroku, Railway, Vercel)

---

**Remember:** *" A backend without proper error handling is like a restaurant without napkins — messy for everyone involved."* 

---

### **Visual Diagram:**

```
┌─────────────┐
│   Browser   │
│  (Frontend) │
└──────┬──────┘
       │ HTTP Request
       ▼
┌─────────────┐
│   Express   │
│  (Backend)  │
├─────────────┤
│ Middleware  │
│   Routes    │
│ Controllers │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Database   │
└─────────────┘
```

*Happy coding! 🚀 🫡❤️‍🔥*
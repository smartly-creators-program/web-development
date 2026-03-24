# Bare Minimum Things to Do for Any Web Project 

1. Initialise / Init 

In your terminal run the command:
```
npm init
```

The npm init command is used to initialize a new Node.js project. When executed in a directory, it interactively prompts the user for information about the project and then generates a package.json file in that directory, which serves as the manifest (a simple JSON text file that tells the browser how your web application should behave when installed on a user's desktop or mobile device) for the project.

2. Setup Prettier Code Formatter 

Prettier is an opinionated code formatter — a tool that automatically formats your code in one fixed style, without giving you many choices.

Instead of developers arguing over things like spacing, tabs, or brackets, the tool just says: "This is the way code should look."

So:
- No time wasted on style debates
- All code looks consistent
- Easier to read and focus on logic instead of formatting

Follow this to setup: https://prettier.io/docs/install

3. Setup Nodemon 

Nodemon solves the problem of having to manually stop and restart a Node.js application every time a code change is made. It watches files in a directory, detects changes, and automatically restarts the server, increasing developer productivity and eliminating repetitive tasks.

Follow this to setup: https://www.npmjs.com/package/nodemon

4. Project Restructuring 


For basic HTML, CSS and JS projects you can use:

```
project/ <----- main folder of your project 
│
├── public/   
│   ├── images/
│   ├── styles/
│   └── scripts/
│
├── pages/
│   ├── index.html        
│   ├── streak.html       
│   └── setup.html        
│
└── README.md
```


Front End with Components:

```
project/
│
├── public/
│   ├── assets/        (images, fonts, icons)
│
├── src/
│   ├── components/    (reusable UI parts)
│   ├── pages/         (page-specific JS)
│   ├── styles/
│   ├── utils/         (helper functions)
│   └── main.js
│
├── index.html
└── README.md
```


Node JS Backend + API

```
project/
│
├── src/
│   ├── controllers/   (logic)
│   ├── models/        (data structure)
│   ├── routes/        (API endpoints)
│   ├── middleware/    (auth, logging)
│   ├── services/      (business logic)
│   ├── utils/         (helpers)
│   ├── validators/    (input validation)
│   └── config/        (DB, env setup)
│
├── public/            (static files if needed)
├── app.js
├── package.json
└── .env
```


Full Stack (Frontend + Backend)

```
project/
│
├── client/            (frontend)
│   ├── src/
│   ├── public/
│   └── index.html
│
├── server/            (backend)
│   ├── src/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   └── middleware/
│   │
│   ├── app.js
│   └── package.json
│
└── README.md
```


MERN or Modern React App

```
project/
│
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/      (API calls)
│   ├── store/         (state management)
│   ├── utils/
│   └── assets/
│
├── public/
├── package.json
└── README.md
```
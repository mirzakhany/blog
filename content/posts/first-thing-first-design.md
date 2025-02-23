---
title: "First things first: Design before you code"
date: 2025-02-23T06:44:00+02:00
draft: false
showReadingTime: true
tags:
  - Desing
  - Code
  - Development
categories:
  - development
---

<img src="/images/design-before-you-code.jpg" alt="Design before you code" style="width: 100%; height: auto;">


Why design first? why not just jump into code and start writing it? I remember one of those old good days when I was learning to code a 
8051 microcontroller in assembly language, I attended a lab session where there was a task to write a clock program. I ran to a issue 
where I was not able to get the clock to work. I was stuck for a while and then I asked the instructor for help. And first thing he asked
was "Where is your flow chart?" I was like its in my head. He said something that I never forgot:

> "I cant see it when its in your head, So I cant help you. Draw it on paper and then we can talk."

If you think about it, its true. without a design you are not able to discuss it with others. You are not able to see the big picture.
So you might start with assumptions that are not correct and as result you might have to rewrite the code or change your path, which mean more time and effort. add to that the maintainability of the code. If you have a design you can always go back to it and see what you have done and why you have done it that way.

> "Design is not just what it looks like and feels like. Design is how it works." - Steve Jobs

So let me jump into the reasons why you should design before you code:
- **Understand the problem**: When you start designing you will have to understand the problem you are trying to solve. You will have to think about the requirements and the constraints. You will have to think about the data and the flow of the program. You will have to think about the user interface and the user experience. and all of that will help you to understand the problem better.

- **Think about the solution**: When you start designing you will have to think about the solution. You will have to think about the architecture and the components. You will have to think about the algorithms and the data structures. You will have to think about the patterns and the practices. and all of that will help you to think about the solution better.

- **Discuss with others**: When you start designing you will have something to discuss with others. You will have something to show and to explain. You will have something to get feedback on. You will have something to improve and to iterate on. and all of that will help you to discuss with others better.

- **Maintain the code**: When you start designing you will have something to maintain. You will have something to go back to and to see what you have done and why you have done it that way. You will have something to refactor and to optimize. You will have something to extend and to scale. and all of that will help you to maintain the code better.

#### How I design before I code:
I usually start with a simple text file. I will go through the requirements and try to find bollet points. things that I would shape the core of my project. things like the data structure to keep, interfaces to expose. experince shows me that having a good ground for the project data needs and the interfaces is like an investment I do for the long run. 

let me walk you through a simple example. lets say I have a requirement to build a simple todo list application. I will start with a simple text file and write down the requirements:

- I will have a list of tasks, each with a title, a description, a due date and a status.
But what if more than one user will use the application? I will have to add a user id to the task. 
- So I will have a list of users, each with a name, an email and a password. but it might be out of scope for now to add authentication and authorization. so I will keep it simple for now. and just add a user id to the task.
- What would be status of the task? do I need to have a list of them? what if user want to add more? from here you can decide to have a list of status or just a string.

Allright now that I have first draft of the requirements, I will do some table design to keep the data. I will have a table for the users and a table for the tasks. I will have a user id in the tasks table to link the task to the user. I will have a status column in the tasks table to keep the status of the task.

```sql 

CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    password VARCHAR(255)
);

CREATE TABLE tasks (
    id INT PRIMARY KEY,
    user_id INT,
    title VARCHAR(255),
    description TEXT,
    due_date DATE,
    status VARCHAR(255),
    FOREIGN KEY (user_id) REFERENCES users(id)
);

```

its a good start but not complete yet. no matter what language I will use there must be an interface to expose. I will have to think about the endpoints and the methods. I will have to think about the request and the response. I will have to think about the validation and the error handling. I will have to think about the security and the performance. and all of that will help me to have a good ground for the project. for these thing I will start by defining the endpoints and the methods in openapi format. 

```yaml
openapi: 3.0.0
info:
  title: Todo List API
  version: 1.0.0
  description: A simple todo list API
paths:
  /tasks:
    get:
      summary: Get all tasks
      responses:
        '200':
          description: A list of tasks
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Task'
...
```

Having the data and the interfaces will help me to start coding. and I can share it with others to get feedback. no matter what kind of project you are working on, having a design before you code is always a good idea. it will help you to understand the problem and the solution. it will help you to discuss with others. 
---
title: "NodeJS"
draft: false
author: "dpak94"
url: "/docs/web-dev/node"
---

# Node JS

[Download](https://nodejs.org/en/download/package-manager) -  
[Official Docs](https://nodejs.org/docs/latest/api/),
[Learn](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs) |

---

- A JavaScript Runtime built on Google's **OpenSource V8 Javascript Engine**

**Node JS** is an environment in which a program written in JS can be executed.

---

## Pros for Node JS

- Single threaded, based on event driven, non-blocking I/O model.
- Perfect for building superfast and scalable data-intensive apps.
- JavaScript for the entire stack resulting in faster and efficient development
- **NPM** : Huge library of open-source packages available for free.
- Very active developer community.

---

## Use Cases for Node

- API with database behind it (preferably NoSQL)
- Data Streaming (eg., YouTube)
- Real time chat apps
- Server-side web apps

---

## Non-use cases

- Applications with heavy server-side processing (CPU intensive) like video compression, audio compression etc. **Ruby on Rails** or **PHP** or **Python** is good for these apps.

---

## Node Terminal

- To enter node, type `node` in the terminal
- To exit, write `.exit` in the node terminal

```bash
> 3 + 8
11
> _ + 11
22 //carries previous results into current command
```

---

## Asynchronous vs Synchronous Code

- **Async** code does not block the execution of consecutive lines of code while **Synchronous** code does.

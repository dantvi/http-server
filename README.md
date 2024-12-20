# HTTP Server

A simple Node.js HTTP server that handles REST-like API endpoints. This project is part of the Complete Node.js Developer course by Zero to Mastery. It demonstrates how to use the built-in http module in Node.js to handle requests for resources like "friends" and "messages," process both GET and POST requests, and dynamically render responses.

## Table of contents

- [HTTP Server](#http-server)
  - [Table of contents](#table-of-contents)
  - [Overview](#overview)
    - [Features](#features)
    - [Technologies Used](#technologies-used)
  - [Getting Started](#getting-started)
    - [Installation](#installation)
    - [Usage](#usage)
  - [API Endpoints](#api-endpoints)
    - [Unknown Routes](#unknown-routes)
  - [Code Overview](#code-overview)
    - [Structure](#structure)
    - [Highlights](#highlights)
    - [Useful resources](#useful-resources)
  - [Author](#author)
  - [Acknowledgments](#acknowledgments)

## Overview

### Features

- Responds to GET requests for a list of "friends" or a specific friend by ID.
- Handles POST requests to add new friends.
- Dynamically renders HTML responses for "messages" endpoint.
- Gracefully handles unknown routes with a 404 status code.

### Technologies Used

- Node.js: Built-in http module for creating the server.
- JavaScript: Standard JavaScript for server logic.

## Getting Started

### Installation

1. Clone the repository:

```bash
git clone https://github.com/dantvi/http-server.git
```

2. Navigate to the project directory:

```bash
cd http-server
```

3. Install Node.js if not already installed. Download Node.js.

### Usage

1. Start the server:

```bash
node server.js
```

2. Open your browser or use a tool like curl or Postman to test the following endpoints:
- http://localhost:3000/friends
- http://localhost:3000/friends/:id
- http://localhost:3000/messages

## API Endpoints

GET /friends
- Returns a list of all friends in JSON format.
GET /friends/:id
- Returns a specific friend by their id in JSON format.
POST /friends
- Accepts a JSON object representing a new friend and adds it to the list. Example:

```json
{
  "id": "6",
  "name": "Ada Lovelace"
}
```

GET /messages
- Returns a simple HTML response simulating a chat interface.

### Unknown Routes

- Returns a 404 Not Found response.

## Code Overview

### Structure

The server logic is contained in a single file for simplicity:
- server.js: Implements the HTTP server, routes, and response logic.

### Highlights

- Dynamic URL Parsing:

```js
const items = req.url.split('/');
```

- POST Request Handling:

```js
if (req.method === 'POST' && items[1] === 'friends') {
    req.on('data', (data) => {
        const friend = data.toString();
        friends.push(JSON.parse(friend));
    });
    req.pipe(res);
}
```

- Dynamic HTML Rendering:

```js
res.setHeader('Content-Type', 'text/html');
res.write('<html><body><ul>');
res.write('<li>Hello Isaac!</li>');
res.write('<li>What are your thoughts on astronomy?</li>');
res.write('</ul></body></html>');
res.end();
```

### Useful resources

- [Node.js HTTP Documentation](https://nodejs.org/api/http.html) - The official Node.js documentation for the http module, essential for understanding request and response handling.
- [MDN Web Docs: HTTP Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) - A great resource to understand HTTP methods, headers, and status codes.

## Author

- GitHub - [@dantvi](https://github.com/dantvi)
- LinkedIn - [@danieltving](https://www.linkedin.com/in/danieltving/)

## Acknowledgments

This project is part of the Complete Node.js Developer course by Zero to Mastery. Special thanks to the instructors for providing a comprehensive curriculum and real-world examples to build foundational Node.js skills.

# Setting Up and Testing a CRUD API with JSON Server

This document provides comprehensive instructions for setting up a local environment to test a CRUD (Create, Read, Update, Delete) API using JSON Server. It includes installation steps, configuration details, and examples of how to interact with the API.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation Steps](#installation-steps)
   - [1. Install Node.js](#1-install-nodejs)
   - [2. Install JSON Server](#2-install-json-server)
   - [3. Create `db.json`](#3-create-dbjson)
   - [4. Start JSON Server](#4-start-json-server)
   - [5. Test the REST API](#5-test-the-rest-api)
4. [CRUD Operations Examples](#crud-operations-examples)
5. [References](#references)

## Introduction
JSON Server is a simple tool that allows you to create a full fake REST API with zero coding in less than 30 seconds. It is ideal for prototyping and testing front-end applications without needing a back-end server.

## Prerequisites
- A terminal or command prompt.
- Basic knowledge of command-line operations.
- Internet access to download Node.js and JSON Server.

## Installation Steps

### 1. Install Node.js
To install Node.js, we will use Node Version Manager (nvm). Follow these steps:

```bash
# Install nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

# Restart your terminal or run the following command to load nvm
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

# Download and install Node.js version 22
nvm install 22

# Verify the installed Node.js version
node -v # should print `v22.12.0`

# Verify the installed npm version
npm -v # should print `10.9.0`
```

### 2. Install JSON Server
Once Node.js is installed, you can install JSON Server using npm:

```bash
npm install json-server
```

### 3. Create `db.json`
Create a file named `db.json` in your project directory with the following content:

```json
{
  "posts": [
    { "id": "1", "title": "a title", "views": 100 },
    { "id": "2", "title": "another title", "views": 200 }
  ],
  "comments": [
    { "id": "1", "text": "a comment about post 1", "postId": "1" },
    { "id": "2", "text": "another comment about post 1", "postId": "1" }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

This file serves as your database, containing sample data for posts, comments, and user profiles.

### 4. Start JSON Server
Run the following command to start the JSON Server:

```bash
npx json-server db.json
```

By default, the server will run on `http://localhost:3000`. You should see output indicating that the server is running and listening for requests.

### 5. Test the REST API
You can test the REST API using curl or any API testing tool like Postman. To test fetching a post, run:

```bash
curl http://localhost:3000/posts/1
```

You should receive a response similar to this:

```json
{
  "id": "1",
  "title": "a title",
  "views": 100
}
```

## CRUD Operations Examples

Here are examples of how to perform basic CRUD operations using curl:

### Create a New Post (POST)
To create a new post, use the following command:

```bash
curl -X POST http://localhost:3000/posts -H 'Content-Type: application/json' -d '{"title": "new post", "views": 50}'
```

### Read All Posts (GET)
To retrieve all posts, use:

```bash
curl http://localhost:3000/posts
```

### Update an Existing Post (PUT)
To update an existing post, use:

```bash
curl -X PUT http://localhost:3000/posts/1 -H 'Content-Type: application/json' -d '{"id": "1", "title": "updated title", "views": 150}'
```

### Delete a Post (DELETE)
To delete a post, use:

```bash
curl -X DELETE http://localhost:3000/posts/1
```

## References
- [JSON Server on npm](https://www.npmjs.com/package/json-server)
- [Node.js Installation Guide](https://nodejs.org/en/download/package-manager)

This README provides detailed instructions for setting up and testing a CRUD API using JSON Server effectively. Enjoy building your applications!

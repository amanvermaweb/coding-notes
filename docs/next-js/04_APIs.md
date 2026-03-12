# ![ ](../assets/nextjs-logo.svg) APIs in Next.js

## Overview

Next.js allows you to create **API routes** as serverless functions that run on the server side. These routes are useful for handling backend logic such as authentication, database operations, form submissions, or third-party API integrations — all within the same Next.js app.

## Creating API Routes

In Next.js (App Router), you define APIs inside the **`app/api`** directory.

### Example Structure

```text
app/
 ├── api/
 │   └── hello/
 │       └── route.js
```

### Example: Basic API Route

```javascript
// app/api/hello/route.js
export async function GET(request) {
  return Response.json({ message: "Hello from Next.js API!" });
}
```

**Result:**
Visiting `/api/hello` will return:

```json
{ "message": "Hello from Next.js API!" }
```

## Supported HTTP Methods

Next.js API routes can handle different HTTP methods:

```javascript
export async function GET(request) {
  return Response.json({ message: "GET request received" });
}

export async function POST(request) {
  const data = await request.json();
  return Response.json({ message: "POST data received", data });
}

export async function PUT(request) {
  return Response.json({ message: "PUT request received" });
}

export async function DELETE(request) {
  return Response.json({ message: "DELETE request received" });
}
```

## Accessing Query Parameters

You can get URL parameters using `request.url`:

```javascript
export async function GET(request) {
  const { searchParams } = new URL(request.url);
  const name = searchParams.get("name");
  return Response.json({ message: `Hello, ${name}` });
}
```

**Example:**
`/api/hello?name=Arjun` → `{ "message": "Hello, Arjun" }`

## Dynamic API Routes

You can create **dynamic routes** using square brackets.

### Example:

```sh
app/api/users/[id]/route.js
```

```javascript
export async function GET(request, { params }) {
  const { id } = params;
  return Response.json({ userId: id });
}
```

**Access:** `/api/users/10` → `{ "userId": "10" }`

## Handling JSON Input

For `POST` or `PUT` requests:

```javascript
export async function POST(request) {
  const body = await request.json();
  return Response.json({ received: body });
}
```

**Send Example (Frontend):**

```javascript
await fetch("/api/hello", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Arjun" }),
});
```

## Using Middleware

You can add logic before sending responses:

```javascript
export async function GET(request) {
  const auth = request.headers.get("authorization");
  if (auth !== "my-secret") {
    return Response.json({ error: "Unauthorized" }, { status: 401 });
  }
  return Response.json({ message: "Access granted" });
}
```

## API Routes vs. Server Actions

- **API Routes**: Used for traditional HTTP endpoints (like REST APIs).
- **Server Actions**: Used for handling form submissions or direct server functions **without API endpoints**.

## Example: Fetching External APIs

```javascript
export async function GET() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const posts = await res.json();
  return Response.json(posts);
}
```

## Folder Structure Summary

```text
app/
 ├── api/
 │   ├── users/
 │   │   ├── route.js
 │   └── products/
 │       ├── route.js
```

Each folder inside `app/api` represents an endpoint.
Example:

- `/api/users`
- `/api/products`

## Notes

- APIs run **only on the server**, never in the client bundle.
- You can use **databases**, **environment variables**, and **server-side packages** safely inside API routes.
- **Response.json()** is the recommended way to return data.

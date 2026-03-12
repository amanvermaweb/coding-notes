# ![ ](../assets/nextjs-logo.svg) Introduction to Next.js

## What is Next.js?

Next.js is a **React-based framework** developed by **Vercel** that simplifies building **server-rendered** and **statically generated** web applications. It enhances React by adding features like **file-based routing**, **SSR (Server-Side Rendering)**, **SSG (Static Site Generation)**, **API routes**, and **optimized performance** out of the box.

## Advantages of Next.js

- Improved SEO (thanks to SSR and SSG)
- Faster page loading with pre-rendering
- API routes (no separate backend needed for small apps)
- Easy file-based routing system
- Optimized images and static assets
- Built-in TypeScript and ESLint support

## How to Create a Next.js App

1. **Install using create-next-app:**

   ```sh
   npx create-next-app@latest my-next-app
   ```

2. **Run the development server:**

   ```sh
   cd my-next-app
   npm run dev
   ```

3. Open in browser:
   `http://localhost:3000`

## Typical Project Structure

```text
my-app/
├── app/
│   ├── index.js
│   ├── about.js
│   └── api/
│       └── hello.js
├── public/
│   └── images/
├── styles/
│   └── globals.css
├── next.config.js
└── package.json
```

## Key Features of Next.js

### 1. **File-Based Routing**

- Each file inside the `pages/` directory automatically becomes a route.
- Example:

  ```text
  pages/
  ├── index.js        → '/'
  ├── about.js        → '/about'
  └── blog/[id].js    → '/blog/:id'
  ```

- No need to manually configure routes like in React Router.

### 2. **Pre-rendering**

Next.js pre-renders every page by default, improving SEO and performance.

#### Types of Pre-rendering:

- **Static Generation (SSG)** – HTML generated at build time.

  ```js
  export async function getStaticProps() {
    const data = await fetchData();
    return { props: { data } };
  }
  ```

- **Server-Side Rendering (SSR)** – HTML generated on each request.

  ```js
  export async function getServerSideProps() {
    const data = await fetchData();
    return { props: { data } };
  }
  ```

### 3. **Client-Side Rendering (CSR)**

Even though Next.js supports pre-rendering, you can still fetch data **on the client side** using React hooks like `useEffect`.

### 4. **API Routes**

You can create backend API endpoints inside the `pages/api` directory.
Example:

```js
// pages/api/hello.js
export default function handler(req, res) {
  res.status(200).json({ message: "Hello from API" });
}
```

### 5. **Image Optimization**

Next.js provides the `<Image />` component for **automatic image optimization**:

```jsx
import Image from "next/image";
<Image src="/profile.jpg" alt="Profile" width={200} height={200} />;
```

### 6. **Built-in CSS and Sass Support**

You can use:

- Global CSS (in `_app.js`)
- CSS Modules (`.module.css`)
- Sass/SCSS files

Example:

```jsx
import styles from "./Home.module.css";
function Home() {
  return <h1 className={styles.title}>Hello Next.js</h1>;
}
```

### 7. **Middleware**

Middleware runs before a request is completed — useful for authentication, redirects, or logging.

```js
// middleware.js
export function middleware(req) {
  return NextResponse.redirect(new URL("/login", req.url));
}
```

### 8. **Static File Serving**

Any files placed in the `public/` directory can be accessed directly via URL.
Example:
`public/image.png` → accessible at `http://localhost:3000/image.png`

### 9. **Deployment**

Next.js apps can be easily deployed on **Vercel**, the platform made by its creators, or any Node.js-compatible service (e.g., Netlify, AWS, etc.).

## Example: Basic Next.js Page

```jsx
// pages/index.js
export default function Home() {
  return (
    <div>
      <h1>Welcome to Next.js</h1>
      <p>This is your first Next.js page!</p>
    </div>
  );
}
```

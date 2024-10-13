<details>
<summary><strong style="font-size: 1.2em;">1. What is Next.js, and what are its key features?</strong></summary>

Next.js is an open-source React framework created by Vercel that allows developers to build web applications with features like **Server-Side Rendering (SSR)**, **Static Site Generation (SSG)**, and **API routes**. It simplifies the process of creating performant and SEO-friendly applications by offering file-based routing, image optimization, and built-in CSS and Sass support. 

Key features include:
- **Server-Side Rendering (SSR)**: Pages are rendered on the server for each request, making it great for dynamic pages.
- **Static Site Generation (SSG)**: Pages are generated at build time and served as static HTML, improving speed and performance.
- **API Routes**: Allows serverless functions to be created within your Next.js app.
- **File-based Routing**: No need for custom route definitions; routes are automatically based on file structure.
- **Automatic code splitting**: Only the required JavaScript is loaded, reducing page load time.
- **Image Optimization**: Out-of-the-box image handling with lazy loading and resizing.

**Hint:** 💡 Next.js is a full-stack framework, providing both client-side and server-side capabilities for web development.

[Further Reading](https://nextjs.org/docs)

</details>

<details>
<summary><strong style="font-size: 1.2em;">2. What is the difference between SSR (Server-Side Rendering) and SSG (Static Site Generation)?</strong></summary>

**SSR (Server-Side Rendering)** and **SSG (Static Site Generation)** are both strategies for pre-rendering in Next.js.

- **SSR**: The page is generated on the server for each request, ensuring the client receives the latest data. This is useful for dynamic pages where data changes frequently, such as a user dashboard or live content feed. The data-fetching method used is `getServerSideProps`, which fetches data at request time.
- **SSG**: The page is pre-rendered at build time, meaning that the HTML is generated once and then reused for every request. This is ideal for content that doesn't change often, such as blogs or documentation pages. The data-fetching method is `getStaticProps`, which runs at build time, not for every request.

**When to use**:
- **SSR**: When content needs to be updated in real-time.
- **SSG**: When the content is mostly static or doesn't require frequent updates.

**Hint:** 💡 Use SSG for better performance and SSR for real-time data that frequently changes.

[Further Reading](https://nextjs.org/docs/basic-features/data-fetching)

</details>

<details>
<summary><strong style="font-size: 1.2em;">3. How does Next.js handle routing? Explain dynamic and nested routes.</strong></summary>

Next.js uses a **file-based routing** system, meaning that the files and directories inside the `pages/` folder automatically become routes. You do not need to configure routes manually.

- **Static Routes**: If you have a file `pages/about.js`, the route `/about` will be automatically created.
- **Dynamic Routes**: You can create dynamic routes using square brackets. For example, `pages/posts/[id].js` creates a dynamic route like `/posts/1`, `/posts/2`, where `id` is the dynamic parameter. Inside the component, you can access the dynamic route using `useRouter()` or via `getStaticPaths`.

  Example of accessing dynamic route parameters:
  ```js
  import { useRouter } from 'next/router';
  const router = useRouter();
  const { id } = router.query;
  ```

- **Nested Routes**: You can create nested routes by organizing files into folders. For instance, `pages/users/[id]/profile.js` will result in the route `/users/1/profile`.

**Hint:** 💡 Next.js simplifies routing with automatic route generation and dynamic routes using file structure.

[Further Reading](https://nextjs.org/docs/routing/introduction)

</details>

<details>
<summary><strong style="font-size: 1.2em;">4. What are `getStaticProps` and `getServerSideProps`, and how do they differ?</strong></summary>

Both `getStaticProps` and `getServerSideProps` are special data-fetching methods in Next.js that allow you to fetch data and pre-render pages:

- **`getStaticProps`**: This function runs at build time and is used for **static generation**. It fetches data once and builds the HTML file at build time, making it ideal for static pages. It’s used for pages where data does not change often, like a blog or product listing.

  Example:
  ```js
  export async function getStaticProps() {
    const res = await fetch('https://api.example.com/data');
    const data = await res.json();
    return {
      props: { data },
    };
  }
  ```

- **`getServerSideProps`**: This function runs on the server for every request and is used for **server-side rendering**. It ensures that the page is rendered with the latest data. Use this for pages that require real-time data, such as a news feed or dashboard.

  Example:
  ```js
  export async function getServerSideProps() {
    const res = await fetch('https://api.example.com/data');
    const data = await res.json();
    return {
      props: { data },
    };
  }
  ```

**Hint:** 💡 Use `getStaticProps` for performance and `getServerSideProps` for dynamic data.

[Further Reading](https://nextjs.org/docs/basic-features/data-fetching)

</details>

<details>
<summary><strong style="font-size: 1.2em;">5. What are API routes in Next.js, and how are they used?</strong></summary>

**API Routes** in Next.js allow you to build backend functionality directly in your Next.js application, effectively creating serverless functions. These routes can be used to handle HTTP requests, perform database operations, or interact with external APIs.

- API routes are defined in the `pages/api/` folder.
- Each file in this folder represents an API endpoint.
- These routes can be accessed via `/api/<filename>`, and they can handle any type of HTTP method (GET, POST, etc.).

Example:
```js
// pages/api/hello.js
export default function handler(req, res) {
  res.status(200).json({ message: 'Hello, Next.js API' });
}
```

When you visit `/api/hello`, this function will respond with a JSON message. API routes are ideal for backend operations such as:
- Submitting forms
- Interacting with a database
- Handling authentication

**Hint:** 💡 API routes are serverless functions that allow you to handle backend logic within the same Next.js app.

[Further Reading](https://nextjs.org/docs/api-routes/introduction)

</details>

<details>
<summary><strong style="font-size: 1.2em;">6. How does Next.js improve SEO and performance with SSR and static generation?</strong></summary>

**Search Engine Optimization (SEO)** and **performance** are critical aspects of modern web applications, and Next.js enhances both through **SSR** and **SSG**:

- **SEO**: Traditional client-side rendered React applications don’t perform well in SEO because search engine crawlers struggle to execute JavaScript and access the full content. With Next.js's SSR and SSG, pages are pre-rendered as HTML, making them immediately accessible to crawlers and improving SEO.

- **Performance**: By serving pre-rendered HTML instead of waiting for JavaScript to load and render the page, Next.js significantly reduces the time to first paint (TTFP). This improves both performance and user experience, as users can see content faster.

Additionally, Next.js offers **automatic code splitting**, which means only the JavaScript necessary for the current page is loaded, further improving load times.

**Hint:** 💡 SSR and SSG boost both SEO and performance by providing pre-rendered HTML to users and crawlers.

[Further Reading](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#seo)

</details>

<details>
<summary><strong style="font-size: 1.2em;">7. How does Next.js handle image optimization?</strong></summary>

Next.js provides built-in **Image Optimization** through the `next/image` component. This allows for automatic image resizing, lazy loading, and serving optimized formats like WebP. The component optimizes images on-demand and serves them in the appropriate size for different screen resolutions, leading to faster load times and better performance.

Example:
```js
import Image from 'next/image';

export default function Home() {
  return (
    <Image
      src="/images/example.jpg"
      alt="Example Image"
      width={500}
      height={500}
    />
  );
}
```

- **Lazy Loading**: Images are only loaded when they appear in the viewport, reducing the initial load time.
- **Responsive Images**: Next.js automatically adjusts image sizes for different screen sizes and resolutions.

**Hint:** 💡 Use `next/image` to optimize images automatically for better performance and responsiveness.

[Further Reading](https://nextjs.org/docs/basic-features/image-optimization)

</details>

<details>
<summary><strong style="font-size: 1.2em;">8. How do `getStaticPaths` and dynamic routes work together?</strong></summary>

`getStaticPaths` is used alongside `getStaticProps` to generate dynamic routes at build time. This is particularly useful when you have a set of pages that depend on dynamic data, such as blog posts or product pages.

- **`getStaticPaths`**: This function returns the paths that should be statically generated based on your data. For example, if you have blog posts with dynamic IDs, `getStaticPaths` fetches the list of IDs that should be pre-rendered.

Example:
```js
export async function getStaticPaths() {
  const res = await fetch('https://api.example.com/posts');
  const posts = await res.json();

  const paths = posts.map((post) => ({
    params: { id: post.id.toString() },
  }));

  return { paths, fallback: false };
}
```

- **`getStaticProps`**: After defining the paths, `getStaticProps` fetches the data for each page.

**Hint:** 💡 `getStaticPaths` is essential for generating dynamic pages during build time.

[Further Reading](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation)

</details>

<details>
<summary><strong style="font-size: 1.2em;">9. What is Incremental Static Regeneration (ISR) in Next.js?</strong></summary>

**Incremental Static Regeneration (ISR)** allows Next.js to update static content **after the build**. Instead of rebuilding the entire application, you can regenerate specific pages by revalidating them in the background. ISR enables you to have static pages that are periodically updated without needing a full redeployment.

- Use `getStaticProps` with the `revalidate` key to specify the time interval (in seconds) for revalidation.

Example:
```js
export async function getStaticProps() {
  const res = await fetch('https://api.example.com/posts');
  const posts = await res.json();

  return {
    props: { posts },
    revalidate: 10, // Rebuild the page every 10 seconds
  };
}
```

In this example, the page will revalidate every 10 seconds. If a request comes in after the revalidation period, Next.js will generate a new static page in the background.

**Hint:** 💡 ISR helps balance the benefits of static generation with the need for fresh data.

[Further Reading](https://nextjs.org/docs/app/building-your-application/upgrading/app-router-migration#incremental-static-regeneration-getstaticprops-with-revalidate)

</details>

<details>
<summary><strong style="font-size: 1.2em;">10. How does Next.js handle caching, and what strategies can be applied for optimal performance?</strong></summary>

Next.js leverages various caching strategies to enhance performance:
1. **Static Page Caching**: For pages generated with `getStaticProps`, Next.js serves static files from the edge. These are cached by CDNs for ultra-fast delivery.
2. **SSR Cache-Control**: For SSR pages using `getServerSideProps`, you can use cache-control headers to specify caching behavior for each request. For instance, caching the server response for a short duration can help offload the server.

Example of setting headers:
```js
export async function getServerSideProps({ res }) {
  res.setHeader('Cache-Control', 's-maxage=60, stale-while-revalidate');
  const data = await fetchData();
  return { props: { data } };
}
```

3. **API Route Caching**: API routes can also utilize caching by setting appropriate headers in the response.

4. **Image Caching**: The `next/image` component uses built-in caching to store and serve optimized images.

**Hint:** 💡 Caching in Next.js can dramatically improve performance when used in conjunction with CDNs and cache-control headers.

[Further Reading](https://nextjs.org/docs/app/building-your-application/data-fetching/fetching)

</details>

<details>
<summary><strong style="font-size: 1.2em;">11. How does Next.js handle middleware, and how can it be used for advanced functionality?</strong></summary>

Next.js **middleware** allows you to run code before a request is completed. This can be used for tasks like authentication, redirection, or rewriting routes dynamically. Middleware executes during the request lifecycle and can modify the response or request.

Example of middleware:
```js
// middleware.js
export function middleware(req, ev) {
  // Check for a specific condition and redirect if necessary
  if (!req.headers.cookie.includes('auth')) {
    return Response.redirect('/login');
  }
  // Continue if authenticated
  return Response.next();
}
```

In this example, middleware checks for an authentication cookie and redirects to the login page if the user is not authenticated.

**Hint:** 💡 Middleware allows you to intercept and manipulate requests before they reach your Next.js routes.

[Further Reading](https://nextjs.org/docs/middleware)

</details>

<details>
<summary><strong style="font-size: 1.2em;">12. How do you handle environment variables in Next.js?</strong></summary>

Next.js has built-in support for environment variables, and you can define them in a `.env` file at the root of your project. There are three types of environment variables based on their scope:
- **Runtime Environment Variables**: Available on both client and server-side if prefixed with `NEXT_PUBLIC_`.
- **Server-Side Only Variables**: Only available during server-side code execution (e.g., `getServerSideProps`, `getStaticProps`).
- **Build-Time Variables**: Available at build time, but not in the client-side bundle.

Example of using environment variables:
```env
# .env.local
NEXT_PUBLIC_API_URL=https://api.example.com
SECRET_API_KEY=your-secret-api-key
```

Accessing them in Next.js:
```js
// Client-side (uses NEXT_PUBLIC_ prefix)
const apiUrl = process.env.NEXT_PUBLIC_API_URL;

// Server-side (accessible in getServerSideProps)
export async function getServerSideProps() {
  const secretKey = process.env.SECRET_API_KEY;
  const res = await fetch(apiUrl);
  const data = await res.json();

  return { props: { data } };
}
```

**Hint:** 💡 Always prefix environment variables with `NEXT_PUBLIC_` if they need to be exposed to the client.

[Further Reading](https://nextjs.org/docs/basic-features/environment-variables)

</details>

<details>
<summary><strong style="font-size: 1.2em;">13. What are custom `&lt;Document&gt;` and `&lt;App&gt;` components in Next.js?</strong></summary>

In Next.js, both `<App>` and `<Document>` components provide customization points for your application.

- **`_app.js`**: This component wraps all page components and allows you to initialize and persist state, add global styles, and manage data that affects all pages. It is re-rendered on every page change.

Example:
```js
// pages/_app.js
export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```

- **`_document.js`**: This component is used to customize the entire HTML document that is sent from the server. It is only rendered on the server side and is helpful for adding meta tags, links, or custom scripts.

Example:
```js
// pages/_document.js
import { Html, Head, Main, NextScript } from 'next/document';

export default function Document() {
  return (
    <Html>
      <Head>
        <meta charSet="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
      </Head>
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  );
}
```

**Hint:** 💡 Use `_app.js` for page-level customizations and `_document.js` for document-level customizations.

[Further Reading](https://nextjs.org/docs/advanced-features/custom-app)

</details>

<details>
<summary><strong style="font-size: 1.2em;">14. What are rewrites and redirects in Next.js, and how are they different?</strong></summary>

**Rewrites** and **redirects** are used in Next.js to manage URL structures and reroute traffic:

- **Rewrites**: Modify the URL of a request before it reaches your page or API route. They change the URL internally without redirecting the user or modifying the browser’s URL. Rewrites are useful for hiding complex API URLs or restructuring routes.

Example:
```js
// next.config.js
module.exports = {
  async rewrites() {
    return [
      {
        source: '/blog/:slug',
        destination: '/posts/:slug',
      },
    ];
  },
};
```

- **Redirects**: Forward users from one URL to another. Unlike rewrites, the user’s browser will be redirected to the new URL. This is helpful for managing legacy URLs or when renaming routes.

Example:
```js
// next.config.js
module.exports = {
  async redirects() {
    return [
      {
        source: '/old-page',
        destination: '/new-page',
        permanent: true, // 301 redirect
      },
    ];
  },
};
```

**Hint:** 💡 Use rewrites for internal URL remapping and redirects for changing the user’s browser URL.

[Further Reading](https://nextjs.org/docs/api-reference/next.config.js/rewrites)

</details>

<details>
<summary><strong style="font-size: 1.2em;">15. How can you use TypeScript in a Next.js project?</strong></summary>

Next.js has built-in support for **TypeScript**. You can either start a project with TypeScript or add it to an existing project.

To add TypeScript:
1. Install TypeScript and types for React and Node.js:
```bash
npm install typescript @types/react @types/node --save-dev
```
2. Create a `tsconfig.json` file by running:
```bash
npx tsc --init
```

Next.js automatically detects and uses TypeScript. All `.js` files can be converted to `.tsx` to enable TypeScript features.

TypeScript improves development by providing static type checking, ensuring safer code, better IDE support, and improved refactoring.

**Hint:** 💡 TypeScript support is seamless in Next.js, with automatic type checking during development and builds.

[Further Reading](https://nextjs.org/docs/basic-features/typescript)

</details>

<details>
<summary><strong style="font-size: 1.2em;">16. How does Next.js implement internationalization (i18n)?</strong></summary>

Next.js supports **internationalization (i18n)** out of the box, allowing you to build multilingual websites easily. The configuration is done via `next.config.js` by specifying the locales, default locale, and domain-specific locales.

Example:
```js
// next.config.js
module.exports = {
  i18n: {
    locales: ['en', 'fr', 'es'],
    defaultLocale: 'en',
    domains: [
      {
        domain: 'example.fr',
        defaultLocale: 'fr',
      },
    ],
  },
};
```

Once configured, Next.js will automatically prepend the locale to the routes (e.g., `/fr/about`, `/es/contact`). You can use the `useRouter` hook to get the current locale and switch between languages.

**Hint:** 💡 Next.js’s built-in i18n support simplifies building multilingual sites without external libraries.

[Further Reading](https://nextjs.org/docs/advanced-features/i18n-routing)

</details>

<details>
<summary><strong style="font-size: 1.2em;">17. What are the different deployment strategies for a Next.js application?</strong></summary>

There are multiple ways to deploy a Next.js application, depending on the nature of the app (static, server-side, or hybrid):

1. **Vercel**: Next.js is created by Vercel, and deploying to Vercel provides instant static optimization, SSR support, and serverless functions. You just need to connect your repository to Vercel, and the deployment is automatic.
2. **Static Export**: If your application only uses static pages (via `getStaticProps` and `getStaticPaths`), you can export the app as static HTML files using `next export` and deploy it to any static hosting service, such as Netlify, GitHub Pages, or AWS S3.
3. **Custom Server**: For SSR apps or apps using API routes, you can deploy Next.js on any Node.js environment (AWS, DigitalOcean, etc.). Ensure your build process includes running `npm run build` followed by `npm start`.

**Hint:** 💡 For serverless deployments, Vercel is the most seamless option.

[Further Reading](https://nextjs.org/docs/deployment)

</details>

<details>
<summary><strong style="font-size: 1.2em;">18. How can you improve Lighthouse scores with Next.js?</strong></summary>

**Lighthouse** scores represent the performance, accessibility, and best practices of your web application. Next.js helps improve Lighthouse scores in the following ways:

1. **Static Site Generation**: Using SSG can reduce load times, which will directly improve the performance metrics.
2. **Image Optimization**: The `next/image` component automatically optimizes images by lazy loading and serving the most efficient image formats (like WebP).
3. **Code Splitting**: Next.js automatically splits code to ensure only the JavaScript needed for the current page is loaded.
4. **Automatic Font Optimization**: Next.js optimizes web fonts by reducing layout shifts (improving CLS scores).
5. **Efficient Caching**: Using caching strategies like `stale-while-revalidate` improves performance by reducing server load.

**Hint:** 💡 Next.js’s default optimizations can significantly boost Lighthouse performance scores.

[Further Reading](https://nextjs.org/docs/advanced-features/measuring-performance)

</details>

---

### Footer
- [Next.js Data Fetching](https://nextjs.org/docs/basic-features/data-fetching)
- [Next.js API Routes](https://nextjs.org/docs/api-routes/introduction)
- [Next.js Image Optimization](https://nextjs.org/docs/basic-features/image-optimization)

*Footnote: Prepared by Husain Amravatiwala*

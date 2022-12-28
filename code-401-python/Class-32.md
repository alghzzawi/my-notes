# __Intro to Next.js & Tailwind CSS__

As we announced at Next.js Conf, Next.js 13 (stable) lays the foundations to be dynamic without limits:

- __app Directory (beta):__ Easier, faster, less client JS.
    - __Layouts__
    - __React Server Components__
    - __Streaming__
- __Turbopack (alpha):__ Up to 700x faster Rust-based Webpack replacement.
- __New next/image:__ Faster with native browser lazy loading.
- __New @next/font (beta):__ Automatic self-hosted fonts with zero layout shift.
- __Improved next/link:__ Simplified API with automatic <a>.


Next.js 13 and the pages directory are stable and ready for production. Update today by running:



    npm i next@latest react@latest react-dom@latest eslint-config-next@latest

---

## __New app Directory (Beta)__

Today, we're improving the routing and layouts experience in Next.js and aligning with the future of React with the introduction of the app directory. This is a follow-up to the Layouts RFC previously published for community feedback.

The app directory is currently in beta and we do not recommend using it in production yet. You can use Next.js 13 with the pages directory with stable features like the improved next/image and next/link components, and opt into the app directory at your own pace. The pages directory will continue to be supported for the foreseeable future.

The app directory includes support for:

- __Layouts:__ Easily share UI between routes while preserving state and avoiding expensive re-renders.
- __Server Components:__ Making server-first the default for the most dynamic applications.
- __Streaming:__ Display instant loading states and stream in units of UI as they are rendered.
- __Support for Data Fetching:__ async Server Components and extended fetch API enables component-level fetching.
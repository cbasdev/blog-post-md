# 99% of Apps Should Be SSR (Update: The Era of Islands)

Hello, I want to update one of the reflections that has resonated most in my journey as a developer: why server-side rendering is not just an option, but a necessity for the modern web.

If in 2021 we said that SSR was the future, today in 2024 the game has evolved. We no longer just care *where* it renders, but **how much JavaScript (JS)** we force the client to load.

---

## The Current Landscape: SSR vs. CSR

To refresh, let's define the base strategies:

### Server Side Rendering (SSR)
* **Advantages:** The best *First Contentful Paint* (FCP), impeccable SEO and the user's browser rests (less RAM consumption).
* **Evolution:** Thanks to **React Server Components (RSC)**, we can now decide which components stay 100% on the server without sending a single byte of JS to the browser.

### Client Side Rendering (CSR)
* **Advantages:** Less initial load for the server and smooth transitions after the initial load.
* **Disadvantages:** The JS "bundle" has grown so much that mobile devices struggle to process heavy websites.

---

## The New Frontier: Islands Architecture 🏝️

This is where my perspective changed. If before SSR sent all the HTML and then "hydrated" the entire page (activating the JS), **Islands** propose something smarter.

Imagine an ocean of **static HTML** (fast, lightweight, without JS) where small **islands of interactivity** float.

* **How does it work?** 90% of your page (texts, images, footers) is served as pure HTML. Only components that really need interaction (a cart, a dynamic search) load their own JavaScript in isolation.
* **Leading frameworks:** Astro, Fresh and Qwik (with its concept of *Resumability*).

### Why is this better than traditional SSR?
1. **Zero JS by default:** If a page has no islands, the user downloads 0KB of JavaScript.
2. **On-demand loading:** Islands can load only when they enter the user's *viewport*, saving data and battery.
3. **Goodbye to main thread blocking:** By not having to "hydrate" the entire page at once, the site is instantly interactive.

---

## Performance Comparison

| Strategy | Interactivity | Client JS Load | Ideal for... |
| :--- | :--- | :--- | :--- |
| **CSR** | Slow at start | Very High | Complex private dashboards. |
| **SSR (Traditional)** | Medium (Hydration) | High | E-commerce and large Blogs. |
| **Islands / RSC** | **Instant** | **Minimal / Selective** | 99% of the public web. |

---

## Conclusion: Performance is the message

I still maintain that **99% of apps must be SSR**, but with the modern nuance: **SSR with Islands Architecture or Server Components**.

Companies like Instagram, TikTok and the largest e-commerce in the world no longer send gigantic applications to the client; they send optimized HTML and only the necessary JS so that the experience feels alive. Talking about performance today is not just talking about servers, it's talking about **sending less code**.

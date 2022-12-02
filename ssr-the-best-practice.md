# 99% of apps should be SSR.

Hello, I want to share one of the experiences that has made me understand the web world and talk about an exciting topic such as performance, and how paying attention to it could make a difference.

To begin with, it is necessary to define in a limited way how the mentioned development strategies differ, highlighting their advantages and disadvantages.

### SSR 
![SSR](https://user-images.githubusercontent.com/33915497/205201292-c8c1fa8e-4ff6-45b8-94be-674ba03c1119.png)

### CSR
![CSR](https://user-images.githubusercontent.com/33915497/205201379-c335e8f4-c01b-4c39-8c5f-69558cf6c215.png)


### Advantages
| Server Side Rendering | Client Side Rendering |
| --- | --- |
| Best First Contentful Paint (FCP) | Release server load (Cheaper) |
| Browser not working (Ram = 😁) | Less requests to the Server |
| Best SEO |  |
### Disadvantages
| Server Side Rendering | Client Side Rendering |
| --- | --- |
| Complete UI reloads. (If the cache is not used well) | Does not optimize SEO |
| Frequent server requests. (if not avoided) | By keeping the javascript loaded, the browser uses more memory (Ram = 😞) |
|  | Bad First Contentful Paint (FCP) |

There is a lot to say, and normally I would say that each development pattern would have a specific use (If it were 2021 hehe). Buuuuuuut, currently with the improvements of frameworks like NextJS, the new features of React Server Components have neutralized most of the disadvantages.

One of the most notable is the constant reloading of the entire page. Normally, it happened because for the cache, to store so much content, it was difficult to maintain; or because you didn't know (from the server) exactly which DOM elements were changing.
With the progressive hydration pattern (which I invite you to read), Next uses react's hydrate algorithm, updating only the necessary elements and thus optimizing the loading in the DOM.

Now, another of the things that SSR is criticized for is that it constantly makes requests to the server, which doesn't make sense to me. In which use case does your business not constantly make requests to the server? What if we better return the parsed html and not have to build views from the client? There may be some cases, but very few, that's why 99% of the title.

As well as progressive hydration, there are different techniques that make the SSR more and more useful. For example selective hydration, the islands architecture, **Streaming Server-Side Rendering** and others. Even giant companies with thousands and millions of components already use it. The largest e-commerce in the world, instagram, tiktok and others.

In short, to talk about performance is to talk about SSR. Cheers! 🪐

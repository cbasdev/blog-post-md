# Understanding the new web vital INP

Interaction to Next Paint (INP)
It is a metric that evaluates the responsiveness of a web using the Event Timing API, which is a tool that provides user interaction data.

The INP observes the latency of all click, tap and keyboard interactions with a page throughout its life and reports the longest duration, without taking into account outliers.

The goal of INP is to minimize the time that elapses from when a user initiates an interaction until the next frame is rendered, for all or most of the interactions that the user initiates.



https://github.com/cbasdev/blog-post-md/assets/33915497/20fe5893-fc6b-4544-a421-85f04ba8c49c


How INP is calculated

The INP is calculated by observing all the interactions that occur on a page and taking the interaction with the worst latency.


> 🗒️ An *interaction* is a group of event handlers that are triggered during the same logical user gesture. For example, "press" interactions on a touch screen device include several events, such as `pointerup`, `pointerdown` and `click`. An interaction can be generated with JavaScript, CSS, built-in browser controls, such as form elements, or a combination of all these elements.

</aside>

<img width="760" alt="image" src="https://github.com/cbasdev/blog-post-md/assets/33915497/4fed60f1-41b8-48d1-b18e-1eb9fbc2f8d6">


**What does an interaction contain?**

<img width="795" alt="image" src="https://github.com/cbasdev/blog-post-md/assets/33915497/d4eb1788-976b-4714-82c3-3f44cf5fca95">


**What is the difference between INP and First Input Delay (FID)?**

While both are responsiveness metrics, FID only measured the input delay of the *first* interaction on a page. INP improves on FID by taking into account *all* page interactions, from input delay to the time it takes to execute event handlers and, finally, until the browser paints the next frame. INP is a more reliable indicator of overall responsiveness, regardless of when the page interactions occur.

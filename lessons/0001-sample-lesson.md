# How a CDN Makes Websites Feel Faster

If you've ever wondered why a website loads instantly no matter where in the world you are, the answer is usually a content delivery network — and being able to explain why one actually helps is the goal of this lesson.

## The problem: distance costs time

A website normally lives on one server, in one place. If that server sits in Virginia and someone in Singapore requests the page, the data has to travel roughly 15,000 kilometres round trip. That trip takes time no matter how fast the connection is — it's a function of physical distance, not bandwidth. [Cloudflare's explainer on latency](https://example.com/cloudflare-latency) puts typical transoceanic round trips at 150–300 milliseconds before a single byte of the actual page has been processed.

A content delivery network (CDN) fixes this by keeping copies of a site's content on servers scattered across the world — called edge servers — so a visitor's request never has to travel further than the nearest one.

```panel:info
CDNs typically cache **static** assets — images, stylesheets, scripts, video — rather than personalized dynamic content, unless the site is specifically configured to cache dynamic responses too.
```

## What happens on a request

```mermaid
flowchart LR
    A[Visitor requests a page] --> B{Nearest edge server}
    B -->|Cache hit| C[Serve cached copy immediately]
    B -->|Cache miss| D[Forward request to origin server]
    D --> E[Origin returns the content]
    E --> F[Edge server stores a copy]
    F --> C
```

The first visitor to a given edge server after content changes causes a "cache miss" — a short delay while the edge server fetches a fresh copy from the origin and stores it. Every visitor after that, until the copy expires, gets the fast path.

```expand:What happens when an edge server doesn't have the content cached yet?
It's called a cache miss. The edge server forwards the request to the origin server, waits for the response, serves it to the visitor, and stores a copy locally so the next visitor to that edge server gets the fast path instead.
```

```expand:Why might a CDN not speed up a page that's mostly personalized content?
Personalized content — a logged-in user's dashboard, a shopping cart — is different for every visitor, so there's nothing reusable to cache. Most requests for that kind of page still have to reach the origin server, which is why CDNs help most with static, shared content.
```

**Further reading**: [How CDNs Work — MDN Web Docs](https://example.com/mdn-cdn-overview)

---
background: https://images.unsplash.com/photo-1523183616954-5d0a9e552cbb?ixlib=rb-4.0.3&q=85&fm=jpg&crop=entropy&cs=srgb&dl=paolo-nicolello-jBohRHjmLeo-unsplash.jpg&w=2400
layout: cover
remoteAssets: true
drawings:
  persist: false
transition: slide-left
title: The REST Rabbit Hole
---

<div class="bg-black/75 p-10">

# The REST Rabbit Hole

Understanding REST

</div>

---

# Why did I venture down the REST Rabbit Hole?

<v-click>

[Open Banking spec - Payment Initiation API](https://openbankinguk.github.io/read-write-api-site3/v3.1.11/profiles/payment-initiation-api-profile.html)

</v-click>

<v-click>
<div class="flex h-100">
<div class="m-auto">

> #### RESTful APIs
>
> The API adheres to RESTful API concepts where possible and sensible to do so.
>
> However, the priority is to have an API that is simple to understand and easy to use. In instances where following RESTful principles would be convoluted and complex, the principles have not been followed.
>
> -- <cite>[Open Banking Docs](https://openbankinguk.github.io/read-write-api-site3/v3.1.10/profiles/read-write-data-api-profile.html#restful-apis)</cite>
>

</div>
</div>
</v-click>

<!--
 - Didn't do comp sci degree so did some research
 - Open Banking spec surely did some good design - why would they not go fully REST?
-->
---

# Where does this term "REST" come from?

- A dissertation published at the start of the century based on the work done in the previous decade.
- Published by Roy Fielding
  - Worked on/led HTTP and URI standards
  - Co-founder Apache HTTP server
- Meaning "Representational State Transfer"

It's available on the internet: [Architectural Styles and
the Design of Network-based Software Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

---

# A bit of history (~1995)

<v-click>

Back then, phones looked like this:

<img src="https://upload.wikimedia.org/wikipedia/commons/6/68/1994_MicroTAC_International_8700.jpg" class="h-80 mx-auto" />

<cite>https://en.wikipedia.org/wiki/Motorola_MicroTAC</cite>

</v-click>

---

# A bit of history (~1995)

Amazon looked like this:

<img src="https://www.webdesignmuseum.org/uploaded/timeline/amazon/amazon-1995.png" class="h-80 mx-auto" />

<cite>https://www.webdesignmuseum.org</cite>

---

# A bit of history (~1995)

Cool kids looked like this:

<img src="https://upload.wikimedia.org/wikipedia/commons/d/dd/Jonathan_Brandis_Wiki.jpg"  class="h-80 mx-auto" />

<cite>By Airwolfberlin - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=9935410</cite>

---

# A bit of history (~1995)

- The number of webservers was growing exponentially and had gone from **130** to **23,517** in the **two years** before **June 1995**.
- The use of the internet was growing beyond academics sharing their papers or creating their personal websites.
- So some people needed to figure out how to make the web work in this "new" world

---

# The reason for the paper

While working on the HTTP standard:

> How do I differentiate through ones that are better for the web and the ones that are back to some older version of an architecture or an architecture that doesn't make sense any more on the internet?

<br />

> This was my model of describing to each other basically how a particular change to the standard would affect the resulting web

<br />

> If someone would offer a feature, or describe what was wrong with the web, I would use the model as a sort of analogy or proof-point to show ... what it is that the new feature might help or might hurt, and that allowed me some intellectual leverage in many ways to affect how the http standard worked.

<cite>-- [Roy Fielding Interview - Understanding the REST style](https://www.youtube.com/watch?v=w5j2KwzzB-0)</cite>

<!-- 
My interpretation: 
- As suggestions came in for changes to the HTTP specs there needed to be someway to decide whether that change was suitable. With a set of agreed upon principles (architectural constraints) that would lead to the properties wanted (requirements fulfilled), the effect a change could be almost quantified.
- Think of it like writing a "definition of ready" or "PR review template". There are outcomes a team wants to achieve through well-written tickets or code, and to guide discussion the teams comes up with constraints on those tickets or code.
- The paper actually came after, or towards the end of the 
-->

---

# The Requirements

> Berners-Lee writes that the "Web's major goal was to be a shared information space through which people and machines could communicate." What was needed was a way for people to store and structure their own information, whether permanent or ephemeral in nature, such that it could be usable by themselves and others, and to be able to reference and structure the information stored by others so that it would not be necessary for everyone to keep and maintain local copies.
> <br /><br />
> The intended end-users of this system were located around the world, at various university and government high-energy physics research labs connected via the Internet. Their machines were a heterogeneous collection of terminals, workstations, servers and supercomputers, requiring a hodge podge of operating system software and file formats. The information ranged from personal research notes to organizational phone listings. The challenge was to build a system that would provide a universally consistent interface to this structured information, available on as many platforms as possible, and incrementally deployable as new people and organizations joined the project.
>

<cite>[Dissertation - 4.1](https://www.ics.uci.edu/~fielding/pubs/dissertation/web_arch_domain.htm#sec_4_1)</cite>

<!--
Note: "requiring a hodge podge of operating system software and file formats"
Summary on this slide but also talks about:
 - Low Entry-barrier
 - Extensibility
 - Not "under the control of one entity" 
 - Independent Deployment
-->

---

# Deciding on an architectural style for the web

|Style | Derivation | NTP | UPP | EFF | SCL | SIM | EVO | EXT | CUS | CFG | REU | VIS | PRT | REL |
|-------|------------|------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|RR |  |  |++|  | +|  |  |  |  |  |  |  |  | +|
|$ |RR |  |+ |+ |+ |+ |  |  |  |  |  |  |  | |
|CS |  |  |  |  |+ |+ |+ |  |  |  |  |  |  |  |
|CSS |CS |- |  |  |++ |+ |+ |  |  |  |  |+ |  |+|
|C\$SS |CSS+\$ |- |+ |+ |++ |+ |+ |  |  |  |  |+ |  |+|

<cite>Cut down version of [Dissertation - 3.9](https://www.ics.uci.edu/~fielding/pubs/dissertation/net_arch_styles.htm#sec_3_9)</cite>

<!--
e.g.
RR = Replicated repository - think git. All stored locally so well fast. Can you store all internet on your laptop?
$ = cache - not quite as fast as RR as you still have network requests to access data
CS = Client Server
CSS = Client Stateless Server
C$SS = Client cached Stateless Server
Like the logical approach that builds on existing arch styles
-->

---

# Derivation

<img src="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_derivation.gif" class="h-80 mx-auto" />

<cite>[Dissertation - 5.1.8](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_8)</cite>

<!-- 
Shows how the different architectural styles are pulled together to reap the benefits needed to fulfill the requirements.

Quite abstract with no information on real implementation. And this is because this is the architectural style that that was used to build a way to distribute a variety of different types of information (text, images, video, etc) to:
 - users located around the world
 - with devices that ran different OS's that didn't understand the same file types
with the NFRs that:
 - it should be easy to use
 - performant
 - scalable
 - ...

So if you want to build something similar then, here's what we used and why we used it
-->

---

# We've not mentioned anything to do with APIs yet

In fact, APIs are only mentioned in the final "evaluation section" of the dissertation and there's nothing called a RESTful API.

# 😕

But we do know a bit more about the intent behind REST, and we can pull out some key ideas from the dissertation (not a comprehensive list) and some of those architectural constraints.

---

# Hypertext / Hypermedia

> Hypertext is text displayed on a computer display or other electronic devices with references (hyperlinks) to other text that the reader can immediately access. Hypertext documents are interconnected by hyperlinks, which are typically activated by a mouse click, keypress set, or screen touch
> -- <cite>https://en.wikipedia.org/wiki/Hypertext</cite>

> Hypermedia, an extension of the term hypertext, is a nonlinear medium of information that includes graphics, audio, video, plain text and hyperlinks
> -- <cite>https://en.wikipedia.org/wiki/Hypermedia</cite>

---

# Resource

> Any information that can be named can be a resource: a document or image, a temporal service (e.g. "today's weather in Los Angeles"), a collection of other resources, a non-virtual object (e.g. a person), and so on. In other words, any concept that might be the target of an author's hypertext reference must fit within the definition of a resource.

<cite>[Dissertation - 5.2.1.1](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_1)</cite>

<!--
This definition of a resource is pretty loose - it can be pretty much anything
-->

---

# Resource Identifier

> REST relies instead on the author choosing a resource identifier that best fits the nature of the concept being identified
> --<cite>[Dissertation - 5.2.1.1](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_1)</cite>

Since this is quite abstract it's useful to ground our understanding in the web "implementation" of REST - i.e. a URI, and for example:

- <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier> (A wikipedia article on URIs)
- tel:+4412345678901 (A telephone number)
- urn:isbn:1234567890 (An identifier for a book)

---

# Representation

> REST components perform actions on a resource by using a representation to capture the current or intended state of that resource and transferring that representation between components. A representation is a sequence of bytes, plus representation metadata to describe those bytes. Other commonly used but less precise names for a representation include: document, file, and HTTP message entity, instance, or variant.

> The data format of a representation is known as a media type

Again, to ground this, let's look at some examples:

- `text/html`
- `image/png`
- `application/json`

This gives the client (in the case of the web: the browser) understanding of what the contents of the message means - e.g. How to display it to the user, how the user can interact with it (remember those hyperlinks from before). It is included in all messages that have content (a Body) so that any component receiving that message also knows how to interpret the contents of that message.

--<cite>[Dissertation - 5.2.1.2](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_2)</cite>

---

# Manipulation of resources through representations

We need to be able to perform actions on resources using their representations - HTTP provides some methods we can use to that along with some rules:

- `GET` - Along with `HEAD`, `OPTIONS` and `TRACE` these must be "safe" - they must not modify resources.
- `PUT` and `DELETE` - Replace or remove all representations of the resource. These must be idempotent.
- `POST` - Perform resource-specific processing on the request content.

<cite>Based off [HTTP spec](https://www.rfc-editor.org/rfc/rfc9110.html#section-9)</cite>

<!--
- Why do they need to be safe? Take example of a google crawling the web - if every time it got a resource it, it modified something, that wouldn't be great. Following the http spec allows google to make these assumptions - that uniform interface is protecting us by providing some guarantees about the verbs
- We also get some nice guarantees with PUT and DELETE that mean the client can retry these 
- Interesting to note that POST can be broader than creating resources - just resource-specific processing. Although does provide you with a location header to link to the "primary resource" you created.
-->
---

# Self-descriptive messages

The idea that along a chain of multiple components, that could have different operating systems and different OS's, there's a shared understanding wholly on the contents of the message (and any agreed standards - e.g. the media types).

The idea being that for someone "discovering" your application, there should be some base understanding of the types of the protocol and the types of messages that can be sent - but these shouldn't be specific to your application. 

So, for example, when we browse the web, all messages should include information on the protocol and the media type. e.g. a simplified response to a `GET` request on website would look like:

```sh
HTTP/1.1 200 OK
Content-Type: text/html

<html></html>
```

This also means that any extra information outside the media type needed to understand the message needs (somehow) be included in the message itself!

---

# Hypermedia as the engine of application state (HATEOAS)

This is essentially what makes the internet so discoverable - by each resource providing links to other resources (either "controlled" by you, or someone else).

Let's take the example of browsing to the home page of a website. The browser makes a request to `GET /` willing to `Accept: text/html`. A key trait of the `text/html` media type is that it allows the inclusion of links, e.g. through `<a href="http://..." />`. This means that anyone arriving at the "home page" can discover the rest of the site. 

Without this, how would Google crawl websites? 

*you can of course maintain a sitemap, but this somewhat goes against the concept of Self-descriptive messages*

<!-- 
Do many "REST" APIs fulfill this requirement? How could you fulfill this requirement?
-->

---

# Stateless

>We next add a constraint to the client-server interaction: communication must be stateless in nature, as in the client-stateless-server (CSS) style of Section 3.4.3 (Figure 5-3), such that each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.

<cite>[Dissertation - 5.2.3](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_3)</cite>

How does this apply to our API? We need to make sure our API allows enough state (in the form of representations) to be transferred to our server-side components so they can be stateless. i.e. All our messages are transferring state in the form of representations - you could call this "Representational State Transfer"!

<!-- 
Back to our architectural constraints
-->
---

# Caching

Considering caching is used to balance the trade-offs of quite "heavy-weight" messaging, it's important to consider this in a RESTful application. For example, HTTP provides multiple well understand headers that serve as meta data to describe how caches should operate. Some examples below:

 - [Cache-Control](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)
 - [Last-Modified](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Last-Modified)
 - [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)

<!--
One thing I really notice is that caching tends to only become **critical** at scale, so the absence of caching consideration from a "REST" API can indicate that API wasn't meant to be used as part of a RESTful application. 
-->

---

# What's next?

<!--
We're done with the basic understanding, so how does this get us closer to what a "RESTful" API is?
-->
---

# A different approach

> An API that provides network-based access to resources via a uniform interface of self-descriptive messages containing hypertext to indicate potential state transitions

<br />

> **might**

<br />

> be part of an overall system that is a RESTful application

<cite>[Roy Fielding REST presentation](https://roy.gbiv.com/talks/201511_Fielding_REST_CF.pdf)</cite>

<!--
 - Maybe could have guessed that REST wasn't written as a spec or a style for API design. This quote confirms that thinking:
 - To have any chance of my API being part of an application I can call RESTful, then there are some constraints it needs to abide by.
-->

---

# Example #0 - The Web

<https://google.com>

---

# Example #1 - A more complex workflow

<https://www.infoq.com/articles/webber-rest-workflow/>

---

# How has REST ended up as an API "style guide" when it was originally a guide for architecting the web?

1. Maybe we mean "Take **some** of those constraints from REST into consideration when designing this API"
e.g. / i.e.:
 - Make sure it supports stateless servers so that I can easily scale my backend and make debugging easier.
 - Use some well understood data types - i.e. `application/json` nowadays.
 - Utilise links where standards exist (e.g. for pagination).

This sounds a lot like our original Open Banking quote: 

> The API adheres to RESTful API concepts where possible and sensible to do so.
>
> However, the priority is to have an API that is simple to understand and easy to use. In instances where following RESTful principles would be convoluted and complex, the principles have not been followed.

---

# How has REST ended up as an API "style guide" when it was originally a guide for architecting the web?

2. Maybe it was a retaliation against the overly verbose SOAP style or proprietary protocols around at the time it took off. Essentially a poster-child for simplicity, efficiency and utilising existing standards.

---

# How has REST ended up as an API "style guide" when it was originally a guide for architecting the web?

3. Maybe as it took off it became a buzzword as companies needed one word to describe their modern APIs

>They could have called their approach Fuck It, Overload HTTP (FIOH), and that would have been an accurate name, as anyone who has ever tried to decide what HTTP status code to return for a business logic error can attest. But that would have seemed recklessly blasé next to all the formal specification work that went into SOAP.

<cite>[Article: Roy Fielding's Misappropriated REST Dissertation](https://twobithistory.org/2020/06/28/rest.html)</cite>

---

# Is there any standard for what a RESTful API looks like now?

The understanding of what a RESTful API has clearly changed over time, so it's useful to look at what tools and standards there are available now.

---

# Richardson Maturity Model

[The Richardson Maturity Model](https://en.wikipedia.org/wiki/Richardson_Maturity_Model) provides a level based guide to how "RESTful" your API is. It covers HATEOAS in there as well (the final level) and is a nice guide to helping designing an API (even if it doesn't end up meeting level 3!)

---

# JSON Hypermedia Formats

If you want to enrich json with hyperlinks, it can be useful to follow one of the JSON hypermedia standards (all of which are published to IANA as media types). There's a good comparison in this article: [JSON Hypermedia Formats](https://sookocheff.com/post/api/on-choosing-a-hypermedia-format/). You may just want to use bits of these!

---

# Does it have to be REST?

> REST has become a BUZZWORD. There's nothing particularly wrong with that unless you happen to be me...
> <cite>-- [Presentation from Roy Fielding - page 3](https://roy.gbiv.com/talks/201511_Fielding_REST_CF.pdf></cite>

Throughout his dissertation Roy talks about understanding the requirements for the application and architecting based on those. So should we take that "RESTful" approach and look to alternatives?

---

# Alternatives

- Just use RPC (e.g. [gRPC](https://grpc.io/))
- [GraphQL](https://graphql.org/)
- Websockets
- WebRTC


---

# RPC

- I know exactly who and what I'm speaking to - we're tightly coupled
- I don't really care about distributing this (without a lot of work)

---

# GraphQL

- I don't care about cachability because my data's always being updated (e.g. chat app)...
- ...Or I always need the most up-to-date version (e.g. status monitor)
- I care about flexibility, minimizing the data I receive and the number of network calls I make

---

# Or a mix of these styles

<!-- 
e.g. Facebook doesn't respond with image data or the html to construct your feed through graphql queries.
-->

---

# The most restful thing to do

<img v-click-hide src="https://images.unsplash.com/photo-1595746262347-3e2b17daf768?ixlib=rb-4.0.3&q=85&fm=jpg&crop=entropy&cs=srgb&dl=greg-rosenke-uMQsB4HPbYE-unsplash.jpg&w=640" class="h-100 mx-auto" />

<v-clicks>

- Design for the needs of the system
- Design for the capabilities of the team
- Design for understanding of consumers and future maintainers
- ...And I'm sure there are more!

</v-clicks>

---

# What I hope you take from this talk

- A broader understanding of how the web was architected, why it was designed in this way and where to look for more information
- Some ideas to use in the designs of your own APIs
- Architecture shouldn't be take "ivory tower" approach, but a lot of thought, discussion, trial and error, and documenting does go into great architecture.
- It's important not to design based on buzzwords.
- Concepts can change over time.
- Everytime you see the words REST or RESTful you'll think back to this talk as a kind of accidental memory aid

<!--
Struggling to put the last one into words, but it's easy for people to claim something isn't RESTful, as there's some vagueness there that makes it possible to do this.
For example:
 - Nice structured URLs - Although REST actually advocates that it doesn't actually matter than much how your URLs are structured, this is still a really good thing to discuss and agree on, 
 - Should it be POST/PUT/PATCH - Look at the HTTP specs to ensure you're conforming to them. Look at what other APIs are doing for consistency. But don't get caught on mapping mapping http methods to CRUD (unless that's what you do everywhere else!).
-->

---

# What I hope you don't take from this talk

- A new found urge to point how your team's new API isn't actually RESTful.
- That all APIs should be RESTful to be considered well designed - "If it worked for the web why wouldn't it work for my API?"
- That just because chequered shirts were cool in the 90's they can't be cool now.

<!--
- ... but it could lead to conversations around the use-cases for the API (e.g. will it really be accessed by web crawlers?)
- ... but it can be useful to take the bits that work well in your use case, or maybe another style is more appropriate
- ... so go out and buy one
-->
---

# Resources (or are they links?)

- [Open Banking RESTful comment](https://openbankinguk.github.io/read-write-api-site3/v3.1.10/profiles/read-write-data-api-profile.html#restful-apis)
- [Roy Fielding Dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)
- [Roy Fielding Interview - Understanding the REST style](https://www.youtube.com/watch?v=w5j2KwzzB-0)
- <https://roy.gbiv.com/talks/200709_fielding_rest.pdf>
- <https://roy.gbiv.com/talks/201511_Fielding_REST_CF.pdf>
- [Roy Fielding's Misappropriated REST Dissertation](https://twobithistory.org/2020/06/28/rest.html)
- [REST: I don't Think it Means What You Think it Does](https://www.youtube.com/watch?v=pspy1H6A3FM)
- [Roy Fielding - REST APIs must be hypertext-driven](https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)
- [JSON Hypermedia Formats](https://sookocheff.com/post/api/on-choosing-a-hypermedia-format/)
- [Richardson Maturity Model](https://en.wikipedia.org/wiki/Richardson_Maturity_Model)
- [Example REST Workflow](https://www.infoq.com/articles/webber-rest-workflow/)

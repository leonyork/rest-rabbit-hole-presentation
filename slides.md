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
 - Heard conversations and been a part of some around "RESTful" API design
-->
---

# Where does this term "REST" come from?

- A dissertation published at the start of the century based on the work done in the previous decade.
- Published by Roy Fielding
  - Worked on/led HTTP and URI standards
  - Co-founder Apache HTTP server

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

But we do know a bit more about the intent behind REST.

---

# A different approach

> An API that provides network-based access to resources via a uniform interface of self-descriptive messages containing hypertext to indicate potential state transitions

<br />

> **might**

<br />

> be part of an overall system that is a RESTful application

<cite>[Roy Fielding REST presentation](https://roy.gbiv.com/talks/201511_Fielding_REST_CF.pdf)</cite>

<!--
 - So this makes a ense. To have any chance of my API being part of an application I can call RESTful, then there are some constraints it needs to abide by.
 - Let's refer back to the dissertation
-->

---

# Resource

> Any information that can be named can be a resource: a document or image, a temporal service (e.g. "today's weather in Los Angeles"), a collection of other resources, a non-virtual object (e.g. a person), and so on. In other words, any concept that might be the target of an author's hypertext reference must fit within the definition of a resource.

<cite>[Dissertation - 5.2.1.1](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_1)</cite>

<!--
This definition of a resource is pretty loose - it can be pretty much anything
-->

---

# Uniform interface

> In order to obtain a uniform interface, multiple architectural constraints are needed to guide the behavior of components. REST is defined by four interface constraints: identification of resources; manipulation of resources through representations; self-descriptive messages; and, hypermedia as the engine of application state.

<cite>[Dissertation - 5.1.5](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5)</cite>

<!--
Makes sense to have a uniform interface so that you 
Let's take each of these constraints and apply them to the web implementation of REST
-->

---

# Identification of Resources (URI in web-speak)

A URI gives us a standard way of identifying resources. To give some examples:

- <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier> (A wikipedia article on URIs)
- tel:+4412345678901 (A telephone number)
- urn:isbn:1234567890 (An identifier for a book)

---

# Manipulation of resources through representations

We need to be able to perform actions on resources - HTTP provides some methods we can use to that along with some rules:

- `GET` - Along with `HEAD`, `OPTIONS` and `TRACE` these must be "safe" - they must not modify resources.
- `PUT` and `DELETE` - Replace or remove all representations of the resource. These must be idempotent.
- `POST` - Perform resource-specific processing on the request content.

<cite>Based off [HTTP spec](https://www.rfc-editor.org/rfc/rfc9110.html#section-9)</cite>

<!--
- Why do they need to be safe? Take example of a google crawling the web - if everytime it got a resource it, it modified something, that wouldn't be great. Following the http spec allows google to make these assumptions - that uniform interface is protecting us by providing some guarantees about the verbs
- We also get some nice guarantees with PUT and DELETE that mean the client can retry these 
- Interesting to note that POST can be broader than creating resources - just resource-specific processing. Although does provide you with a location header to link to the "primary resource" you created.
-->

---

# And what about these "representations"?

---

# ...Well, we should be able to find out from the "self-describing message" part, right?

> A REST API should spend almost all of its descriptive effort in defining the media type(s) used for representing resources and driving application state, or in defining extended relation names and/or hypertext-enabled mark-up for existing standard media types

<cite>[Blog post from Roy Fielding: REST APIs must be hypertext driven](https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)</cite>
---

# And so what are media types?

Some example media types:

- `text/html`
- `image/png`
- `application/json`

Which gives us a way to respresent our resources:

- a `text/html` representation

---

# Example #0 - A static website

A "home" to start from: "<https://example.com/>".

Multiple media types including [text/html](https://www.iana.org/assignments/media-types/text/html) that describes how html should behave in an application (web browser), including:

- Links to other pages using an anchor (`<a>`) tag including a URI that the browser will perform a `GET` request to and perform an action based on what the response was (e.g. if it's another `text/html`, then display that page).
-
  
---

# Example #1 - Orders (HATEOAS)

> As a user I should be able to place an order, but only if I've logged in

Some solutions over HTTP:

1. `OPTIONS` HTTP verb
2. `Expect` HTTP header
3. `302` Found (redirect to login)
4. URI for action to take: e.g. `https://login.example.com/?redirect_uri=/order`

<!--
In the solutions I'm focussing on the HATEOAS side of things we'll ignore:
 - Mediatypes
 - Self descriptive messages (no schemas)
-->

---

# Example #1, Solution #1

We need a "home" to start at so that users can discover our API

Request:

```sh
GET /
```

Response:

```json
{
  "_context": {
    "base": "https://example.com"
  },
  "_links": {
    "self": "/",
    "orders": "/orders"
  }
}
```

<!--

-->

---

# Example #2 - Rebooting a PC

- `PUT`/`PATCH` `/server/1234`: `Content-Type: application/json`, Body: `{ status=rebooting }`
- `POST` `/server/1234/command`: `Content-Type: text/plain`, Body: `sudo shutdown -r now`
- Just use another architectural style

-<cite>[Original Problem](https://nicholassterling.wordpress.com/2014/02/16/rebootrestart-in-a-rest-api-using-put/)</cite>

---

# Alternatives

- Just use RPC (e.g. [gRPC](https://grpc.io/))
- [GraphQL](https://graphql.org/)
- Websockets

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
- Concepts can change over time
- Everytime you see the words REST or RESTful you'll think back to this talk as a kind of accidental memory aid

---

# What I hope you don't take from this talk

- A new found urge to point how your team's new API isn't actually RESTful.
- That all APIs should be RESTful to be considered well designed - "If it worked for the web why wouldn't it work for my API?"
- That just because chequered shirts were cool in the 90's they can't be cool now.

<!--
- ... but it could lead to conversations around the use-cases for the API (e.g. will it really be accessed by web crawlers?)
- ... but it can be useful to take the bits that work well in your use case, or maybe another style is more approprate
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

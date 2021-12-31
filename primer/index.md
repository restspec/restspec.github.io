---
layout: page
title: REST Primer
permalink: /primer/index.html
---

# Introduction

REST is a set of rules that make the World Wide Web possible.

As organizations have adopted Web technologies in countless ways,
a foundation in the Web's underlying principles has become a crucial
competency.

This primer provides the foundation in REST used by the designers
of web resources, including APIs, to take advantage of the Web's
advantages and avoid predictable pitfalls.

# What is REST?  A Bit of History

**REST**, an abbreviation for **RE**resentational **S**tate **T**ransfer, is 
an architetural style defined by Roy Fielding in his doctoral thesis,
_Architectural Styles and the Design of 
Network-based Software Architectures_, published in 2000.  Fielding developed REST 
to explain and justify decisions made on the formal standard for the 
Web's key protocol, HyperText Transfer Protocol, or HTTP.

Several standards for HTTP were released between 1996 and 1999, making 
way for a more useful, robust World Wide Web.  His 2000 dissertation
and publication of similar work through the International Conference on 
Software Engineering (ISCE) provided REST sufficient public awareness to
lure a return to the style less than a decade later, when popular 
Web-based integration technologies, including the W3C's SOAP, began to
reveal their shortcomings.

As it turned out, Fielding had produced something quite special.
More than merely enabling the Web to function, he had developed a
framework for exposing a Web of interactable resources.  More than
a network of linked documents, the subtle changes in Fielding's  
Web could robustly express semantics for _anything_.  It provided the
flexibiilty enjoyed by software developers in Object Oriented
(OO) design, and it provided a way to meaningfully convey objects,
their states, and their methods.

REST was not appreciated at first.  The Web, through the HTTP standard, 
was sufficiently successful on its own.  One work in
particular, the W3C's
_[Architecture of the World Wide Web, Volume One](https://www.w3.org/TR/webarch/)_,
provide a significant step forward by further articulating the core
concepts intended for the Web.  REST offered a set of constraints,
while the W3C provided Web resources designers guidelines for the use
of HTTP borne out of about a decade of experience, by that point.

Through the work of the Internet Engineering Task Force (IETF), the
management of protocol registries by the Internet Assigned Numbers Authority
(IANA), and the crucial work of the World Wide Web Consortium (W3C), we have
an extraordinary foundation upon which to realize REST and an interactable
Web.

#### What does this have to do with APIs?

If you have this question, it may be coming from the common view that 
the Web and HTTP APIs are separate things.  Under-the-hood, they are not.

Creating great HTTP APIs requires understanding REST and the reasons why its
constraints yield such a palette of useful instruments and benefits. 

# REST's Constraints



RESTspec focuses primarily on the REST architecture style, which provides
the philosophical foundation for the World Wide Web and the design philosophy
for its primary protocol, HyperText Transfer Protocol (HTTP).  Along the way, it
also draws from normative Web standards provided by the Internet Engineering
Task Force (IETF), the World Wide Web Consortium (w3c), and related organizations.
In addition to normative sources, RESTspec incorporate modern API authoring
formats, including JSON Schema and OpenAPI.



## REST Overview

RESTspec focuses primarily on the REST architecture style, which provides
the philosophical foundation for the World Wide Web and the design philosophy
for its primary protocol, HyperText Transfer Protocol (HTTP).  Along the way, it
also draws from normative Web standards provided by the Internet Engineering
Task Force (IETF), the World Wide Web Consortium (w3c), and related organizations.
In addition to normative sources, RESTspec incorporate modern API authoring
formats, including JSON Schema and OpenAPI.

By focusing on established standards, RESTspec guides API authors
toward better design practices
Alignment with existing industry standards makes
Web Resources and APIs readily acceptable to developers
and the tools they use.

Although REST, as a topic, is broader than HTTP and the World Wide Web, RESTspec
focuses on HTTP and the ecosystem of tools, formats, and technologies found
in and around the modern Web and Web APIs.

## Concepts

### The API Program

...

### The API Portfolio


RESTspec is designed to be applied to a _Web Resource Porfolio_, or API Portfolio.
A Web Resource Portfolio organizes, governs, and provides a purpose for a collection of web
resources.  A portfolio provides rules that constrain its member APIs and resources,
sets style standards, and servers as an anchor for a variety of practices that apply to
the API portfolio.

#### Why not simply govern at a program level?

While it is possible for an organization to simply manage one portfolio, doing so may come
with costs.

...
- Legacy
- Consistency Avoidance
- Obstacle to Scale


### REST
REST, or REpresentational State Transfer, is the architectural style developed by
Roy Fielding to support design decisions for the HTTP Protocol.  Developed in the
1990's, it was originally published in Fielding's 2000 doctoral dissertation.

Those seeking a full explanation of REST should read Fielding's work.  A number of
other sources, including the w3c's
_Architecture of the World Wide Web, Volume One_, and Tim Berners-Lee's
collection of notes on architectural, and the excellent _RESTful Web Services,
by Leonard Richardson and Sam Ruby, cover much of the remaining ground.


To expedite things, this guideline will summarize REST's constaints and
the takeaways that influence this guideline.

**REST's Ten Constraints**:
- **Client-Server**: All REST interactions are between Client and Server. Establishes separation of concerns.
- **Stateless**: State of the client is never stored with the server.  Further supports separation of concerns and avoids scalability pitfalls.
- **Caching**: Content explicitly identified as cacheable may be stored by the client or intermediaries instead of making another request to the server.
- **Layered System**: Network elements handling HTTP requests may only concern themselves with interactions with directly adjacent elements.
- **Uniform Interface**: Regardless of the resource or service, the subject of the request and response, the protocol's interface will be the same.  The following four constraints further inform *Uniform Interface*.
    - **Identification of Resources**: All REST interactions must be in the context of an identified resource.
    - **Resource Interaction via Representations**: Resource interactions are always about the state of the resource, and content payloads are always representations of the state of the resource, typically current or desired.
    - **Self-describing Messages**: Messages must be fully self-descriptive; a sufficiently qualified message handler will be able to fully understand the message's meaning based only on content of the message.
    - **Hypermedia** (or HATEOAS): The resource and application state transitions available are provided to the client via hypermedia; response messages will provide links.
- **Code On Demand**: The server may facilitate client processing by providing supplemental code as needed.

**RESTspec Assumptions based on the modern Web practices**:
- HTTP semantics, specially its methods, response codes, headers,
  and content negotiation rules govern web communication.
- Resource Identifiers are URIs.
- Resource Representations come formatted according to _media types_.
  Publicly-registered media types may be found in the
  [IANA Media Type Registry](https://www.iana.org/assignments/media-types/media-types.xhtml).
  For a client to understand a media type not found in the registry, some
  mechanism must be provided to enable that client to do so.
- In practice, message Self-description requires not only on
  the content of the message being sufficiently informative,
  but also that the handler of the message be sufficiently
  qualified to read it.
- Hypermedia is instrumental in enabling the client and its user to self-direct.
  Lacking hypermedia, a resource does not support REST.






#### REST: It's not about APIs

The original designers of the Web were primarily concerned with creating a
browsable, multimedia, interactable, anarchically manageable,
scalable network of interconnected documents and resources.  REST was not
about APIs; API designers adopted REST because it was a good fit for their needs.

BUT, with sufficient analysis, the parallels between Object-Oriented and
Resource-Oriented design will become apparent. 


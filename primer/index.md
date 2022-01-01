---
layout: page
title: REST Primer
permalink: /primer/index.html
---

## Introduction

REST is a set of rules that make the World Wide Web possible.

As organizations have adopted Web technologies in countless ways,
a foundation in the Web's underlying principles has become a crucial
competency.

This primer provides the foundation in REST used by the designers
of web resources, including APIs, to take advantage of the Web's
advantages and avoid predictable pitfalls.

## What is REST?  A Bit of History

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
a strong foundation upon which to realize REST and an interactable
Web.

While it should be noted that REST does not require HTTP, nor must it 
be implemented using the familiar technologies used in the modern Web,
this explanation will center on these technologies.

#### What does this have to do with APIs?

If you have this question, it may be coming from the common view that 
the Web and HTTP APIs are separate things.  Under-the-hood, they are not.

Creating great HTTP APIs requires understanding REST and the reasons why its
constraints yield such a palette of useful instruments and benefits. 

## REST's Constraints

The REST architecture is defined by ten constraints, 
six primary and four supportive.  Here they are at a glance.

| Constraint                                                               | Definition                                                                                                                                                   |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Client-Server**                                                        | All REST interactions are between _client_ and _server_.                                                                                                     |
| **Stateless**                                                            | The state of the client is _never_ stored with the server.                                                                                                   |
| **Caching**                                                              | Content explicitly identified as cacheable may be stored and reused by the client or intermediaries.                                                         |
| **Layered System**                                                       | Message handlers may only concern themselves with interactions with directly adjacent handlers.                                                              |
| **Uniform Interface**                                                    | Regardless of service or resource, the protocol's interface will be generic.                                                                                 |
| Uniform Interface: **Identification of Resources**                       | All interactions must be in the context of an identified resource.                                                                                            |
| Uniform Interface: **Manipulation of Resources through Representations** | Messages are representations of the resource.  They about the current or intended state of the resource.                                                     |
| Uniform Interface: **Self-descriptive Messages**                         | To enable processing by intermediaries, interactions must be stateless, use standard media types and method semantics, and explicitly indicate cacheability. |    
| Uniform Interface: **Hypermedia**                                        | The resource and application state transitions available are provided to the client via hypermedia; response messages will provide links.                    |
| **Code on Demand**                                                       | The server may facilitate client processing by providing supplemental code as needed.                                                                        | 

According to Fielding, REST was developed to enable a "distributed hypermedia system."  In other words, REST makes a _browsable_, interlinked network of disparately-managed media possible.  Browseability is crucial; the use of HTTP for APIs has usually neglected some of RESTs constraints, despite adoption of the term.

#### REST: It's not about APIs

The original designers of the Web were primarily concerned with creating a
browsable, multimedia, interactable, anarchically manageable,
scalable network of interconnected documents and resources.  REST was not
about APIs; API designers adopted REST because it was a good fit for their needs.

BUT, with sufficient analysis, the parallels between Object-Oriented and
Resource-Oriented design will become apparent. 



####

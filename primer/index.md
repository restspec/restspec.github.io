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
this explanation will center on these technologies.  In addition, this
primer will refer to the HTTP specifications being drafted for 2022 release.

#### What does this have to do with APIs?

If you have this question, it may be coming from the common view that 
the Web and HTTP APIs are separate things.  Under-the-hood, they are not.

Creating great HTTP APIs requires understanding REST and the reasons why its
constraints yield such a palette of useful instruments and benefits. 




## REST's Constraints In Brief

The REST architecture is defined by ten constraints, 
six primary and four supportive.  Together, the constraints provide 
the familiar characteristics of the World Wide Web while
avoiding architectural pitfalls that could undermine its manageability,
scalability, and reliability.

Here they are at a glance.

| Constraint                                                                     | Definition                                                                                                                                                    |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Client-Server**                                                              | All REST interactions are between _client_ and _server_.                                                                                                      |
| **Stateless**                                                                  | The state of the client is _never_ stored with the server.                                                                                                    |
| **Caching**                                                                    | Content explicitly identified as cacheable may be stored and reused by the client or intermediaries.                                                          |
| **Layered System**                                                             | Message handlers may only concern themselves with interactions with directly adjacent handlers.                                                               |
| **Uniform Interface**                                                          | Regardless of service or resource, the protocol's interface will be generic.                                                                                  |
| Uniform Interface:<br /> **Identification of Resources**                       | All interactions must be in the context of an identified resource.                                                                                            |
| Uniform Interface:<br /> **Manipulation of Resources through Representations** | Messages are representations of the resource.  They about the current or intended state of the resource.                                                      |
| Uniform Interface:<br /> **Self-descriptive Messages**                         | To enable processing by intermediaries, interactions must be stateless, use standard media types and method semantics, and explicitly indicate cacheability.  |    
| Uniform Interface:<br /> **Hypermedia** as the Engine of Applicatino State     | The resource and application state transitions available are provided to the client via hypermedia; response messages will provide links.                     |
| **Code on Demand**                                                             | The server may facilitate client processing by providing supplemental code as needed.                                                                         | 

## Implementing REST

REST's constraints apply not only to the HTTP protocol, but also its use.

REST can be seen in _HTTP message syntax_, _HTTP semantics_, 
_resource semantics_, _media type semantics_, _link semantics_,
and elsewhere.  By choosing HTTP, support for REST is much
easier; some of the most difficult and mundane aspects of design
are addressed up front.  But HTTP does not address 
the design of web resources, portfolios or content.  This, it
delegates to other sources, and quite often, to you.

#### Client Competency

Although REST constrains messages to be *Self-descriptive*,
the less-celebrated complement is that the message processor
must be able to understand the message.  For example,
when client encounters content whose media type is
"text/html", the client must be capable of understanding HTML.
**Client competency** is required for a REST-based solution
to function.

What client competency is required?

It depends on the solution.  If the modern
Web is the solution, the modern Web browser is
the most typical client; it will
understand HTTP, standard headers, and media types
for markup, style,
code, images, etc.  It will also understand how to
interact with the user, apply security patterns as
directed, and support a variety of client-side features.

If the solution provides publicly-accessible Web
APIs, but is not
intended for modern Web browsers, it simply has
different client competency requirements.  It is
still uplifted by adopting public standards,
suffers from not respecting REST constraints.  The
client must still implement HTTP syntax, _should_
respect HTTP semantics, and _should_ apply REST's
constraints in its design.


### REST in Message Syntax

To implement REST, the _messaging protocol_ must be able to express 
REST's key elements.  The protocol syntax has a number of specifications;
the most common is HTTP/1.1, but HTTP/2 and the forthcoming HTTP/3 are 
gaining traction fast. 
Despite the differences, they all support REST's constraints.

In HTTP, we see support in a number of ways:
- **Client-Server**: Every message is either a request or a response.
- **Stateless**: HTTP messages is _capable_ of passing messages that 
support stateless interactions by providing the headers and content 
to be used to express the resource state and related metadata
- **Caching**: HTTP's cache-related headers enable responses to 
explicitly convey response cachability, provide metadata to enable 
detection of state change, and enable requests to direct
conditional processing based on cached content and associated
attributes.
- **Layered System**: HTTP is designed to be implemented in layers
and deliberately avoids message processing rules that concern
themselves beyond the current layer's processing.
- **Uniform Interface**: HTTP provides a standard set of methods,
a way to stipulate a URI to provide message context, header for metadata,
and resource content.
- **Code On Demand**: Late feature binding through
code on demand is supported through client support for 
code-bearing content types.

### REST in HTTP Semantics

Unlike the message syntax, HTTP semantics are common across versions
of the HTTP messaging protocol.

**Caching** is addressed through the well-defined HTTP headers
and HTTP method semantics.

**Client-Server**, **Stateless**, and **Layered System** are
largely addressed in HTTP message syntax.

The **Uniform Interface** constraint heavily informs HTTP semantics.

Uniformly standardized semantics are provided as follows:
- HTTP's methods - GET, PUT, DELETE, POST, and so on - convey
the intent of the client toward the resource.  In addition to
standardizing how methods are to be processed, 
each method has specific semantics relative to being
_safe_, _idempotent_, and _cachable_.
- HTTP's response codes each have specific semantic meaning.
- Each of HTTP's headers conveys semantic meaning about the
message.  Standardized headers are available to indicate 
a wide variety of things.
- HTTP's URI field provides the resource context 
of the request-response pair.  This directly supports the
**Identification of Resources** constraint.
- HTTP provides the Content-Type header to indicate the
media type for content-bearing messages.  This specifies the
format of _Resource Representations_, enabling **Manipulation
of Resources through Representations**.  It is also part
of supporting **Self-descriptive Messages**.

In addition to standardized HTTP semantics, messages bind
semantics from the resource, via URI, and 
representations, based on the content type.  

Links also provide semantics; they indicate what can be done 
with a resource. According to the core HTTP specifications, 
these are provided in content.  They may also be provided
in a _Link_ header, provided in a standards-track IETF document.
Through links, HTTP supports the **Hypermedia** constraint.

While HTTP does not have specific support for 
**Code On Demand**, solutions using HTTP may support
late feature binding and server-facilitated processing
by supporting server-provided code-based content.
Through this method, HTTP-baed solutions can support 
arbitrary semantics.

### Semantics and Public Standards

Public standards bodies supplement REST by 
creating concrete specifications for a wide variety of
concerns that, for REST, an architectural style, are
out of scope.  For designing Web APIs and resources,
familiarity with the available public standards is
paramount.  Most of the time, it is a bad idea to
reinvent something that public standards bodies have
addressed.

It is worth noting that while REST has an 
important role in constraining semantics,
public standards that provide semantics do not
always require HTTP or a REST solution.
For example, the URI "mailto:bob@example.com" and
the features inherent to "image/png" content
can exist outside the context of the web.  Thus,
the available standards can help inform REST
solutions, but their use is not what makes
a REST solution.

#### Public Sources for Client Competency

Standards bodies are typically private organizations,
often funded by industry participants or governments,
to advance the state of a particular topic or concern.
The use of standards from these organizations is
generally not a legal requirement, but their 
adoption often improves interoperability.

For the Web, the most important contributing
standards bodies are:
- The **Internet Engineering Task Force** (IETF): 
The IETF provides the standards for HTTP syntax
and semantics, a vast collection of supporting
standards, and provides formal IANA membership
registration.  While the IETF focuses on 
the Internet's infrastructure- and protocol-level
concerns.
- The **World Wide Web Consortium** (W3C): The
W3C provides application-level standards,
including many of the Web's core content
formats.
- **Internet Assigned Numbers Authority** (IANA):
Coordinates DNS, IP, and protocol assignments.
For REST Web Services, its often-overlooked
[protocol registries](https://www.iana.org/protocols)
provide the most concentrated reference for
public Web semantics.

There are quite a few additional sources:
- **OpenID Foundation** (OIDF): Provides 
standards user authorization and trust.
- **Web Hypertext Application Technology Working Group** (WHATWG)
- **Organization for the Advancement of Structured Information Standards** (OASIS)
- **International Standards Organization** (ISO)

#### IANA's Special Role for Client Competency

Unlike other sources, IANA's role providing
public registries makes it the de facto
authority for public standards.  Its registries
provide a starting point for discovering the 
available options for publicly-available semantics.

The **[Media Types Registry](https://www.iana.org/assignments/media-types/media-types.xhtml)**
provides the publicly-registered media types.
Media types registered through the IETF may
be _standards track_ formats.  For REST on 
the Web, these are crucial, since they
provide an objective source for client
competency regarding media types, supporting
the **Self-descriptive Messages** constraint. 

The **[Link Relation Types Registry](https://www.iana.org/assignments/link-relations/link-relations.xhtml)**
provides the registered _link relations_.
This registry and [RFC 8288: Web Linking](https://datatracker.ietf.org/doc/html/rfc8288) 
provide an objective source for what a
link _means_ to a given resource or context.
By having links and meaning, a REST client
can support browser- and user-directed
resource interactions.  REST's **Hypermedia**
constraint depends on this functionality.

IANA provides many more, including:
- [HTTP Methods](https://www.iana.org/assignments/http-methods/http-methods.xhtml)
- [HTTP Headers](https://www.iana.org/assignments/http-fields/http-fields.xhtml)
- [HTTP Status Codes](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml)
- [HTTP Cache Directives](https://www.iana.org/assignments/http-cache-directives/http-cache-directives.xhtml)
- OAuth parameters, JSON Web Token fields, URI Schemes, etc.

### REST in Web Resource Design

Given all the REST support in syntax, from HTTP semantics, 
by public sources, it is easy to assume that REST is
easy, and even inevitable.  But REST only comes together
when it is applied in resource design.

REST Web Resource Design relies on understanding 

1. The nature of the resource
2. How the resource may be represented

#### What is the nature of the resource?

The resource provides semantics.  What is it?  _What is the resource?_

In design, resource definition can be difficult.  But
it is mandatory.  How can one go on to represent
a thing if one does not know what the thing is?


Fortunately and unfortunately, the question is 
rather open-ended:

- Is it a mouse?  A published work?  An event 
from the past?
- Is it the inventory of a warehouse?  A
planet?  A cake recipe?
- Is it a collection of similar things?  What 
about a member in that collection?

- What do we know about the thing?  Are there
many things like it that are similar?  What
are the common attributes of things like it?  
- What can be done with the thing?  What
can it do?

There are methods to help produce answers.  
Some use Unified Modeling Language (UML) and
class diagrams.  The [IANA Link Relations Registry](https://www.iana.org/assignments/link-relations/link-relations.xhtml)
may be helpful when trying to understand 
relationships between one resource and another.

The crucial point of understanding the
resource is that it is a source of
semantics.  Interactions with a 
Web Resource will be informed by the
nature of that resource.

#### How will the resource be represented?

In addition to understanding the nature of 
the resource, the design process must
determine the ways by which its state
may be conveyed.  The representation will
be in a digital, serialized format.  It
will need a media type that will be
recognized by its intended processors, 
most importantly, the _client_ and _server_. For example, a parrot may
be represented in an HTML page, a JSON
object, a PNG image, or a number of
other formats.  

Through content negotiation, the same
resource may be represented multiple ways.
Merely by asking, the client may indicate
that HTML, an image, or a JSON object are
acceptable, and the server may determine
which to offer.  The fact that the 
formats are categorically different may
not be a problem for the client, 
depending on what it is doing.  In
Web Design, these options open up
a world of opportunity.

Just as with resources, media types provide
semantics.  While a picture may be 
displayed, stretched, scaled, analyzed, 
and altered, a structured data format, 
such as JSON, can be understood to 
provide specific, unambiguous information
about a thing.  Likewise, HTML can be
rendered into a user interface and provide
interactability.

#### Semantic Resource Design

REST resource design requires that the
constraints be met. Let's assuming that
we understand the nature of the resource
and its representations.  In addition,
let's assume that we understand other
related resources and their 
representations.

**Resource Identification**: 
Do the resources have assigned URIs or URI 
patterns?

**Manipulation of Resources through Representations**: 
For each resource interaction or manipulation, have we
identified the method, URI, and media type to use
patterns?  ARe they consistent with the semantics of
HTTP, the resource, and the representation?

**Self-descriptive Messages**:
Does the message provide enough information for 
the intended processors to understand them?

Message self-description cannot rely on the 
method or URI to provide the 
nature of the resource.  To do so
would require message processors to have had
out-of-channel knowledge of the resources and
their addresses.  This would be a sign of
_tight coupling_, an architecture pattern
that REST aims to avoid. For the client, nature of the resource
must be understood through its media type and
the options provided through hypermedia.

In the case of markup, stylesheets, code, and
common multimedia, the public formats provide
sufficient semantics to enable browsers to 
use them.  However, media types for structured 
data formats, such as JSON and XML, do not
provide more semantics than what is required
for simple validation of well-formedness.
For web resource designers using these
formats, the use of named formats with 
structured syntax suffixes 
(per [RFC6839](https://datatracker.ietf.org/doc/html/rfc6839))
are a good way to improve message self-description,
providing its tradeoffs are acceptable.

Web APIs that neglect providing sufficient
message self-description may be 
resource-oriented without supporting REST.
This primer offers the term 
**Resource-Oriented Service Integration**, 
or **ROSI**,
as an alternative to REST, to describe these
types of APIs. 

**Hypermedia**:
Does the resource design account for the relationships
between one resource and those to which it is related?
Will representations of the resource include links
that enable the client to self-direct interactions?
Will the links indicate the type, format, language,
and related information necessary to facilitate 
informed self-direction?

Browser-based solutions typically account for linking.
However, like self-descriptive messaging, API-centric
solutions often neglect 
hypermedia.  The term
**Resource-Oriented Service Integration**,
or **ROSI** may be better for describing these.

**Client-Server** and **Stateless**:
REST solutions should avoid state sharing
and separate client and server concerns to
the extent that they remain independently
evolvable and operationally independent.

Does the resource design intermingle 
client and server state or draw on 
knowledge not available in the message or
in the defined client competencies?  If so
these issues should be addressed for the
solution to respect REST and preserve the
benefits it provides.

**Code On Demand**:
Code on Demand is common in browsers, but less
so for Web API clients.  The potential to
introduce security issues makes introduction
arbitrary code a daunting prospect in API
clients.  Where these concerns can be managed
Code on Demand offers a client an ability to
understand new media types, address issues
related to versioning, and correct
implementation problems after a client has
shipped.

Outside of using an off-the-shelf browser,
supporting code on demand requires
significantly more up front planning
and management.

**Caching**: 
Does the design define the nature of the
resource and use representations to 
reflect and manipulate its state?

Does the design intend to indicate
cachability and the associated response
headers?  Will it respect and respond
to cache-enabling request headers?

**Layered System**:
The **Layered System** 
constraint requires that resource design
will avoid incorporating prior or
runtime knowledge of intermediate 
message processors.


## Concepts And Takeaways

### Resource-Orientation

Fielding was focused on enabling what he called a "distributed 
hypermedia system," the browseable web. REST's viability as a 
foundation for API integrations was a byproduct of it being
a good architecture style for arbitrary resource 
interactions.  But Fielding was keenly aware of the crucial
of the significance of _resource orientation_.  According to
Fielding, "The key abstraction of information in REST is a 
resource."

### Message Self-Description

### Public vs Scoped Semantics





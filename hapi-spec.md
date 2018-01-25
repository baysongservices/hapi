Hypermedia Web API - hAPI


Abstract

The Hypermedia Web API (hAPI) specification defines strict Hyper Text Transfer Protocol (HTTP) behavior profiles to support the creation of lightweight generic hypermedia driven API clients.  This document provides an overview of interaction constraints for hypermedia aware clients to support unbound service discovery, and eliminate service related a priori knowledge requirements.  This document defines the Goals header, and the Application Level Profile Semantics (ALPS) protocol binding format.


Status of This Memo

UPDATE FOR SUBMISSION
This is a proposal, IEFT and W3C know nothing about it.. YET!

Copyright Notice

Copyright (c) 2017 Baysong Services LLC, and the persons identified as the document authors.  All rights reserved.

Table of Contents

UPDATE FOR SUBMISSION

1. Introduction

The proliferation of unique custom web apis of many different types burdens service providers, integrators, and consumers with unnecessary work to support the nearly boundless supply of custom formats and types.  Utilizing the HTTP protocol as a tunnel, these services fail to leverage many of the protocols native functionalities and properties thereby creating redundant custom solutions for protocol solved issues.

Building upon the single most successful API model of HTTP with HTML, this specification intends to craft strong behavior profiles for HTTP services in order to facilitate the proliferation of generic clients of various hypermedia formats.  Since the internet boom of the late ninties, the general trend of API design has drifted towards completely dynamic client server interaction, and slowly been pulled back towards statically bound clients and servers.  Positional and large batch integration services were replaced with more dynamic plain XML services.  Plain XML services were replaced by tightly bound and coupled SOAP.  SOAP services were replaced by ReST-ish crud web services.  ReST-ish crud web services are now being actively challenged by statically bound technologies like OAS (Swagger) and gRPC.  The trend is cyclical and clear, without a strong standard for dynamically bound  services, the ease of initial development and conceptual understanding of statically typed interfaces will continue the broad proliferation of statically bound clients. Proponents of the semantic web argue their proposed global models offer the best solution for removing the barrier of custom model and interface definitions.  While this may be true in an academic sense, the distribution of computing power, design of current networking protocols, difficulty of creating perfect enduring ontologies, and the limitations of networking infrastructure lead one to conclude the solution could be decades away. Current systems and infrastructure simply can not handle the infinite combinations of the semantic web style tools like RDF.

This specification creates a method for creating static http behavioral profiles with a reference behavior profile which used in conjunction with a Application Level Profile Semantics (ALPS) profile and HTTP Protocol binding will provide a strong bounded context for dynamic client server binding.

2. hAPI Behavioral Profiles

The HTTP specification creates a protocol with an eye to fault tolerance, flexibility, and lenient server restrictions.  This has proven to be a primary cause for the success of the proliferation of distributed computing into nearly every facet of business and everyday life.  However, with the maturation of the protocol, and the ubiquity of deployment and continuous deployment it is critical to begin to form more strict standards around certain uses of the protocol to continue progress in reducing redundant work when undefined de-facto standards exist. Modern service design and deployment trends have largely contributed to changing the standard deployment paradigm from static application servers to included self contained dynamic embedded artifacts.  The self contained design paradigm has established the precedent of abstracting many application deployment details, and allowing framework providers to create implicit but opaque opinionated default behavior standards for web applications. With an established precedent for centralized design and application behavior, the opportunity to further develop and reveal these implicit standards constitutes a generational leap in service orchestration. Concurrent progress in development of dynamic application profile descriptions, formalized service contracts and vocabularies, and establishment of lightweight hypermedia formats have supplied nearly all the conditions necessary for the proliferation of generic hypermedia clients over HTTP.  This document provides the final conditions to allow dynamically bound generic hypermedia clients to interoperate with remote services with no a priori knowledge beyond which is required or defined by this specification.

2.1 HTTP Behavioral Profile

DEFINE THE FORMAT OF A PROFILE,

2.2 hAPI Profile Header

DEFINE THE "hapi-profile" header

Hapi services which make use of the HTTP protocol, will announce this via the Hapi-profile header.  Consumer agents will use this discovered information along with the relevant Application Profiles to dynamically understand the range of potential interactions the service MAY support and provide.  It is important for consumer agents to carefully control the cached values for these properties to allow easy discovery.  Any conflicts SHOULD result in the client querying for new Hapi-profile or Application Profile representations.  Consumers should not view this as a guaranteed contract, as the internal state of the server and the home document should be used to discover the current state of available resources to the consumer.

The Hapi-profile header should contain a valid and dereferenceable URL which represents a binding of ALPS semantics to the desired behavioral profile of the Hapi server, as well as any globalized HTTP protocol behaviors the designer may wish to provide.

3 Application Profile

DEFINE THE USE OF PROFILES - Should this be restricted to ALPS profiles specifically, or should it be open to formats which provide a certain minimum amount of detail for the semantics?  The alps profile is likely the ontology, so would other ontology formats be feasible?

The Application Profile provides the protocol agnostic resource and affordance description to convey interaction context to both machine and human clients.  Unlike other efforts in semantically driven service interaction and design, the goal of this profile is to consolidate the description of this service for all consumers to facilitate the creation of lightweight generic clients.  This application profile is referred to as the vocabulary, and can be self contained or an aggregate.  The Application Profile format MUST support the following constraints.

  * Protocol Agnostic
  * Semantically Complete
  * Unambiguously Resolvable
  * Supports Deprecation
  * Extensible
  * Self Documenting
  * Composable
  * Defines Generic Action Properties

3.1 Application-Level Profile Semantics

The Application-Level Profile Semantics (ALPS) is the reference format for defining and exposing the Application Profile, or vocabulary.  This format supports all of the required features, and allows the consumer agent the ability to dynamically discover all necessary resource and message structure information without coupling the consumer agent to any protocol constraint.  An example of this agnosticism over the HTTP protocol would be the resource type `foo` described in the ALPS vocabulary document being available at the path `http://example.org/bar` or `http://example.org/asdf123xyz`, with no impact on the functionality of the consumer agent.  This lack of impact is important as it provides the lose coupling necessary to support a truly ReSTful hAPI service.

The protocol agnosticism is important in the minimal case of dual support of HTTP1.2 and HTTP/2, but can be equally useful if used to expose the vocabulary over alternate protocols such as gRPC or WebSockets.  Therefore the agnosticism allows the vocabulary of resources and affordances to be defined independent of protocol details which are technically necessary, but needlessly coupled to the technical implementation details.

4 Semantic Protocol Binding

DEFINE THE PROTOCOL BINDING - Should this be ALPS specific, or are we going to support larger domains of profiles in order to increase the adoptability of this standard over http, or other protocols.

The semantic-protocol binding is used to couple the independently defined vocabulary to the protocol or protocols a service uses for transmission.  For example using HTTP as the protocol if an ALPS profile defines a resource affordance as SAFE and IDEMPOTENT, this method could be bound to a GET request.  Using the same preconditions, an UNSAFE and IDEMPOTENT request could be bound to a DELETE request.  There is no need for the vocabulary to define all protocol level capabilities as these allow messages to transact more naturally or efficiently.  The HTTP request types OPTIONS and HEAD are examples of protocol level request types which offer HTTP clients useful optimizations, which have no equivalent representation outside of the HTTP protocol.  The protocol binding is therefor used both to bind the abstract vocabulary to the protocol, as well as to broadcast specific protocol capabilities which may interest the client of that protocol only.

4.1 Hapi-profile Header

Hapi services which make use of the HTTP protocol, will announce this via the Hapi-profile header.  Consumer agents will use this discovered information along with the relevant Application Profiles to dynamically understand the range of potential interactions the service MAY support and provide.  It is important for consumer agents to carefully control the cached values for these properties to allow easy discovery.  Any conflicts SHOULD result in the client querying for new Hapi-profile or Application Profile representations.  Consumers should not view this as a guaranteed contract, as the internal state of the server and the home document should be used to discover the current state of available resources to the consumer.

The Hapi-profile header should contain a valid and dereferenceable URL which represents a binding of ALPS semantics to the desired behavioral profile of the Hapi server, as well as any globalized HTTP protocol behaviors the designer may wish to provide.

5 Goal Header

This specification defines the HTTP header "goals".

A Representation State Transfer architectural style (ReST) has many constraints in order to realize the intended properties of scalability, discoverability, and evolvability among others.  Of the primary listed constraints Stateless Interaction and Hypermedia as the Engine for Application State (HATEOAS) pose particular difficulty for implementation when coupled together.  It is difficult to design complex systems which are stateless and do not require previous knowledge of domain semantics or internal implementation details while allowing them to discover future capabilities with any sort of guaranteed outcome.  This difficulty often results in many systems implementing less than optimal trade-offs and failing to acheive the properties of a ReSTful achitecture.  The resulting difficulties creates a value based dissonance where the requirements of the intended purpose of the system is lost in the management of more technical concerns.  In order to prevent this loss of focus on the intended outcomes, the system can make use of a domain defined, service supported, and user provided goal header.  This header is declared as a domain based task which may require more than one interactions with the service in order to fullfil its stated goals.  The goals are then defined by a simple state machine which is defined by the set of interactions with the service as the states, and the relevant affordances as the edges.  This arrangement of responsibility is critical, as it preserves the statelessness of the server interaction to reduce overhead while still allowing the user interaction to be orchestrated with result based interaction in mind.

Similar in behavior to the Prefer header, with one critical difference, the Goals header is sent as a request header to a server as an item of content negotiation.  If the server acknowledges and supports the use of the Goals header, the resulting hypermedia controls will be shaped to match the current position within the state machine by providing the subset of hypermedia controls which conforms to the edges on the current state.  Use of the Goals header will invalidate the use of cache control on the resource request as this is a means for altering the resource representation returned by the service.  However, the use of Location and ETag headers for the resulting representations is possible if the action was to invalidate the previous ETag headers, or to allow the user to cache a reference to the current ETag of the resource.

6 IANA Considerations

6.1 Header Field Registration

HTTP header fields are registered within the "Message Headers" registry maintained at <http://www.iana.org/assignments/message-headers/>.

This document defines the following HTTP header fields, so the "Permanent Message Header Field Names" registry has been updated accordingly (see [BCP90]).

+-------------------+----------+--------------+---------------+
| Header Field Name | Protocol | Status       | Reference     |
+-------------------+----------+--------------+---------------+
| Goal              | http     | expirimental | Section 5     |
| Hapi-profile      | http     | expirimental | Section 5.1   |
+-------------------+----------+--------------+---------------+

6.2 Internet Media Type Registration

IANA maintains the registry of Internet media types [BCP13] at <http://www.iana.org/assignments/media-types>.

This document serves as the specification for the Internet media types "message/hapi-profile" and "application/hapi-profile".  The following has been registered with IANA.

6.2.1 Internet Media Type message/hapi-profile

DEFINE THE FORMAT OF HAPI-PROFILE

6.2.2 Internet Media Type application/hapi-profile

DEFINE THE FORMAT OF HAPI-PROFILE

7 Security Considerations

DEFINE SECURITY CONSIDERATIONS

8 Acknowledgements

DEFINE ACKNOWLEDGEMENTS

9 References

DEFINE REFERENCES - boil this down go back through all the links and videos

NORMATIVE AND INFORMATIVE REFERENCES

Appendicies

Add any which need adding.

Index

Add index of terms.. use affordances, goals.. profiles.. etc.. etc..

Authors' Addresses

Michael Hibay
Baysong Services
Email: michael.hibay@baysong.com
URI: https://blog.michaelhibay.com
GitHub: https://github.com/hibaymj

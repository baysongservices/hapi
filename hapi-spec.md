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

The HTTP specification creates a protocol with an eye to fault tolerance, flexibility, and lenient server restrictions.  This has proven to be a primary cause for the success of the proliferation of distributed computing into nearly every facet of business and everyday life.  However, with the maturation of the protocol, and the ubiquity of deployment and continued deployment it is critical to begin to form more strict standards around certain aspects of the protocol to continue progress in reducing redundant work when de-facto if undefined standards exist. Modern service design and deployment trends havechanged the deployment paradigm from solely static application servers to included self contained embedded artifacts.  The self contained artifact design paradigm has established the precedent of abstracting many application deployment details, and allowing framework providers to create implicit opinionated default behavior standards for web applications. With an established precedent for centralized design and application behavior, the opportunity to further develop these implicit standards for a generational leap in service orchestration has arisen. Concurrent progress in development of dynamic application profile descriptions and establishment of lightweight hypermedia formats has supplied nearly all the conditions necessary for the proliferation of generic hypermedia clients.  This document provides the final conditions to allow dynamically bound generic hypermedia clients to interoperate with remote services with no a priori knowledge beyond which is required or defined by this specification.

2.1 HTTP Behavioral Profile

DEFINE THE FORMAT OF A PROFILE,

2.2 hAPI Profile Header

DEFINE THE "hapi-profile" header

3 ALPS Profile

DEFINE THE USE OF PROFILES - Should this be restricted to ALPS profiles specifically, or should it be open to formats which provide a certain minimum amount of detail for the semantics?  The alps profile is likely the ontology, so would other ontology formats be feasible?

4 Semantic Protocol Binding

DEFINE THE PROTOCOL BINDING - Should this be ALPS specific, or are we going to support larger domains of profiles in order to increase the adoptability of this standard over http, or other protocols..

5 Goals Header

This specification defines the HTTP header "goals".

6 IANA Considerations

6.1 Header Field Registration

HTTP header fields are registered within the "Message Headers" registry maintained at <http://www.iana.org/assignments/message-headers/>.

This document defines the following HTTP header fields, so the "Permanent Message Header Field Names" registry has been updated accordingly (see [BCP90]).

+-------------------+----------+--------------+---------------+
| Header Field Name | Protocol | Status       | Reference     |
+-------------------+----------+--------------+---------------+
| Goal              | http     | expirimental | Section 2.2   |
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

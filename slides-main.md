### SATOSA &mdash; Current status

* Proxy for translating between authentication protocols
* Current support for SAML2, OIDC and OAuth2
* Utilizes most of IdentityPython projects
* Designed to be very flexible and configurable


notes:

- SATOSA is a proxy for translating between different authentication protocols
- It currently supports SAML2, OpenID Connect and OAuth2
- It can do SAML2<->SAML2 / SAML2<->OIDC / SAML2<->Social-logins (OAuth2)

- To make this happen, we have defined three types of plugins
- The first set we call _frontends_ and those present an IdP/OP interface to
  the world and converts the externally connecting protocol to an internal
  representation
- The second set we call _micro-services_, before they were what we currently
  mean by that term). Those allow users to plug in their own code and modify
  the internal representation of that data.
- The third set we call _backends_ and those present an SP/RP interface to the
  world and converts the externally connecting protocol to an internal
  representation
- You can guess now, that we have frontends and backend for SAML (built with
  pysaml2) and OIDC (built with pyop)

- use cases:
  - Protocol conversion
  - Policy enforcement (InAcademia)
  - "Social" ID proxy (IdHub)
  - Make a non-conformant SP/IdP, SAML-compatible
  - Proxy an SP to many SAML IdPs and provide interface to IdP-discovery
  - Collaboration Management: Manage federated identities with
    customizing options, policies and custom attributes
  - Single point of trust

---

### SATOSA &mdash; Future plans

- Support more protocols
  - OIDC Federations
- Improve plugins interface
- Non-stop work on the internals
  - protocol translation
  - policies
- Analytics


notes:

- we are planning to support more protocols
  - starting with OIDC Federations
    by integrating the oidcendpoint library
  - and then there are also ideas about WebAuthn
    - the new Web Authentication standardized by a W3C Specification

- we are reworking the plugins interface
- we have observed certain patterns in the micro-services that users implement
- this hints that some of the things should be supported directly by the proxy
- or, that the proxy should provide mechanisms to support these functionalities

- part of this is a rules engine that we're building
- and adding support for async interfaces

- we are always -continuously- working on the internals of the proxy
- to reduce complexity and make it easier for users and contributors to add
  more features, plugins and protocol adapters
  - we are switching to a declarative approach on the way we translate between
    protocols and how we define policies

- Analytics / Monitoring / Health status

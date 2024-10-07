---
description: Defines terms used in Origin documentation.
---

# Glossary

_Note: Mostly, this terminology is specific to the Origin platform. Theoretical and formally standardized cryptographic and cybersecurity terms are introduced only lightly. For more details about those concepts, see the_ [_KERI ecosystem_](https://keri.one)_'s_ [_KERISSE website_](https://kerisse.org)_,_ [_GLEIF_](https://gleif.org)_'s_ [_vLEI Governance Framework_](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework)_, the_ [_Trust Over IP Glossary_](https://trustoverip.github.io/toip/glossary)_,_ [_Hyperledger Aries RFCs_](https://github.com/hyperledger/aries-rfcs/blob/main/index.md)_, and W3C's_ [_Verifiable Credentials Data Model_](https://www.w3.org/TR/vc-data-model/) _and_ [_Decentralized Identifiers (DIDs)_](https://www.w3.org/TR/did-core/)_._

### AID

A self-certifying identifier which cryptographically binds an identifier to a public and private key pair. It is an identifier that can be proven to be the one and only identifier tied to a public key using cryptography alone. A vLEI formally references its issuee by the issuee's AID.

### client

An org that operates on the Origin platform to create, manage, and use its digital identity. Contrast [service provider](glossary.md#service-provider).&#x20;

### CSP (communications service provider)

A [service provider](glossary.md#service-provider) that provides telecom services such as A2P messaging or VOIP, and that uses Origin to help [clients](glossary.md#client) make their traffic verifiable.&#x20;

### DAR (designated authorized representative)

A formally defined role in the [vLEI Governance Framework](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework). A DAR represents a client during [vLEI](glossary.md#vlei) issuance. They designate [LARs](glossary.md#lar-legal-entity-authorized-representative), formally commit their org to governance rules, and establish a contractual relationship between their org and a [QVI](glossary.md#qvi-qualified-vlei-issuer).

### digital credential

A small, digitally signed file that provides evidence that the holder is entitled to a privilege. X509 certificates and SSH keys are familiar but old examples. A second generation of digital credentials solves some centralization and maintenance problems and has come of age in the past decade. It is associated with AnonCreds, the ISO mobile driver's license spec, and W3C verifiable credential spec. Origin can help support these technologies. However, the focus of Origin is a third generation of digital credentials called ACDCs. These offer dramatically improvements in security and efficiency. [vLEIs](glossary.md#vlei) are an example of a ACDC-based credential supported by Origin.

### facilitator

A [service provider](glossary.md#service-provider) that helps a [client ](glossary.md#client)build the foundation of their digital identity. Typically a client contracts with a facilitator; the facilitator then vets the org and its staff, issues important credentials, and provides training and support. Origin may be the delivery channel for only a subset of these things. A client may interact with other service providers, but its relationship is typically mediated by its facilitator, at least at first. [QVIs](glossary.md#qvi-qualified-vlei-issuer) are often facilitators because [vLEIs](glossary.md#vlei) are foundational to the digital identity strategy of many orgs. See [Origin for Service Providers](perspectives/sps/) > [Facilitating](perspectives/sps/#facilitating) for details.

### LAR (legal entity authorized representative)

A formally defined role in the [vLEI Governance Framework](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework). They are a member of a committee that uses cryptographic keys to jointly manage their org's identity by providing formal approvals of all operations that the org performs directly. They also delegate, so other representatives of the org can function autonomously.

### QVI (qualified vLEI issuer)

A [service provider](glossary.md#service-provider) accredited by GLEIF to issue vLEIs to [client](glossary.md#client) orgs. See the [vLEI Governance Framework](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework) for details.

### service provider

An org that operates on the Origin platform to deliver services consumed by [clients](glossary.md#client). Two examples of a service provider are a [QVI ](glossary.md#qvi-qualified-vlei-issuer)and a [CSP](glossary.md#csp-communications-service-provider).

### vLEI

A category of [digital credential](glossary.md#digital-credential) that was designed by [GLEIF ](https://gleif.org)to embody extremely high assurance of identity for organizations and the people who represent them. There are multiple subtypes of vLEI, including one that certifies a [QVI ](glossary.md#qvi-qualified-vlei-issuer)(QVI vLEI), one that identifies legal entities (LE vLEI), one that identifies officers of an organization with legally recognized roles (OOR vLEI), and one that identifies staff of an organization with arbitrary job titles (ECR vLEI). See the [vLEI Governance Framework](https://www.gleif.org/en/vlei/introducing-the-vlei-ecosystem-governance-framework) for details.

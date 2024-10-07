---
description: what it means to "sign with" a vLEI
---

# Sign with a vLEI

In casual speech, we sometimes say that an organization or a person can "sign with" a [vLEI](../concepts/creds/vleis/). We need to define this behavior carefully.

The party that receives a vLEI is called its _issuee_. For LE vLEIs, the issuee is the legal entity (an organization). For OOR and ECR vLEIs, the issuee is an individual who has a specific role at the organization. A vLEI formally references its issuee by their [AID](../../glossary.md#aid) (a long, hard-to-remember string -- something like`EBMYrQqWyRLAYqMLYv_qm-qP7eKN81Wmjyz5nXQvYLY`).

The AID of the issuee can be used to look up a cryptographic [public key](https://en.wikipedia.org/wiki/Public-key\_cryptography) controlled by the issuee. The corresponding private key is a secret known only to the issuee. The issuee can use the private key to create digital signatures, and anybody in the world can use the public key to check those signatures. This is how an issuee proves they control the vLEI.

But how does an issue prove, with their vLEI, that they signed a PDF, a social media post, or some other kind of content? There are two approaches:

1. **Simple mode**: the issuee can use the same key pair that's resolvable from their vLEI to create ordinary digital signatures. For example, [this blog post](https://www.agwa.name/blog/post/ssh\_signatures) explains how to sign arbitrary content (files, messages, etc.) with SSH keys. The key pair held by a vLEI issuee can be used with SSH, and can therefore be used to create digital signatures exactly as this article describes. Since the keys used in these ordinary signatures are bound to the vLEI, the reputation of the vLEI is implicitly associated with such ordinary digital signatures.
2. **Chained mode**: the issuee can create (meaning, sign) new ACDCs (typically but not always, credentials) that explicitly reference their vLEI. For example, a company could issue an Employee of the Month credential that contains a reference to the company's LE vLEI.

Each mode has pros and cons.

## Simple mode

Simple mode requires no new technology. Anywhere that Ed25519 key pairs can sign something today, with non-vLEI technology, the key pairs of vLEI issuees can be used as the input. No modifications are needed to software, documentation, or human or automated processes on the signing side. On the verification side, standard signature verification will also work without modifications. However, if the verifier wants to consider the vLEI reputation when verifying, the vLEI or at least the AID of the signer must be communicated out of band.

Simple mode is fragile in the face of key rotation or revocation. The keys bound to a vLEI can change over time. Verifiers with no knowledge of AIDs and their resolution algorithm could make bad judgments about whether a signature is truly bound to a vLEI, in a given time context.

Simple mode hides sophisticated multisig relationships; depending on how the issuee is configured, this may or may not create a false sense of security.

## Chained mode

Chained mode is powerful, flexible, and robust under maintenance. However, it requires the signer and the verifier to do something more sophisticated.

By default, KERI technology will detect and validate chained relationships in data. This means that if an issuee presents ACDC _N_ in a chain from 1 to _N_ of ACDCs or credentials, and any item in the chain prior to N is revoked or fails a signature integrity check, _N_ is deemed invalid. However, this is not enough. Both the issuee and the verifier must must evaluate whether the data in items 1.._N_-1 satisfy their trust requirements with respect to business rules. For example, a diploma issued by Faber College may have a valid signature, and may chain back to a credential of accreditation for Faber College that is unrevoked and correctly signed. However, only the issuee can decide if they are willing to use Faber College's accreditation credential as upstream evidence of the quality of their education, and only the verifier can decide if they consider the signer of that accreditation credential to be reputable enough to accept the diploma.

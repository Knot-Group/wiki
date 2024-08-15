# Attestations (verifiable claims)

Attestations are verifiable claims which consist of a statement and a cryptographic proof of that statement. Examples include biometric passports which are cryptographically signed by the issuing government, emails with DKIM signatures by the sending server, claims of group membership with accompanying Merkle inclusion proofs, and computation outputs with accompanying zero-knowledge proofs.

Attestations can be claims about:
- *identity*, such as birthdate or citizenship, attested by signed government-issued ID
- *social facts*, such as group membership attested a Merkle proof of inclusion, or network connections attested by signed claims from members of the network
- *ownership*, such possession of an NFT (attested on-chain) or a house (attested by a digitally signed PDF)
- *historical activity*

The main challenges with attestations are:
- How to *produce* new attestations permissionlessly. For example, ZK Email can be used to produce an attestation to ownership of a specific social media handle.
- How to *consume* attestations permissionlessly. For example, an application requiring a user to be over 18 must verify the attestation before trusting the claim.
- How to *transform* existing attestations into a more usable or redacted form. For example, an application requiring users to be over 18 should not need to read and verify a signed biometric passport.
- How to *compose* multiple attestations together into a single attestation that meets the requirements of an application. For example, an application may require membership in a specific group in addition to the over 18 age requirement, and these requirements should still be attested in a single proof.
- How to make them *portable* across systems, platforms, networks, and computing environments

There is currently no generic widely-used framework for how attestations are produced, consumed, transformed, or composed. The closest existing solution is possibly the Proof-Carrying Data SDK, which can be used by any third-party as long as it provides a zkSNARK circuit for querying about its set of requirements.

## Producing attestations

Attestations can be created in two ways:
1. A trusted source issues a new attestation, for example by cryptographically signing a claim, performing a verifiable computation (e.g. zk proof) that does not require verifiable inputs, or adding a person to a private membership group and issuing an inclusion proof. Sources of attestations can be anything from a government (electronic ID) to an individual to a device. We call attestations that rely directly on a trusted source ["base" attestations](./sources.md).
2. A new attestation can also be created by [transforming an existing attestation](#transforming-attestations), for example by redacting or processing the original claim.

## Consuming attestations

Applications consume attestations by verifying the associated cryptographic proof and then taking action based on the claim.

Consuming attestations is simple in the case of a single specific claim, but the question of how to consume attestations becomes more complex when thinking about a framework for composing attestations while maintaining portability across many systems and environments.

## Transforming attestations

Attestations can be transformed by first consuming the attestation and then producing a new one using its claims, which can be done using zero-knowledge proofs.

Given a base attestation, the general transformation process is to verify the cryptographic proof of the base attestation (consume the attestation) and then compute the transformed claim from the base claim inside a zk circuit.

For example, ZK Email transforms (signed) emails into attestations to more specific claims that are contained in those emails by first verifying the email's DKIM signature, then proving that the transformed claim is contained in the email body and that the hashed email body is the same as the hash in the signed email header.

## Composing attestations

There is no framework that we know of for composing attestations, so this can only be done by writing custom solutions. For example, a single user could combine multiple attestations using recurive zk proof composition.  In theory, collaborative SNARKs could be used to combine attestations from multiple parties.

## Portability

Because there is no well-defined framework for issuing, consuming, and manipulating attestations, they are not easily portable, and incorporating attestations into an application currently requires custom solutions, although the [tools listed below](#tools-for-transforming--creating-attestations) reduce this workload in many cases.

## References

- ["Stuff with Signatures"](https://github.com/cursive-team/stuff-with-signatures?tab=readme-ov-file) by the Cursive Team
- ["Thinking about Attestations"](https://zkresear.ch/t/thinking-about-attestations/75) by gubsheep
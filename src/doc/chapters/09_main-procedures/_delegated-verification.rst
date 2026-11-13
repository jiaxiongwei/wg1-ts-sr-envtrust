Delegated verification
----------------------

In resource-constrained deployments where relying parties lack policy engines or PKI trust anchors, delegated verification is supported through a Trusted Verifier Service (TVS):

a) The relying party sends the attestation token to a designated TVS.

b) The TVS performs full signature, chain and policy verification in accordance with Clause 9.5.

c) The TVS issues a signed Verifier Result Token, such as an OAuth/OIDC claim or short-lived assertion token, back to the relying party to convey the trust decision.

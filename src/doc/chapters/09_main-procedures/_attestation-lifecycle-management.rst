Attestation lifecycle management
--------------------------------

Environment attestation credentials and keys are managed throughout their lifecycle:

a) Key provisioning: Attestation keys are generated on-device within a secure enclave or injected during secure manufacturing.

b) Evidence refresh: Attestation evidence is regenerated periodically or when state transitions trigger it.

c) Revocation handling: The verifier checks Certificate Revocation Lists (CRLs) or queries Online Certificate Status Protocol (OCSP) responders to confirm that attestation keys or platform identities remain valid and unrevoked.

d) Termination: Upon platform decommissioning or container termination, associated attestation credentials and private keys are zeroised.

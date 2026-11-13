Attestation exchange
--------------------

The inter-agent attestation exchange protocol defines how AI agents request, send and verify environment attestations, supporting four modes:

a)Push mode: the attester AI agent attaches its attestation to the collaboration request for initial trust establishment, periodic attestation updates or broadcasts to multiple receivers. The attester AI agent generates the attestation and sends it with the collaboration request to the verifier. The verifier extracts and verifies the attestation, makes a trust decision and returns that decision. Both sides then continue or abort.

b)Pull mode: the verifier requests the attestation on demand for verification, audit and compliance checks, or for attesters that do not push data. The verifier sends an attestation request, the attester AI agent generates and returns the attestation, the verifier verifies it and makes a decision, and both sides continue or abort.

c)Challenge-response mode: this mode combines pull mode with anti-replay protection. The verifier generates a random nonce of at least 128 bits using a cryptographically secure RNG and places it in the request. The attester AI agent populates attestationMetadata, challengeNonce with the nonce, signs the complete measurement report containing the nonce and returns the attestation. The verifier then checks that the returned challengeNonce matches exactly and that the attestation falls within an acceptable time window. The challenge-response exchange succeeds only if both checks pass.

d) Delegated verification mode: A resource-constrained agent, such as an IoT device, sends its attestation to a trusted third-party verification service. This service runs the full verification and returns a report containing the original attestationId, the result, the verification timestamp and a third-party-signed verification assertion. The constrained agent then verifies the signature and trusts the result.

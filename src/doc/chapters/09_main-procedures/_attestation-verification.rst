Attestation verification
------------------------

To comply with REQ-VR-01 to REQ-VR-08, the verifier follows a six-step validation procedure when receiving an attestation payload:

- Step K - Schema verification: The verifier checks that the structure matches the data model, and that mandatory fields are present and well-formed.

- Step L - Signature verification: The verifier checks that the algorithm is supported, the signature covers the complete measurement report, and the signature is valid using the correct public key from a certificate chain, a trust anchor or a TEE-specific verification interface.

- Step M - Timeliness verification: The verifier checks that the current time falls between notBefore and notAfter, measurementTime is within an acceptable window, and challengeNonce matches the verifier's nonce when using challenge-response mode.

- Step N - Measurement-value verification: The verifier checks that environmentType and securityLevel use predefined acceptable values, integrity measurements match known reference values or the trust policy, and the platform identity is consistent.

- Step O - Identity-binding verification: The verifier checks that runtimeContext.agentId matches the identity the agent claims, and that the attestation binds to the correct agent instance.

- Step P - Policy evaluation: The verifier evaluates data against its trust policy, deriving the trust level from the environment type, security level and integrity measurements.

The verification outcome is exactly one of Verified when all checks pass, VerifiedWithWarnings when core checks pass with only non-critical warnings, or Failed when one or more critical checks fail.

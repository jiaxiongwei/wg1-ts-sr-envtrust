Attestation generation
----------------------

An environment attestation consists of three parts: measurement, signature and attestationMetadata.

The measurement component is a structured environment measurement report.

The signature component contains an algorithm, a value and an optional certificateChain.

- The algorithm field specifies ES256, RS256 or Ed25519.

- The value field stores a Base64 signature.

- The certificateChain field holds an optional X.509 chain.

The attestationMetadata part contains attestationId, attestationVersion, challengeNonce and verifierPublicKey.

- The attestationId field contains a unique attestation identifier.

- The attestationVersion field contains the protocol version.

- The challengeNonce field contains the nonce used in challenge-response mode.

- The verifierPublicKey field is used in challenge-response mode.

The attestation generation procedure carries out these steps:

- Step G - Serialization: the attestation module serializes the measurement report using deterministic rules and canonical JSON or CBOR, so that different platforms produce identical byte sequences.

- Step H - Signing: For a TEE environment, the attestation module uses native signing capability including SGX quoting, SEV signing or TrustZone signing, and otherwise performs software signing with the private key held in secure media including TPM or HSM.

- Step I - Signature object composition: the attestation module composes the algorithm identifier, signature value and optional certificate chain into the signature object.

- Step J - Attestation assembly: the attestation module combines the measurement, signature and metadata into the complete attestation.

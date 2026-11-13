Appendix I Use cases for trusted environment measurement and attestation
========================================================================

(This appendix is not an integral part of this Recommendation.)

Use case 1: Cross-domain agent collaboration
--------------------------------------------

Scenario: An enterprise cloud AI agent delegates an execution sub-task to a peer AI agent operating on an edge or mobile platform across distinct trust domains. The delegated workload involves sensitive operational payloads that transit public networks between the heterogeneous runtime environments.

How measurement and attestation apply: The edge agent uses environment sensing and measurement report generation modules to collect measurements across dimensions including environment type identification, security level classification, integrity measurements, platform identity, and runtime context. It formats the evidence using the environment measurement data model and transfers it using the push or challenge-response exchange mode under Clause 9.4. The verifier executes verification steps K-P while timeliness management checks measurementTime, notBefore, and notAfter parameters to mitigate measurement tampering (RSK-01), replay attacks (RSK-03), identity binding weakness (RSK-05), and cross-domain trust issues (RSK-08).

Trust decision and outcome: The dynamic trust decision module evaluates the verification result alongside graded trust decay rules under Clause 9.9. Upon obtaining a Verified outcome, the cloud agent establishes cross-domain session keys and releases the sub-task payload to the trusted edge enclave.

Benefit: This use case demonstrates how the Recommendation standardizes secure cross-domain evidence exchange (Clause 9.4) and verification (Clause 9.5) to enable multi-tenant agent task delegation without compromising runtime trust.

Use case 2: Dynamic risk-based authorization
--------------------------------------------

Scenario: An AI agent processing sensitive enterprise assets and personally identifiable information requests dynamic data access from a Policy Enforcement Point (PEP). The access privileges depend continuously on the health and posture of the host hardware platform.

How measurement and attestation apply: The PEP pulls signed attestation evidence containing the reference data model fields such as teeTechnology, integrityMeasurements, platformIdentity, and runtimeContext. Through the procedures in Clauses 9.3, 9.5, and 9.8, the verifier checks signatures and validity windows to prevent attestation forgery (RSK-02), stale or freshness verification failure (RSK-04), environment spoofing (RSK-06), and context-ignorant trust decisions (RSK-10).

Trust decision and outcome: If environment measurements deviate or exhibit temporal decay, the verifier returns a VerifiedWithWarnings or Failed result and the trust decision module returns degrade or reject. The PEP immediately restricts or revokes the agent's data access privileges based on these real-time post-verification signals.

Benefit: This use case highlights how continuous timeliness management (Clause 9.8) and dynamic trust decisions (Clause 9.9) enforce real-time, posture-aware access control for AI workloads.

Use case 3: Multi-party computation
-----------------------------------

Scenario: Independent autonomous AI agents collaborate across organizational boundaries to execute multi-party computation and joint federated model training. Each agent contributes proprietary model weights and private data inputs to the shared analytics pipeline.

How measurement and attestation apply: Peer agents conduct mutual attestation exchange via challenge-response protocols prior to initiating computation. Each node generates attestation evidence containing schemaVersion, measurementId, and extensions fields, passing them to the attestation verification module and trusted verifier service under delegated verification (Clause 9.6). This process directly mitigates denial of attestation (RSK-07), temporal decay (RSK-09), and measurement tampering (RSK-01).

Trust decision and outcome: Participating nodes evaluate mutual verification results using Clause 9.9 trust decision rules. Once all peers receive a Verified status confirming execution within genuine TEE enclaves, the multi-party computation protocol begins securely.

Benefit: This use case shows how hardware-backed measurement collection (Clause 9.2) and delegated verification (Clause 9.6) enable secure collaborative analytics across untrusted multi-party environments.

Use case 4: Audit and compliance
--------------------------------

Scenario: An organization deploying autonomous AI agents in a regulated sector requires continuous compliance tracking and lifecycle oversight. External auditors demand immutable evidence showing that all agent runtime contexts meet regulatory security standards.

How measurement and attestation apply: The agent platform continuously executes attestation lifecycle management (Clause 9.7) by refreshing evidence and archiving signed reports into the attestation store. Captured records incorporate temporalInfo, temporal validity windows, and cryptographically bound platform identities, preventing stale verification failures (RSK-04), replay attacks (RSK-03), and unrecorded posture drift.

Trust decision and outcome: The verifier continuously evaluates stored claims, logging non-repudiable audit records that reflect past and present environment integrity. Regulators verify these historical trails to confirm uninterrupted adherence to security baselines.

Benefit: This use case illustrates how the attestation store module and attestation lifecycle procedures (Clause 9.7) provide verifiable, non-repudiable audit trails for enterprise governance.

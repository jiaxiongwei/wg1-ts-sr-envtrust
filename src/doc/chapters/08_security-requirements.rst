Security requirements for trusted environment measurement and attestation
=========================================================================

This clause specifies security requirements for trusted environment measurement and attestation of AI agents. The requirements cover seven functional perspectives—the environment measurement module, the environment attestation module, the verifier, the whole service, the timeliness management module, the trust decision module and the attestation store and audit trail—to ensure end-to-end security, support operations and systematically mitigate the security risks in Clause 7.

Requirements for the environment measurement module
---------------------------------------------------

REQ-MM-01: The environment measurement module is required to collect runtime telemetry and environment measurement data in a tamper-resistant manner that prevents unauthorized modification during collection (mitigates RSK-01).

REQ-MM-02: The environment measurement module is required to structure measurement evidence using a standardized data model that contains core attributes for environment type, security level, integrity measurements, platform identity, timestamp, validity period and attestation mechanism (mitigates RSK-01, RSK-02).

REQ-MM-03: The environment measurement module is required to capture continuous or event-triggered re-measurements when detecting critical state changes, policy updates or container lifecycle transitions (mitigates RSK-02, RSK-08).

REQ-MM-04: The environment measurement module is required to establish a cryptographic binding between measurement evidence and the public identity of the hosting AI agent (mitigates RSK-05).

REQ-MM-05: The environment measurement module is required to support machine-readable data serialization formats (such as JSON or CBOR) to ensure deterministic measurement encoding across heterogeneous platforms (mitigates RSK-06).

REQ-MM-06: The environment measurement module is recommended to include human-readable representations or diagnostics alongside machine-readable claims to simplify logging and security auditing (mitigates RSK-06).

REQ-MM-07: The environment measurement module is recommended to include clear reference descriptors specifying the underlying hardware security module or TEE platform technology (mitigates RSK-01, RSK-06).

Requirements for the environment attestation module
---------------------------------------------------

REQ-AM-01: The environment attestation module is required to generate environment attestations using private keys isolated in hardware or software media, with each attestation comprising a measurement report, a signature object containing an algorithm identifier, a signature value and an optional certificate chain, and attestation metadata containing an attestation identifier, a protocol version, a challenge nonce and a verifier public key (mitigating RSK-01 and RSK-03).

REQ-AM-02: The environment attestation module is required to isolate attestation keys and signing operations from the untrusted agent runtime environment, preventing key exfiltration and unauthorized signing (mitigates RSK-03).

REQ-AM-03: The environment attestation module is required to bind attestation evidence directly to interaction sessions, transaction contexts and the public identity of the target AI agent to prevent identity spoofing and token hijacking (mitigates RSK-05).

REQ-AM-04: The environment attestation module is required to embed a measurement time and explicit temporal validity bounds, including a notBefore and a notAfter field, in every generated measurement report (mitigates RSK-04).

REQ-AM-05: The environment attestation module is required to support challenge-response mechanisms using a challengeNonce of at least 128 bits supplied by the verifier in a challengeNonce field in attestation metadata to guarantee evidence freshness and prevent replay attacks (mitigates RSK-04).

REQ-AM-06: The environment attestation module is required to support periodic attestation updates and attestation renewals before token expiration to maintain uninterrupted operational trust (mitigates RSK-04, RSK-07).

REQ-AM-07: The environment attestation module is recommended to support extensible token structures to allow custom platform claims without breaking core attestation syntax (mitigates RSK-06).

Requirements for the verifier
-----------------------------

REQ-VR-01: The verifier is required to perform comprehensive cryptographic validation on received attestation evidence, including signature verification, certificate trust chain anchor validation and revocation checking (mitigates RSK-01, RSK-03).

REQ-VR-02: The verifier is required to enforce strict temporal validation, rejecting attestation claims that contain expired validity windows, invalid timestamps or mismatched nonces (mitigates RSK-04).

REQ-VR-03: The verifier is required to evaluate validated measurement payloads against dynamic security trust policies before granting system access or resource permissions to an AI agent (mitigates RSK-01, RSK-02).

REQ-VR-04: The verifier is required to produce verification outcome decisions resulting in exactly one of Verified, VerifiedWithWarnings or Failed (mitigates RSK-01, RSK-02).

REQ-VR-05: The verifier is required to perform continuous or periodic re-evaluations of attestation state during long-running AI agent interaction sessions (mitigates RSK-04, RSK-08).

REQ-VR-06: The verifier is required to support cross-domain evidence verification using federated PKI, published trust anchors or distributed trust registries (mitigates RSK-06).

REQ-VR-07: The verifier is recommended to integrate attestation verification outputs into broader multi-dimensional risk evaluation frameworks (mitigates RSK-01, RSK-08).

REQ-VR-08: The verifier is recommended to support secure delegated verification architectures that offload trust evaluation to an authorized third-party verification service (mitigates RSK-06, RSK-07).

Requirements for the whole service
----------------------------------

REQ-WS-01: The whole service is required to support push mode, pull mode, challenge-response mode and delegated verification mode attestation delivery workflows to suit diverse service topologies (mitigates RSK-07).

REQ-WS-02: The whole service is required to maintain interoperability across diverse TEE and HSM hardware implementations using standardized claim schemas and protocol abstractions (mitigates RSK-06).

REQ-WS-03: The whole service is required to remain deployable across diverse AI agent runtime architectures, including containerized, edge and cloud-hosted environments (mitigates RSK-07).

REQ-WS-04: The whole service is required to enforce secure end-to-end transport protection for measurement data and attestation evidence transmitted across networks (mitigates RSK-01, RSK-03).

REQ-WS-05: The whole service is recommended to maintain semantic alignment and claim mappability with international standards such as IETF RATS Entity Attestation Token (EAT) and TCG specifications (mitigates RSK-06).

REQ-WS-06: The whole service is recommended to optimize attestation protocols to reduce verification latency and computational overhead on resource-constrained agent runtimes (mitigates RSK-07).

REQ-WS-07: The whole service is recommended to support incremental deployment options and backward-compatible fallback paths for legacy or non-TEE AI agent runtimes (mitigates RSK-07).

Requirements for the timeliness management module
-------------------------------------------------

REQ-TM-01: The timeliness management module is required to assign timestamps including measurementTime, notBefore and notAfter to measurement reports, deriving measurementTime from a trusted time source such as NTP, PTP or TEE-internal time. (mitigates RSK-04).

REQ-TM-02: The timeliness management module is required to set validity periods dynamically based on environment type and risk level, such as 10–30 min for TEE, 5–15 min for containers, 15–60 min for virtual machines and 30–120 min for bare metal. (mitigates RSK-04, RSK-09).

REQ-TM-03: The timeliness management module is required to monitor remaining validity against a threshold, such as 20 % of the total validity period or 5 minutes, triggering re-measurement before expiry. (mitigates RSK-04, RSK-09).

REQ-TM-04: The timeliness management module is required to consume environment-change events, including OS or security-module configuration changes, TEE or security-module state changes, software version upgrades or patch installations, agent migration to a different execution environment and security policy changes requiring re-evaluation of environment trustworthiness, to trigger immediate re-measurement. (mitigates RSK-04, RSK-09).

Requirements for the trust decision module
------------------------------------------

REQ-TD-01: The trust decision module is required to evaluate attestation results using trust policies defined as rules that use environmentType, securityLevel, integrityMeasurements and taskSensitivity. (mitigates RSK-10).

REQ-TD-02: The trust decision module is required to enforce securityLevel ordering such as hardwareIsolated \> softwareIsolated \> standard. (mitigates RSK-10).

REQ-TD-03: The trust decision module is required to apply graded trust based on task sensitivity, where low sensitivity requires standard or above, medium sensitivity requires softwareIsolated or above and high sensitivity requires hardwareIsolated. (mitigates RSK-10).

REQ-TD-04: The trust decision module is required to adjust trust decisions dynamically using task context, including task type, data classification, compliance requirements and time window. (mitigates RSK-10).

REQ-TD-05: The trust decision module is required to apply configurable linear or step-wise decay to trust levels over time within the validity period. (mitigates RSK-09).

REQ-TD-06: The trust decision module is required to raise an alert or automatically downgrade the trust level when verification results show anomalous patterns, such as frequent verification failures or abnormal changes to integrity measurements. (mitigates RSK-09, RSK-10).

REQ-TD-07: The trust decision module is required to output trust decisions that contain decision, confidence, reason, constraints, timestamp and verificationId. (mitigates RSK-10).

Requirements for the attestation store and audit trail
------------------------------------------------------

REQ-AS-01: The attestation store module is required to store attestations, verification results, trust decisions and audit logs persistently.

REQ-AS-02: The attestation store module is required to support querying, trace-back and export functions for compliance auditing.

Mapping between the security risks and requirements
---------------------------------------------------

Table 1 provides a mapping between the security risks and requirements.

.. list-table:: Table 1 - Mapping between the security risks and requirements
    :header-rows: 0
    :widths: 11 29 61

    * - **Security risk**
      - **Security risk description**
      - **Mitigating security requirements**
    * - RSK-01
      - Measurement tampering
      - REQ-MM-01, REQ-MM-02, REQ-MM-07, REQ-AM-01, REQ-VR-01, REQ-VR-03, REQ-VR-04, REQ-VR-07, REQ-WS-04
    * - RSK-02
      - Attestation forgery
      - REQ-MM-02, REQ-MM-03, REQ-VR-03, REQ-VR-04
    * - RSK-03
      - Replay attack
      - REQ-AM-01, REQ-AM-02, REQ-VR-01, REQ-WS-04
    * - RSK-04
      - Stale or freshness verification failure
      - REQ-AM-04, REQ-AM-05, REQ-AM-06, REQ-VR-02, REQ-VR-05, REQ-TM-01, REQ-TM-02, REQ-TM-03, REQ-TM-04
    * - RSK-05
      - Identity binding weakness
      - REQ-MM-04, REQ-AM-03
    * - RSK-06
      - Environment spoofing
      - REQ-MM-05, REQ-MM-06, REQ-MM-07, REQ-AM-07, REQ-VR-06, REQ-VR-08, REQ-WS-02, REQ-WS-05
    * - RSK-07
      - Denial of attestation
      - REQ-AM-06, REQ-VR-08, REQ-WS-01, REQ-WS-03, REQ-WS-06, REQ-WS-07
    * - RSK-08
      - Cross-domain trust issues
      - REQ-MM-03, REQ-VR-05, REQ-VR-07
    * - RSK-09
      - Undetected temporal decay of attestation trust
      - REQ-TM-02, REQ-TM-03, REQ-TM-04, REQ-TD-05, REQ-TD-06
    * - RSK-10
      - Context-ignorant trust decision
      - REQ-TD-01, REQ-TD-02, REQ-TD-03, REQ-TD-04, REQ-TD-06, REQ-TD-07

NOTE - REQ-AS-01 and REQ-AS-02 require the attestation store and the audit trail to hold the attestations, verification results and trust decisions persistently; they support all of the requirements above by keeping the evidence and the decisions auditable.

Security risks of trusted environment measurement and attestation for AI agents
===============================================================================

This clause identifies security risks for trusted environment measurement and attestation of AI agents.

**RSK-01: Measurement tampering**

Description: An attacker modifies, injects or suppresses measurement data during collection or before the platform root of trust seals the attestation payload.

Consequences: Relying parties receive inaccurate or malicious status information, creating false trust in an altered or unsafe execution environment.

**RSK-02: Attestation forgery**

Description: An unauthorized entity generates fake attestation evidence by spoofing signing keys, exploiting cryptographic weaknesses or compromising platform attestation keys.

Consequences: Untrusted or compromised platforms impersonate compliant hardware environments, gaining unauthorized access to sensitive tasks and data.

**RSK-03: Replay attack**

Description: An adversary intercepts valid attestation evidence and retransmits it during subsequent challenges without updating the underlying platform measurements.

Consequences: Compromised or modified environments pass verification by presenting outdated valid states, bypassing real-time integrity controls.

**RSK-04: Stale or freshness verification failure**

Description: Attestation evidence lacks adequate temporal controls, such as missing nonces or broad validity windows, or relying parties fail to enforce strict freshness checks.

Consequences: The relying party acts on obsolete security claims, allowing operations on platforms that suffered runtime compromise after initial attestation.

**RSK-05: Identity binding weakness**

Description: The system decouples or insufficiently binds the environment attestation payload to the operational identity of the resident AI agent.

Consequences: A malicious agent on an untrusted runtime attaches a legitimate platform attestation claim from a co-located or distinct trusted instance.

**RSK-06: Environment spoofing**

Description: An untrusted runtime or hypervisor emulates expected environment responses, system calls or isolated enclave behavior to deceive the agent or challenger.

Consequences: The AI agent executes sensitive logic or model inference assuming isolation, exposing models, prompts and memory to the host platform.

**RSK-07: Denial of attestation**

Description: Malicious actors or platform hosts intentionally disrupt or block access to attestation services, measurement verification endpoints or revocation check channels.

Consequences: Legitimate AI agents cannot establish verified status, causing service outages or forcing fallback to insecure operational modes.

**RSK-08: Cross-domain trust issues**

Description: Heterogeneous trust roots, incompatible attestation schemes or unmapped endorsement chains across administrative or platform domains fail to establish mutual verifiability.

Consequences: Inter-agent delegation and cross-domain collaboration fail or downgrade security checks to unverified baselines.

**RSK-09: Undetected temporal decay of attestation trust**

Description: An AI agent operates under a valid attestation near the end of its validity period without accounting for trust decay over time.

Consequences: Relying parties treat aging attestations as fully trustworthy, permitting operations in environments with unmonitored security degradation or undetected compromise.

**RSK-10: Context-ignorant trust decision**

Description: A relying party evaluates environment attestation in isolation without incorporating task sensitivity, data classification or dynamic task context into the evaluation.

Consequences: Insufficiently isolated environments receive permission for high-sensitivity tasks or restricted data access, leading to unauthorized data disclosure or policy violations.

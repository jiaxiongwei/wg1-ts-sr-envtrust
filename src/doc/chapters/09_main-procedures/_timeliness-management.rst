Timeliness management
---------------------

Every measurement report features the field measurementTime, sourced from a trusted reference like NTP, PTP or internal TEE time, alongside notBefore and notAfter.

Validity periods are set dynamically based on environment type and risk: For example, TEE is set to 10–30 min, container to 5–15 min, virtual machine to 15–60 min and bare metal to 30–120 min.

The verifier checks that the current time falls between notBefore and notAfter, failing which the attestation expires. The verifier checks that measurementTime is within an acceptable window; if the measurement time deviates too far from the current time, the attestation becomes untrusted even before notAfter.

The agent records notAfter when generating the attestation, periodically compares the remaining validity against a threshold such as 20 % of the validity period or an absolute 5 minutes, and re-measures before expiry. The new attestation then replaces the old one for future collaboration requests.

Immediate event-driven re-measurement occurs upon an OS or security-module configuration change, a TEE or security-module state change, a software version upgrade or patch installation, agent migration to a different execution environment, or a security policy change that requires re-evaluating environment trustworthiness.

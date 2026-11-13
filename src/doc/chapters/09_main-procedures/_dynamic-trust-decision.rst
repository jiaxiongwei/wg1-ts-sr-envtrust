Dynamic trust decision
----------------------

Policies consist of rules. Each rule defines a decision under specific conditions and uses the following structure:

- IF environmentType IN [allowed_types] AND securityLevel \>= required_level AND integrityMeasurements MATCH [expected_values] AND taskSensitivity = [level] THEN trust_decision = [accept\|reject\|degrade]

- The ordering for required_level values is hardwareIsolated \> softwareIsolated \> standard, and expected_values is an allowed list of integrity baselines.

Graded trust based on task sensitivity balances security and availability. Low sensitivity requires standard or above for public information retrieval and non-sensitive queries. Medium sensitivity requires softwareIsolated or above for general business processing without personal data. High sensitivity requires hardwareIsolated for personal privacy data, key operations and sensitive decisions.

Trust is adjusted dynamically based on task context. This includes task types such as data access, decision-making or tool invocation; data classifications such as public, internal, confidential or top secret; compliance requirements such as GDPR or the EU AI Act; and specific time windows that apply extra restrictions.

Within the validity period, the trust level decays over time even before the attestation expires. The system configures this decay function as linear or step-wise.

If verification results reveal anomalies like frequent verification failures or unusual changes in integrity measurements, the system raises an alert or automatically downgrades the trust level.

The trust decision output includes decision with a value of accept, reject or degrade, where degrade limits collaboration or data access, confidence as a value of 0–100 showing decision reliability, reason as text for audit and manual review, constraints specifying extra conditions in degrade mode such as restricted tools or data range, timestamp, and verificationId as a unique identifier of the verification record for an audit trail.

Gap analysis
============

A systematic analysis of existing ITU-T Recommendations and international standards shows that no existing normative instrument covers trusted environment measurement and attestation for AI agents. The section below details the identified gaps across key functional dimensions.

Gap: Environment measurement data model
---------------------------------------

**ITU-T F.751.9 — TEE-based confidential computing in DLT systems**

Coverage: Outlines a TEE-based confidential computing framework designed specifically for DLT transaction environments.

Gap: Does not specify a standardized data model for expressing environment trust properties applicable to AI agents.

**ITU-T X.LLMCC — Guidelines for LLM data security using confidential computing**

Coverage: Covers system-layer isolation and encrypted execution for LLMs through confidential computing.

Gap: Applies only to LLM data protection constraints rather than establishing a generic AI agent environment measurement format.

**ITU-T Y.3165 — Remote attestation of TEE instances in network slices**

Coverage: Defines procedures to attest TEE instances remotely within 5G/IMT-2020 network slicing.

Gap: Tailored strictly to network infrastructure and lacks application-layer data models for AI agent execution contexts.

**IETF RATS — Remote Attestation Procedures**

Coverage: Establishes general architecture, roles and terminology for remote attestation procedures.

Gap: Provides generic procedural primitives without normative definitions for AI-agent environment trust attributes.

Gap conclusion: No existing standard provides a machine-readable, interoperable data model to express the trust properties (e.g. TEE type, isolation guarantees, measurement logs and runtime integrity) of an AI agent's execution environment.

Gap: Attestation protocol for AI agent environments
---------------------------------------------------

**ITU-T F.751.9 — TEE-based confidential computing on DLT systems.**

Coverage: Specifies TEE attestation verification procedures. These procedures bind to DLT smart contract execution.

Gap: Monolithic and tied to DLT architectures; lacks support for dynamic agent-to-agent attestation flows.

**ITU-T X.LLMCC — Guidelines for LLM data security based on confidential computing.**

Coverage: Outlines attestation protocols for verifying runtime trust in LLM hosting environments.

Gap: Lacks detailed, normative protocol specifications for multi-agent, cross-domain invocations.

**ITU-T Q.5015 — Signalling requirements for TEE remote attestation in MEC.**

Coverage: Specifies signalling protocols for remote attestation of TEEs in Mobile Edge Computing (MEC).

Gap: Bound to MEC network signalling topologies; unsuited to general application-layer AI agent communication protocols.

Gap conclusion: No existing standard defines an attestation exchange protocol designed for AI agents to cryptographically demonstrate execution environment integrity to peer agents or authorization endpoints.

Gap: Temporal validity management
---------------------------------

Existing Standards Coverage: None identified.

Gap conclusion: A complete standardization gap exists. No current standard provides normative requirements for managing the freshness, validity window, replay prevention or real-time revocation/refresh of environment attestation claims for AI agents.

Gap: Dynamic trust decision framework
-------------------------------------

**ITU-T XSTR.atcp — Cryptographic primitives for enhancing AI agent trustworthiness.**

Coverage: Defines trust score primitives and confidence representations for agent-to-agent interactions.

Gap: Focuses on mathematical and cryptographic trust representations without specifying how to evaluate or integrate environment measurements.

**ITU-T X.sr-taimas — Security requirements for terminal-based AI multi-agent systems.**

Coverage: Specifies trusted authorization and intent verification requirements for terminal agents.

Gap: Does not incorporate verifiable environment integrity measurements into authorization decision logic.

Gap conclusion: No standard defines how a relying entity (e.g., receiving agent or service endpoint) processes, evaluates, and factors environment attestation reports into dynamic, risk-based access control decisions.

Summary of gaps
---------------

.. list-table::
    :header-rows: 1
    :widths: 11 28 35 25

    * - Gap Area
      - Existing Coverage
      - Gap Description
      - Scope of This Proposal
    * - Measurement Data Model
      - None
      - Lacks standardized schemas for environment properties in AI agents
      - Defines normative, machine-readable data models
    * - Attestation Protocol
      - Partial (F.751.9, X.LLMCC — domain-specific)
      - Lacks protocol specifications for peer-to-peer agent attestation
      - Defines agent-tailored attestation exchange protocols
    * - Temporal Validity
      - None
      - Lacks mechanics for measurement freshness, re-attestation and revocation
      - Establishes normative temporal validity management
    * - Trust Decision Framework
      - Partial (XSTR.atcp, X.sr-taimas — focus on identity/intent)
      - Lacks rules for evaluating environment state within authorization policies
      - Defines an environment-aware trust decision framework
    * - Interoperability
      - Partial (Y.3165 — network-slice specific)
      - Lacks cross-TEE and cross-cloud measurement abstraction
      - Delivers cross-platform interoperability requirements

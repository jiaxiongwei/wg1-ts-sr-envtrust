.. raw:: latex

    \pagestyle{plain}
    \thispagestyle{plain}
    %% Suppress all TOC entries for the front matter (sections, subsections and
    %% any addcontentsline) — restored just before \sphinxtableofcontents so the
    %% numbered clauses appear in the TOC normally.
    \let\osiaorigaddcontentsline\addcontentsline
    \renewcommand{\addcontentsline}[3]{}

.. _front-matter:

Security requirements for trusted environment measurement and attestation of AI agents
======================================================================================

.. only:: html

    **Draft new Technical Specification TS.sr-envtrust — Security requirements for trusted environment measurement and attestation of AI agents**

.. raw:: latex

    \begin{center}\textbf{Draft new Technical Specification TS.sr-envtrust — Security requirements for trusted environment measurement and attestation of AI agents}\end{center}

Abstract
--------

This contribution proposes a new work item of Technical Specification on "Security requirements for trusted environment measurement and attestation of AI agents".

Background
----------

Context of the study
~~~~~~~~~~~~~~~~~~~~

Rapid advances in agentic AI mark a fundamental shift in operations. Unlike traditional software operating in static environments, AI agents increasingly run across varied, distributed and untrusted execution environments, including cloud data centers, edge nodes, mobile devices and IoT endpoints.

This growth exposes a critical architectural gap: existing AI agent security standards verify identity (“who”) and authorization (“what”), but ignore runtime platform integrity (“where”). An agent on a compromised platform—such as a rooted edge node—remains untrustworthy despite valid credentials. Although Trusted Execution Environments (TEEs) provide hardware-isolated execution, TEE adoption across AI agent ecosystems remains fragmented because the ecosystem lacks standardized measurement formats, uniform attestation protocols, temporal validity models and dynamic trust decision frameworks.

ITU-T SG17 initiatives, including the Focus Group on Trust and Identity for Humans and Agentic AI (FG-TIDA) and work item XSTR.atcp, stress the need to quantify trust confidence. However, existing standards leave trusted environment measurement and attestation for AI agents unaddressed.

To close this gap, this proposal specifies security risks, security requirements and methodologies for trusted environment measurement and attestation for AI agents. This proposal establishes the essential platform trust anchor needed for secure agentic interactions.

Why this study is needed
~~~~~~~~~~~~~~~~~~~~~~~~

Without standardized mechanisms to measure, attest and verify runtime platform integrity, critical security gaps persist across AI agent ecosystems:

-Environment blind spot in existing frameworks – Current standards focus on identity, communication and authorization, but lack specifications for platform attestation. Without standardized measurement and attestation, security risks (such as measurement tampering, attestation forgery, replay attacks and stale attestation identified in Clause 7) persist unmitigated.

\- Fragmented and non-interoperable trust implementations – Disparate TEE architectures (e.g. Intel SGX, AMD SEV and ARM TrustZone) rely on proprietary attestation formats, preventing cross-platform and cross-domain environment trust verification.

\- Inability to support dynamic, risk-based authorization – Existing access control models lack the standardized environment measurement inputs needed for real-time, context-aware trust evaluation.

\- Compliance and auditability challenges – Emerging regulatory frameworks (e.g. EU AI Act and NIST AI RMF) require verifiable evidence of platform integrity, which relies on standardized cryptographic attestation.

\- Strategic alignment with ITU-T priorities – Environment measurement and attestation serves as the hardware root of trust supporting higher-level identity and authorization frameworks developed under FG-TIDA and SG17.

What this study is
~~~~~~~~~~~~~~~~~~

This proposal specifies the concept and overview, the security framework, security risks, security requirements and main procedures and methodologies for trusted environment measurement and attestation for AI agents. It is structured as follows:

\- Part 1: Overview and concept of trusted environment measurement and attestation for AI agents (Clause 6.1), covering the service model and its technical characteristics.

\- Part 2: The security framework and its systems, functional entities and equipment (Clause 6.2).

\- Part 3: Security risks of trusted environment measurement and attestation for AI agents (Clause 7), analyzing operational threats and platform vulnerabilities, including measurement tampering, attestation forgery, replay and state expiration (RSK-01 to RSK-10).

\- Part 4: Security requirements (Clause 8), defining normative security capabilities to mitigate identified risks across measurement modules (REQ-MM-01 to REQ-MM-07), attestation modules (REQ-AM-01 to REQ-AM-07), verifiers (REQ-VR-01 to REQ-VR-08), overall service scenarios (REQ-WS-01 to REQ-WS-07), the timeliness management module (REQ-TM-01 to REQ-TM-04), the trust decision module (REQ-TD-01 to REQ-TD-07) and the attestation store (REQ-AS-01 to REQ-AS-02).

\- Part 5: Main procedures and methodologies for trusted environment measurement and attestation (Clause 9), specifying procedures for data collection, measurement encoding and the data model, evidence generation, cryptographic attestation exchange, verification, delegated verification, lifecycle, timeliness management and dynamic trust decisions.

Appendix I provides practical use cases, and Appendix II provides a reference data model for environment measurement.

Key benefits
~~~~~~~~~~~~

The proposal offers key benefits to ITU-T SG17 and the wider international standardization community:

\- Fills a critical gap in the AI agent trust framework – Complements existing standards on identity, intent and authorization by adding the missing “environment” dimension, completing the “who-what-where” trust triad.

\- Enables cross-platform interoperability – Establishes a standardized data model and protocol for environment trust measurement that operates seamlessly across varied TEE architectures, cloud providers and device platforms.

\- Supports dynamic, risk-based trust decisions – Allows receiving agents and verifiers to run context-aware trust evaluations based on verifiable execution environment properties.

\- Provides auditable compliance evidence – Generates cryptographic evidence of environment integrity to satisfy strict regulatory, policy and audit requirements.

\- Anchors higher-level trust claims – Establishes a hardware-rooted baseline to securely anchor identity assertions, intent verifications and authorization decisions.

\- Accelerates secure agentic AI deployment – Removes deployment barriers for AI agents across complex, multi-domain environments through a unified trust measurement framework.

\- Aligns with and complements ITU-T work – Directly complements XSTR.atcp (trust confidence primitives), X.sr-taimas (terminal-based multi-agent trust), X.aaia-sec (autonomous agent security framework) and FG-TIDA (trust and identity framework).

Relationship to existing ITU-T Recommendations and other standards
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The relationship between this proposal and relevant existing standards or ongoing standardization work is outlined below:

**Recommendation ITU-T F.751.9 (2023), Confidential computing based on trusted execution environments in distributed ledger technology systems**

Scope: Specifies the general architecture, security requirements and functional components for TEEs in blockchain applications.

Relationship: Provides foundational concepts for trusted execution environments. This proposal references ITU-T F.751.9 informatively in the Bibliography for underlying TEE baseline concepts, while extending attestation protocols to AI agent environments.

**Draft Recommendation ITU-T X.LLMCC, Guidelines for large language model data security using confidential computing**

Scope: Establishes guidelines to secure large language models through confidential computing, focusing on system-layer isolation, encrypted model execution, algorithm integrity and attestation protocols.

Relationship: Complementary work item. While X.LLMCC focuses on LLM application-layer execution safety, this proposal provides the lower-level environment measurement and attestation needed to protect agent workloads.

**Draft Technical Report ITU-T XSTR.atcp, Cryptographic primitives to enhance AI agent trustworthiness**

Scope: Establishes a taxonomy and primitives for assessing trust confidence in AI agent interactions.

Relationship: Complementary work item under FG-TIDA. XSTR.atcp defines high-level primitives for trust scoring, while this proposal sets out the concrete platform measurement and attestation evidence required to feed those trust decisions.

**Draft Recommendation ITU-T X.sr-taimas, Security requirements for terminal-based artificial intelligence multi-agent systems**

Scope: Focuses on multi-agent collaboration security, identity management and message verification on end-user terminal devices.

Relationship: Complementary work item. X.sr-taimas covers terminal multi-agent communication and application security, while this proposal provides the trusted environment attestation layer required by terminal-based agents.

**Draft Recommendation ITU-T X.aaia-sec, Security framework and technical requirements for autonomous AI agents**

Scope: Defines a comprehensive security framework and functional architecture for autonomous AI agents, including lifecycle management, intent validation and policy enforcement.

Relationship: Complementary work item. X.aaia-sec sets the overarching security architecture for AI agents, while this proposal provides the specialized technical specification for platform environment measurement and attestation.

**Draft Recommendation ITU-T X.S-AIAI, Security framework and requirements for AI agent invocation**

Scope: Addresses security threats in agent-to-agent, agent-to-tool and agent-to-MCU invocations.

Relationship: Complementary work item. X.S-AIAI covers interaction security protocols, while this proposal ensures that interacting agent endpoints run inside verified trusted execution environments.

**IETF RATS Architecture (RFC 9334) and Entity Attestation Token (EAT) (RFC 9674)**

Scope: Defines a generic remote attestation architecture (Attester, Verifier, Relying Party) and cryptographic token formats for platform claims.

Relationship: Complementary external standards. This proposal adopts RATS architectural roles and EAT claim structures, adapting them with AI agent-specific environment measurement payloads, data models and dynamic verification logic.

**ETSI TS 104 050, Securing Artificial Intelligence (SAI); AI Threat Ontology**

Scope: Sets out guidelines to secure AI workloads using hardware security modules and TEEs.

Relationship: Complementary external standard. ETSI TS 104 050 provides general guidance on hardware protection, while this proposal establishes normative requirements and attestation methodologies tailored specifically for AI agents.

**NIST AI Risk Management Framework (AI RMF 1.0)**

Scope: Provides frameworks for managing AI risks and applying Zero Trust principles across software and infrastructure.

Relationship: Complementary external frameworks. This proposal supplies the concrete technical measurements and cryptographic evidence needed to apply Zero Trust "never trust, always verify" principles to AI agent platform execution.

Summary of gap: Existing standards focus on generic remote attestation (IETF RATS), generic hardware security (ETSI, ITU-T F.751.9) or high-level AI application security (X.aaia-sec, X.LLMCC). None specify standard environment measurement formats, attestation protocols or freshness mechanisms tailored specifically for AI agents operating across heterogeneous TEE platforms. This proposal fills this architectural gap.

Summary
-------

Artificial Intelligence (AI) agents increasingly run outside static environments on distributed platforms such as cloud data centers, edge nodes, mobile devices and IoT endpoints. Existing AI agent security standards check identity and authorization, but fail to verify runtime platform integrity. An agent on a compromised platform is untrustworthy even with valid credentials. Trusted Execution Environment adoption remains fragmented across different hardware architectures using proprietary attestation formats. Systems lack standardized ways to measure, attest or verify platform integrity. This gap leaves networks vulnerable to measurement tampering, attestation forgery, replay attacks and stale attestations. Access control models lack standardized environment measurement inputs for dynamic authorization. Emerging regulations require verifiable evidence of platform integrity. Environment measurement and attestation acts as the hardware root of trust for identity and authorization frameworks.

This draft new Technical Specification adds the missing environment dimension to complete the who-what-where trust triad, enables cross-platform interoperability and supports dynamic, risk-based trust decisions. The scope covers security risks, security requirements and methodologies for trusted environment measurement and attestation of AI agents.

History
-------

.. list-table::
    :widths: 10 26 18 14 32

    * - Version
      - Document
      - Approval
      - Focus Group
      - Working Group

To access this Document as a PDF, open the published documentation site in your web
browser and click the PDF download link, or navigate directly to the PDF target of
this repository.

Authors
-------

.. list-table::
    :header-rows: 1
    :widths: 30 40 30

    * - Name
      - Affiliation
      - Contact
    * - Xiongwei Jia
      - China Unicom
      - jiaxw9@chinaunicom.cn

Keywords
--------

Artificial Intelligence (AI) agent, attestation, environment measurement, trusted environment, methodology, trusted execution environment (TEE).

Foreword
--------

Agentic AI systems now act as autonomous entities capable of reasoning, planning, and
executing tasks across services, infrastructures, and organizational boundaries. This
fundamentally changes the nature of identity in digital systems: identity is no longer
limited to human users and static machine instances but must also encompass autonomous,
dynamic, and goal-oriented agents. And identity alone is insufficient — the core question
extends beyond "what an entity is" to "whether, and under what conditions, that entity
should be trusted to act".

The Focus Group on Trust and Identity for humans and agentic AI (FG-TIDA) addresses trust
management and interoperable digital identity infrastructure for humans and for agentic AI,
supporting the development of secure, trustworthy digital ecosystems in which humans and
agentic AI can safely interact and collaborate.

FG-TIDA was established under Recommendation ITU-T A.7 (Focus groups: Establishment and
working procedures), with ITU-T Study Group 17 as its parent group. Further details are
available in the group's terms of reference.

For more news and updates about the TIDA Community, including its supporter organizations,
please refer to the community's published resources.

Note
----

*[Editor: add any note on the status of this Technical Report.]*

.. raw:: latex

    %% Copyright notice commented out. To restore, uncomment the lines below.
    %% \vspace{4em}
    %% \begin{center}\textcopyright{} ITU 2026\end{center}
    %%
    %% \medskip
    %% All rights reserved. No part of this publication may be reproduced, by any means whatsoever, without the
    %% prior written permission of ITU.

    %% Restore \addcontentsline so the TOC below (and Chapter 1 onward) populate.
    \let\addcontentsline\osiaorigaddcontentsline
    \sphinxtableofcontents
    \osiamainmatter
    %% Clauses are \section under an unnumbered chapter, so LaTeX would print
    %% them 0.1, 0.2, ...  Number them from 1, and restart the counter here:
    %% the unnumbered front-matter subsections step it before this point.
    \makeatletter
    \renewcommand{\thesection}{\arabic{section}}
    \renewcommand{\thesubsection}{\thesection.\arabic{subsection}}
    \renewcommand{\thesubsubsection}{\thesubsection.\arabic{subsubsection}}
    \makeatother
    \setcounter{section}{0}

.. toctree::
    :maxdepth: 3
    :numbered:
    :hidden:

    chapters/01_scope
    chapters/02_references
    chapters/03_definitions
    chapters/04_abbreviations
    chapters/05_conventions
    chapters/06_overview
    chapters/07_security-risks
    chapters/08_security-requirements
    chapters/09_main-procedures/index

.. toctree::
    :maxdepth: 3
    :hidden:

    chapters/10_appendix-i_use-cases
    chapters/11_appendix-ii_data-model
    chapters/12_bibliography
    chapters/13_annex-a_justification
    chapters/14_gap-analysis

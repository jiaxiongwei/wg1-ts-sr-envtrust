# TS.sr-envtrust

**Security requirements for trusted environment measurement and attestation
of AI agents**

Proposed new Technical Specification of the Focus Group on Trust and Identity
for humans and agentic AI (FG-TIDA), Working Group 1 (WG1). Status: **draft (V1)**.

📄 **Web page:** https://jiaxiongwei.github.io/wg1-ts-sr-envtrust/
📥 **PDF:** https://jiaxiongwei.github.io/wg1-ts-sr-envtrust/specification.pdf

## What this document is

AI agents increasingly run outside static environments, on distributed
platforms such as cloud, edge and confidential-computing enclaves. Existing
work verifies **who** an agent is and **what** it intends to do, but not
**where** it is running — the environment dimension of the trust triad is
missing. Without it, an authorisation decision cannot distinguish an agent
executing inside a verified enclave from one reporting from a compromised host.

This Technical Specification fills that gap. It specifies the concepts and the
security framework for trusted environment measurement and attestation of AI
agents, the security risks that arise when the environment is unverified, the
security requirements that answer them, and the procedures and methodologies
that implement measurement, attestation generation and exchange, verification,
delegated verification, lifecycle and timeliness management, and dynamic trust
decision. Appendix II provides a JSON reference implementation of the
measurement data model.

## Contents

| | |
|---|---|
| 1–5 | Scope, References, Definitions, Abbreviations, Conventions |
| 6 | Overview of trusted environment measurement and attestation |
| 7 | Security risks (RSK-01 – RSK-10) |
| 8 | Security requirements (REQ-AM / REQ-AS / REQ-VR / REQ-WS / REQ-TM / REQ-TD) |
| 9 | Main procedures and methodologies (9.1–9.9) |
| Appendix I | Use cases |
| Appendix II | Reference environment measurement data model |
| Bibliography, Annex A | References and the A.1 justification |
| Gap analysis | The four gaps this work item addresses |

## Working on the document

The document is authored in reStructuredText and built with Sphinx into a web
page and a print PDF.

```shell
pip install -r requirements.txt
sphinx-build -b html src/doc target/html                            # web
sphinx-build -b latex src/doc target/latex && make -C target/latex  # PDF
```

`target/` is a **local build directory only** — it is git-ignored and never
published. The public site and PDF are built by GitHub Actions on every push to
`main` and deployed to the addresses above.

- `src/doc/index.rst` — title, abstract, background, summary, history, authors,
  keywords, foreword, note.
- `src/doc/chapters/` — one file per clause, `01`–`09`, then Appendix I–II, the
  bibliography, the Annex A justification and the gap analysis.
  `chapters/09_main-procedures/` is an `index.rst` plus one `_fragment.rst` per
  procedure, pulled in with `.. include::`.
- `src/doc/images/` — figures.
- `src/doc/conf.py` — project metadata and the `cover_*` values used on the PDF cover.

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for how to propose a change, and
**[WG-ONBOARDING.md](WG-ONBOARDING.md)** for the TIDA authoring workflow.

## Editor

Xiongwei Jia, China Unicom — jiaxw9@chinaunicom.cn

## Licence

MIT, per [LICENSE](LICENSE). See [CHANGELOG.md](CHANGELOG.md) for document history.

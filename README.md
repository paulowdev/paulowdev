<div align="center">

# Paulo Costa

**Lead Software Engineer · Backend & Cloud Architecture · AI Platform Engineering**

[Portfolio](https://paulowdev.github.io) · [GitHub](https://github.com/paulowdev) · [LinkedIn](https://www.linkedin.com/in/paulowdev) · [Português (Brasil)](README.pt-BR.md)

![Java](https://img.shields.io/badge/Java_21-0f172a?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-0f172a?style=flat-square&logo=springboot&logoColor=6DB33F)
![Python](https://img.shields.io/badge/Python-0f172a?style=flat-square&logo=python&logoColor=3776AB)
![TypeScript](https://img.shields.io/badge/TypeScript-0f172a?style=flat-square&logo=typescript&logoColor=3178C6)
![AWS](https://img.shields.io/badge/AWS-0f172a?style=flat-square&logo=amazonaws&logoColor=FF9900)
![MCP](https://img.shields.io/badge/Model_Context_Protocol-0f172a?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-0f172a?style=flat-square)

</div>

## Executive Summary

I engineer backend platforms and cloud systems where reliability, security, and operational cost are first-class requirements. My work spans Java and Spring Boot microservices, AWS infrastructure, event-driven systems, and production-oriented AI engineering.

I build AI-enabled engineering workflows around **agents, Model Context Protocol (MCP), retrieval-augmented generation (RAG), and reusable agent tooling**. The design goal is controlled capability: explicit tool permissions, bounded context, observable execution, and predictable trade-offs between quality, latency, reliability, and model cost.

My background includes fintech, logistics, and agricultural technology, with hands-on technical leadership, service modernization, performance work, vulnerability remediation, and cross-team engineering standards.

## Engineering Focus

- **Backend & distributed systems:** Java 21, Spring Boot, REST APIs, microservices, domain-driven design, Clean Architecture, Kafka, RabbitMQ.
- **Cloud & delivery:** AWS, Docker, Kubernetes, OpenShift, Terraform, CI/CD, infrastructure automation, observability.
- **AI platform engineering:** MCP servers, agent harnesses, skills and toolkits, RAG, pgvector, Qdrant, context engineering, model routing.
- **Security & resilience:** least privilege, secure service boundaries, dependency remediation, input validation, auditability, failure handling.
- **Technical leadership:** architecture reviews, mentoring, engineering standards, roadmap alignment, and pragmatic delivery.

## Selected Work

### OrkStage - Open-source multicloud orchestration

**Status:** Alpha / active testing · [orkstage.io](https://orkstage.io) · [GitHub organization](https://github.com/orkstage)

A control-plane project for defining and operating infrastructure across cloud providers. The project explores a provider-oriented architecture, infrastructure-as-code execution, asynchronous work, and a centralized view of provisioning.

- Focus: cloud orchestration, tenant-aware platform design, infrastructure automation, and operational visibility.
- Public project status and provider support should be read from the repository documentation; alpha capabilities may change.
- **Architecture note:** describe a provider as supported only when its implementation is available and tested in the current repository. Do not interpret roadmap or preview support as production readiness.

### Papers Hub - Academic call-for-papers discovery

**Role:** Full-stack project development · **Year:** 2025 · **Context:** University research project, A Coruña, Spain · [Website](https://papershub.net)

A discovery platform for calls for papers and academic submission opportunities. A scheduled Python collection workflow gathers and extracts source metadata, then indexes records in MongoDB for a TypeScript-based web search application.

- **Known from project description:** Python scheduled collection, MongoDB, Next.js, React, Node.js, and TypeScript.
- **Architecture interpretation:** a batch ingestion pipeline separated from the query-facing web application.
- Responsible crawling and source load limits were part of the stated collection approach.
- Deduplication, retry semantics, monitoring, and specific search/indexing strategies are not claimed here because they have not been independently confirmed.

### EdukaHub / ArboEduca - Collaborative learning

**Role:** Part-time co-founder / developer · **Years:** 2024–2025 · **Country:** Brazil · [Website](https://arboeduca.com.br/)

An educational platform for active-learning workflows, including teacher-created activities and peer assessment.

- **Known from project description:** React, TypeScript, Chakra UI, NestJS, and MongoDB.
- **Architecture interpretation:** a web presentation layer backed by a modular Node.js application and document persistence.
- The description reflects a part-time contribution; it does not imply sole ownership of the product.

### Flytech Agro - Agricultural pest monitoring

**Role:** Part-time co-founder / developer · **Years:** 2022–2024 · **Country:** Brazil · [Archived website](https://web.archive.org/web/20220123083940/https://flytechagro.com.br/)

A pest-monitoring platform focused on fruit-fly management, combining a web dashboard, API services, a model-training workflow, and mobile/offline synchronization.

- **Known from project description:** React, TypeScript, Tailwind UI, Python, FastAPI, TensorFlow Lite export, and Firebase.
- **Architecture interpretation:** a separated model-training pipeline and application backend, with an offline-first synchronization strategy.
- On-device inference is only implied if the mobile app actually loaded and executed the exported TFLite model; verify this detail before making a stronger claim.

## Enterprise Architecture Showcase

The following cases are intentionally anonymized. They communicate architectural decisions and security boundaries without disclosing confidential implementation details. They should be retained as implementation case studies only to the extent that they reflect work actually designed or delivered.

### Enterprise GenAI Orchestrator - Confidential Case

**Objective:** expose approved internal capabilities to LLM-powered agents without granting models unrestricted access to enterprise systems.

**Conceptual request flow**

1. **Request and identity:** authenticate the caller and establish tenant, user, and request scope.
2. **Security gateway:** enforce request limits, policy checks, and execution budgets.
3. **Context validation:** validate context provenance, authorization, and permitted data scope.
4. **LLM / Claude router:** select an approved model and workflow based on policy, latency, quality, and cost.
5. **MCP server:** expose narrowly scoped tools with schema validation and explicit authorization.
6. **Tool execution:** execute approved operations with bounded permissions, timeouts, and audit events.
7. **Output security:** apply data-loss-prevention and disclosure policies to retrieved context and generated output before returning the response.

**Engineering concerns:** least privilege, tool allowlists, argument validation, tenant isolation, secret handling, timeouts, idempotency for consequential actions, auditability, and safe failure behavior. RAG is not an authorization boundary; access must be enforced before sensitive data is retrieved and again before it is disclosed.

### Secure Enterprise RAG Pipeline - Confidential Case

**Objective:** connect enterprise knowledge retrieval to Java/Spring Boot services while preserving document-level authorization.

**Conceptual data and request flow**

1. **Ingestion:** validate source documents, normalize content, classify sensitivity, and retain source/ownership metadata.
2. **Input and content defenses:** detect suspicious instructions and treat retrieved documents as untrusted data; use layered prompt-injection defenses rather than relying on keyword filtering alone.
3. **Asynchronous vectorization:** Python workers generate embeddings and update the vector index through a retryable, observable processing workflow.
4. **Authorized retrieval:** apply tenant and RBAC constraints during retrieval; re-check permissions before retrieved passages enter model context.
5. **Context assembly:** minimize the context to relevant, permitted passages and preserve source references for traceability.
6. **Model invocation and output controls:** call the approved model, validate the response against disclosure policies, and record security-relevant events.

**Engineering concerns:** access-aware retrieval, stale-permission handling, asynchronous retries, poison-message handling, data retention, index consistency, evaluation quality, prompt-injection resilience, and traceable source attribution.

## Professional Experience

### Lead Software Engineer - Solutis Tecnologias, client Santander
**Nov 2025 – Present · São Paulo, Brazil**

- Designed and implemented MCP servers integrated with vector databases and RAG workflows for AI-assisted engineering.
- Built reusable agent harnesses, skills, and toolkits for Anthropic Claude, OpenAI models, and Devin.
- Reduced token spend by optimizing context, removing unnecessary model calls, and selecting workflows based on quality, latency, and reliability.
- Automated development and operations processes and applied AI to project and production monitoring.
- Supported foundation-team tooling, shared libraries, and Spec-Driven Development practices for global cards teams.
- Contributed to anti-fraud and fallback systems, including migration of the fraud engine from on-premises infrastructure to AWS.
- Led vulnerability and outdated-dependency remediation across microservices.
- Led legacy microservice migrations to Java 21, Spring Boot, and AWS.

### Senior Engineering Consultant - Globant, client PagBank
**Aug 2024 – Jun 2025 · Brazil · Remote**

- Optimized critical application microservices, including services supporting high-volume Pix flows.
- Refactored high-criticality services to reduce latency and improve stability under load.
- Aligned engineering changes with product requirements and financial-sector compliance constraints.

### Senior Engineering Consultant - Tecla T
**May 2024 – Aug 2024 · Remote**

- Built Java and Spring Boot integrations with payment gateways and white-label fintech providers.

### Platform Software Engineer - Syngenta Digital Brasil
**Nov 2022 – May 2024 · Remote**

- Led the separation of an annotations feature into an independent platform integrated with internal services.
- Developed features and maintained Cropwise microservices.
- Defined integration interfaces with multiple engineering teams.

### Senior Software Engineer - iFood
**Jan 2022 – Oct 2022 · Remote**

- Contributed to migration from a legacy logistics platform to microservices.
- Delivered backend features and supported production systems handling real-time transactions.

### Earlier Experience
act digital - Senior Software Engineer (2021–2022) · Zup Innovation - Senior IT Analyst (2021) · GREat / UNIFOR - Software Developer and Senior Software Developer (2017–2021) · Earlier web development and network technician roles (2011–2017).

## Education

- **MBA in Cybersecurity - USP/Esalq** · In progress, 2026–2027. Research topic: behavioral biometrics SDK for continuous authentication and fraud detection using embeddings and a vector database.
- **Undergraduate degree in Systems Analysis and Development - Universidade Estácio de Sá.**

## Languages

Portuguese (native) · English (B1/B2) · Spanish (A2)

---

<sub>Confidential case studies are anonymized and intentionally omit internal identifiers, sensitive data, and implementation details. Architectural patterns described as conceptual should not be interpreted as claims about a specific production implementation.</sub>

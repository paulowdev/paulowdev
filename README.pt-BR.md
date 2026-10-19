<div align="center">

# Paulo Costa

**Lead Software Engineer · Backend e Arquitetura Cloud · Engenharia de Plataformas de IA**

[Portfólio](https://paulowdev.github.io) · [GitHub](https://github.com/paulowdev) · [LinkedIn](https://www.linkedin.com/in/paulowdev) · [English](README.md)

</div>

## Resumo Executivo

Projeto plataformas backend e sistemas cloud em que confiabilidade, segurança e custo operacional são requisitos de primeira classe. Minha experiência abrange microsserviços Java/Spring Boot, infraestrutura AWS, sistemas orientados a eventos e engenharia de IA voltada à produção.

Desenvolvo fluxos de engenharia assistida por IA com **agentes, Model Context Protocol (MCP), geração aumentada por recuperação (RAG) e ferramentas reutilizáveis para agentes**. O objetivo é oferecer capacidades controladas: permissões explícitas para ferramentas, contexto limitado, execução observável e trade-offs previsíveis entre qualidade, latência, confiabilidade e custo de modelos.

Minha trajetória inclui fintech, logística e tecnologia agrícola, com liderança técnica hands-on, modernização de serviços, otimização de performance, correção de vulnerabilidades e definição de padrões de engenharia.

## Foco de Engenharia

- **Backend e sistemas distribuídos:** Java 21, Spring Boot, APIs REST, microsserviços, DDD, Clean Architecture, Kafka e RabbitMQ.
- **Cloud e entrega:** AWS, Docker, Kubernetes, OpenShift, Terraform, CI/CD, automação de infraestrutura e observabilidade.
- **Engenharia de plataformas de IA:** servidores MCP, agent harnesses, skills e toolkits, RAG, pgvector, Qdrant, engenharia de contexto e roteamento de modelos.
- **Segurança e resiliência:** menor privilégio, fronteiras seguras entre serviços, correção de dependências, validação de entradas, auditabilidade e tratamento de falhas.
- **Liderança técnica:** revisões de arquitetura, mentoria, padrões de engenharia, alinhamento de roadmap e entrega pragmática.

## Projetos em Destaque

### OrkStage - Orquestração multicloud open source

**Status:** Alfa / testes ativos · [orkstage.io](https://orkstage.io) · [Organização no GitHub](https://github.com/orkstage)

Projeto de control plane para definir e operar infraestrutura entre provedores cloud. Explora arquitetura orientada a provedores, execução de infraestrutura como código, processamento assíncrono e visibilidade centralizada de provisionamento.

A documentação do repositório deve ser usada para confirmar o estado de cada integração. Recursos em preview ou no roadmap não devem ser apresentados como prontos para produção.

### Papers Hub - Busca de chamadas para artigos científicos

**Responsabilidade:** desenvolvimento completo · **Ano:** 2025 · **Contexto:** projeto de pesquisa universitária, A Coruña, Espanha · [Website](https://papershub.net)

Plataforma para descoberta de chamadas para submissão de artigos científicos. Um processo programado de coleta em Python extrai metadados das fontes e indexa os registros no MongoDB para consulta por uma aplicação web em TypeScript.

- **Informações fornecidas:** Python, coleta programada, MongoDB, Next.js, React, Node.js e TypeScript.
- **Interpretação arquitetural:** pipeline de ingestão em lote separado da aplicação de consulta.
- A coleta foi descrita como responsável, com limites para evitar sobrecarga das fontes.
- Deduplicação, retries, monitoramento e estratégias específicas de indexação não são alegados sem confirmação adicional.

### EdukaHub / ArboEduca - Aprendizagem colaborativa

**Responsabilidade:** sócio e desenvolvedor part-time · **Período:** 2024–2025 · **País:** Brasil · [Website](https://arboeduca.com.br/)

Plataforma educacional para metodologias ativas, atividades criadas por professores e avaliação por pares.

- **Informações fornecidas:** React, TypeScript, Chakra UI, NestJS e MongoDB.
- **Interpretação arquitetural:** camada de apresentação web apoiada por uma aplicação Node.js modular e persistência documental.
- A descrição reflete uma contribuição part-time, não autoria exclusiva do produto.

### Flytech Agro - Monitoramento de pragas agrícolas

**Responsabilidade:** sócio e desenvolvedor part-time · **Período:** 2022–2024 · **País:** Brasil · [Website arquivado](https://web.archive.org/web/20220123083940/https://flytechagro.com.br/)

Plataforma de monitoramento de pragas com foco no manejo da mosca-da-fruta, combinando dashboard web, API, fluxo de treinamento de modelo e sincronização móvel/offline.

- **Informações fornecidas:** React, TypeScript, Tailwind UI, Python, FastAPI, exportação TensorFlow Lite e Firebase.
- **Interpretação arquitetural:** pipeline de treinamento separado do backend e estratégia de sincronização offline-first.
- A inferência no dispositivo só deve ser afirmada se o aplicativo realmente carregava e executava o modelo TFLite exportado.

## Showcase de Arquitetura Enterprise

Os cases abaixo são anonimizados. Eles apresentam decisões arquiteturais e fronteiras de segurança sem expor detalhes confidenciais. Devem ser descritos como casos implementados apenas na medida em que correspondam ao trabalho efetivamente realizado.

### Enterprise GenAI Orchestrator - Case confidencial

**Objetivo:** expor capacidades internas aprovadas a agentes de IA sem conceder acesso irrestrito aos sistemas corporativos.

**Fluxo conceitual:** requisição e identidade → gateway de segurança → validação de contexto → roteador LLM/Claude → servidor MCP → execução de ferramenta → controles de saída.

O desenho considera autenticação, autorização, limites de requisição e execução, validação de argumentos, isolamento por tenant, tratamento de segredos, timeouts, idempotência para operações com efeitos colaterais e auditoria. RAG não é uma fronteira de autorização: o acesso deve ser verificado antes da recuperação dos dados e novamente antes da divulgação.

### Secure Enterprise RAG Pipeline - Case confidencial

**Objetivo:** integrar recuperação de conhecimento corporativo a microsserviços Java/Spring Boot preservando a autorização por documento.

**Fluxo conceitual:**

1. Ingestão, validação, normalização e classificação de documentos.
2. Defesas em camadas contra prompt injection, tratando documentos recuperados como conteúdo não confiável.
3. Vetorização assíncrona por workers Python, com retries e observabilidade.
4. Recuperação autorizada com filtros de tenant e RBAC, revalidando permissões antes de inserir trechos no contexto do modelo.
5. Montagem de contexto mínimo, com referências às fontes.
6. Invocação do modelo, controles de saída e trilha de auditoria.

Os principais pontos de engenharia são recuperação sensível a permissões, atualização de acessos, retries assíncronos, consistência do índice, retenção de dados, avaliação de qualidade e rastreabilidade das fontes.

## Experiência Profissional

### Lead Software Engineer - Solutis Tecnologias, cliente Santander
**Nov/2025 – atual · São Paulo, Brasil**

- Projetei e implementei servidores MCP integrados a bancos vetoriais e fluxos RAG para engenharia assistida por IA.
- Estruturei agent harnesses, skills e toolkits reutilizáveis com Claude, modelos OpenAI e Devin.
- Reduzi o consumo de tokens por meio da otimização de contexto e eliminação de chamadas desnecessárias a modelos.
- Automatizei processos de desenvolvimento e operação e apliquei IA ao monitoramento de projetos e soluções em produção.
- Apoiei tooling, bibliotecas compartilhadas e práticas de Spec-Driven Development para times globais de cartões.
- Atuei na plataforma antifraude e na migração do motor de fraude de ambiente on-premises para AWS.
- Liderei a remediação de vulnerabilidades e dependências obsoletas em microsserviços.
- Liderei migrações de microsserviços legados para Java 21, Spring Boot e AWS.

### Senior Engineering Consultant - Globant, cliente PagBank
**Ago/2024 – jun/2025 · Brasil · Remoto**

- Otimizei microsserviços críticos do aplicativo, incluindo módulos do fluxo Pix.
- Conduzi refatorações para reduzir latência e melhorar estabilidade sob carga.
- Alinhei mudanças técnicas a requisitos de produto e conformidade do setor financeiro.

### Senior Engineering Consultant - Tecla T
**Mai/2024 – ago/2024 · Remoto**

- Desenvolvi integrações em Java e Spring Boot com gateways de pagamento e fintechs white label.

### Platform Software Engineer - Syngenta Digital Brasil
**Nov/2022 – mai/2024 · Remoto**

- Liderei a separação de uma funcionalidade de anotações em uma plataforma independente integrada a serviços internos.
- Desenvolvi funcionalidades e mantive microsserviços do Cropwise.
- Defini interfaces de integração entre times de engenharia.

### Senior Software Engineer - iFood
**Jan/2022 – out/2022 · Remoto**

- Contribuí para a migração da plataforma legada de logística para microsserviços.
- Entreguei funcionalidades backend e sustentei sistemas de produção com transações em tempo real.

### Experiência anterior
act digital - Senior Software Engineer (2021–2022) · Zup Innovation - Senior IT Analyst (2021) · GREat / UNIFOR - Software Developer e Senior Software Developer (2017–2021) · Experiências anteriores em desenvolvimento web e suporte de redes (2011–2017).

## Formação

- **MBA em Cibersegurança - USP/Esalq** · Em andamento, 2026–2027. Tema de pesquisa: SDK de biometria comportamental para autenticação contínua e detecção de fraude usando embeddings e banco vetorial.
- **Tecnólogo em Análise e Desenvolvimento de Sistemas - Universidade Estácio de Sá.**

## Idiomas

Português (nativo) · Inglês (B1/B2) · Espanhol (A2)

---

<sub>Os cases confidenciais são anonimizados e omitem identificadores internos, dados sensíveis e detalhes de implementação. Padrões descritos como conceituais não devem ser interpretados como afirmações sobre uma implementação específica em produção.</sub>

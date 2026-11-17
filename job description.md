# Capgemini AI Engineer — Job Description & Role Requirements

> **Source:** Recruiter-supplied “AI Engineer” job specification, file dated **15 October 2026** (reviewed 17 November 2026).  
> **Document status:** Historical supplied job description and practical preparation guide; **not** a live-vacancy confirmation or an official assessment guide.  
> **Related project:** [Nebula — Email Outreach Agent](INSTRUCTIONS.md). The proposed project demonstrates relevant engineering techniques but does not replace professional experience or guarantee selection.

## 1. Position at a glance

| Field | Supplied job description |
| --- | --- |
| Employer | Capgemini |
| Job title | AI Engineer |
| Function | Engineering Augmentation |
| Location | Anywhere in the UK or remote; Greater London preferred |
| Experience | **2+ years of professional software engineering**, including hands-on LLM application or agent development |
| Start date | “Immediate” in the supplied specification dated 15 October 2026 |
| Working relationship | Follow standards and patterns set by the AI Engineering Lead |

**Purpose of the role:** Build, test, deploy and support AI agents, automations and reusable accelerators that help delivery teams work faster and adopt AI.

> **Eligibility distinction:** The **2+ years' professional software-engineering experience** is an explicitly stated role requirement. A portfolio agent, however sophisticated, is **not automatically equivalent** to that experience. The employer decides what experience it accepts.

## 2. Key responsibilities — employer-stated

1. Build agents, tools, prompts, workflows and integrations connected to delivery tooling.
2. Implement human-approval checkpoints and safe failure handling according to the agreed design.
3. Write and maintain evaluation test cases; run evaluations before each release.
4. Add tracing and telemetry, including **usage, cost and adoption** measures.
5. Support delivery teams with implementation, testing and troubleshooting.
6. Improve systems and reusable accelerators using feedback, evaluation evidence and telemetry.

## 3. Required skills — employer-stated

The following reproduces the **substance** of all twelve requirements in the supplied job description.

| # | Capability | What the JD requires |
| --- | --- | --- |
| 1 | **Python engineering** | Clean, testable code; virtual environments, packaging and pytest unit tests |
| 2 | **APIs and data** | Build and call REST APIs; JSON, authentication tokens, and error handling |
| 3 | **Development/delivery** | Daily Git skills and working knowledge of CI/CD pipelines and Docker |
| 4 | **LLM application development** | Prompt design; tool/function calling; structured JSON outputs; token budgets and context limits |
| 5 | **Agent implementation** | At least one agent or multi-step workflow using an appropriate agent framework |
| 6 | **Agent design patterns** | ReAct, plan-and-execute, routing, and judgement about when a deterministic script is sufficient |
| 7 | **RAG** | Chunking, embeddings and querying a vector store |
| 8 | **MCP** | Awareness of Model Context Protocol and how to expose a tool to an agent |
| 9 | **LLM evaluation** | Evaluation test cases and familiarity with a tracing/evaluation tool |
| 10 | **AI safety** | Prompt injection, output validation and sensitive-data handling |
| 11 | **Engineering approach** | Problem solving, debugging and rapid prototyping |
| 12 | **Learning and communication** | Learn new AI tools quickly and explain technical trade-offs clearly |

**Framework clarification:** The JD gives **LangGraph, Semantic Kernel/Microsoft Agent Framework, OpenAI Agents SDK, Claude Agent SDK and CrewAI as examples**. It does **not** require implementing every listed framework. Its tracing/evaluation examples include promptfoo, LangSmith and Langfuse; one tool used competently is the appropriate evidence.

## 4. What you need to demonstrate to compete for this role

The table below is **preparation guidance**, not extra employer-mandated criteria. It translates the JD into demonstrable evidence.

| Requirement | Strong, inspectable evidence |
| --- | --- |
| Professional experience | Accurate employment history explaining what you personally built, tested, maintained and supported; distinguish production work from assisted prototypes |
| Python, packaging, pytest | Installable Python package; typed interfaces; pytest results; one independently explained bug fix |
| REST/JSON/auth | Validated FastAPI endpoints; request/response schemas; OAuth or token handling; 400/401/429/5xx and timeout tests |
| Git/Docker/CI | Reviewable commits, versioned dependencies, a reproducible container and a CI pipeline that blocks broken changes |
| LLM tools and structured output | Live demonstration of a model invoking an allowed tool, returning schema-valid JSON and respecting context/output limits |
| Agent architecture | Explain graph nodes, edges, typed state, conditional routing, checkpointing, interrupt/resume and stopping rules |
| ReAct and plan-and-execute | Trace one bounded tool-observation loop and one validated multi-step plan; justify deterministic alternatives |
| RAG | Demonstrate document ingestion, chunking, embeddings, vector search, filtering, evidence citations and abstention for missing support |
| MCP | Run a minimal server exposing a typed read-only tool; show a client discovering/calling it and handling invalid arguments |
| Human-in-the-loop | Demonstrate first-email review, rejection/edit, exact-content approval, scoped remaining-batch mode and safe interruption |
| Robustness | Show duplicate suppression, idempotent send intent, crash recovery and reconciliation of an uncertain Gmail response without blind resending |
| Evaluation | Versioned offline test cases plus LLM-output checks; demonstrate that a failing regression blocks release |
| Tracing and telemetry | Correlated traces, latency/errors and measured usage; document cost assumptions and meaningful adoption metrics |
| Security | Prompt-injection tests, secret isolation, input/output validation, read-only tools, PII redaction and least-privilege access |
| Communication and debugging | Walk through a real failure, its root cause, the fix, a regression test and the design trade-off |

## 5. Using Nebula as a role-relevant project

The [Nebula architecture specification](INSTRUCTIONS.md) deliberately targets these role capabilities. Its proposed responsibilities are:

- **LangGraph** — sole outer orchestrator: planning, routing, graph state, durable checkpoints, approval interrupts and recovery.
- **LangChain** — prompts, structured outputs, tool integration and evidence-grounded RAG.
- **OpenAI Agents SDK** — a bounded, read-only evidence-review specialist with MCP tool access, **not** a second campaign controller or an email sender.
- **LangSmith** — tracing, evaluation and debugging, with privacy and free-tier controls.
- **Ollama** — local open-weight generation and embedding models without mandatory paid inference.
- **FastAPI, PostgreSQL/pgvector, Docker and GitHub Actions** — application boundaries, durable state, retrieval, reproducible execution and release checks.
- **Gmail, Google Drive and Atlas** — external providers behind authenticated, independently testable adapters.

**Important:** These are **design commitments**, not completed implementation claims. A listed file, architecture diagram or passing scaffold smoke test is not proof of live provider integration, independently written code, production reliability or the candidate's professional experience.

### Minimum project walkthrough to prepare

Practice explaining the following scenario from first principles, using actual code and verified runs once implemented:

1. A user requests **N email-only outreach units for one country** and supplies approved CV facts and a career-intent policy.
2. The graph validates the request, researches permitted professional contacts, checks historical outreach and suppresses duplicates.
3. The RAG pipeline retrieves approved evidence; the generator creates a grounded CV and email; the SDK specialist reviews claims through read-only MCP tools.
4. Deterministic validators check facts and policy. The user approves the **first exact email/recipient/CV**, then selects individual review or bounded automation for the remaining units.
5. A controlled Gmail adapter sends an authorised message and reconciles its outcome. Checkpoints and a send ledger prevent blind retries.
6. Source references, receipts and documents are retained; LangSmith/local metrics support diagnosis; feedback feeds a reviewed regression test before release.

A strong explanation must cover **why this design uses an agent for uncertain research but deterministic code for rules and sending**. The project must never treat a Gmail Sent copy as proof of inbox delivery, employer response or a formal job application.

## 6. L1/L2 interview and assessment preparation checklist

The original JD does **not** specify exact interview rounds, questions, marking criteria or assessment duration. The items below are recommended ways to prepare, **not confirmed Capgemini interview questions**.

- [ ] Explain in Python how functions, dictionaries, type hints, exceptions and pytest fixtures support a graph node.
- [ ] Trace an HTTP request through FastAPI validation, authentication, service logic and a structured response.
- [ ] Explain tool calling vs ordinary model text, including input schemas, JSON errors and execution permissions.
- [ ] Draw a LangGraph state transition with routing, an approval interrupt and a safe resume.
- [ ] Compare ReAct, plan-and-execute and deterministic orchestration, naming a sensible use case for each.
- [ ] Walk through chunking, embeddings, similarity search, provenance, retrieval failure and hallucination prevention.
- [ ] Demonstrate a typed MCP tool and explain the client/server permission boundary.
- [ ] Show a real LLM trace and explain latency, token usage, error attribution and evaluation metrics.
- [ ] Diagnose a prompt-injection attempt from an untrusted job page and identify which boundary stops it.
- [ ] Debug a simulated duplicate email, a Gmail timeout, a failed database commit and an expired token.
- [ ] Demonstrate local Docker startup and the CI tests that gate a change.
- [ ] Recount a genuine implementation failure and what was changed, tested and learned.
- [ ] Clearly distinguish personal contributions from AI-assisted build work, design-only components and production work.

**Interview-level goal:** independently explain, trace, modify and debug the core agent/RAG/Python behaviour. Reading or displaying a finished repository is not equivalent to demonstrating those skills.

## 7. Requirements not established by the supplied JD

The supplied specification **does not establish** a salary, visa sponsorship policy, current vacancy status, guaranteed remote-from-anywhere permission, recruiter decision, interview format, evaluation pass mark or offer likelihood. Confirm these directly with the employer. The historic “Immediate” start date should not be treated as a live November 2026 deadline without fresh confirmation.

**Document control:** This file preserves the employer's role information and labels additional preparation advice separately. Update the source snapshot only when a newer employer-authenticated JD is received; do not silently rewrite the original requirements.

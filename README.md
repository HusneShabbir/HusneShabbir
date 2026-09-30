# Husne Shabbir

**Associate Software Quality Engineer**
Red Hat · Bangalore, India

[github.com/HusneShabbir](https://github.com/HusneShabbir) · husneshabbir447@gmail.com

## Summary

Quality engineer for [Red Hat Developer Hub](https://developers.redhat.com/rhdh). I evaluate Lightspeed RAG answers with DeepEval, and I write the Playwright, integration, and CI coverage that ships with Intelligent Assistant, MCP integrations, and model serving. **111 merged pull requests**, including **68** in [redhat-developer](https://github.com/redhat-developer).

## Experience

### Associate Software Quality Engineer
**Red Hat** · Bangalore, India

- Built a pytest suite that scores Lightspeed RAG answers with DeepEval. A local Ollama model (`mistral:7b`) is the judge. Core checks are answer relevancy, faithfulness, bias, and hallucination. Optional GEval checks cover informativeness, clarity, completeness, tone, and broken generation. Reports keep the judge’s reason, RAG latency, and score movement across runs.
- Automated Intelligent Assistant in Developer Hub: notebook flows for Release 2.1, saved prompts, screen context, RBAC permissions, and bring-your-own-key RAG source labels.
- Added the Lightspeed end-to-end workspace and notebook coverage in the plugin export overlays, including a backport to release 1.10.
- Covered Model Context Protocol integrations: Kubernetes actions, orchestrator tools, scorecard tools, and dynamic client registration.
- Added Playwright coverage for the KServe / Kubeflow connector, and kept the AI rolling-demo CI running with a gpt-4o-mini fallback while the vLLM endpoint was down.
- Landed topology and ACR end-to-end tests, including i18n, in Backstage community plugins.
- Added a Jira integration and a Feature-to-QE planner to the automation-coverage MCP, so a product Feature can be split into the cheapest useful test layer.

## Skills

| | |
| --- | --- |
| AI evaluation | DeepEval, GEval, answer relevancy, faithfulness, bias, hallucination, Ollama, vLLM |
| Test automation | Playwright (TypeScript and Python), pytest, React Testing Library, Backstage `startTestBackend`, GitHub Actions |
| Platforms | Red Hat Developer Hub, Backstage, Kubernetes, OpenShift, Helm, GitOps, Model Context Protocol |
| Languages | TypeScript, JavaScript, Python, Shell |

## Projects

**[rhdh-Lightspeed-Evaluation](https://github.com/HusneShabbir/rhdh-Lightspeed-Evaluation)**
RAG evaluation for Developer Hub Lightspeed. Calls the Lightspeed API, attaches retrieved context, scores the answer with a local Mistral judge, and writes an HTML report with metric trends. Playwright refreshes the bearer token when the target is a local Developer Hub.

**[LLMEvaluation_Deepeval_Learnings](https://github.com/HusneShabbir/LLMEvaluation_Deepeval_Learnings)**
Working notes on DeepEval before a metric goes into the Lightspeed suite: factual accuracy, coherence, toxicity, and custom criteria.

**[automation-coverage-mcp](https://github.com/rhdh-pai-qe/automation-coverage-mcp)**
Coverage-driven test planning for RHDH plugins, with a Jira path from a Feature to concrete test work.

## Open source

| Project | Merged | Contribution |
| --- | ---: | --- |
| [redhat-developer/rhdh-plugins](https://github.com/redhat-developer/rhdh-plugins) | 46 | Assistant, MCP, Boost, and KServe coverage |
| [redhat-developer/rhdh](https://github.com/redhat-developer/rhdh) | 14 | Showcase tests for scorecard, catalog, and adoption insights |
| [redhat-developer/rhdh-plugin-export-overlays](https://github.com/redhat-developer/rhdh-plugin-export-overlays) | 8 | Lightspeed and Intelligent Assistant end-to-end tests |
| [redhat-ai-dev/ai-rolling-demo-gitops](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops) | 5 | GitOps CI and model-serving coverage |
| [backstage/community-plugins](https://github.com/backstage/community-plugins) | 3 | Topology and ACR end-to-end tests, including i18n |
| [rhdh-pai-qe/automation-coverage-mcp](https://github.com/rhdh-pai-qe/automation-coverage-mcp) | 2 | Jira-driven test planning |

Further merged pull requests are on collaborator forks of these repositories, usually during review. Full list: [merged pull requests](https://github.com/search?q=author%3AHusneShabbir+is%3Apr+is%3Amerged&type=pullrequests).

### Selected pull requests

- [Notebook Release 2.1 end-to-end coverage](https://github.com/redhat-developer/rhdh-plugins/pull/4551)
- [RBAC permission tests for Intelligent Assistant](https://github.com/redhat-developer/rhdh-plugins/pull/4693)
- [BYOK RAG source label tests](https://github.com/redhat-developer/rhdh-plugins/pull/4650)
- [Lightspeed end-to-end workspace](https://github.com/redhat-developer/rhdh-plugin-export-overlays/pull/2453)
- [KServe / Kubeflow connector tests](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops/pull/339)
- [Topology end-to-end tests](https://github.com/backstage/community-plugins/pull/6344) and [ACR tests with i18n](https://github.com/backstage/community-plugins/pull/6365)
- [Feature-to-QE ticket planner](https://github.com/rhdh-pai-qe/automation-coverage-mcp/pull/3)

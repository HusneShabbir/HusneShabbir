<div align="center">

# Husne Shabbir

**Associate Software Quality Engineer at Red Hat** · Bangalore, India

I test whether an AI answer is actually good. On [Red Hat Developer Hub](https://developers.redhat.com/rhdh) that means scoring Lightspeed RAG responses for faithfulness and hallucination, then automating the product those models sit inside.

[Merged pull requests](https://github.com/search?q=author%3AHusneShabbir+is%3Apr+is%3Amerged&type=pullrequests) · [Lightspeed RAG evaluation](https://github.com/HusneShabbir/rhdh-Lightspeed-Evaluation) · [DeepEval notes](https://github.com/HusneShabbir/LLMEvaluation_Deepeval_Learnings)

</div>

## AI evaluation

I built [rhdh-Lightspeed-Evaluation](https://github.com/HusneShabbir/rhdh-Lightspeed-Evaluation), a pytest suite that calls the Lightspeed RAG API and scores every answer with [DeepEval](https://github.com/confident-ai/deepeval). The judge is a local Ollama model (`mistral:7b`, with `deepseek-r1:8b` as a fallback), so scoring does not depend on a hosted eval API. When the target is a local Developer Hub, Playwright opens the Lightspeed UI and refreshes the bearer token before the run.

Each case is an `LLMTestCase`: the question, the model answer, and the retrieved context. Core metrics always run. A second set of custom [GEval](https://deepeval.com/docs/metrics-llm-evals) checks turns on with `ENABLE_GENERAL_EVAL_METRICS`.

| Metric | What a failure means |
| --- | --- |
| Answer relevancy | The answer does not address the question |
| Faithfulness | Claims drift outside the retrieved context |
| Hallucination | The answer adds facts the context does not support |
| Bias | The wording is skewed or unfair |
| Informativeness | The answer stays generic and adds no depth |
| Clarity | A reader in this product cannot follow it |
| Completeness | Part of the question is left unanswered |
| Tone | The voice does not fit the context |
| Output glitch | Repeated tokens, broken casing, or other generation noise |

Faithfulness and hallucination run only when retrieval context exists, so a missing context does not get scored as a faithful answer. The suite asserts DeepEval’s success threshold and keeps the judge’s reason next to the score. pytest writes a self-contained HTML report with metric charts, RAG latency, and the delta against earlier runs stored in `test_history.jsonl`.

The companion repo, [LLMEvaluation_Deepeval_Learnings](https://github.com/HusneShabbir/LLMEvaluation_Deepeval_Learnings), is where I try metrics before they land in that suite: factual accuracy, coherence, toxicity, and custom criteria.

```text
question → Lightspeed RAG (vLLM or the configured provider)
        → answer + retrieved context
        → local Mistral judge
        → score, reason, latency
        → threshold gate + HTML trend report
```

## The product around the model

Evaluation only matters if the assistant, the retrieval path, and the cluster are testable. That work is in upstream Red Hat repositories.

| Surface | What I added |
| --- | --- |
| [Intelligent Assistant](https://github.com/redhat-developer/rhdh-plugins) | Notebook e2e for Release 2.1, saved prompts, screen context, RBAC permission tests, [BYOK RAG source labels](https://github.com/redhat-developer/rhdh-plugins/pull/4650) |
| [Lightspeed overlays](https://github.com/redhat-developer/rhdh-plugin-export-overlays) | [E2E workspace](https://github.com/redhat-developer/rhdh-plugin-export-overlays/pull/2453) and [notebook coverage](https://github.com/redhat-developer/rhdh-plugin-export-overlays/pull/2605), backported to release 1.10 |
| [AI rolling demo](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops) | Playwright TypeScript migration, [KServe / Kubeflow connector e2e](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops/pull/339), and a [CI fallback to gpt-4o-mini](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops/pull/364) while the vLLM endpoint is down |
| MCP integrations | Kubernetes actions, orchestrator tools, scorecard tools, and dynamic client registration |
| Model serving | KServe connector coverage in plugins and in the GitOps demo |

## Open source

**111 merged pull requests**, **68** of them in [redhat-developer](https://github.com/redhat-developer).

| Project | Merged | Focus |
| --- | ---: | --- |
| [rhdh-plugins](https://github.com/redhat-developer/rhdh-plugins) | 46 | Assistant, MCP, Boost, and KServe test coverage |
| [rhdh](https://github.com/redhat-developer/rhdh) | 14 | Showcase e2e for scorecard, catalog, and adoption insights |
| [rhdh-plugin-export-overlays](https://github.com/redhat-developer/rhdh-plugin-export-overlays) | 8 | Lightspeed and Intelligent Assistant e2e |
| [ai-rolling-demo-gitops](https://github.com/redhat-ai-dev/ai-rolling-demo-gitops) | 5 | GitOps CI and model-serving coverage |
| [community-plugins](https://github.com/backstage/community-plugins) | 3 | Topology and ACR e2e, including i18n |
| [automation-coverage-mcp](https://github.com/rhdh-pai-qe/automation-coverage-mcp) | 2 | Jira-driven planning from a Feature down to the cheapest test layer |

Other merged pull requests are on collaborator forks of these repositories, usually while a change is still in review.

A few that show the range beyond the AI suites: [topology e2e](https://github.com/backstage/community-plugins/pull/6344) and [ACR e2e with i18n](https://github.com/backstage/community-plugins/pull/6365) in Backstage community plugins, [Boost catalog coverage](https://github.com/redhat-developer/rhdh-plugins/pull/4501), and the [Feature-to-QE planner](https://github.com/rhdh-pai-qe/automation-coverage-mcp/pull/3).

## Stack

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img alt="DeepEval" src="https://img.shields.io/badge/DeepEval-111111?style=flat-square&logo=pytest&logoColor=white" />
  <img alt="Ollama" src="https://img.shields.io/badge/Ollama-black?style=flat-square&logo=ollama&logoColor=white" />
  <img alt="pytest" src="https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white" />
  <img alt="Playwright" src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" />
  <img alt="Jupyter" src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white" />
</p>
<p>
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" />
  <img alt="React" src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" />
  <img alt="Backstage" src="https://img.shields.io/badge/Backstage-9BF0E1?style=flat-square&logo=backstage&logoColor=black" />
  <img alt="Kubernetes" src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white" />
  <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" />
</p>

DeepEval · Ollama · vLLM · RAG metrics · pytest · Playwright (Python and TypeScript) · React Testing Library · Backstage · Model Context Protocol · OpenShift · GitOps

## GitHub activity

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=HusneShabbir&show_icons=true&hide_border=true&theme=tokyonight&rank_icon=percentile&include_all_commits=true" />
  <img height="165" alt="GitHub stats for Husne Shabbir" src="https://github-readme-stats.vercel.app/api?username=HusneShabbir&show_icons=true&hide_border=true&theme=default&rank_icon=percentile&include_all_commits=true" />
</picture>
&nbsp;
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=HusneShabbir&layout=compact&hide_border=true&theme=tokyonight&langs_count=6&include_all_commits=true" />
  <img height="165" alt="Most used languages for Husne Shabbir" src="https://github-readme-stats.vercel.app/api/top-langs/?username=HusneShabbir&layout=compact&hide_border=true&theme=default&langs_count=6&include_all_commits=true" />
</picture>

<br />

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=HusneShabbir&hide_border=true&theme=tokyonight" />
  <img height="165" alt="Contribution streak for Husne Shabbir" src="https://streak-stats.demolab.com?user=HusneShabbir&hide_border=true&theme=default" />
</picture>

</div>

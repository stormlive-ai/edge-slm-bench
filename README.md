# edge-slm-bench

**Reproducible Evaluation Harness & Synthetic Distillation Pipeline for Specialized On-Device Small Language Models (SLMs)**

[![License: MIT](https://shields.io)](https://opensource.org)
[![Status: Active Research](https://shields.io)]()
[![Focus: On-Device AI](https://shields.io)]()

## Overview

`edge-slm-bench` is an open-source research repository investigating the trade-offs between **parameter scaling, quantization, and domain specialization** for compact language models (`0.5B` to `3B` parameters) running locally on resource-constrained mobile hardware.

Rather than evaluating general-purpose world knowledge, this project focuses on how **frontier-model synthetic distillation** and **multi-agent evaluation pipelines** can compress high-accuracy, specialized capabilities (structured extraction, offline tool routing, and localized reasoning) into sub-2GB memory footprints suitable for mobile NPUs and CPUs.

---

## Core Research Objectives

1. **High-Signal Synthetic Distillation:** Utilizing frontier reasoning models (via multi-agent orchestration in Google Antigravity) to generate verified, domain-specific instruction and preference datasets with minimal noise.
2. **Quantization vs. Task Fidelity:** Measuring accuracy degradation across `FP16`, `INT8`, and `INT4` (GGUF / LiteRT / ExecuTorch) formats on narrow, structured mobile tasks where small models frequently hallucinate.
3. **Hardware-Aware Benchmarking:** Profiling real-world mobile metrics alongside accuracy:
   - Time-to-First-Token (TTFT) and generation throughput (tokens/sec)
   - Peak RAM allocation and KV-cache growth
   - Thermal throttling and battery draw over multi-turn sessions
4. **Automated Agentic Grading:** Replacing brittle string-match metrics with reproducible, rubric-driven multi-agent evaluators for edge outputs.

---

## Planned Repository Structure

```text
edge-slm-bench/
├── configs/                # Distillation prompts, task schemas, and quantization configs
├── distillation/           # Multi-agent synthetic dataset generation & filtering scripts
├── eval_harness/           # Automated rubric grading & structured output validators
├── mobile_profiler/        # On-device latency, memory, and throughput logging utilities
├── benchmarks/             # Curated evaluation splits for specialized mobile tasks
└── docs/                   # Methodology notes, hardware test matrices, and findings
```

---

## Target Model & Runtime Matrix

* **Candidate Base Architectures:** Compact open-weight backbones (`0.5B` – `3B` parameter class)
* **Quantization Schemes:** `Q4_K_M`, `Q8_0`, `INT4-AWQ`, and dynamic 4-bit quantization
* **Target Mobile Runtimes:** LiteRT (TensorFlow Lite), ExecuTorch, llama.cpp (ARM NEON / Vulkan), and ONNX Runtime Mobile

---

## Research Roadmap (Q4 2026 – Q2 2027)

- [x] **Phase 1 — Scope & Architecture:** Define specialized mobile task taxonomy (offline JSON/schema extraction, local intent routing, concise summarization) and evaluation metrics.
- [ ] **Phase 2 — Synthetic Data Pipeline:** Build multi-agent synthetic data generation and verification workflows to curate high-density training splits.
- [ ] **Phase 3 — Fine-Tuning & Quantization:** Run LoRA/QLoRA adaptation and post-training quantization sweeps across sub-3B candidate models.
- [ ] **Phase 4 — On-Device Profiling & Release:** Benchmark across physical Android/ARM edge devices, publish open-weight adapters, and release an accompanying research preprint.

---

## License & Non-Commercial Research Notice

This project is developed strictly for **open, non-commercial scientific research**. All evaluation scripts, synthetic data schemas, and benchmark findings will be released under the **MIT License** to support reproducible on-device AI research.

## Maintainer

**Rovaid Khan**  
Independent AI Researcher · MSc in Data Analytics & Artificial Intelligence (Hong Kong Baptist University)

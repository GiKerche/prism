# PRISM

**Transfer and Limits of Activation Interventions in Tool-Calling Language Models**

This repository accompanies the final author manuscript dated 11 October 2026.
It contains the paper, experimental inputs, frozen fitting artifacts, response-level
outcomes, analysis code, and the three LoRA adapters evaluated in the paper.

[Read the paper](paper/main.pdf) · [Reproduce the results](REPRODUCIBILITY.md) ·
[Experimental code](experiments/README.md) · [Verification](reproduction/verification.json)

## Reproduce the published results

The statistical checks run locally on CPU, without model downloads, API keys,
or calls to an external judge:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
make reproduce
```

For a smaller first check, run `python paper/analysis/reproduce_primary.py`.
To refit every construction probe as well, run `make refit`.

The checks cover the main effects, language transfer and Arabic, BFCL capability,
source and receiver controls, LoRA, SODA, layer selection, intervention directions,
PCA/ridge transport, dose selection, label scarcity, and the complete Llama70B
evaluator panel. Results are conditional on the recorded automatic labels;
reproducing the statistics does not independently validate the judges.

## Contents

| Location | Contents |
| --- | --- |
| `paper/` | Final 31-page PDF, LaTeX/Overleaf sources, tables and figures |
| `paper/task/` | LUMEN scenarios, translations, tools, prompt contexts, family partitions and judge rubrics |
| `paper/data/` | Published numerical exports and compressed response-level endpoints |
| `paper/analysis/` | Family-bootstrap estimators and result verification scripts |
| `reproduction/` | Construction/validation activations, labels, probes, directions, benign anchors, maps and LoRA adapters |
| `experiments/` | Model revisions, generation/steering code, parsers, benchmark interfaces and LoRA training code |

This release contains one final study configuration. Both Llama models use
Prompt/Python for BFCL; Qwen and Ministral use their native tool interfaces.
Llama70B uses transported doses `+4/-4` and receiver-native doses `+8/-4`.
The Validation II capability tolerance is five percentage points.

The numerical artifacts make this repository larger than a paper-only release.
They contain numeric arrays, not base-model checkpoints. Base models and
external benchmark software retain their upstream access and licensing terms.

## Build the manuscript

```bash
make figures
make paper
```

Use `paper/main.tex` as the root file in Overleaf. The build needs a LaTeX
installation with the packages declared there; shell escape is disabled.

Private credentials, machine addresses, cluster configuration, scheduler jobs,
operational logs and local account paths are not part of this release.
Only aggregate scientific measurements of resource use are retained.

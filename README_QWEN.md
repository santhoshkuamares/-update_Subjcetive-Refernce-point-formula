# Ipseitas Gap Learner with Qwen

This repository contains a small proof-of-concept implementation of the **Ipseitas Framework** using a Hugging Face Qwen instruction model.

The project demonstrates a recursive learning loop based on the theory that cognition can be modeled as information-gap reduction relative to a **Subjective Reference Point (SRP)**. The system generates an information gap, asks a sub-question, answers it, evaluates progress metacognitively, and updates a temporary self-model.

This is **not** a claim of AI consciousness. It is a computational prototype showing how the theoretical framework can be implemented as a recursive self-questioning and gap-reduction pipeline.

## Files

- `ipseitas_pipeline.py`  
  Main pipeline code. It contains the `IpseitasGapLearner`, model providers, metacognitive evaluation logic, and output-saving functions.

- `qwen_run.py`  
  Example script for running the pipeline with a Hugging Face Qwen model.

- `requirements.txt`  
  Python dependencies needed to run the project.

- `sample_output.md`  
  Example readable output from a run.

- `sample_output.json`  
  Example structured output from a run, if generated.

## Model Used

The Qwen example uses:

```python
Qwen/Qwen2.5-1.5B-Instruct
```

This model is loaded through Hugging Face Transformers.

## Installation

Install the required packages:

```bash
pip install transformers torch accelerate
```

If using Google Colab, run:

```python
!pip install transformers torch accelerate -q
```

## How to Run in Google Colab

Upload the project files or unzip the project folder, then run:

```python
from ipseitas_pipeline import IpseitasGapLearner, HuggingFaceLLM

norm = """
Understand why particles can behave like waves and how this relates to the double-slit experiment.
"""

provider = HuggingFaceLLM(model_name="Qwen/Qwen2.5-1.5B-Instruct")

learner = IpseitasGapLearner(provider=provider)

result = learner.run(norm_of_study=norm, steps=3)

report = learner.report_markdown(norm)
print(report)
```

## How the Pipeline Works

The system follows this sequence:

```text
Norm of Study
→ Information Gap
→ Self-Generated Sub-Question
→ Answer
→ Metacognitive Evaluation
→ Self-Model Update
→ Next Gap or Closure
```

The purpose is to show that the system does not only answer a question once. It tracks what it knows, what remains uncertain, and whether the current answer reduces the active information gap.

## Metacognitive Evaluation

The pipeline evaluates progress using several dimensions:

- gap reduction
- coherence gain
- compression potential
- confidence calibration
- evidence grounding
- false closure risk

These dimensions are used to decide whether the system should continue inquiry or treat the gap as sufficiently reduced.

## Example Norm of Study

```text
Understand why particles can behave like waves and how this relates to the double-slit experiment.
```

## Important Note

This prototype does not update the neural weights of the model. It only updates a temporary working self-model during the run. Therefore, it should be understood as a proof-of-concept for recursive metacognitive processing, not as a complete model of consciousness or biological cognition.

## Thesis Relevance

This implementation supports the thesis by showing that the Ipseitas Framework can be translated into a computational process. It demonstrates that a system can:

1. identify a knowledge gap,
2. generate a sub-question,
3. answer the sub-question,
4. evaluate whether progress was made,
5. update a working self-model,
6. continue inquiry if the gap remains unresolved.

## License

This project is for academic and demonstration purposes.

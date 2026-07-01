# Hype-or-Truth: UXR-b Benchmark Suite

An un-cooked, absolute evaluation framework measuring raw visual layout replication, prompt specification compliance, and generation velocity.

## Repository Architecture

Download or reference these core configuration files to align your evaluation pipeline:
* `Rulebook.txt` — The strict baseline rules and disqualification parameters.
* `vllm_promptmaker.txt` — Translates core layout concepts into strict Detail Scale (D) values.
* `vllm_designmaker.txt` — System instructions forcing models to emit pure code output.
* `vllm_designjudge.txt` — The spatial layout evaluation engine prompt for the Judge AI.

---

## Technical Specifications

The benchmark uses two evaluation scopes to establish a model's true performance curve:

1. **One-Config Test:** Isolates a single specific configuration tracking performance across the Prompt Detail Intensity ($D$ Scale) to find the exact boundary where a model's capability drops off.
2. **General Baseline Index:** An un-padded macro score showing the total average across all configuration parameters, styles, and community prompts.

---

## Quickstart Guide

### 1. Pick Your Evaluation Path
Choose between the two core testing vectors based on your benchmarking goals:
* **Visual (V) Mode:** The primary track. Focuses on spatial layout, absolute coordinate matching, and structural grid convergence.
* **Text (T) Mode:** The semantic track. Focuses on structural hierarchy, text element placement, and markdown/tag accuracy.

### 2. Source Your Target Layouts
If you selected **Visual (V) Mode**, prep your testing assets:
* **Custom Route:** Take a clean screenshot of the static GUI mockup you want your model to replicate. Ensure it matches your target baseline frame resolution.
* **Standard Route:** Use the built-in reference mockups pre-loaded within the repository's evaluation asset directory to prevent data profile contamination.

### 3. Generate the Prompt Specification
Use `vllm_promptmaker.txt` to structure your design concept. Pass your raw layout requirements through this prompt configuration to apply your target Detail Scale ($D$) properties. This step outputs the exact technical layout instructions for the evaluation run.
$\color{red}{\text{On V: Attach your Image and let it run, then reattach the image to step 4}}$
$\color{green}{\text{On T: Attach your Image and let it generate the prompt do not reattach it on step 4 as T means your model is physically incapable of seeing images, for this use Gemini,Qwen,Kimi,GLM or any other free model to not waste money!}}$

### 4. Execute the Target Model (Design Maker)
Take the generated prompt specification from Step 3 and feed it to the fresh instance of the model you are testing via your chosen Chat GUI or API endpoint. You must attach the instructions from `vllm_designmaker.txt` as the system prompt to force the model to output pure standalone code. Note the exact execution time from the first token to the completed output stream.

### 5. Run the Evaluation (Design Judge)
Pass the final code rendering or static frame screenshot to your vision-capable evaluation model. Feed it the strict grading rubric inside `vllm_designjudge.txt` to calculate the final visual parity percentage score and output the telemetry logs.

---

## Submission Protocol

To submit your model logs to the live index leaderboard on the Hugging Face Space, open an issue or pull request containing your structured database block alongside an unedited screen recording showing the final static frame execution output.

Every submission block must follow this JSON telemetry schema perfectly or it will face automatic rule filtering:

```json
{
  "model": "Your-Model-Name",
  "config": {
    "run_type": "One-Config or Multi-Config",
    "mode": "modeyouused",
    "detail_scale_d": 0.40,
    "tries_spent": 1
  },
  "telemetry": {
    "replica_percentage": e.g 94.5,
    "time_taken_seconds": e.g 8.42,
    "calculated_u_s": e.g 0.9852
  }
}

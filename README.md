# Digital Forensics Final Project

## Project overview

This repository documents a digital forensic investigation of **text, image, audio, and video** evidence using an AI agent and independent validation. It preserves the original inputs, any prepared inputs, exact prompts, complete agent outputs, screenshots, validation records, and scripts so another examiner can inspect and repeat the observable steps.

## Final deliverables

- **Final report (including appendices):** [`report/final_report.pdf`](report/final_report.pdf)
- **Final presentation:** [`presentation/final_presentation.pptx`](presentation/final_presentation.pptx)

These links will work once the files have been added at the specified paths.

## Final commit identifier

**Submitted commit SHA:** `TO_BE_RECORDED_AT_SUBMISSION`

After all project files are committed, obtain the SHA using:

```bash
git rev-parse HEAD
```

**Important:** Editing this README to insert a commit SHA creates a *new* commit. Record the final submitted SHA in the submission portal or a release/tag record as well, and ensure that it matches the version submitted for grading. A README cannot contain its own final commit hash without changing that hash.

## Repository organization

```text
README.md
report/
  final_report.pdf
presentation/
  final_presentation.pptx
environment/
text/
image/
audio/
video/
```

Each of `text/`, `image/`, `audio/`, and `video/` contains:

```text
test_record.md
evidence/
  original/
  prepared/
prompts/
outputs/
screenshots/
validation/
scripts/
```

| Path | Purpose |
| --- | --- |
| `report/` | Complete final PDF report and appendices. |
| `presentation/` | Final PowerPoint presentation. |
| `environment/` | Installation notes, OS/tool/agent versions, model and provider, relevant permissions, settings, and sanitized configuration. **Never commit passwords, API keys, tokens, or private credentials.** |
| `text/`, `image/`, `audio/`, `video/` | Separate investigations organized by evidence type. |
| `*/test_record.md` | Complete required eight-field investigation record for that evidence type. |
| `*/evidence/original/` | Verified, unchanged original evidence; preserve source and record cryptographic hashes. |
| `*/evidence/prepared/` | Inputs derived before analysis, e.g., OCR, transcripts, extracted frames, conversions; include a short `README.md` if no preparation was needed. |
| `*/prompts/` | Exact initial and follow-up prompts in order. |
| `*/outputs/` | Complete agent responses, action/tool logs, errors, and agent-generated files, with sensitive details removed. Do not put prepared input evidence here. |
| `*/screenshots/` | Numbered, legible screenshots of steps, important results, errors, and checks. |
| `*/validation/` | Independent checks, hash records, comparisons, and supporting results. |
| `*/scripts/` | Commands or scripts used to prepare, inspect, or validate evidence. |

## Investigation environment

The planned investigation environment uses **Kali Linux**, **Hermes**, and a local language model served through **Ollama**. Record the *actual* software versions, model name/tag, provider, permissions, installation commands, and relevant settings in `environment/`. Do not assume that a tool or model was used unless it appears in the investigation record.

Suggested environment checks:

```bash
cat /etc/os-release
uname -a
ollama --version
ollama list
```

Record the Hermes version using the version-reporting method supported by the installed release. Save sanitized outputs in `environment/`.

## Reproducing the observable investigation

1. Clone the repository and check out the **submitted commit SHA**:
   ```bash
   git clone <REPOSITORY_URL>
   cd <REPOSITORY_DIRECTORY>
   git checkout <SUBMITTED_COMMIT_SHA>
   ```
2. Read `environment/` and recreate the documented operating system, tool versions, AI agent, model, provider, and relevant settings in an isolated examination environment.
3. Choose one evidence type (`text/`, `image/`, `audio/`, or `video/`) and read its `test_record.md` to understand the objective, inputs, procedure, observations, and conclusions.
4. Obtain the original evidence from `evidence/original/` and compare its cryptographic hash with the value documented in `validation/`. For example:
   ```bash
   sha256sum image/evidence/original/<ACTUAL_FILENAME>
   ```
5. Read `evidence/prepared/` and repeat any recorded preparation commands or scripts. Keep derived inputs separate from the original evidence. If no preparation occurred, consult its `README.md`.
6. Replay the exact initial and follow-up prompts from `prompts/` in the documented order, using the same input files and recorded model settings.
7. Preserve the new outputs and compare them with the original responses, logs, and errors in `outputs/`.
8. Review numbered screenshots in `screenshots/` to confirm which steps and results were actually visible during the original investigation.
9. Repeat the independent checks in `validation/`, using scripts in `scripts/` where available. Record matches, differences, uncertainties, and failures.
10. Repeat the process for the other three evidence types and consult the final report for cross-evidence findings and limitations.

**Reproducibility boundary:** Screenshots and logs document observed behavior, but AI responses may differ across runs because of nondeterminism, model revisions, and environment differences. Do not claim that an unrecorded action or conclusion is reproducible.

## Evidence handling and limitations

- Do not modify the files in `evidence/original/` during analysis.
- Document all transformations, tools, timestamps, and hash checks where applicable.
- Distinguish direct observations from AI-generated interpretations and independently verified findings.
- Remove secrets and sensitive personal information before committing. Do not publish restricted evidence without authorization.
- If evidence is too large for GitHub, document its approved storage location, access procedure, and hash in the relevant evidence folder rather than silently omitting it.

## Submission checklist

- [ ] Final PDF is present at `report/final_report.pdf`.
- [ ] Final PowerPoint is present at `presentation/final_presentation.pptx`.
- [ ] Each evidence type contains the required eight-field `test_record.md`.
- [ ] Original evidence, prepared inputs or no-preparation README, prompts, outputs, screenshots, validation, and scripts are included as applicable.
- [ ] Environment records are complete and sanitized.
- [ ] Submitted commit SHA is recorded and matches the graded version.
- [ ] Another examiner can follow the recorded steps without relying on undocumented assumptions.

CYFI 725 — Final Project: Evaluation of Hermes Agent for Digital Forensics
Course: CYFI 725: Computer and Digital Forensics
Institution: University of Baltimore, Department of Cyber Forensics
Instructor: Dr. Frank Xu
Team: Courtney Cannon, Olajide Arodoye, and Jada Bracewell
Report date: November 16, 2026
Project overview
This project evaluates Hermes Agent as an investigative assistant for four instructor-provided digital evidence types: text, image, audio, and video. The team examined evidence integrity, factual accuracy, uncertainty, traceability, tool behavior, and the need for independent examiner validation. Hermes output is treated as an investigative lead rather than a substitute for verified forensic findings.
Final deliverables
- Final report: [`report/final_report.pdf`](report/final_report.pdf) — complete report, references, and appendices.
- Final presentation: [`presentation/final_presentation.pptx`](presentation/final_presentation.pptx) — project summary and supporting screenshots.
- Final commit ID: TO BE FILLED AFTER FINAL COMMIT (run git rev-parse HEAD and replace this text).
These links indicate the required submission paths. Confirm the files exist before submitting.

Repository organization
README.md
report/
  final_report.pdf
presentation/
  final_presentation.pptx
environment/
  README.md
  installation_commands.md
  agent_configuration.md
text/
  test_record.md
  evidence/original/
  evidence/prepared/
  prompts/
  outputs/
  screenshots/
  validation/
  scripts/
image/
  test_record.md
  evidence/original/
  evidence/prepared/
  prompts/
  outputs/
  screenshots/
  validation/
  scripts/
audio/
  test_record.md
  evidence/original/
  evidence/prepared/
  prompts/
  outputs/
  screenshots/
  validation/
  scripts/
video/
  test_record.md
  evidence/original/
  evidence/prepared/
  prompts/
  outputs/
  screenshots/
  validation/
  scripts/
.github/workflows/validate.yml  # if included in final repository
What belongs in each folder
Path	Contents
report/	Final PDF report including appendices.
presentation/	Final PowerPoint presentation.
environment/	Sanitized installation commands, observed Hermes versions, model/provider, tool permissions, configuration, troubleshooting, and installation screenshots.
<type>/test_record.md	Complete required eight-field investigation record for that evidence type.
<type>/evidence/original/	Verified, unchanged source evidence.
<type>/evidence/prepared/	Derived analysis inputs (e.g., resized images, transcripts, extracted frames). If none, include a README saying so.
<type>/prompts/	Exact initial, follow-up, retry, and corrective prompts actually sent to Hermes, in order.
<type>/outputs/	Complete Hermes responses, tool/action logs, errors, and generated outputs; never place prepared input evidence here.
<type>/screenshots/	Numbered, legible screenshots with descriptive figure titles or an index.
<type>/validation/	Independent tool results, hash comparisons, claim-by-claim assessments, and limitations.
<type>/scripts/	Scripts and commands actually used; add a README if no scripts were used.


Evidence investigations
Type	Evidence	Method and principal finding
Text	case_text_01.txt	Direct text examination, line-supported event review, and prompt-injection testing. Hermes also produced contradictory or truncated output and risked amplifying an unsupported accusation.
Image	case_image_01.png	An initial .png download was actually HTML. The correct PNG was obtained and a resized working copy used for analysis. Hermes described visible details but made some unsupported interpretations.
Audio	case_audio_01.wav	An initial .wav download was actually HTML. File checks established the valid WAV, and a faster-whisper small.en transcript supported speech analysis. An ambiguous word remained unverified.
Video	case_video_01.mp4	ffprobe/`ffmpeg` inspection and frame/audio extraction were used to check a 10-second title-card video. Limited sampling initially missed title-card states and a continuous tone.


The original benchmark evidence comes from the instructor-provided 2026F_benchmark/student_package directory. Preserve the original evidence and record full SHA-256 hashes in each evidence-type validation record. An HTML page saved with an image or audio extension is not the original image or audio artifact.
Agent environment
The report documents Hermes Agent on Linux, using model qwen3.8:27b through a custom Ollama-compatible endpoint, a local terminal backend, and medium reasoning effort. Installation involved a Python distutils error, retry with commit d923a5e, and a successful pwd test after restarting. Different report sections show different Hermes versions (including v0.23.1 and v0.22.5); retain each observed version with its session evidence instead of merging them into one assumed configuration.

Do not publish API keys, passwords, access tokens, sensitive endpoint details, or other credentials. Sanitize logs and screenshots before committing.
How another examiner can repeat the observable steps
1. Set up an isolated Linux examination environment. Consult environment/ for the recorded installation, model/provider configuration, permissions, errors, and session-specific version information. Do not assume that every isolation or permission control was independently verified.
2. Acquire the instructor-provided benchmark artifacts. Download the actual raw files, not GitHub HTML viewer pages. Run file to check formats and sha256sum to compare with the supplied SHA256SUMS.txt manifest; retain unchanged originals in each evidence/original/ folder.
3. Prepare only working copies where needed. Document image resizing, audio transcription, or video frame/audio extraction in evidence/prepared/ and record the commands, settings, source files, and hashes of derived files. For text, the report records direct access without preparation.
4. Run the recorded prompts in order. Use the exact prompts in each prompts/ folder, including retries and corrections. Record Hermes version, model, provider, tool availability, and approval settings for the run. Do not treat reconstructed example prompts as original session logs.
5. Capture all observable behavior. Save complete responses, tool calls, errors, unexpected actions, and screenshots to the appropriate outputs/ and screenshots/ folders. Record any network access or file changes.
6. Validate independently. Compare hashes, file formats, log lines, visible image details, transcript uncertainties, and full-video observations using standard tools and manual examination. Classify material claims as supported, incorrect, unsupported, missing, ambiguous, or unverifiable.
7. Record differences and limitations. Document timeouts, truncated answers, model instability, incomplete frame sampling, and claims that cannot be confirmed. Do not claim exact repeatability where source logs or configuration records are absent.
Useful verification commands
file evidence/original/*
sha256sum evidence/original/*
# For the audio or video file, when ffprobe is installed:
ffprobe -hide_banner -show_format -show_streams path/to/media_file
These are reference commands. For the exact commands used during the project, consult the corresponding investigation records and scripts.
Validation and responsible use
- Preserve evidence integrity and chain-of-custody documentation.
- Distinguish direct observations from model inference.
- Do not infer identity, intent, theft, or image manipulation without independent corroboration.
- Use the original media, not just a transcript or sampled frames, for final validation.
- Human examiners must approve evidence changes, external network contact, and final forensic conclusions.
Team contributions
- Courtney Cannon: Text investigation and eight audio-specific evaluation questions; introduction and background/expectations sections.
- Olajide Arodoye: Complete image investigation (11 general and eight image-specific questions) and audio general investigation Questions 1–11.
- Jada Bracewell: Video investigation, repository validation scripts, and GitHub Actions workflow validation.
See the final report's Appendix A for the fuller team contribution descriptions.
Submission checks
Before submission, verify that all linked deliverables exist, each evidence folder has its eight-field test record, exact prompts and full outputs are included, screenshots are legible and numbered, original evidence hashes are documented, sensitive information is removed, and the final commit ID above is updated.

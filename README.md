# AutoEIT - Test I: Audio Transcription

This repository contains my submission for Test I of the AutoEIT project 
for GSoC 2026 under HumanAI Foundation.

## Overview
The task involved transcribing 4 Spanish EIT (Elicited Imitation Task) audio 
recordings, where each participant listens to 30 sentences and repeats them. 
I used OpenAI Whisper large-v3 for transcription.

## Approach
- Skipped the first 2:30 mins of each audio (English instructions + practice sentences)
- Used Whisper large-v3 with language forced to Spanish
- Mapped Whisper's timestamped segments to each of the 30 stimulus sentences
- Preserved all participant errors as-is — only corrected clear ASR mistakes

## Challenges
- Participant 38012-2A had very low Spanish proficiency, making responses difficult to map
- Some segments had multiple sentences merged together by Whisper
- Whisper hallucinated repeated text during long silences
- Participant 38015-1A missed sentence 1 completely, marked as [inaudible]

## Results
| Participant | Transcribed | WER vs Stimulus |
|-------------|-------------|-----------------|
| 38010-2A    | 30/30       | 69.08%          |
| 38011-1A    | 30/30       | 82.73%          |
| 38012-2A    | 30/30       | 79.12%          |
| 38015-1A    | 29/30       | 53.47%          |

Note: High WER is expected — it reflects participant deviation from the stimulus, 
not transcription accuracy.

## Files
- `AutoEIT_Test1.ipynb` — full pipeline notebook with output
- `AutoEIT_Transcriptions_FINAL.xlsx` — transcriptions filled in column C
- `AutoEIT_Test1.pdf` — PDF export of the notebook

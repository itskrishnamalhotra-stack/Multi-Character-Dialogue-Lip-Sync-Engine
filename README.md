# Multi-Character Dialogue Lip-Sync Engine

A computer-vision pipeline for assigning different audio tracks to multiple faces in one video and compositing the independently lip-synchronised results back into the original scene.

> Built as an experimental applied-AI pipeline in 2024.

## How it works

1. Detect faces in the first frame.
2. Associate each detected person with a name and audio track.
3. Track identities frame-to-frame using Intersection over Union (IoU).
4. Smooth bounding boxes over time to reduce visible jitter.
5. Create an isolated masked video for each character.
6. Run Wav2Lip independently for every character.
7. Composite the processed regions back with feathered masks.

## Technical highlights

- Multi-face processing beyond Wav2Lip's typical single-face workflow
- Lightweight IoU-based temporal tracking
- Bounding-box smoothing for more stable masks
- Per-character inference jobs
- Feathered OpenCV/MoviePy compositing

## Tech stack

Python · Wav2Lip · OpenCV · MoviePy · face_recognition · NumPy · FFmpeg · Google Colab

## Repository contents

```text
LipSync_with_Multiple_Characters.ipynb
README.md
```

## Running the notebook

1. Open the notebook in Colab.
2. Enable a GPU runtime.
3. Provide a source video containing visible faces.
4. Upload one audio file per character.
5. Run the stages in order and verify the identity assignments before inference.

## Limitations

- IoU tracking can lose identities during long occlusions or large movements.
- Source videos with profile faces, motion blur or overlapping subjects may require a stronger tracker.
- Processing time grows with both video duration and character count.
- Use only media for which you have the necessary consent and rights.

## Status

Research prototype. The next engineering step is to extract the notebook into tested tracking, inference and compositing modules.

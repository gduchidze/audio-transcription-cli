# Audio Transcription CLI

A real-time audio transcription tool that runs 100% locally on your machine using the LFM2-Audio-1.5B model.

## Quick Start

### Install uv on your system, if you don't have it already.

<details>
<summary>Click to see installation instructions for uv</summary>

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
</details>

### Download a few audio samples

```bash
uv run download_audio_samples.py
```

### Run the transcription CLI

```bash
uv run transcribe --audio './audio-samples/barackobamafederalplaza.mp3' --play-audio
```

By passing the `--play-audio` flag, you will hear the audio in the background during transcription.

## Understanding the architecture

This example is a **100% local audio-to-text transcription CLI**, that runs on your machine thanks to llama.cpp. Neither input audios nor output text are sent to any server. Everything runs on your machine.

The tool features:
- Real-time transcription with chunked processing
- Optional audio playback during transcription
- Text cleaning with language model
- Typewriter effect for character-by-character display
- Automatic model and binary download from Hugging Face

## Additional Options

```bash
uv run transcribe --audio path/to/audio.mp3 \
  --play-audio \
  --clean-text \
  --typewriter \
  --typewriter-speed 0.01 \
  --log-partial-transcripts datasets/output.csv
```

| Option | Description |
|--------|-------------|
| `--audio` | Path to audio file (required) |
| `--play-audio` | Play audio in background during transcription |
| `--clean-text` | Clean transcription with language model |
| `--typewriter` | Enable typewriter effect (default: enabled) |
| `--typewriter-speed` | Speed in seconds per character (default: 0.01) |
| `--log-partial-transcripts` | CSV file path to log incremental transcriptions |

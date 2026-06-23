# Audio Recorder

A simple Python audio recording script that captures microphone input in real time and saves it as a WAV audio file when the recording is stopped.

## Table of Contents

- Introduction
- Features
- Requirements
- Installation
- Usage
- How It Works
- Output
- Troubleshooting
- License

## Introduction

This project records audio from the system's default microphone using the PyAudio library and stores the captured audio data in memory. Recording continues until the user interrupts execution (Ctrl+C), after which the audio is saved as a WAV file named `output.wav`.

## Features

- Records audio from the default input device
- Mono audio recording (1 channel)
- 44.1 kHz sample rate
- Saves recordings as standard WAV files
- Stops gracefully using keyboard interruption

## Requirements

- Python 3.x
- PyAudio

## Installation

### Install PyAudio

#### Windows

```bash
pip install pyaudio
```

#### Linux (Ubuntu/Debian)

```bash
sudo apt-get install portaudio19-dev
pip install pyaudio
```

#### macOS

```bash
brew install portaudio
pip install pyaudio
```

## Usage

Run the script:

```bash
python main.py
```

The application will begin recording immediately.

To stop recording and save the file:

```text
Press Ctrl + C
```

The recorded audio will be saved as:

```text
output.wav
```

## How It Works

1. Initializes a PyAudio instance.
2. Opens an audio input stream:
   - Format: 16-bit PCM
   - Channels: 1 (Mono)
   - Sample Rate: 44,100 Hz
   - Buffer Size: 1024 samples
3. Continuously reads audio data from the microphone.
4. Stores audio frames in memory.
5. Stops recording when a keyboard interrupt occurs.
6. Writes the collected audio data to `output.wav`.

## Configuration

The following parameters can be modified:

| Parameter | Current Value | Description |
|------------|--------------|-------------|
| `channels` | `1` | Mono audio |
| `rate` | `44100` | Sample rate (Hz) |
| `frames_per_buffer` | `1024` | Audio buffer size |
| `output.wav` | File name | Output audio file |

Example:

```python
stream = audio.open(
    format=pyaudio.paInt16,
    channels=2,
    rate=48000,
    input=True,
    frames_per_buffer=2048
)
```

## Output

After recording, a WAV file is generated:

```text
output.wav
```

This file can be opened with most audio players and audio editing software.

## Troubleshooting

### PyAudio installation fails

Install PortAudio development libraries before installing PyAudio.

### No microphone detected

- Verify your microphone is connected.
- Check operating system permissions.
- Ensure the correct input device is configured.

### Audio is distorted

Try adjusting:

- Sample rate
- Buffer size
- Input device settings

## Possible Improvements

- Recording duration limit
- Pause/resume functionality
- Device selection
- Stereo recording support
- Output file naming via command-line arguments
- Audio level monitoring
- Compression formats (MP3, FLAC)

## License

Specify your preferred license (MIT, Apache 2.0, GPL, etc.).
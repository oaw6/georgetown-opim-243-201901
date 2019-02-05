# The `speech_recognition` Package

The `speech_recognition` package provides a high-level interface to record and process audio inputs in Python.

Reference:

  + https://github.com/Uberi/speech_recognition
  + http://people.csail.mit.edu/hubert/pyaudio/#downloads
  + https://github.com/Uberi/speech_recognition/blob/master/reference/library-reference.rst
  + https://github.com/Uberi/speech_recognition/blob/master/examples/write_audio.py
  + https://github.com/Uberi/speech_recognition/blob/master/examples
  + https://github.com/Uberi/speech_recognition/blob/master/speech_recognition/__main__.py
  + https://github.com/s2t2/learning-new-sounds

## Installation

First install the `SpeechRecognition` package and its `pyaudio` dependency:

```sh
# see http://people.csail.mit.edu/hubert/pyaudio/#downloads
pip install pyaudio # on Mac OS, first run: `brew install portaudio`

pip install SpeechRecognition # depends on pyaudio
```

## Usage

### Recording Audio

Record audio using your computer's built-in microphone, and save that to a file:

```py
import speech_recognition as sr

client = sr.Recognizer()

with sr.Microphone() as mic:
    print("Say something!")
    audio = client.listen(mic)

with open("my-recording.flac", "wb") as f:
    f.write(audio.get_flac_data())
```

### Recognizing Speech

Record audio using your computer's built-in microphone, and recognize the spoken words:

```py
import speech_recognition as sr

client = sr.Recognizer()

with sr.Microphone() as mic:
    print("Say something!")
    audio = client.listen(mic)

transcript = client.recognize_google(audio)
#> 'how old is the Brooklyn Bridge'

response = client.recognize_google(audio, show_all=True)
#> {
#>   'alternative': [
#>     {
#>       'transcript': 'how old is the Brooklyn Bridge',
#>       'confidence': 0.987629
#>     }
#>   ],
#>   'final': True
#> }
```

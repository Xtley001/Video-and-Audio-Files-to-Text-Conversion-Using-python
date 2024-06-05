# Video/Audio files to text conversion using python an d IBM Watson

This Python script demonstrates how to use IBM Watson's Speech to Text API to transcribe audio files into text. It provides step-by-step instructions on how to set up and run the code.

## Prerequisites

Before running the script, ensure you have the following:

- Python installed on your system (Python 3.6 or higher recommended).
- An IBM Cloud account with access to the Speech to Text service.
- An API key and service URL for the IBM Watson Speech to Text service.

## Installation

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/Xtley001/https://github.com/Xtley001/Video-and-Audio-Files-to-Text-Conversion-Using-python/tree/main.git
    ```

2. Navigate to the cloned directory:

    ```bash
    cd ibm-watson-speech-to-text
    ```

3. Install the required Python packages using pip:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Open the `transcribe_audio.py` file in a text editor or IDE.

2. Replace the placeholders `'your_api_key'` and `'your_service_url'` with your actual API key and service URL obtained from the IBM Cloud dashboard.

3. Set the `audio_file_path` variable to the full path of the audio file you want to transcribe.

4. Customize the optional parameters such as `model`, `timestamps`, `word_confidence`, and `max_alternatives` according to your requirements.

5. Save the changes to the file.

6. Run the script:

    ```bash
    python transcribe_audio.py
    ```

    The transcription results will be printed to the console.

## Example

Here's a basic example of how to run the script:

```python
from ibm_watson import SpeechToTextV1
from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

# API key and service URL from IBM Cloud
apikey = 'your_api_key'
url = 'your_service_url'

# Authenticate to the service
authenticator = IAMAuthenticator(apikey)
stt = SpeechToTextV1(authenticator=authenticator)
stt.set_service_url(url)

# Full path to the audio file
audio_file_path = '/path/to/your/audio.wav'

# Transcribe the audio file
try:
    with open(audio_file_path, 'rb') as f:
        res = stt.recognize(
            audio=f,
            content_type='audio/wav',
            model='en-AU_NarrowbandModel',  # Optional: Customize the language model
            timestamps=True,  # Optional: Include timestamps
            word_confidence=True,  # Optional: Include word confidence scores
            max_alternatives=3  # Optional: Set maximum alternatives
        ).get_result()

    # Print the transcription results
    print(res)

except FileNotFoundError:
    print(f"The file at path {audio_file_path} was not found. Please check the path and try again.")
```

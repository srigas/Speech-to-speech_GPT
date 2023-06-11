# Speech-to-speech GPT

This repo contains a single `.py` file which creates an interaction by voice between the user and OpenAI's LLM models. To run the script, first create a new conda environment, typing

```
conda create -n ENV_NAME python==3.10.9
```

and then install the requirements, typing

```
pip install -r requirements.txt
```

To run the script simply type

```
python script.py
```

and follow the instructions to interact with the chatbot. The way this works can be summarized as follows:

- When prompted, the user records their query to the LLM (in English). This recording is saved locally and processed using OpenAI's Whisper API, in order to get a transcription.
- The transcription is passed to OpenAI's LLM (which is wrapped around a langchain model), so the LLM's response to the query is returned.
- The response is read by a voice bot and the whole thing can be repeated as many times as the user wants, simply by answering "Yes" when asked by the bot if there are additional questions.

This script is by no means a complete project; for instance, langchain is simply used as a wrapper, while its functionalities are far greater than this and this simple script could be developed directly through the corresponding openai library module. Instead, its purpose is to showcase how easily one can construct a speech-to-speech bot in very few lines of code, simply by performing some API requests to OpenAI and using audio-related libraries such as `pyaudio`. From this very basic version, anyone can build up additional features, such as incorporating the Chat modules of langchain as components of Chains including Memory (see langchain's documentation [here](https://python.langchain.com/en/latest/index.html)), or creating a user interface to accommodate the user-bot interaction, or devising a less clumsy way of parsing audio files than the one presented here.

**NOTE**: To run the script successfully, a microphone is required. Additionally, an OpenAI API key must be exported as an environment variable, for example using the `os` library as follows:

```
import os
os.environ["OPENAI_API_KEY"] = "sk-XXXXXXX"
```

# ChatGPT Voice Assistant

## Overview
The **ChatGPT Voice Assistant** is a C# console application that allows users to interact with OpenAI's ChatGPT using voice input and hear the responses in real-time through text-to-speech. This project integrates:

1. **Speech Recognition**: Using the **Vosk** library for offline voice-to-text transcription.
2. **ChatGPT Integration**: Sending the transcribed input to OpenAI's ChatGPT API to generate meaningful responses.
3. **Text-to-Speech**: Using the built-in `System.Speech.Synthesis` library to convert ChatGPT's responses to audio.

---

## Features
- **Voice Input**: Capture spoken words using your microphone and convert them into text.
- **AI-Powered Responses**: Use ChatGPT to generate intelligent responses to your input.
- **Voice Output**: Hear ChatGPT's responses using text-to-speech.
- **Real-Time Interaction**: Continuous conversation with a simple quit option.

---

## Prerequisites

### Tools and Libraries
1. **.NET SDK**: Install the latest [.NET SDK](https://dotnet.microsoft.com/download).
2. **Vosk Model**: Download the [vosk-model-small-en-us-0.15](https://alphacephei.com/vosk/models) and extract it into the project directory.
3. **NuGet Packages**:
   - Install the following packages:
     - `NAudio`
     - `Newtonsoft.Json`
     - `Vosk`

### Environment Setup
1. **OpenAI API Key**:
   - Set your OpenAI API key as an environment variable:
     - **Windows**:
       ```cmd
       set OPENAI_API_KEY=your_openai_api_key
       ```
     - **macOS/Linux**:
       ```bash
       export OPENAI_API_KEY=your_openai_api_key
       ```

---

## How It Works

1. **Voice Input**:
   - The application uses the Vosk library to process audio input from the microphone and convert it into text. The recognized text serves as input for ChatGPT.

2. **ChatGPT API Interaction**:
   - The transcribed text is sent to the OpenAI API, which generates a response using the `gpt-3.5-turbo` model. The response is parsed and returned to the application.

3. **Text-to-Speech**:
   - The response from ChatGPT is converted into speech using the `System.Speech.Synthesis` library and played back to the user.

4. **Loop**:
   - The application continues the interaction in a loop until the user decides to quit.

---

## Code Explanation

### Main Flow
The `Main` method coordinates the primary workflow:
1. Prompts the user to speak.
2. Captures audio input and converts it to text using `GetVoiceInput()`.
3. Sends the text to ChatGPT via `GetChatGPTResponse()`.
4. Converts ChatGPT's response into speech with `SpeakText()`.

### Key Methods

#### **GetVoiceInput()**
- Uses the Vosk library to capture microphone input.
- Transcribes the input into text.
- Returns the transcribed text or a fallback message if no speech is detected.

#### **GetChatGPTResponse(string prompt)**
- Sends the user's text input to the OpenAI ChatGPT API.
- Uses the `gpt-3.5-turbo` model to generate a response.
- Parses and returns the response text.
- Handles API errors and invalid responses gracefully.

#### **SpeakText(string text)**
- Converts the provided text into speech using `System.Speech.Synthesis`.
- Handles errors in speech synthesis.

---

## Installation and Usage

### Steps to Run the Application
1. Clone the repository or copy the source code.
2. Ensure all dependencies are installed.
3. Place the Vosk model (`vosk-model-small-en-us-0.15`) in the project directory.
4. Set the `OPENAI_API_KEY` environment variable with your OpenAI API key.
5. Build and run the application:
   ```bash
   dotnet run
   ```

### Interacting with the App
- Speak into your microphone when prompted.
- Hear the response from ChatGPT.
- Press any key to continue or 'Q' to quit.

---

## Error Handling
- **Missing Vosk Model**: Ensure the `vosk-model-small-en-us-0.15` directory exists in the correct path.
- **API Key Issues**: Confirm the `OPENAI_API_KEY` environment variable is set correctly.
- **Audio Input Problems**: Verify your microphone is connected and accessible.

---

## Customization
- **Vosk Model**: Replace the model with other language models for non-English speech recognition.
- **ChatGPT Model**: Modify the model (`gpt-3.5-turbo`) to other available OpenAI models if needed.
- **Max Tokens**: Adjust the `max_tokens` parameter in `GetChatGPTResponse()` to control the length of responses.

---

## Dependencies
- [.NET SDK](https://dotnet.microsoft.com/download)
- [Vosk](https://alphacephei.com/vosk/)
- [NAudio](https://github.com/naudio/NAudio)
- [Newtonsoft.Json](https://www.newtonsoft.com/json)

---

## License
This project is licensed under the MIT License.

---

## Acknowledgments
- [OpenAI](https://openai.com/) for ChatGPT
- [Vosk](https://alphacephei.com/vosk/) for speech recognition
- [NAudio](https://github.com/naudio/NAudio) for audio handling

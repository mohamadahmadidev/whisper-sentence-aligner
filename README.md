# AI-Powered Sentence Timestamp Finder

A simple, powerful web tool to find the precise start and end timestamps of sentences within a WAV audio file. This application uses OpenAI's Whisper API for accurate, word-level transcription and then aligns it with a provided list of sentences in a JSON file.

## How It Works

The tool streamlines the process of audio-text alignment without requiring complex software or command-line tools.

1.  **Transcription:** The uploaded WAV file is sent to the OpenAI Whisper API, which performs a speech-to-text transcription and returns a detailed list of every word spoken along with its start and end time.
2.  **Sentence Matching:** The application iterates through each sentence provided in your JSON file. It cleans and normalizes both the input sentence and the transcribed words to ensure accurate matching.
3.  **Timestamp Extraction:** A search algorithm locates the sequence of transcribed words that exactly matches the input sentence.
4.  **Result Generation:** The start time of the first word and the end time of the last word are extracted and added to the original JSON data for that sentence. If a sentence isn't found in the audio, it's flagged accordingly.
5.  **Output:** The final, timestamp-enriched JSON data is displayed and made available for download.

## Usage

1.  **API Key:** Enter your OpenAI API Key. The key is stored locally in your browser's `localStorage` for convenience and is not sent anywhere except directly to OpenAI.
2.  **Upload WAV File:** Click or drag-and-drop your audio file into the designated area. It must be in `.wav` format.
3.  **Upload JSON File:** Provide a JSON file containing the sentences you want to find timestamps for. The required format is detailed below.
4.  **Process:** Click the "Find Timestamps" button to start the analysis.
5.  **Download:** Once the process is complete, the results will be displayed. You can then download the new JSON file with the added `startTime`, `endTime`, and `status` fields.

## Required File Formats

### Audio File

* Must be a standard **`.wav`** file.
* For best results, use audio with clear speech and minimal background noise.

### JSON File

* The JSON file must be an array of objects.
* Each object must contain a `full_sentence` key.

**Example Input `sentences.json`:**

```json
[
  {
    "id": 1,
    "full_sentence": "Hello world, this is the first sentence."
  },
  {
    "id": 2,
    "full_sentence": "And this is the second one."
  },
  {
    "some_other_data": "value",
    "full_sentence": "Whisper is a powerful tool for transcription."
  }
]
````

**Example Output `ai_timestamps_result.json`:**

```json
[
  {
    "id": 1,
    "full_sentence": "Hello world, this is the first sentence.",
    "startTime": 0.54,
    "endTime": 3.21,
    "status": "found"
  },
  {
    "id": 2,
    "full_sentence": "And this is the second one.",
    "startTime": 3.8,
    "endTime": 5.1,
    "status": "found"
  },
  {
    "some_other_data": "value",
    "full_sentence": "Whisper is a powerful tool for transcription.",
    "startTime": 5.9,
    "endTime": 8.4,
    "status": "found"
  }
]
```

## Technology Stack

  * **HTML5:** For the core structure of the application.
  * **Tailwind CSS:** For modern, responsive styling.
  * **JavaScript (Vanilla):** For all client-side logic, including file handling, API interaction, and data processing.
  * **OpenAI Whisper API:** For the core speech-to-text and timestamp generation.

## Local Setup

This is a self-contained HTML file, so no complex setup is needed.

1.  Clone the repository:
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    ```
2.  Open the `index.html` file in your web browser.

## License

This project is open-source and available under the [MIT License](https://www.google.com/search?q=LICENSE).

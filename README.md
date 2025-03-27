# YouTube Transcript Downloader V1

## 1. Overview

This program allows users to extract YouTube video transcripts by entering either the video URL or video ID. The extracted transcript is displayed in a text box, and users have the option to download the transcript or summarize it into bullet points. The program utilizes the `YouTubeTranscriptApi` library to retrieve transcripts and offers a clean and intuitive graphical user interface (GUI) using PyQt5.

## 2. Features

- **Video ID/URL Input**: Users can enter either the YouTube video URL or video ID.
- **Transcript Display**: Displays the full transcript of the video in a scrollable text area.
- **Download Transcript**: Allows users to download the full transcript of the video.
- **Summarize Transcript**: Summarizes the transcript into bullet points using an external summarization API.
- **GUI**: Built with PyQt5 for an intuitive and user-friendly interface.

## 3. Requirements/Dependencies

- Python 3.10.9
- `PyQt5`: for the GUI components.
- `YouTubeTranscriptApi`: to retrieve video transcripts from YouTube.
- `markdown`: for formatting the summarized transcript into HTML.
- `groq`: for generating summaries via a chat model (if applicable).
- `re`: for regex operations to extract video IDs.

You can install the dependencies using `pip`:

```bash
pip install PyQt5 YouTubeTranscriptApi markdown groq
```


## 4. Usage Instructions

1. **Launch the application**: Run the script to start the application.
2. **Enter video ID or URL**: Input a YouTube video ID or URL into the provided field.
3. **Download the transcript**: Click the "Download Transcript" button to retrieve the transcript.
4. **Summarize the transcript**: Click the "Summarize Transcript" button to generate a summarized version of the transcript in bullet points.
5. **View the results**: The full transcript or summarized text will be displayed in the output text area.

## 5. Known Issues & Limitations

- **URL Format**: The program only supports YouTube URLs in the standard format (`youtube.com` or `youtu.be`).
- **Error Handling**: If a video does not have a transcript or the video ID is incorrect, an error message is displayed.
- **API Key**: Ensure that you have a valid API key for any external summarization services (e.g., `groq`).
- **Styling**: If the custom CSS file (`darkpro.css`) is missing, the default style is applied.

## 6. Future Enhancements

- Support for more video platforms (e.g., Vimeo, Dailymotion).
- Option to choose the location for saving transcripts.
- Improve error handling for different types of video IDs or invalid URLs.
- Allow users to export the summarized transcript in different formats (e.g., PDF, text file).

## 7. Testing

The program was tested with various YouTube videos to ensure that:

- The video ID or URL is correctly extracted.
- The transcript is correctly retrieved and displayed.
- The summarize function returns a concise and readable summary of the transcript.

## Code Example

Here is the core logic for extracting the video ID from a URL:

```python
def extract_video_id(input_string):
    if re.match(r'http(s)?:\/\/', input_string):
        if 'youtube.com' in input_string:
            match = re.search(r'v=([^&]*)', input_string)
            if match:
                return match.group(1)
        elif 'youtu.be' in input_string:
            match = re.search(r'youtu\.be\/([^&]*)', input_string)
            if match:
                return match.group(1)
    return input_string
```


![YouTube Summary Application](https://github.com/huntahgarcia/YouTube_Summary/assets/140458716/976dea8a-9292-4b5f-9689-15a7ad8c3a45)

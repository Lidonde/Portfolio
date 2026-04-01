# YouTube Transcript Collection

This folder contains transcripts of selected YouTube videos used for research in the **LinkedIn Organic Content Strategy for B2B SaaS** project.

The goal of collecting these transcripts is to analyze how experienced B2B marketers structure messaging, explain frameworks, and communicate growth strategies. These transcripts will later be used to extract insights and patterns that can inform a practical LinkedIn growth playbook.


# How the Transcripts Were Collected

The transcripts were collected using the **YouTube Transcript API** in **Google Colab**.

I chose this method because it allowed me to quickly extract transcripts without building a full backend script or environment locally.

### Step 1 — Install the Transcript API

```python
!pip uninstall -y youtube-transcript-api
!pip install youtube-transcript-api
```


### Step 2 — Fetch a Transcript

```python
from youtube_transcript_api import YouTubeTranscriptApi
import re

url = "https://www.youtube.com/watch?v=dMZ-n2KSlxE"

# extract video id
video_id = re.search(r"v=([^&]+)", url).group(1)

ytt_api = YouTubeTranscriptApi()

transcript = ytt_api.fetch(video_id)

for line in transcript:
    start = line.start               # start time in seconds
    minutes = int(start // 60)
    seconds = int(start % 60)
    
    print(f"[{minutes:02d}:{seconds:02d}] {line.text}")
```

This script:

1. Extracts the **video ID** from the YouTube URL.
2. Uses the **YouTube Transcript API** to fetch the transcript.
3. Adds **timestamps** to each line.
4. Prints the transcript in a readable format that can easily be copied into Markdown files.


# Why I Used Google Colab Instead of Local Coding Tools

As I worked on collecting YouTube transcripts, I initially explored using the recommended tools like Codex or Claude Code. However, as a beginner in working with APIs and coding workflows, I found it challenging to set up and consistently extract transcripts using those approaches.

To move forward without getting blocked, I did additional research on alternative methods and discovered that I could use the YouTube Transcript API through Google Colab.

I chose this approach because:

- **Lower setup barrier** – Colab runs in the browser, so I didn’t need to configure a local Python environment or manage dependencies  
- **Easier experimentation** – I could test and adjust the script quickly while learning how the API works  
- **Beginner-friendly workflow** – It allowed me to focus on understanding the data and completing the research rather than getting stuck on technical setup  

I also used tools like Gemini to help me understand the code, troubleshoot errors, and refine the workflow as I went.

This approach reflects how I worked through technical constraints during the project — by researching alternatives and choosing a method that allowed me to complete the task effectively while still learning.
# Transcript Files

Each transcript is saved as a Markdown file using the format:

```
/research/youtube-transcripts/{video-title}.md
```

All filenames are:

* lowercase
* spaces replaced with hyphens
* based on the video title


## Available Transcripts

* [how-this-saas-2xd-demos-with-seo-aeo.md](./how-this-saas-2xd-demos-with-seo-aeo.md)
* [the-best-saas-marketing-strategy-for-2026.md](./the-best-saas-marketing-strategy-for-2026.md)
* [the-best-linkedin-content-strategy-for-saas.md](./the-best-linkedin-content-strategy-for-saas.md)
* [the-best-linkedin-growth-strategy-for-2025-full-course.md](./the-best-linkedin-growth-strategy-for-2025-full-course.md)
* [alex-hormozi-linkedin-growth-hacks-for-2026.md](./alex-hormozi-linkedin-growth-hacks-for-2026.md)
* [my-actual-social-strategy-media-for-2026.md](./my-actual-social-strategy-media-for-2026.md)

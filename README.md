![image](https://github.com/user-attachments/assets/fc099838-7c8c-4996-9f90-36727faa781b)

# 🎬 AI Faceless Shorts Automation (n8n Workflow)

This is a fully automated video generation workflow using **n8n**, powered by **OpenAI**, **Flux**, **RunwayML**, and **Creatomate**. It generates viral faceless short videos (e.g., "Countries as Presidents Bodybuilders") and uploads them to YouTube — end to end!

---

## 🚀 Workflow Overview

1. **Trigger**: Manual or Scheduled
2. **Idea Generation**: Extract past titles from Google Sheets → GPT generates a new idea
3. **Character Assignment**: Predefined famous world leaders (no real name is used in final output)
4. **Image Prompt Generation**: GPT builds photorealistic prompts for each character
5. **Image Generation**: Flux (via PiAPI) generates images
6. **Video Prompt Generation**: GPT rewrites prompts for motion
7. **Video Generation**: RunwayML converts images to motion
8. **Editing**: Combines 4 motion videos + AI-generated text into 1 video via Creatomate
9. **Publishing**: Uploads video to YouTube
10. **Log & Notify**: Adds the video to Google Sheets and sends a Gmail alert

---

## 🧩 Nodes Used

- 📅 `Schedule Trigger` — Runs daily at 5 PM
- 🧾 `Google Sheets` — Fetches existing titles & logs new output
- 🤖 `OpenAI GPT-4o` — For title, image prompt, video prompt
- 🧠 `Langchain Agent` — Structured creative prompting
- 🖼️ `PiAPI (Flux)` — Text-to-image generation
- 🎞️ `RunwayML` — Image-to-video conversion
- 🎬 `Creatomate` — Video editing and rendering
- ⏱️ `Wait` — Delays to allow async API processing
- 📤 `YouTube` — Uploads generated videos
- 📧 `Gmail` — Sends final video notification
- 🔁 `Set`, `Split Out`, `Code` — Data transformation

---

## 📋 Requirements

| Tool / API      | Notes |
|----------------|-------|
| n8n             | Self-hosted or cloud version |
| OpenAI API Key  | GPT-4 access |
| Google Sheets   | For logging and input |
| PiAPI (Flux)    | For image generation |
| RunwayML API Key| For image-to-video conversion |
| Creatomate Key  | For final rendering |
| YouTube OAuth   | For video publishing |
| Gmail OAuth     | For notification |

---

## 🔐 Environment Variables

Set these in your `.env` or directly in n8n credentials:

```env
OPENAI_API_KEY=sk-...
PIAPI_KEY=...
RUNWAYML_API_KEY=...
CREATOMATE_API_KEY=...
YOUTUBE_OAUTH=... # via n8n YouTube credentials
GMAIL_OAUTH=...   # via n8n Gmail credentials

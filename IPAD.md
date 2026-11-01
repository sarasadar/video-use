# Using video-use from an iPad

video-use normally runs on a computer. On an iPad, Claude runs it for you in a cloud workspace and sends the finished video back. You never type commands.

## How to use it

1. Open a Claude chat (claude.ai or the Claude app) that can reach this repo.
2. Say: **"Use my video-use repo (sarasadar/video-use) to edit my clips."**
3. Tap **+** and attach your clips from Photos. Short clips upload most reliably.
4. Say what you want in normal words, for example:
   - "Cut out the long pauses and make it feel cozy."
   - "Make a 45-second vertical Short from these."
   - "Put the clips in order and add 'Pinkqahwaa' at the start."
5. Claude shows you a plan, waits for your OK, then sends back the finished video. Save it to Photos or drop it into CapCut.
6. Ask for changes the same way: "make it shorter", "less orange", and so on.

## What works on iPad

| Works | Needs a real transcript (ElevenLabs) |
|---|---|
| Cutting pauses and dead air | Removing "umm" and "uh" |
| Trimming and reordering clips | Automatic subtitles from your speech |
| Colour grading (warm, cinematic, etc.) | Picking cuts by what you said |
| Text and title cards | |
| Subtitles from text you type | |

If you get an ElevenLabs API key and the workspace can reach ElevenLabs, everything in the right column turns on automatically. Without it, video-use uses **offline mode**: ffmpeg detects when someone is talking, so Claude can cut the silences even though it can't read the words.

## For the agent

- No key or no network to ElevenLabs → `transcribe.py` / `transcribe_batch.py` fall back to offline mode on their own. `--offline` forces it.
- Uploaded clips arrive read-only in the uploads folder: copy them into a working folder (e.g. `~/footage/`) and use that as `<videos_dir>`.
- Deliver `edit/final.mp4` with the file-sending tool. The user can't see the workspace.
- Prefer vertical 1080x1920 for Shorts and Reels unless the user says otherwise.

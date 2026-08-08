# Adding your demo video

The README shows `docs/demo.gif`. Right now that is a placeholder — replace it with the real thing.

## Option 1 — a GIF (best, plays automatically, no click needed)

1. Record your screen (phone + laptop).
2. Convert the clip to a GIF and **keep it under 10 MB**, or GitHub will refuse to show it.
   Free tools: [ezgif.com/video-to-gif](https://ezgif.com/video-to-gif) or [gifski](https://gif.ski).
   Good settings: **800px wide, 10–12 fps, 15–30 seconds**.
3. Name it `demo.gif`, put it in this `docs` folder, replacing the placeholder.
4. Commit and push:
   ```bash
   git add docs/demo.gif
   git commit -m "Add demo"
   git push
   ```

## Option 2 — an MP4 video (better quality, viewer clicks play)

1. Open your repo on **github.com** and click **edit** (pencil) on `README.md`.
2. **Drag the .mp4 file straight into the editor.** GitHub uploads it and pastes a link.
3. Replace this line:
   ```markdown
   ![Zara demo](docs/demo.gif)
   ```
   with the link GitHub just pasted.
4. Commit the change.

Max upload is 10 MB for images, 100 MB for videos.

## What makes a good demo

- Start with the **phone** — show yourself sending the voice note. That is the hook.
- Then cut to the **laptop** doing the work by itself.
- End with the **reply arriving on the phone**.
- Keep it **under 30 seconds**. People decide in the first 5.
- Before recording: close WhatsApp, personal chats and email, hide your bookmarks bar
  (`Ctrl+Shift+B`), and clear personal icons off the desktop.

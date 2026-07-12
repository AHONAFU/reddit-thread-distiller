# Reddit Thread Distiller

A standalone browser app that converts raw Reddit thread `.json` files into a clean, anonymized, trimmed format — ready for analysis, summarization, or content research.

No installs. No API keys. No server. Open the HTML file and use it.

---

## What it does

Reddit's raw `.json` files are messy — nested listings, verbose metadata, real usernames, hundreds of low-score comments. Thread Distiller strips all of that down to what matters:

- Top N comments, sorted by score
- Nested replies preserved under each comment
- Usernames replaced with consistent anonymized aliases
- Clean `{post, comments}` JSON output you can actually work with

---

## Quick Start

1. Download [`thread-distiller.html`](thread-distiller.html) (or clone the repo)
2. Open the file in any modern browser
3. Get your raw Reddit JSON — add `.json` to any Reddit post URL:
   ```
   https://www.reddit.com/r/europe/comments/1ds63nu/2024_french_legislative_election/
   → https://www.reddit.com/r/europe/comments/1ds63nu/2024_french_legislative_election/.json
   ```
4. Copy the contents of that page and paste into the left panel, **or** drag and drop `.json` files directly
5. Click **Convert** — clean output appears on the right
6. Copy to clipboard or **Download** the result

---

## How to Use

### Single thread (paste)

1. Open a Reddit post, add `.json` to the URL, open it in your browser
2. Select all (`Ctrl+A`) and copy the raw JSON
3. Paste into the left panel of Thread Distiller
4. Hit **Convert** or press `Ctrl+Enter`

### Batch mode (drag and drop)

1. Save your Reddit `.json` files locally
2. Drag all of them onto the dropzone in the left panel
3. Each file converts instantly — click **View** to preview any one, or **Download all** to get a single combined JSON array

---

## Settings

| Setting | Description |
|---------|-------------|
| **Top comments** | How many top-level comments to keep — 5, 10, 15, 20, or All |
| **Anonymize usernames** | Replaces real usernames with `user_xxxxxx` aliases. Deterministic — same author always gets the same alias, consistent across all files in a batch |
| **Include nested replies** | Whether to include reply threads under each top comment |

---

## Output Format

```json
{
  "post": {
    "title": "2024 French Legislative Election",
    "author": "user_a1b2c3d4",
    "score": 2841,
    "num_comments": 4392,
    "subreddit": "europe",
    "created_utc": "2024-06-30T18:42:11"
  },
  "comments": [
    {
      "author": "user_e5f6g7h8",
      "body": "Comment text here",
      "score": 941,
      "depth": 0,
      "replies": [
        {
          "author": "user_i9j0k1l2",
          "body": "Reply text",
          "score": 312,
          "depth": 1,
          "replies": []
        }
      ]
    }
  ]
}
```

Comments are sorted by score, highest first. Batch output is a JSON array of these objects, one per thread.

---

## Browser Compatibility

| Browser | Support |
|---------|---------|
| Chrome / Edge | ✅ |
| Firefox | ✅ |
| Safari | ✅ |

---

## Privacy

- Everything runs locally in your browser — no data is sent anywhere
- Username anonymization is one-way — original usernames are not stored in the output
- No analytics, no tracking, no external scripts

---

## License

MIT — see [`LICENSE`](LICENSE)

---
description: Copy an HTML lesson file into this repo, commit and push it to GitHub
arguments:
  - name: file_path
    description: Absolute path to the HTML file (e.g. /Users/di/Downloads/my-lesson.html)
    required: true
---

# Deploy lesson

You are given an HTML file path: `$ARGUMENTS.file_path`

Follow these steps exactly:

1. Verify the file exists and has an `.html` extension. If not, tell the user and stop.
2. Copy the file into the repository root at `/Users/di/Desktop/interactive-lessons/`.
3. Stage the file with `git add <filename>`.
4. Commit with a message describing the lesson being added (use the filename or `<title>` from the HTML if available).
5. **Update README.md** — rebuild the lessons table:
   - For every `*.html` file in the repo root, extract the `<title>` tag content.
   - Build a markdown table sorted by git commit date (newest first): use `git log --diff-filter=A --format=%at -- <file>` to get the timestamp when each file was first added.
   - Write the updated README.md with this exact structure:

```
# Interactive Lessons

Repository with interactive English lessons.

## Lessons

| Lesson | File |
|--------|------|
| <title> | [filename](filename) |
...
```

6. Stage README.md and create a second commit: `Update README with latest lessons list`.
7. Push to `origin main`.
8. Report the result — confirm success or show the error.

Important:
- The repo is at `/Users/di/Desktop/interactive-lessons`
- Always push to `origin main`
- If the file already exists in the repo, overwrite it and commit as an update
- Add `Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>` to both commit messages
- The newest lesson must always be at the top of the table
- If a file has no `<title>` tag, use the filename (without .html) as the lesson name

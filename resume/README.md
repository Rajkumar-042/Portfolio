# Résumés

The contact section of the site links to three PDFs from this folder. The links open
the PDF in a new browser tab, so a visitor can read it on screen and use the viewer's
own download button if they want the file. To update a résumé, replace the file here,
keeping the filename exactly as listed — nothing in `index.html` needs to change.

| Put your file here                | Appears on the site as        |
| --------------------------------- | ----------------------------- |
| `resume/rajkumar-hr.pdf`          | HR & People Operations        |
| `resume/rajkumar-developer.pdf`   | Software Development          |
| `resume/rajkumar-data-ml.pdf`     | Data & Machine Learning       |

## Uploading or updating one

1. Export the résumé as a PDF and rename it to the exact filename above (lowercase).
2. Copy it into this folder, replacing the old one:

   ```sh
   cp ~/Downloads/my-resume.pdf /Users/raj/Portfolio_Raj/Portfolio/resume/rajkumar-hr.pdf
   ```

3. Commit and push:

   ```sh
   cd /Users/raj/Portfolio_Raj/Portfolio
   git add resume/
   git commit -m "Update HR résumé"
   git push
   ```

Vercel redeploys on push, so the link serves the new file within a minute or so. The
URL never changes, so a résumé you have already shared keeps working and starts
serving the new version.

You can also upload through GitHub in the browser instead of the command line: open
<https://github.com/Rajkumar-042/Portfolio> → `resume` folder → **Add file ▸ Upload
files** → drag the PDF in (same filename) → **Commit changes**.

## Notes

- Keep the filenames lowercase and unchanged — the links are hardcoded to them.
- A visitor who filters the site to one discipline sees the matching résumé flagged
  "Matches your filter", so the track names and these files need to stay in step.
- Until a file is uploaded its link will 404, so upload all three (or tell me to hide
  the rows you do not want yet).
- PDF only. A .docx downloads instead of previewing, which defeats the point.
- Keep each file reasonably small (under ~5 MB) so it opens quickly on mobile.

# Résumés

The contact section of the site links to three PDFs from this folder. To update a
résumé, replace the file here, keeping the filename exactly as listed — nothing in
`index.html` needs to change.

| Put your file here                | Appears on the site as        |
| --------------------------------- | ----------------------------- |
| `resume/rajkumar-hr.pdf`          | HR & People Operations        |
| `resume/rajkumar-developer.pdf`   | Software Development          |
| `resume/rajkumar-data-ml.pdf`     | Data & Machine Learning       |

## Updating one

1. Drop the new PDF in this folder under the exact filename above, replacing the old one.
2. Commit and push:

   ```sh
   git add resume/
   git commit -m "Update HR résumé"
   git push
   ```

Vercel redeploys on push, so the download link serves the new file within a minute or
so. The URL never changes, so a résumé you have already shared keeps working and
starts serving the new version.

## Notes

- Keep the filenames lowercase and unchanged — the links are hardcoded to them.
- A visitor who filters the site to one discipline sees the matching résumé flagged
  "Matches your filter", so the track names and these files need to stay in step.
- Until a file is uploaded its download link will 404, so upload all three (or tell
  me to hide the rows you do not want yet).
- PDFs are the only expected format here; a .docx will download rather than preview
  in the browser.

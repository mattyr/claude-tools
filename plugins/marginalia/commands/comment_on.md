---
description: Open a markdown file for inline review comments
---

The user wants to add inline review comments to a markdown file.

$ARGUMENTS is the file path. If empty, ask the user which file to annotate.

1. Run the marginalia editor on the file. IMPORTANT: This command blocks until
   the user finishes commenting and clicks "Done" or closes the browser tab.
   This may take several minutes. Use a timeout of 600000 (10 minutes):

   ${CLAUDE_PLUGIN_ROOT}/scripts/server $ARGUMENTS

2. After the command completes, it prints the sidecar path (e.g. "3 comments
   saved to plan.md.comments"). Read ONLY that .comments file — it is small.
   Do not re-read the original markdown file; you already have it in context.

3. Address each comment:
   - Find the quoted text in the original document
   - Revise it according to the feedback
   - If the feedback is a question, use your judgment

4. Edit the original file with the revisions applied.

5. Delete the .comments sidecar file when done.

TaskScore Codemagic Mobile Upload Fix

Why this exists:
The previous cloud build failed because Codemagic could not find www/index.html.
This version keeps index.html at the repository root and the Codemagic workflow automatically creates www and copies the app into it before Capacitor sync.

Upload ALL files in this folder to the TOP LEVEL of your GitHub repository, replacing files with the same names.
Then rerun: TaskScore iOS Cloud Build Check.

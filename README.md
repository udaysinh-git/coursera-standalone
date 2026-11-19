# Coursera Standalone Tools

An unofficial userscript for studying browser automation and course interfaces. It runs on Coursera course pages in the browser with a userscript manager. It requires no Tether extension, Codex bridge, local server, or API key.

> **Educational use only.** Use the script only where you have permission to automate the activity and handle its content. You are responsible for everything submitted from your Coursera account.

## Install

1. Install a browser userscript manager such as [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/).
2. Open [coursera-standalone.user.js](coursera-standalone.user.js) and copy the full file, including the metadata header.
3. Create a new script in the manager, replace the template with the copied code, and save it. When upgrading, replace the existing userscript so only one copy runs.
4. Reload an authorized Coursera course page. Disable the script in the manager to stop playback and form automation.

## Playback and navigation

Lecture playback defaults to 16×. Where the browser and player support seeking and autoplay, the script plays the first 3 seconds and last 10 seconds. It can skip in-video questions when Coursera provides a **Skip** button, use **Mark as done** where offered, and advance using the course controls. To change the playback settings, edit the constants near the top of the file.

## Apply answers and submit

1. Open an authorized assignment attempt and select **Copy AI prompt**. The prompt includes the question order and an identifier for that question set. Use your own answers for the JSON, or use a tool to format them only if the activity permits it. For figure-based questions, refer to the figures on the page and share screenshots only if you have permission.
2. Open **Answers** and paste the JSON. Choice numbers start at 1. Use arrays for choices and strings for short or written answers. Keep the exact identifier copied from the same attempt.
3. Review your answers and the applicable acknowledgment before clicking **Apply & submit**. The script fills the choice and short-answer fields, verifies that the answers stayed in place, checks the acknowledgment, and requests one submission. It confirms Coursera’s submission dialog if it appears.
4. The script compares the latest result with the passing threshold displayed by Coursera. It opens the next course item if the attempt passed and a next-item control is available. If the attempt fails or Coursera’s result cannot be verified, check the assignment page for the outcome. The script does not retry.

Long written responses stay in the pasted JSON for manual entry and submission. For discussions, Dialogues, and Role Plays, the panel copies the current prompt. You write, review, and send the reply yourself.

## Data and compatibility

The script works with the course page and your clipboard. It does not call an AI provider or send copied prompts to a separate server. Coursera receives submissions through its normal page controls. What you paste into another service is subject to that service’s data handling. Keep credentials, personal data, and restricted course material out of copied prompts and screenshots.

Coursera can change its interface, and browser settings can limit seeking, playback speed, or autoplay. If a submission appears stuck, verify its status in Coursera before attempting another submission.

## Responsible use and disclaimer

Follow applicable law, the rules of your course or institution, and Coursera’s Terms of Use, Acceptable Use Policy, and Honor Code. Obtain any required permission before automating a course activity or sharing assessment content. Use only your own account and answer material you are permitted to use. This independent project has no affiliation with or endorsement from Coursera or any course provider. [Coursera Terms of Use and Honor Code](https://www.coursera.org/about/terms)

The software is provided **as is**, without warranties of any kind. Use it at your own risk. To the extent permitted by applicable law, the author and maintainers disclaim liability for losses, claims, or consequences arising from use, misuse, or inability to use it, including lost attempts, incorrect submissions, or account or academic penalties. This disclaimer does not limit rights or liabilities that applicable law makes nonwaivable.

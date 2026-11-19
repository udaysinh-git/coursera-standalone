# Coursera Standalone Tools

## Why I built this

Our CS program gave us a list of Coursera courses we had to finish. One of them was biology. Why the hell couldn't we pick a course that had something to do with what we were studying? I got fed up, started messing around with the course page, and ended up writing this script.

An unofficial userscript for studying browser automation and course interfaces. It runs on Coursera course pages in the browser with a userscript manager. It requires no Tether extension, Codex bridge, local server, or API key.

> **Educational use only.** Use the script only where you have permission to automate the activity and handle its content. You are responsible for everything submitted from your Coursera account.

## Install

[**Install v1.4.0 with Tampermonkey**](https://raw.githubusercontent.com/udaysinh-git/coursera-standalone/v1.4.0/coursera-standalone.user.js)

1. Install or update [Tampermonkey](https://www.tampermonkey.net/) and enable userscript access if your browser prompts for it.
2. Click the install link and confirm in Tampermonkey. If you're upgrading, replace the existing script so only one copy runs.
3. Reload an authorized Coursera course page. Open **About** for a quick guide to the buttons.

If the link opens as plain text, copy the full script, including its metadata header, into a new script in Tampermonkey or [Violentmonkey](https://violentmonkey.github.io/) and save it. Disable the script in the manager to stop playback and form automation.

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

On first run, the welcome dialog links to [Tether in the Chrome Web Store](https://chromewebstore.google.com/detail/tether/bdkhlojbkkldeehiolelnmnpaanjdncc). Open the store page once to enable **Continue with standalone**. Installing Tether and leaving a review are optional. Your browser remembers the visit and acknowledgment locally. The **About** button explains playback, the activity panel, and what happens when you submit.

A dismissible message occasionally invites you to star [Tether on GitHub](https://github.com/udaysinh-git/tether). It appears on course overview, reading, or lecture pages at most about once a week when local storage is available. The browser stores the last display time locally and opens GitHub only if you click the link.

## What course platforms can do

This project illustrates a limit of browser-based assessment interfaces. The userscript operates in the learner's signed-in tab and uses ordinary form and navigation controls. A checkbox and a confirmation dialog can make intent clear to a learner. Authorship needs separate evidence. These are general design options based on the userscript's behavior and public standards.

- **Enforce attempt rules on the server.** Verify enrollment, attempt ownership, deadlines, and attempt limits when accepting a submission. Bind it to the current attempt and make repeated requests return the same result without consuming an extra attempt. Calculate the grade and record course credit on the server. These checks protect the attempt lifecycle even when a browser automates the form. [OWASP REST Security guidance](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html)
- **Give learners a meaningful review step.** Show the final answers and acknowledgment together before a high-stakes submission. Where stronger assurance is warranted, consider a separate, accessible approval bound to the exact attempt and answer snapshot. An extra click in the same page adds friction and offers limited assurance of authorship. [OWASP transaction authorization guidance](https://cheatsheetseries.owasp.org/cheatsheets/Transaction_Authorization_Cheat_Sheet.html)
- **Treat browser event checks as a limited safeguard.** The browser marks clicks produced by a page script with `HTMLElement.click()` as untrusted. A submit handler that rejects those events would stop the click path used by this script. Use that signal as a supplemental check and preserve keyboard and assistive-technology workflows. [WHATWG DOM Standard](https://dom.spec.whatwg.org/#dom-event-istrusted)
- **Assess understanding directly.** Keep practice quizzes low stakes and make tool-use rules explicit. For credential-bearing work, ask learners to explain their reasoning, apply concepts to a new example, or submit a small artifact with a short rationale. If mastery is the goal, assess it separately from whether a video reached its end.
- **Use signals for review.** Unusual submission patterns can justify a closer look. Fast completion, pasting, and keyboard-only interaction can also be legitimate. Use proportionate review and an appeal path. Preserve assistive technology and accessible alternatives if extra verification is required. [W3C accessible authentication guidance](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html)

For this repository, a possible follow-up would be a draft-only mode that pauses after filling answers and lets the learner complete the acknowledgment and submission directly in Coursera.

## Responsible use and disclaimer

Follow applicable law, the rules of your course or institution, and Coursera’s Terms of Use, Acceptable Use Policy, and Honor Code. Obtain any required permission before automating a course activity or sharing assessment content. Use only your own account and answer material you are permitted to use. This independent project has no affiliation with or endorsement from Coursera or any course provider. [Coursera Terms of Use and Honor Code](https://www.coursera.org/about/terms)

The software is provided **as is**, without warranties of any kind. Use it at your own risk. To the extent permitted by applicable law, the author and maintainers disclaim liability for losses, claims, or consequences arising from use, misuse, or inability to use it, including lost attempts, incorrect submissions, or account or academic penalties. This disclaimer does not limit rights or liabilities that applicable law makes nonwaivable.

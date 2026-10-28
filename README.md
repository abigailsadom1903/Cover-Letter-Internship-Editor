# Cover Letter Editor

A small, offline page for tailoring my internship cover letter: type the company's name and
address, check the A4 preview, and download a one-page PDF (or a Word file).

It is not part of the published portfolio site; it runs on your own computer.

## Project Overview

Cover Letter Editor is a single-page, browser-based tool for producing a tailored internship cover letter. Enter the company's name and address, review a live A4 preview, and download the finished letter as a one-page PDF or as a Word file. Everything runs locally in the browser; nothing is uploaded to a server.

## Problem Statement

Applying to several internships means sending a near-identical letter to many companies. Editing a word-processor file each time is slow and error-prone: addresses are missed, the layout shifts, the letter spills onto a second page, and personal details end up copied into places they should not be.

This tool keeps the letter text fixed, lets you change only what differs per application, and guarantees a clean one-page result.

## Features

- Live **A4 preview** that updates as you type the recipient's details.
- **One-page PDF export**, shrinking the text slightly when needed so the letter always fits.
- **Word file export** as an alternative format.
- **Editable letter text**, saved in the browser's local storage between visits.
- **Privacy-friendly:** personal address, phone number and signature stay in local files that are excluded from the repository.
- **Fully offline:** no backend, no accounts, no data leaves the computer.

## Technology Stack

| Area | Technology |
| --- | --- |
| Interface | HTML5, CSS3, JavaScript (single page, `index.html`) |
| PDF generation | jsPDF 2.5.1 (bundled in `lib/`, MIT licence) |
| Storage | Browser local storage |
| Optional local server | XAMPP (Apache) |

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/abigailsadom1903/Cover-Letter-Internship-Editor.git
   ```

2. **Open the editor.** Double-click `index.html`, or serve the folder with XAMPP (see *Open it* below). No build step or dependencies are required.

3. **Add your private details (optional).** Create `personal.local.js` and `signature.local.js` next to `index.html` as described in *Private details* below. Without them, you can enter your details in the page and they are remembered in your browser.

## Open it

- With XAMPP running (if this folder is inside `htdocs`): http://localhost/digital-portfolio/cover-letter-editor/
- Or double-click `index.html`.

## Private details (not on GitHub)

Your home address, phone number and signature are kept out of this repository. Put them in two
files next to `index.html`; both are listed in `.gitignore`:

`personal.local.js`

```js
window.PERSONAL_DEFAULTS = {
  senderAddress: 'Line 1,\nLine 2,\nPostcode City,\nState',
  phone: '012-345 6789',
};
```

`signature.local.js`

```js
window.DEFAULT_SIGNATURE = 'data:image/png;base64,...'; // a transparent PNG of your signature
```

Without these files the editor still works: enter your details once under
**Greeting, your details and signature** (and upload a signature image); they are remembered in
your browser.

## How it works

- Everything runs in the browser; nothing is uploaded.
- PDFs are created with [jsPDF](https://github.com/parallax/jsPDF) 2.5.1 (bundled in `lib/`, MIT licence),
  shrinking the text slightly when needed so the letter fits on one page.
- Edits to the letter text are saved in the browser's local storage.

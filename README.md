# Rich-Text Cleaner & Copier

This is a simple, single-file web-based tool to clean rich text content from unwanted invisible characters while preserving the original formatting.

## What it does

The tool provides a content-editable `div` where a user can paste rich text. When the "Clean & Copy" button is clicked, the tool performs the following actions:

1.  **Removes problematic characters**: It iterates through a predefined list of invisible or problematic Unicode characters (like soft hyphens, zero-width spaces, etc.) and removes them from the HTML content.
2.  **Normalizes spaces**: It replaces non-breaking spaces (`&nbsp;` and `\u00A0`) with regular spaces and collapses multiple consecutive spaces into a single one.
3.  **Preserves formatting**: All HTML tags responsible for formatting (like `<b>`, `<i>`, `<span>` with styles, etc.) are kept intact.
4.  **Copies to clipboard**: The cleaned rich text (as HTML) is copied to the user's clipboard.
5.  **Updates the editor**: The editor content is replaced with the cleaned version.

## How to use

1.  Open the `index.html` file in a modern web browser.
2.  Paste your rich text content into the editor area.
3.  Click the "✨ Bereinigen & Kopieren" button.
4.  The cleaned, formatted text is now in your clipboard, ready to be pasted elsewhere.

## Technical Details

The entire logic is contained within the `<script>` tag in the `index.html` file.

-   **`replacements` object**: This JavaScript object stores the key-value pairs of characters to be replaced. The key is the problematic character, and the value is what it should be replaced with (usually an empty string or a standard space).
-   **`cleanCopyBtn` Event Listener**:
    -   It reads the `innerHTML` of the editor.
    -   It iterates through the `replacements` object, using a regular expression to replace all occurrences of each problematic character.
    -   It uses the `navigator.clipboard.write()` API with a `Blob` of type `text/html` to copy the rich text.
    -   It provides visual feedback to the user by changing the button text and color upon successful copy.
-   **Styling**: The tool is styled with modern CSS, including a responsive layout, subtle animations, and a clean user interface.

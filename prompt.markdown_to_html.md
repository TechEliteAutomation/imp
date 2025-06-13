**[START OF PROMPT]**

**Your Task:**

Act as an expert web developer. I will provide you with Markdown text. Your sole function is to convert that Markdown into a single, self-contained HTML document.

**Requirements:**

1.  **HTML Structure:**
    *   Generate a complete and valid HTML5 document.
    *   The main content should be wrapped in an `<article>` tag for semantic clarity.

2.  **Styling (Embedded CSS):**
    *   All CSS must be embedded within a `<style>` block in the HTML `<head>`. Do not use external stylesheets.
    *   The styling must strictly adhere to the **Solarized Dark** color theme.
    *   All fonts and font sizes must be optimized for maximum readability on both desktop and mobile screens.

3.  **Solarized Dark Color Palette (Strict Adherence Required):**
    *   **Background:** `#002b36`
    *   **Main Text:** `#839496`
    *   **Headings:** `#93a1a1`
    *   **Borders/Muted Text:** `#586e75`
    *   **Code Blocks/Highlight Background:** `#073642`
    *   **Links:** `#268bd2`
    *   **Bold/Strong Text:** `#b58900`
    *   **Italic/Emphasized Text:** `#cb4b16`

4.  **Typography for Optimal Viewing:**
    *   **Font Family:** Use a clean, sans-serif font stack like `'Helvetica Neue', Arial, sans-serif`.
    *   **Base Font Size:** `16px`.
    *   **Line Height:** `1.6` for body text.
    *   **Responsive Units:** Use `rem` for font sizes so they scale correctly.
    *   **Line Length:** The main content container should have a `max-width` of approximately `45rem` to ensure comfortable line lengths for reading.
    *   **Heading Hierarchy:** Ensure a clear visual distinction between `<h1>`, `<h2>`, `<h3>`, etc., with progressively smaller font sizes.

**Execution:**

Upon receiving the Markdown text from me, provide only the complete, final HTML code as your response. Do not add any conversational text, explanations, or apologies.

---

**Model Settings to Use:**

*   **Temperature:** `0.2`
*   **Top P:** `0.4`
*   **Output Length:** Default settings are sufficient. The model should not truncate the output as long as the input Markdown is of a reasonable length.

**[END OF PROMPT]**

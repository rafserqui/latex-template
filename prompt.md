Files and evidence:
- Current style: clean_style_beamer.sty
- Directory for reference: /home/rafserqui/Data/RESEARCH/teachers-quality/
- Previous reference PDF: tex/slides/design-audit-2026-10-24/previous.pdf
- Full design audit: tex/slides/design-audit-2026-10-24/README.md
- Paired comparison: tex/slides/design-audit-2026-10-24/comparison.pdf

Read the current style and audit, and inspect the reference PDF before editing. Make the smallest complete change that restores the following design.

1. Typography

- Restore actual Source Serif Pro Regular, Bold, and Italic throughout presentation text, including titles, body text, citations, captions, tables, and theorem prose.
- Source Serif 4 is a different font and does not satisfy this requirement.
- Preserve proportional old-style numerals in ordinary text.
- Identify an explicit, reliable way to select the original font with the existing compilation engine. Verify the embedded PDF font names. If the font is unavailable, report the missing dependency rather than silently substituting another face.
- Preserve the professionalfonts treatment and Palatino/Pazo mathematics through mathpazo, including the existing mathematical symbol packages.
- Preserve the Latin Modern variable-width monospace family used for buttons and code.
- Use semantic LaTeX sizes that follow the document class. Preserve the existing hierarchy: huge presentation title, Large frame/section titles, large proposition headings, normalsize body text, small nested-list text, footnotesize reduced citations, and tiny button labels.
- Do not globally shrink tables or figures.

The reference uses a 10pt Beamer class. Its approximate rendered sizes are 20.66 PDF pt for the presentation title, 14.35 for frame titles, 11.96 for proposition headings, 9.96 for body text, 8.97 for nested lists, and 7.97 for reduced citations. These are validation measurements, not fixed sizes to impose on every class option.

2. Colours and emphasis

- MainColor: #0077B6, used for titles, section headings, structural elements, bullet/number labels, caption labels, theorem headings, and button outlines/text.
- Restore a separate alert colour: #FE5F55.
- \alert must use the coral alert colour.
- Ordinary blue bold emphasis, including \tbf where provided, must remain MainColor with bold weight.
- Ordinary text is black; the slide background is white.
- Standard citation links: #B50045.
- Reduced/discrete citations: #3E3D40.
- Preserve the existing URL/file-link colour #8338EC and remaining named colours unless evidence requires a change.
- Preserve the existing primary/secondary/tertiary/quaternary palette definitions.
- Do not introduce new decorative backgrounds, gradients, shadows, or accent colours.

3. Lists

- First-level itemize marker: Font Awesome regular dot-circle.
- Second-level marker: Font Awesome solid long-arrow-alt-right, replacing the current hollow square.
- Restore fixed-width Font Awesome icon boxes. Loading fontawesome5 with its fixed option reproduced the previous alignment.
- Preserve text indentation and label separation through relative list layout; do not hardcode slide coordinates.
- Preserve the existing additional item separation of 0.8\baselineskip for itemize and enumerate, including nested lists.
- Keep numbered-list labels blue.
- Preserve Beamer overlay syntax, optional list arguments, nesting, and grouping. Apply spacing once per environment; avoid wrappers that swallow optional arguments.
- Third-level bullet appearance is not established by the reference. Preserve its current setting rather than inventing a historical design.

For validation only: in the reference 10pt/16:9 layout, ordinary bullet origins are approximately x=30.837 PDF pt with text at x=48.272; nested arrow origins are x=52.568 with text at x=68.197. Restore these through fixed-width boxes, not manual shifts.

4. Title page and slide layout

- Preserve the existing plain Beamer layout, margins, and default body alignment.
- Presentation title: centred, blue, regular serif, huge.
- Authors: centred, smaller black text, with normal Beamer affiliation superscripts.
- Institutions: centred, smaller black text.
- Allow titles and author lists to wrap naturally.
- Respect \title, \subtitle, \author, \institute, \date, and their short forms.
- The reference has an empty date because its document supplies \date{}. Do not globally suppress dates.
- Do not hardcode title line breaks, author rows, affiliations, presentation metadata, aspect ratio, or document-class font size.
- Keep navigation symbols hidden.
- Preserve the absence of visible footer text, progress bars, and slide numbers in the restored default design.

5. Section and subsection pages

- Preserve automatic section divider frames with centred blue serif section names on a white background.
- Retain the current section-page template’s relative spacing: its 1em vertical skip and centred colour box with 12pt separation.
- Use the document’s section names dynamically.
- Preserve current subsection-page support and its matching treatment; the old PDF does not establish a different subsection design.
- Keep starred-section and overlay behaviour compatible with Beamer.

6. Theorems and equations

- Preserve the AMS-style theorem presentation: blue numbered headings, italic prose for propositions and other plain-style theorem environments, and no filled theorem box.
- Keep normal definition/example theorem-style semantics.
- Preserve optional theorem names and equation numbers on the right.
- Reuse existing Beamer theorem environments and counters where available; define missing environments without duplicate-definition errors.
- Support both ordinary Beamer documents and documents using the notheorems class option.
- Preserve existing public theorem environments and aliases.
- Do not hardcode theorem or equation numbers.

7. Citations

- Preserve biblatex author–year citations with Biber and existing natbib-compatible commands.
- Preserve maxcitenames=2 and uniquelist=false.
- Add uniquename=false to restore the previous compact surname presentation instead of expanded initials/given names.
- Preserve hyperlink treatment of citation authors and years.
- Preserve \smallcite: footnotesize, square-bracket wrapper, locally dark-grey citation links, with normal colours restored afterward.
- Keep ordinary citation links magenta.
- Preserve existing citation commands and custom macros unless a change is necessary for restoration.
- Do not add presentation-specific bibliography paths, bibliography entries, or metadata.

8. Captions, tables, and buttons

- Preserve numbered figure/table captions with blue labels and black descriptive text.
- Preserve blue subfigure letters and black subcaption text.
- Keep captions centred within their containing width and allow natural wrapping.
- Preserve the existing caption-size hierarchy and normal placement conventions.
- Keep counters automatic; do not encode the reference deck’s number of figures or tables.
- Preserve booktabs-compatible table styling without adding vertical rules, shaded rows, or forced table dimensions.
- Buttons retain white fill, blue text and border, rounded outlines, the normal directional arrow, and small monospace labels.
- Preserve hyperlink functionality and existing appendix-numbering support.

9. Reusable emphasis and callout helpers

The reference also uses two generic helpers currently defined in the presentation preamble:

- \tbf: MainColor plus bold weight.
- mblock: a tcolorbox with colback=gray!10, border colour #E4572E, boxsep=1pt, and arc=2pt.

Make these reusable through the shared preamble while preserving existing callers. If their definitions move into the style, remove only the duplicate preamble definitions in affected callers. Do not change slide content or convert all Beamer blocks into mblock.

Retain existing code-listing support and other public helpers. Their historical appearance is not established by this PDF, so preserve current behaviour rather than inventing a redesign.

10. Scope and verification

- Implement this in the shared style and any strictly necessary font/helper files.
- Presentation changes should be limited to necessary preamble compatibility adjustments.
- Leave slide bodies, wording, equations, data, bibliography contents, chart assets, and plotting code unchanged.
- The chart palettes, plot markers, legends, panel arrangements, image aspect ratios, and table-content differences documented in the audit are outside this preamble restoration.
- Do not compensate for font changes with slide-specific \vspace, \hspace, absolute positioning, automatic fitting, or content-dependent patches.
- Do not chase sub-point rendering differences using arbitrary offsets.

Validate with:
- A representative reference build using 10pt and 16:9.
- A second small presentation using another class font size and aspect ratio, with a long title, multiple authors, and a supplied date.
- Nested lists and overlays, section/subsection dividers, theorem environments, numbered equations, citations, captions/subfigures, a table, buttons, and the callout helper.
- Embedded-font inspection confirming Source Serif Pro.
- A visual comparison of unchanged reference material, especially nested bullets, alert text, and proposition slides.

Use temporary build directories. Return the updated reusable style, a concise explanation of the changes, and the validation results. Clearly identify any unavailable font or historically unobservable setting.

I haven’t applied changes. Unused features remain uncertain because the previous PDF cannot reveal their original settings.

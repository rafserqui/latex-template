# Latex Templates

For my own use, I have a template for slides and a template for articles.

Locate them in `~/texmf/tex/latex/` and save them as `.sty` files. Then, to use them, just include

```{latex}
\usepackage{name_of_template}
```

## Beamer design

`clean_style_beamer.sty` uses the current `sourceserif` package (Source Serif 4),
proportional old-style numerals, Pazo mathematics, and Latin Modern variable-width
monospace. Source Serif Pro is intentionally not restored.

Alerts use coral `#FE5F55`; structural elements and `\tbf{...}` use blue
`#0077B6`. The shared `mblock` environment provides the grey callout with an
orange border. Remove duplicate `\tbf` and `mblock` definitions from a caller's
preamble when switching to this style.

List spacing preserves Beamer's optional arguments and overlays. Theorem
environments work with ordinary Beamer and the `notheorems` class option; native
Beamer counters are reused when present, and the style's independent counters
are retained with `notheorems`.

## Design proof

Open [the 10pt/16:9 test deck](beamer_design_test.pdf) or
[the 12pt/4:3 test deck](beamer_design_test_12pt_4x3.pdf).
Both are built from [the same source](beamer_design_test.tex) and illustrative
bibliography. The source includes assertions for list spacing and availability
of all public theorem environments/aliases.

Build from this directory with pdfLaTeX and Biber, keeping intermediate files
outside the repository:

```sh
build_dir=$(mktemp -d /tmp/beamer-design-test-XXXXXX)
latexmk -pdf -interaction=nonstopmode -halt-on-error -recorder \
  -outdir="$build_dir" beamer_design_test.tex
cp "$build_dir/beamer_design_test.pdf" beamer_design_test.pdf
```

To exercise another configuration, create a temporary driver containing the
following and pass that file to the same `latexmk` command:

```tex
\def\DesignTestOptions{12pt,aspectratio=43,notheorems}
\input{beamer_design_test.tex}
```

### Validation, 25 October 2026

| Class configuration | Pages | Warnings / overfull boxes | Internal links resolved |
| --- | ---: | --- | ---: |
| 10pt, 16:9 | 23 | 0 / 0 | 29 |
| 10pt, 16:9, `notheorems` | 23 | 0 / 0 | 29 |
| 12pt, 4:3 | 23 | 0 / 0 | 29 |
| 12pt, 4:3, `notheorems` | 23 | 0 / 0 | 29 |

Embedded fonts include Source Serif 4 Regular/Bold/Italic, Pazo/Palatino math,
and LMMonoProp. The 10pt title/frame/theorem/body/nested/citation/button sizes
measure 20.6625 / 14.3462 / 11.9552 / 9.9626 / 8.9664 / 7.9701 / 4.9813 PDF pt.
PDF inspection also checked citation colours before/inside/after `\smallcite`,
compact surnames, coral alerts, blue emphasis and theorem headings, subcaption
labels, centred wrapped captions, and internal link destinations.

The historical 52-page reference and both current teachers decks (52 and 13
pages) compile using the workspace style, with no font-substitution warnings or
overfull boxes. On reference page 3, bullet origins match the audit exactly:
30.837 PDF pt for dot-circles and 52.568 PDF pt for nested arrows. Visual
comparisons covered the title, section divider, nested lists, coral callout,
and unchanged proposition pages 23–24.

The teachers decks retain their existing missing citation-destination warnings
(28 historical, 30 current full, 1 current short); the full deck's destination
warnings were verified against a build using the original installed style.
Slide bodies, bibliographies, chart assets, and the installed `~/texmf` style
are unchanged. Settings unseen in the historical PDF retain current behaviour;
the font remains the explicitly chosen Source Serif 4.

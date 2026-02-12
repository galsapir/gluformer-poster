# Creating an outstanding GluFormer poster for the European AI Forum

**GluFormer — a foundation model that predicts diabetes up to 12 years early using continuous glucose monitoring data — deserves a poster that matches the ambition of its Nature publication.** This report synthesizes research on the PaperBanana tool, modern poster design best practices, creative visualization strategies, and audience context to deliver a concrete blueprint for building a stunning, narrative-driven scientific poster. The key insight: for a mixed policy-industry-academic audience in Paris, the poster must communicate clinical impact at a glance while offering depth for specialists — and an interactive web version can extend its reach far beyond the conference hall.

---

## PaperBanana is powerful but has critical limitations for this use case

PaperBanana is an agentic AI framework from Peking University and Google Cloud AI Research (arXiv:2601.23265, January 2026) that uses five specialized AI agents to transform scientific text descriptions into publication-quality illustrations. Its pipeline works in two phases: a **linear planning phase** (retriever → planner → stylist agents) followed by an **iterative refinement phase** (visualizer → critic agents, 3 rounds). It runs on Google's Gemini models and can generate methodology diagrams, flowcharts, statistical plots, and architecture figures.

For GluFormer's poster, PaperBanana can generate several critical assets. It excels at creating **transformer architecture diagrams**, system pipeline illustrations, and bar/line charts via executable Matplotlib code (which eliminates numerical hallucination). Its NeurIPS-trained aesthetic guidelines produce clean, professional-looking diagrams. The tool is available via CLI (`paperbanana generate --input method.txt`), Python API, or MCP server through an unofficial community implementation at github.com/llmsresearch/paperbanana — the official code has not yet been released.

However, three limitations matter for a Nature-quality poster:

- **Raster-only output** (PNG/JPG, no vector SVG/EPS) — a significant constraint for large-format printing. Workaround: generate at 4K resolution and use PaperBanana's Matplotlib code-generation mode for statistical plots, then customize the code manually for precise styling.
- **Content fidelity scored only 45.8%** on benchmarks, with connecting lines and arrows frequently misaligned. Every generated diagram must be manually verified.
- **Non-editable outputs** — you cannot tweak individual elements post-generation. The recommended workflow is to use PaperBanana for rapid prototyping and initial drafts, then recreate final figures in Adobe Illustrator or Figma for full control.

The best strategy is to use PaperBanana as a **design accelerator**: generate initial versions of the architecture diagram, prediction pipeline, and result charts, then refine the best outputs manually or use the generated Matplotlib code as a starting point for publication-quality statistical figures.

---

## The GluFormer story has a powerful narrative arc for poster design

The paper, "A foundation model for continuous glucose monitoring data," presents a decoder-only GPT-style transformer with **16 layers and 16 attention heads** trained on over **10 million glucose measurements** from 10,812 adults. Its core innovation is treating CGM data like language — tokenizing raw glucose values (40–500 mg/dL) into 460 discrete bins and applying autoregressive next-token prediction with causal masking. This "grammar of glucose dynamics" approach captures far richer information than traditional summary metrics like time-in-range or GMI.

The poster's narrative should follow the paper's most compelling arc. Start with the global diabetes crisis (**10% of world population affected, projected to exceed 1.3 billion by 2050**), then reveal that standard clinical metrics vastly underutilize the information in raw glucose dynamics. Present GluFormer as the solution — a foundation model that extracts deep representations from CGM data, validated across **19 external cohorts spanning 5 countries and 8 CGM devices**. Build to the headline result: in the AEGIS cohort with 11-year median follow-up, **66% of incident diabetes cases fell in GluFormer's top risk quartile** versus only 7% in the bottom quartile (p = 2.3 × 10⁻⁶), and **69% of cardiovascular deaths occurred in the top quartile** with 0% in the bottom — while HbA1c, the clinical gold standard, showed no significant predictive power over this timeframe. Close with the multimodal "Digital Twin" dietary extension for precision nutrition.

The five main paper figures map naturally to poster sections: Figure 1 (architecture overview), Figure 2 (generative capabilities), Figure 3 (risk stratification — the showstopper result), Figure 4 (clinical prediction benchmarks), and Figure 5 (dietary multimodal extension).

---

## A concrete poster layout combining Better Poster principles with Nature quality

Mike Morrison's **#BetterPoster framework** (250,000+ downloads, preferred by 68% of conference attendees in surveys) provides the structural foundation. His key insight: a poster must work at three distances — the **10-foot glance** (title + central finding readable across the room), the **3-foot browse** (visual story comprehensible in 60 seconds), and the **1-foot deep read** (supporting details for engaged visitors). For a European conference, **A0 portrait format** (84.1 × 118.9 cm) is standard.

Here is a recommended layout with six zones:

**Zone 1 — Title Banner (top 12%).** Use a declarative title that states the finding: *"A Foundation Model for Glucose Data Predicts Diabetes and Cardiovascular Mortality Up to 12 Years Ahead."* Author names, affiliations (Weizmann, NVIDIA, Pheno.AI), and the Nature citation. Include institutional logos sized modestly. A QR code in the top-right corner linking to the GitHub repo and interactive web poster.

**Zone 2 — Hero Central Panel (30%).** The single most important visual: a **combined risk stratification figure** showing Kaplan-Meier-style curves or stacked bar charts for the AEGIS 11-year outcomes. The "66% of diabetes in top quartile vs. 7% in bottom" and "69% of cardiovascular deaths in top quartile vs. 0%" results, with GluFormer's prediction compared side-by-side against HbA1c's failure to discriminate. Use AGP-standard color conventions: green for low-risk, progressing through yellow to red for high-risk quartiles. This is the figure that stops people walking past.

**Zone 3 — Architecture Pipeline (left column, 20%).** A clean left-to-right (or top-to-bottom) flow diagram: raw CGM waveform → tokenization into 460 discrete bins → causal transformer (show a simplified block with attention heads) → learned embeddings → downstream prediction heads. Use PaperBanana to generate the initial draft, then refine. Color-code each stage consistently. Below the pipeline, include a small "Ambulatory Glucose Profile" (AGP) modal day plot showing the input data format — this is instantly recognizable to anyone in diabetes/metabolic health.

**Zone 4 — Key Results Dashboard (right column, 20%).** A compact multi-panel figure showing: (a) bar chart of GluFormer vs. baseline metrics across clinical predictions (HbA1c, visceral adipose tissue, liver function, blood pressure), (b) generalization validation across 19 cohorts with a small world map highlighting the 5 countries, and (c) the multimodal dietary extension showing predicted vs. actual glucose response to different meals. Generate these charts using PaperBanana's Matplotlib code mode for numerical accuracy.

**Zone 5 — Punchline Statement (center-bottom, 10%).** In large, bold text (≥48pt): *"Two weeks of glucose monitoring data encodes a decade of health trajectory — and standard clinical metrics miss most of it."* This is the Morrison-style "punchline" readable from across the room.

**Zone 6 — Methods Summary + QR Codes (bottom 8%).** Minimal text: training data (10M measurements, 10,812 adults), architecture specs (16 layers, 16 heads, 1024-dim embeddings), and validation scope (19 cohorts, 5 countries, 8 devices). Two QR codes: one to the Nature paper, one to the interactive web poster.

---

## Color scheme and typography designed for impact and accessibility

For a Nature-published paper about metabolic health, the color palette should blend clinical authority with modern AI aesthetics. Here is a specific, tested recommendation:

**Primary palette (3 colors):**
- **Deep navy (#1B2A4A)** — backgrounds, headers, authority
- **Teal/cyan (#00B4D8)** — the "AI/tech" accent color, used for the transformer architecture elements and model-related graphics
- **Warm coral (#E63946)** — the "health/alert" accent, used sparingly for key findings, risk highlights, and above-range glucose zones

**Supporting palette:**
- **Soft green (#2A9D8F)** — for time-in-range glucose zones and positive results
- **Light grey (#F8F9FA)** — panel backgrounds
- **Amber (#F4A261)** — secondary accent for moderate risk/transition zones

This palette is **colorblind-safe** when tested with the Coblis simulator — the teal and coral maintain distinct hue separation for deuteranopia and protanopia. It also aligns with the **AGP standard color conventions** (green = in range, yellow/amber = above range, red = high risk) that diabetes clinicians recognize instantly.

**Typography:** Use **two font families maximum**. For a clean, modern feel: **Inter or Source Sans Pro** for body text (sans-serif, excellent screen and print legibility), paired with **Playfair Display or Source Serif Pro** for the title and section headers (serif, adds authority). Title at **85–100pt**, section headers at **36–48pt**, body text at **24–28pt**, captions at **18–20pt**. Left-align all text. Line spacing at 1.3×.

---

## An interactive web poster doubles the impact

The most forward-thinking approach for 2025–2026 is to create **both a physical poster and an interactive web version** hosted on GitHub Pages. The web version transforms a static poster into a living document with hover-over tooltips on glucose traces (via Plotly), zoomable ROC curves, and clickable links to the paper, code, and data.

The best template for this is **cpitclaudel/academic-poster-template** (GitHub) — a pure HTML5 + CSS framework that scrolls left-to-right on wide screens and top-to-bottom on mobile, supports MathJax for equations, and is fully accessible to screen readers. An alternative is **martinlicht/SciPosterHTML**, which offers lightweight HTML+CSS+MathJax examples that can print to PDF directly from the browser.

The implementation workflow: build the poster layout in HTML/CSS using the template, embed Plotly.js charts for interactive glucose traces and prediction results, add the static hero figures generated via PaperBanana and refined in Illustrator/Figma, then deploy to GitHub Pages at a URL like `guylu.github.io/gluformer-poster`. The physical poster includes a prominent QR code linking to this URL. Visitors who scan it during the poster session get the interactive experience; those who discover it later can explore the full results at their leisure.

Key interactive elements to include: a **glucose trace explorer** (select different patient profiles to see model predictions overlaid on real CGM data with confidence bands), an **attention heatmap** showing which time windows the transformer focuses on for each prediction type, and a **cohort comparison tool** letting users toggle between the 19 validation cohorts.

---

## Specific figure designs that communicate complex ML results visually

**Hero Figure — "From Glucose Grammar to Health Predictions":** A horizontally flowing infographic spanning the poster's width. Left panel: a raw CGM trace (the familiar ambulatory glucose profile with median line, IQR band, and 5th–95th percentile envelope). Center panel: the tokenization step shown as the continuous signal being discretized into colored blocks, feeding into a simplified transformer block with attention arcs connecting distant time points. Right panel: the learned embedding space visualized as a UMAP plot where points are colored by metabolic phenotype (healthy → prediabetic → diabetic), with arrows pointing to the downstream prediction targets arranged in a radial layout (HbA1c, cardiovascular risk, liver function, etc.). This single figure tells the entire story.

**Attention Visualization — "What the Model Sees":** An innovative strip visualization where a 24-hour glucose trace runs horizontally, with a heatmap strip directly below showing attention weights — bright (teal) regions indicate where the transformer focuses most. Overlay vertical dashed lines at meal times. This immediately communicates that the model learns clinically meaningful patterns (post-meal glucose excursions, overnight dynamics) without requiring the viewer to understand transformer internals.

**Risk Stratification — "A Decade of Prediction from Two Weeks of Data":** The poster's centerpiece. Two side-by-side panels: left shows GluFormer's quartile stratification with dramatically divergent outcome curves (Q1 = 0% cardiovascular deaths, Q4 = 69%); right shows HbA1c quartiles with overlapping, non-significant curves. The contrast is visually striking and immediately communicates the paper's most important finding. Use the coral-to-green color gradient for quartiles.

**Generalization Map:** A minimal world map with five highlighted countries (Israel, Spain, Australia, and others) connected by lines to a central "GluFormer" node, with small icons indicating the 8 different CGM devices used. Annotate with "19 cohorts, 6,044 participants" — this communicates robustness in seconds.

**Digital Twin Panel:** A split-screen showing two simulated glucose responses — one for pizza, one for salad — generated by the multimodal model for the same virtual patient. This is the most accessible, engaging element for non-specialist audience members and demonstrates the precision nutrition application.

---

## Tailoring the poster for a European policy-industry-academic audience

The European AI Forum (EAIF) is an umbrella organization of 13 national European AI associations representing **3,000+ members** across SMEs, corporates, and research institutions. Its events attract a distinctive mix of **EU policymakers, AI entrepreneurs, and academics** — this is not a pure ML research conference. Previous editions featured EU Commissioners and national ministers alongside startup founders. The 5th edition was held in Paris during France's 2022 EU Presidency, organized by Hub France IA.

This audience mix demands a poster that works on multiple levels. For **policymakers**: lead with clinical impact and public health relevance (the 1.3 billion diabetes projection by 2050, the potential for early intervention enabled by over-the-counter CGM devices recently cleared by the FDA). For **industry attendees**: highlight the practical applications (precision nutrition, clinical trial optimization, Digital Twin simulations) and the foundation model paradigm's scalability. For **researchers**: provide the technical depth through the architecture diagram, validation rigor across 19 cohorts, and the QR code to the full Nature paper.

Avoid dense equations entirely. The poster should contain **fewer than 500 words** of body text. Replace every paragraph you'd normally write with a figure, a bold statistic, or a one-sentence takeaway. At an event where ministers share the room with machine learning researchers, visual storytelling wins over mathematical formalism.

---

## Avoiding the mistakes that made the previous poster "not very good"

The LMRL workshop poster (presented at ICLR 2025) preceded the Nature publication and likely suffered from common ML poster pitfalls. Research on thousands of conference posters identifies the most damaging mistakes: **too much text** (the "wall of text" problem affects roughly 75% of academic posters according to a 2023 Frontiers in Communication study), **poor visual hierarchy** (key findings buried instead of highlighted), **tables of raw numbers** (unreadable at poster distance), **excessive math** (CVPR attendee Paul Gavrikov: "some concepts might be hard to grasp after a long conference day"), and **architecture diagrams shrunk to accommodate text**.

The new poster should invert every one of these patterns. Where the LMRL poster likely had paragraphs, use bold single-sentence takeaways. Where it had comparison tables, use bar charts with highlighted winners. Where it had a small architecture figure squeezed between text blocks, make the pipeline diagram a full-width hero element. Where it had standard ICLR workshop formatting, adopt the Nature-quality billboard approach where the main finding is readable from 10 feet away.

Expert Colin Purrington recommends a maximum of **800 words** total (700 body + 100 in figure legends). For this poster, aim for **400–500 words** — the figures and bold statistics should carry the narrative load. Computer scientist Ruben Verborgh captures it perfectly: *"The job of an effective poster is to get people's attention. No less, no more."*

---

## Conclusion: a step-by-step production workflow

The path from research to finished poster is concrete. **Week 1:** Write the declarative title and five one-sentence section summaries. Generate initial architecture and pipeline diagrams using PaperBanana (`paperbanana generate --input gluformer_method.txt --caption "GluFormer architecture overview"`). Generate statistical charts using PaperBanana's Matplotlib code mode, then customize the code for the exact Nature figure style. **Week 2:** Refine the best PaperBanana outputs in Figma or Illustrator — fix any connection errors, apply the navy/teal/coral color palette, ensure all text is ≥24pt. Build the poster layout in either Figma (for print) or the cpitclaudel HTML template (for the web version). **Week 3:** Create the interactive web version with Plotly-embedded glucose traces and attention visualizations, deploy to GitHub Pages. Print the physical poster at 300 DPI on A0 matte paper. Add QR codes linking to the web poster, Nature paper, and GitHub repo. **Day before:** Practice a 2-minute pitch that starts with "Two weeks of glucose data can predict your health a decade from now" and builds to the AEGIS cohort results.

The result will be a poster that works as a billboard for passersby, a visual story for browsers, a technical reference for specialists, and an interactive web experience for anyone with a phone — all communicating that GluFormer represents a paradigm shift in how we extract health insights from wearable glucose data.
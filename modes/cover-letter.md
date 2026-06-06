# Mode: cover-letter — 1-Page Cover Letter PDF

## Full pipeline

1. Read `cv.md`, `modes/_profile.md`, and `article-digest.md`
2. Get the evaluation report:
   - If a report number or company name is given → read from `reports/`
   - If no report exists → ask for JD text or URL, run a quick read to extract signals (no full A-F evaluation needed)
3. Extract key signals:
   - **Fit signals** (from Block A / JD): top 3 requirements the candidate directly meets
   - **Company hook** (from Block D / company research): one concrete and specific detail — a product, publication, funding round, stated mission, or team fact. Never use generic descriptions.
   - **What to lead with** (from Recommendation block): the angle the evaluation already identified
   - **What to avoid** (from Recommendation block): gaps, irrelevant experience to not mention
4. Select top 3 proof points from `article-digest.md` that map directly to the JD's top requirements
5. Detect JD language → letter language (EN default)
6. Detect company location → paper format: US/Canada → `letter`; rest of world → `a4`
7. Write 4 paragraphs (fill the page — see Writing rules for length guidance):

   **Opening:** Start with a specific, concrete observation about the company — not a compliment, a fact. Then one sentence on why this role specifically, not the company generally.

   **Body 1:** Two or three proof points mapped directly to the JD's top requirements. Name the project or system. Use quantified outcomes where available. Mirror the JD vocabulary exactly — same words, not synonyms.

   **Body 2:** Domain fit and role-specific angle. Connect the candidate's background to the company's specific challenge identified in the evaluation. If a required skill is missing, omit it entirely. Do not reframe gaps as adjacent strengths, and do not acknowledge them.

   **Closing:** Direct CTA. Reference CV and portfolio URL. Mention EU Blue Card if the role is in Europe and visa is relevant.

8. Read `name` from `config/profile.yml` → normalize to kebab-case lowercase → `{candidate}`
9. Slugify company name → `{company}`
10. Write HTML to `/tmp/cover-letter-{candidate}-{company}.html` using `templates/cover-letter-template.html`
11. Execute:
    ```bash
    node generate-pdf.mjs /tmp/cover-letter-{candidate}-{company}.html output/cover-letter-{candidate}-{company}-{YYYY-MM-DD}.pdf --format={letter|a4}
    ```
12. Report: PDF path, word count

## Writing rules

- **Length: fill the page, stay on 1 page** — write enough to leave no more than 2-3 cm of white space at the bottom. After generating the PDF, check the page count: if 2 pages, trim Body 2 first then Body 1; if the bottom margin looks excessive, expand with a concrete detail or additional proof point. Word count is irrelevant — the page is the constraint.
- **Selective, not comprehensive** — pick only the 2-3 experiences most relevant to this specific JD. Do not list the full portfolio. What is not mentioned is as important as what is.
- **No fabrication, no reframing** — if a required skill is missing, omit it. Do not present adjacent experience as a substitute or acknowledge the gap. The letter covers only genuine fit.
- **Industry-friendly language** — prefer plain, direct terms over academic phrasing. "Built" not "architected". "Improved" not "ameliorated". "Tested" not "empirically validated". Write as a practitioner, not a researcher writing a paper.
- **No long dashes** — never use "—". Use a comma, a full stop, or rewrite the sentence instead.
- **No clichés:** "excited to apply", "passionate about", "I believe I would be a great fit", "team player", "results-driven", "leverage my skills"
- **First sentence is about them, not you** — anchor to something specific about the company: a product, a publication, a stated research direction, a funding round.
- **Mirror JD vocabulary exactly** — if the JD says "training dynamics", use "training dynamics", not "model training behavior".
- **Never invent** experience or metrics — only what is in `cv.md` and `article-digest.md`.
- Follow `## Writing Style` in `_profile.md` if it exists.

## Template placeholders

| Placeholder | Content |
|-------------|---------|
| `{{LANG}}` | `en` (or language code if non-English) |
| `{{PAGE_WIDTH}}` | `210mm` (A4) or `8.5in` (letter) |
| `{{NAME}}` | from `config/profile.yml` |
| `{{PHONE}}` | from `config/profile.yml` (omit span + separator if empty) |
| `{{EMAIL}}` | from `config/profile.yml` |
| `{{LINKEDIN_URL}}` | from `config/profile.yml` |
| `{{LINKEDIN_DISPLAY}}` | from `config/profile.yml` |
| `{{PORTFOLIO_URL}}` | from `config/profile.yml` |
| `{{PORTFOLIO_DISPLAY}}` | from `config/profile.yml` |
| `{{LOCATION}}` | from `config/profile.yml` |
| `{{DATE}}` | formatted as "June 6, 2026" |
| `{{COMPANY_NAME}}` | company name from report |
| `{{ROLE_TITLE}}` | job title from report |
| `{{ADDRESSEE}}` | "Hiring Team" unless a specific recruiter/HM name is known from the report or JD |
| `{{OPENING_PARAGRAPH}}` | hook paragraph (60–80 words) |
| `{{BODY_PARAGRAPH_1}}` | proof points paragraph (90–110 words) |
| `{{BODY_PARAGRAPH_2}}` | domain fit paragraph (80–100 words) |
| `{{CLOSING_PARAGRAPH}}` | CTA paragraph (40–60 words) |

## Post-generation

Update tracker if the job is already registered: append cover letter path to the notes column.

# Deliverable 8 — Legal Disclaimer Language

Legal safety language appears **at the beginning, throughout the experience, and
in the final report**. This file is the single source of truth for that language.

## 1. Core disclaimer (canonical — use verbatim)

> **This tool provides general education and navigation support for Harris County
> residents. It is not legal advice, does not create an attorney-client
> relationship, and should not be relied upon to make legal decisions. For advice
> about your specific situation, please speak with a licensed Texas attorney.**

## 2. Framing statement (what the tool can / cannot do)

> "I can help you understand what issues may be present, what records may be
> needed, what public offices or partners may be involved, and what questions you
> may want to ask a licensed Texas attorney. I cannot provide legal advice,
> determine ownership, determine heirship, or tell you what legal action to take."

## 3. Placement matrix

| Location | Language used |
|---|---|
| Landing page (above the fold) | Core disclaimer (short form link to full) |
| Welcome & Consent (Section 1) | Core disclaimer + framing + consent checkbox |
| Persistent screener banner | "Educational only — not legal advice." (links to full) |
| Sensitive sections (family conflict, taxes) | Inline reminder relevant to that section |
| Escalation flag moment | Escalation language (below) |
| Conversational mode | Legal-advice-refusal language (below) |
| Family Property Roadmap §1 | Core disclaimer + framing (full) |
| Every page footer | "This is not legal advice." → links to `/disclaimer` |
| PDF/email export | Core disclaimer on first and last page |

## 4. Consent confirmation (Section 1)

Checkbox the user must select to proceed:

> "I understand this tool is educational and does not provide legal advice."

## 5. Do-not-say list (never output)

- "You should file probate."
- "You are the owner."
- "You are the legal heir."
- "This person owns the property."
- "This legal option applies to you."
- "This will clear your title."
- "You qualify for this remedy."
- "You should sell."
- "You should transfer the property."
- "You should sign this document."

## 6. Safer-language substitutions (use instead)

| Instead of a conclusion | Say |
|---|---|
| "You should file probate." | "This may be something to discuss with a licensed Texas attorney." |
| "You are the owner / heir." | "Your answers suggest this may involve a probate, title, tax, or heirship question." |
| "This option applies to you." | "A licensed attorney can help determine whether this option applies." |
| "This will clear your title." | "This pathway is intended to help you prepare for professional review." |
| (any directive) | "You may want to gather these records before speaking with legal aid or an attorney." |
| (any determination) | "This is not a legal conclusion." |

## 7. Escalation language (when an urgent flag fires)

> "Because you mentioned a notice, court paper, tax issue, foreclosure risk, or
> pressure to sign documents, this may require urgent review by a licensed attorney
> or qualified legal aid organization. This tool cannot tell you what legal action
> to take, but it can help you organize records and questions to bring to a
> professional as soon as possible."

## 8. Legal-advice refusal (Conversational Navigation Mode)

When a user asks for legal advice:

> "I cannot provide legal advice or tell you what legal action to take. I can
> explain the general issue, help you identify records to gather, and suggest
> questions to ask a licensed Texas attorney."

Then continue helping educationally.

## 9. Data-sharing & confidentiality note (where consent is requested)

> "Information is shared with a partner organization only if you give consent.
> Legal confidentiality and privacy rules are protected, and you may decline data
> sharing." (Full language in [Deliverable 9](./09-privacy-and-consent.md).)

## 10. Implementation guidance

- Store these strings centrally (one constants module / CMS entry) so wording is
  consistent and auditable.
- The roadmap generator and conversational engine must run output through the
  **do-not-say** filter ([Deliverable 5](./05-pathway-decision-tree.md), anti-
  conclusion checks) before display.
- Disclaimers must be readable (not buried in fine print): adequate contrast,
  reasonable font size, and present on mobile.

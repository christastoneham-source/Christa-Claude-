# HLB 7811 Harrisburg — Development Partner RFP Review Workspace

This folder holds everything the Houston Land Bank (HLB) Evaluation Committee
needs to review the developer submissions for the **7811 Harrisburg Blvd
Development Partner RFP** in a consistent, fair, and well-documented way.

> **Purpose:** support reviewers' judgment with plain-language analysis,
> a repeatable scoring process, and a clean documentation trail. This
> workspace does **not** replace the Evaluation Committee, HLB legal counsel,
> or the HLB Board. Nothing here is legal advice or a final underwriting
> opinion.

## How this workspace is organized

| Folder | What goes here |
|---|---|
| `reference/` | The official RFP requirements and scoring rubric, extracted for quick reference, plus finance-training notes. |
| `submissions/` | One subfolder per developer submission (`submission-A`, `-B`, `-C`). Drop **all** files for each submission into its folder. |
| `templates/` | Blank templates: reviewer report, responsiveness checklist, scorecard, and comparison analysis. |
| `reviews/` | One subfolder per reviewer (`reviewer-1`, `-2`, `-3`). Each reviewer's completed reports for each submission live here. |
| `comparison/` | The final cross-submission comparison analysis and the aggregated scorecard across all reviewers. |

## How to give the documents to Claude

Each submission has several files (proposal, pro forma, site plans, AMI tables,
audited financials, references, letters, etc.). Pick whichever is easiest:

1. **Google Drive folder (recommended for many files).** Put all files for a
   submission in a Drive folder and tell Claude the folder name. Claude can
   pull them directly (Google Drive is connected to this session).
2. **Upload in chat.** Drag and drop the files into the chat. You can attach
   several at once. Tell Claude which submission they belong to
   (A, B, or C), and Claude will sort them into the right `submissions/` folder.
3. **Add to the repo.** Commit files directly into the matching
   `submissions/submission-X/` folder.

Tell Claude the developer/team name for each submission so the reports are
labeled correctly.

## The review flow

1. **Provisional read first.** Claude produces a quick provisional reviewer
   report per submission so you can react early.
2. **Full structured report per reviewer.** Each of the (up to three) reviewers
   gets a complete 15-section report per submission, including reviewer notes
   and questions, saved under `reviews/reviewer-N/`.
3. **Aggregate across reviewers.** Scores from all reviewers are combined on the
   aggregated scorecard so HLB has a defensible committee result.
4. **Comparison analysis.** Once all submissions are reviewed one by one, Claude
   produces a side-by-side comparison in `comparison/`.

See [`WORKFLOW.md`](./WORKFLOW.md) for the step-by-step review method and
[`reference/rfp-key-requirements.md`](./reference/rfp-key-requirements.md) for
the official requirements and rubric.

## Building the reviewer platform (Lovable)

To turn this into a real app where HLB staff upload submissions and get walked
through the review with live AI feedback, use
[`lovable-build-prompt.md`](./lovable-build-prompt.md). Copy that file into
Lovable to generate the platform. Build the prototype with **sample/fake data
only**, then transfer the project to an HLB-owned workspace (reconnecting
Supabase and the Claude API key) before loading real, confidential submissions.

## A note on documentation and procurement

HLB is a public-purpose entity running a competitive solicitation. A clean,
consistent paper trail — identical criteria applied to every submission,
independent reviewer scoring, documented strengths/concerns, conflict-of-interest
disclosures, and confidentiality until award — supports a defensible process.
This workspace is built to produce that trail. **Confirm the specific
procurement and public-records requirements with HLB counsel; this workspace
does not provide legal or compliance determinations.**

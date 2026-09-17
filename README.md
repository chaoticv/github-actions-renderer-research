# GitHub Actions job-summary renderer baseline

This repository fixture creates one manually triggered Actions run whose only
purpose is to render a benign `GITHUB_STEP_SUMMARY`. It establishes a stable
control for later, one-variable-at-a-time renderer research.

The summary contains a unique text marker plus common GitHub Flavored Markdown
forms: a heading, emphasis, a blockquote, a list, a task list, a table, a fenced
code block, and a collapsed `<details>` block. It contains no script, event
handler, image, link, external URL, secret, or network command.

## Run the baseline

1. Put this README and `.github/workflows/summary-renderer-baseline.yml` on the
   default branch of a researcher-owned public repository.
2. Open the repository's **Actions** tab.
3. Select **Actions summary renderer baseline**.
4. Choose **Run workflow** on the default branch.
5. Open the completed run and inspect the job summary.

Expected marker:

```text
GHBB-ACTIONS-SUMMARY-BASELINE-20260917-A1
```

Expected behavior: the marker is visible, Markdown renders as the corresponding
static elements, and the collapsed section reveals only inert text when opened.
Record the run URL and timestamp in the hunt evidence; do not commit credentials,
cookies, tokens, or browser exports to the repository.

## Safety properties

- Manual trigger only (`workflow_dispatch`).
- No third-party actions or checked-out repository code.
- No secrets, external URLs, uploads, or network commands.
- Empty `permissions` map, so the workflow token receives no repository scopes.
- One short job with a five-minute timeout.

This fixture is a rendering baseline. It does not contain an XSS payload.

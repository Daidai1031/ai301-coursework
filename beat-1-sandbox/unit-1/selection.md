# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/26

**Verdict output**

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/26",
    "checks": [
      {
        "name": "maintainer-alive",
        "grade": "pass",
        "evidence": "Non-bot commit by Andrew Burke on 2026-09-16, 7 days before today (2026-09-23)"
      },
      {
        "name": "repo-in-use",
        "grade": "pass",
        "evidence": "archived: false; last push 2026-09-16 (7 days ago, within 180-day window)"
      },
      {
        "name": "scope-fits",
        "grade": "pass",
        "evidence": "Bug fix: safety_events_last_hour hardcoded to 0 instead of reading SafetyMonitor.get_event_count(); named files api/routes/health.py, safety/monitoring.py; effort estimate 2-4h"
      },
      {
        "name": "unclaimed",
        "grade": "pass",
        "evidence": "Assignees: none; 0 comments; repo-wide PR search returned 0 pull requests"
      },
      {
        "name": "ai-contribution-policy",
        "grade": "pass",
        "evidence": "docs/CONTRIBUTING.md and PR template contain no AI-use restriction or ban"
      },
      {
        "name": "newcomer-signal",
        "grade": "pass",
        "evidence": "Labels include 'good first issue'"
      }
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

My first attempt did not complete and therefore produced no agreement score. It stopped with the following encoding error:

> UnicodeEncodeError: 'gbk' codec can't encode character '\u2728'

After configuring the terminal to use UTF-8, I completed one full scored run. The final output reported:

> categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 2/4

> agreement: 18/20 scored items  (bar: 18/20: PASS)

> run written to eval-run.txt

This was the final completed run and is the run recorded in `eval-run.txt`.

**Issue analysis**

I analyzed `issue-15`. The final eval output reported:

> issue-15  reject  accept   NO     graded accept

My rubric returned `accept`, while the gold label was `reject`. The issue had no current assignee, no open associated pull request, and no sufficiently recent claim, so it passed my required `unclaimed` check. However, the issue had been open for a long time and had several abandoned contribution attempts. My rubric treated those attempts as inactive because none represented a current claim. The issue's age and abandoned attempts suggest hidden difficulty that my current ownership rule does not capture.

**Check rationale**

The following is the exact `unclaimed` check from the `rubric.md` used for my final eval run:

> | Check | Evidence | Pass condition | Weight |
> |---|---|---|---|
> | unclaimed | Read "this issue: assignees" and "linked PRs" under Repo facts. Read the Comments section for referenced PRs and claim statements such as "I'll take this," "can I work on this," or "working on this." | Pass if there is no assignee, no open linked or comment-referenced PR, and no explicit claim made within the last 30 days. An open PR or any assignee fails the check. A claim older than 30 days passes only when there is no open associated PR and no later comment showing continued work. | required |

I made this check required because an assignee, an open pull request, or a recent explicit claim is direct evidence that another contributor is already working on the issue. I used a 30-day threshold so an old statement of interest does not block an issue indefinitely. Assignees and open pull requests are stronger evidence of active work, so either one causes the check to fail.

**Trade-offs**

The result for `issue-15` demonstrates the trade-off:

> issue-15  reject  accept   NO     graded accept

The check prioritizes evidence of current ownership and allows old, inactive claims to expire. As a result, it can miss issues whose repeated abandoned pull requests reveal hidden difficulty even when nobody is currently working on them. Treating every abandoned attempt as an automatic failure could catch cases like `issue-15`, but it could also reject manageable issues simply because an earlier contributor stopped working.

---

## Selection rationale

**Selection rationale**

1. Issue #26 fits my interest in Trust & Safety because it concerns safety-event monitoring and the accuracy of a health endpoint. I am currently studying Trust & Safety and have experience with Python and FastAPI, so it gives me a bounded way to apply both. Its estimated effort of 2–4 hours is realistic for the time I have available for a first contribution.

2. The verdict correctly identified that the repository is active, AI-assisted contributions are not prohibited, the issue is currently unclaimed, and the requested change is bounded and testable. It also recognized the `good first issue`, `safety`, and `tier-1` labels. The rubric could not weigh my personal interest in Trust & Safety or compare my comfort with the implementation areas. I chose #26 over #58 because #58 involves broader regex behavior across nine tests, and over #40 because #40 is a tier-2 feature spanning frontend and backend files.

3. I expect the issue to be relatively straightforward to claim because it is open, has no assignee, has no comments, and has no associated open pull request. I will check those signals again immediately before claiming it in Unit 2 because another student could begin working on it after this selection.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/issue-select/`.

# COMP0104 Week 1 — Coursework and Practice Checklist

[繁體中文版](../README.md) · [Week 1 notes](../../dict/README.md)

Personal completion status refers to the repository owner, not the reader.

> Checked on 2026-10-12 (Europe/London). This page consolidates official task requirements and the author's visible status; it is not a set of completed lab answers. See the [Week 1 notes](../../dict/README.md) for the classroom concepts.

## What needs doing, and when?

| Item | What to do | Deadline / grading | Visible personal status |
|---|---|---|---|
| [Starting Experience and Expectations](https://moodle.ucl.ac.uk/mod/questionnaire/view.php?id=8512795) | Anonymously report prior tools/coursework/personal projects/work experience and interests/expectations; “none” or “not sure” are acceptable answers. | **Friday 2026-10-09 16:00 UK**; not a test. Moodle completion requires a submitted questionnaire. | Currently displays **Closed** and **To do: Student must submit this questionnaire to complete it**. No personal answers were available to read; it was not filled in on the author's behalf. |
| [Lab 1 — Preparations](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512843) | Complete Exercises 0–5: diff, patch, diff3, and AI or supplied-response evaluation. | The [Labs page](https://moodle.ucl.ac.uk/course/section.php?id=1379312) explicitly says **not assessed**. The PDF recommends attempting it before online lab support and continuing afterwards; no fixed date/time or upload deadline is stated. | The Week 1 manual-completion button is still not marked done; this does not prove that the author has never attempted the work. No readable lab implementation/reflection is present in the repository. |
| [Lab 2A — Subversion](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512848) | Complete Setup and Exercises 1–9: GNU Hello/SVN changes, patch, history, rename and build repair. | **Not assessed**; attempt the whole worksheet first, then ask questions in the support session. No submission deadline/upload entry was found. | As above; commands were not executed and exercise results were not committed on the author's behalf. |
| [Required Reading](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512850) | Read the **Preface, Chapter 1 and Chapter 2** of *Version Control with Subversion*. | Explicitly labelled **Required Reading** in Week 1, with no specific date/time; it must not be relabelled optional just because it is ungraded. | Moodle manual completion is not yet marked done. These notes analyse the reading, but that does not mean the user personally finished it. |

The questionnaire deadline has passed and the activity is closed. If the author did not submit it, they need to ask the module team whether a late completion is possible. No message was sent, no answers were submitted, and completion status was not changed on their behalf.

## Lab 1 — Preparations

**Primary source:** [official Lab Sheet](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512843), 6 pages. The entire worksheet should be attempted, using a personal computer or the [departmental Linux environment](https://moodle.ucl.ac.uk/course/section.php?id=1379312).

### Part I: Command-Line Tools

| Exercise | Required work | Evidence to retain / check |
|---|---|---|
| **0 — Questionnaire** | Complete the Moodle starting questionnaire if not already submitted; it is now closed, as noted above. | Actual submission status; opening the page does not count as submitting it. |
| **1 — DIFF** | Create the `lab01` working directory and the worksheet's two text files, `be` and `ae`. Compare `diff be ae` with the reverse direction, then compare normal, `-c`, `-u` and `-y` formats; read `man diff`. | Output in both directions and differences between formats; inspect the exit status with `echo $?` immediately after diff. |
| **2 — PATCH** | Save the `be → ae` diff in `DIFFS`; apply it with `patch --verbose --backup be < DIFFS`; use diff to check the result. | `DIFFS`, the modified file and the backup; verify the comparison result, rather than merely checking that patch reported no error. |
| **3 — DIFF3** | Restore `be`, copy it to `be2`, and change `approximately` to `around`. Test automatic merging with `diff3 -m be2 be ae`, save the output as `merged`, and inspect it. Then copy the original `be` to `be3`, change `the most` to `some of the most`, and observe the conflict markers when merging it with `ae`. | The conflict-free merged text should retain both sides' changes. Keep the conflicted output, exit status and argument order, and confirm that `-m` did not automatically rewrite the input files. |

**Exit-status traps (official PDF):**

- `diff`: 0 = identical, 1 = differences found, 2 = error. A status of 1 is not itself an execution failure.
- `diff3 -m`: 0 = no conflicts, 1 = conflicts found, 2 = error. Output with status 1 may contain conflict markers and still requires resolution.
- Changes on different lines may still conflict if adjacent; inspect the tool's actual output.

### Part II: Using AI Tools

Use an AI tool of your choice, or evaluate the **Supplied Responses for Evaluation** on page 6 of the PDF. Choosing not to use AI does not remove the command-line, manual-resolution or reflection tasks. Supplied responses are material to evaluate, **not model answers**.

| Exercise | Required work | Evidence / reflection |
|---|---|---|
| **4 — AI for Understanding and Summarising Changes** | Generate `diff -u be ae`; ask AI for a line-by-line explanation and a short imperative commit message, or evaluate the supplied explanation/message. | Retain the unified diff, evaluated explanation, commit message and required corrections. Write a short paragraph assessing accuracy, clarity, and whether the message is concise/conventional. |
| **5 — AI for Resolving Merge Conflicts** | Reproduce the conflict with `diff3 -m be3 be ae`; **resolve it yourself first** and save `merged-manual` before looking at AI or the supplied response. | Keep `merged-manual`, the evaluated proposed merge and corrections. Following the worksheet, check that `ae`'s American spellings, `be3`'s `some of the most`, and `ae`'s currency note are retained, with no conflict markers. Compare the intent and differences of both resolutions, and explain whether you would trust the output without manual verification. |

Record the tool used, or state that supplied responses were used. Each reflection must use actual output as evidence; keep the files and notes for discussion in online lab support. No readable personal answers were found in this repository, so no “I observed…” statements or completed reflections have been filled in.

## Lab 2A — Subversion

**Primary source:** [official Lab Sheet](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512848), 6 pages. It requires `svn`, `svnadmin`, `wget`, `tar`, `patch`, `make` and a C compiler; the worksheet uses **GNU Hello 2.12.1**. This lab builds on Lab 1's command-line/patch skills.

### Setup

1. Create the **repository** `svnrepos/helloworld` in the practice environment and a separate **workspace** `lab02a`; do not confuse them as a single directory.
2. Check out the empty repository, then create/add/commit `trunk`.
3. Following the worksheet, obtain Hello 2.12.1 from the GNU archive, retain the tarball, and unpack it into the trunk.
4. Use `svn status` to inspect untracked entries, then `svn add` and commit the initial source; confirm a clean status.

If the lab has already been attempted, use new repository/workspace names and adjust the worksheet paths consistently. The example revisions 1, 2, 3, etc. apply only to a fresh repository; do not blindly use fixed revision numbers.

### Exercises 1–9

| Exercise | Required work | What to verify / keep |
|---|---|---|
| **1 — Compile and Modify** | Run `./configure`, `make`, and `LC_ALL=C ./hello`. Change the greeting to German as instructed, then build/run again. | The source change and actual compile/run output; `LC_ALL=C` fixes the language environment for this command. |
| **2 — See Changes** | Run `svn status`; use `svn diff src/hello.c` to compare the working file with its checked-out base. | The `M` status and modifications shown in the diff; build outputs may appear as `?`. **Do not add** generated outputs for this lab. |
| **3 — Commit Changes** | Commit only the specified source change with a meaningful message, then inspect the diff again. | The commit revision/log; plain `svn diff` should no longer show the local changes that were committed. |
| **4 — Create a Patch** | Use `svn log` to find the actual original/German revisions. Generate a patch with `svn diff -r OLD:NEW src/hello.c` and place it outside the working copy. Unpack a clean tarball separately, test with `patch -p0` from the source-tree root, then build/run. | The patch, test copy and output. Observe the prompts when applying the same patch again; follow the worksheet by neither reversing nor forcing it, and explain why it cannot simply be applied twice. |
| **5 — More Modifications** | Change the greeting to French; build/run, diff, commit and inspect the log. | The French revision and diff/log evidence. |
| **6 — Navigate History** | Identify the English/German/French revisions from the log. Retrieve each with `svn update -r` on the source file, rebuilding when needed; finally update to the latest revision. | An older working revision is not a new local edit and does not undo repository commits; confirm that the final source contains the latest French version. |
| **7 — Rename Files** | Rename using `svn move src/hello.c src/hallo.c`, inspect status, then commit. | The old path is scheduled for deletion and the new path for addition with history (`A +`); rename does not automatically update build-system references. |
| **8 — Investigate History** | Inspect the renamed file's `svn log` and find commits from when it had the old name. Use a revision-range diff to examine the English-to-German change. | Explain the difference between comparing two repository revisions and comparing a working file with its base; keep the log/diff and use your own revision numbers. |
| **9 — AI Task: Diagnose and Repair the Build** | Run `make` and record the error after renaming. Inspect the generated root `Makefile`, `hello_SOURCES` in the root `Makefile.am`, and `Makefile.in`. Use AI to explain the failure, or analyse the evidence yourself. Following the worksheet, restore the filename expected by the original build system, using `svn move` to preserve history; retain the French greeting and existing build files. | Review status/diff, confirm a successful build/run, then commit the repair. `svn log` should retain the history of the translations and both renames. |

### Exercise 9 reflection and final checkpoint

Base the reflection on personal observations: what evidence identified the cause of failure? Did the AI explanation match the actual files? Why might editing only the generated Makefile be a temporary repair? Why would a plain SVN commit not save an untracked Makefile? What does each of compilation, running and history inspection verify?

Final checkpoint: the working copy builds successfully and the repaired source has no uncommitted changes; untracked build outputs may remain. Keep the repository, working copy, archive and patch for reference. These are the worksheet's target outcomes, not results already achieved by the author.

## Required Reading and extra material

- **Required:** [Version Control with Subversion](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512850), Preface + Chapters 1–2. Connect the reading to repository vs working copy, atomic/global revisions, copy-modify-merge, the four file states, status/diff/commit/update, and history/rename.
- **Extra, not required for the module:** [Miller and Myers — A file comparison program](https://moodle.ucl.ac.uk/mod/lti/view.php?id=9428318), [SVN for Java Developers](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512852).

## Submission, marks and questions

- Both labs this week are **ungraded**, and no specified upload/submission deadline was found. The PDFs recommend attempting them before the support session and continuing afterwards; this must not be converted into an invented fixed weekday or time.
- **Mark as done** on [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379313) is manual completion. Opening a resource or reading these notes does not establish that the author has completed the lab.
- The starting questionnaire is a separate activity with a definite deadline and submission-based completion; it is not assessed coursework.
- [Announcements](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8512798) contained no announcements when checked, and no additional deadline for this week was found.
- Worksheet questions can be posted in [Questions on the Labs](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8512836). No post or other submission was made as part of preparing these notes.
- Every unchecked/unrecorded status on this page means **insufficient readable evidence**, not a claim that the user never attempted the work. Completion records and personal reflections should only be added when the user's command outputs/answers are available to read.

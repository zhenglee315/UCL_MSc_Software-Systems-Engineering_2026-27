# COMP0235 — Week 1 Tasks and Reading Record

[繁體中文版](../README.md)

Personal answers and completion status in this document refer to the repository owner, not to every reader.

**Topic:** Course Welcome and Remedial Software Engineering Practice

**Checked:** 2026-10-12, Europe/London

**Study notes:** [Weekly README](../../dict/README.md)

This page records Moodle's published requirements, how to complete them and the visible completion status. **No Unix forum answers were written, discussions/replies posted, Git levels completed, VMs created or assignments submitted on the student's behalf.** Where there is no personal answer, only the task and checklist are recorded; teaching examples are not treated as evidence of the student's own practical work.

## Task overview — what to do first

| Suggested order | Task | Official requirement/output | Deadline/status |
| --- | --- | --- | --- |
| 1 | **Environment and SSH** | Be able to use a Unix terminal, check your own Condenser namespace/image, create or use a practice VM and log into remote Linux through SSH. | The 6 October announcement asks for an immediate namespace check; no submission deadline was published. The student's environment was not operated or verified on their behalf during the review. |
| 2 | **Unix Commands forum** | Add a discussion topic introducing a command, then ask a question on another student's topic. | This week's activity; no exact date or time was found. No personal topic/reply was found during the check on 2026-10-12. |
| 3 | **Required reading** | Familiarise yourself with PEP 8; read Chapter 2 of Research Software Engineering with Python. | No submission requirement or exact deadline was published. A Moodle tick is not taken as evidence that the student has finished reading. |
| 4 | **Learn Git Branching** | Complete the four specified Main groups. | This week's exercise; no exact deadline was found. Progress on the external website was not checked. |
| 5 | **Remedial materials / in-class practice** | YAML, Python code, unit testing and the Git/GitHub pair exercise; work through Moodle's numbered materials. | No separate Week 1 assignment upload portal or additional deadline was found. Do not automatically treat a classroom activity as a completed submission. |

This is a suggested work order, **not a new deadline published by the lecturer**. Moodle says the numbering indicates the ideal learning order. Use [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270) as the authoritative entry point for requirements.

## 1. Environment and SSH — environment check

Sources: [Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269), [Rancher/SSH MD](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523816), [6 October Condenser fixes](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710), and the class of 7 October at 18:37.

- [ ] Locate a Unix terminal. On a Mac, Terminal is in Applications → Utilities; on Windows, use WSL as the course recommends.
- [ ] Have a suitable code editor and understand basic shell navigation.
- [ ] Be able to open [Rancher](https://rancher.condenser.arc.ucl.ac.uk/) and the [SSH entry point](https://ssh.condenser.arc.ucl.ac.uk/) on campus or through the UCL VPN.
- [ ] Find and activate your own **`<UCL-ID>-comp0235-ns`** in **`sl-t01`**.
- [ ] See AlmaLinux images when creating a VM. Select your own network rather than copying the lecturer's namespace.
- [ ] Understand the difference between a public key, a private key and a signed certificate, and complete the required configuration using the handout.
- [ ] Successfully log into your VM and understand the prompt's user/host/working directory.
- [ ] If you followed the Apache demonstration, also check `ServerName localhost:80` and the hostname address in the [HTTP Hostnames correction](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852).

**Source conflict:** `sl-p01` and `ds4eng-ns/ds4eng` in the older MD are example values. The 6 October update and that week's class confirm that students use `sl-t01` and their individual namespaces. The lecturer asks anyone unable to find a namespace to contact him immediately. The [demonstration video entry](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808) can help with checking/activating it; the video was not played during the review.

You may retain your own non-sensitive evidence: the date of the operation, the image used, a brief description of a successful login and any problems encountered. **Do not put private keys, certificates, tokens, passwords or a complete personal connection configuration in the repository.**

### Personal operation record

The student's practical results were not verified during the review. Complete the following after carrying out the work yourself:

| Item | Personal record |
| --- | --- |
| Date/environment | To be filled in |
| VM/image choice | Add a non-sensitive description |
| Was SSH successful? | To be filled in |
| Problems and solutions | To be filled in |

## 2. Unix Commands — two required actions

[Official forum entry](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523826)

### A. Add a discussion topic

The original task asks you to select a command from Unix or a related operating system, research it using man pages, the internet and appropriate documentation, and add a Discussion Topic explaining it to the class.

Your post needs to include:

1. **What does the command do?** Explain its purpose.
2. **Why / when would you need it?** Describe a practical use case.
3. **A short example.** Give a brief usage example whose arguments and result you can explain.

### B. Ask a question on another student's topic

Go to **another student's** topic and ask a question about the command they described. Adding only your own introduction does not complete the entire task.

### Verification and personal answer

On 2026-10-12, the forum contained **six discussion topics**, none started by Wilson Lee. All visible reply authors in the three threads with replies—systemctl, grep and find—were also checked; none was the student. The other three threads had no replies at that time.

Therefore, **no personal answer was found to include**. Other students' introductions are not copied, and no personal post is written on the student's behalf. Only the following tasks are recorded:

- [ ] Choose a command and first read the man page/official documentation for the version on your actual system.
- [ ] Test the example using your own practice files, and be able to explain the input and expected output.
- [ ] Write your own command topic and save its permalink.
- [ ] Read another student's topic, ask your own question and save its permalink.

| Personal record | Content |
| --- | --- |
| Selected command | For the student to choose |
| Personal topic permalink | Not found yet |
| Personal question permalink | Not found yet |
| Personal answer/reflection | No verifiable content yet |

**Deadline:** The readable forum requirements and Week 1 page did not list an exact deadline date/time. Command names in Moodle emails about classmates' posts are notifications from the same forum exercise, not a new assignment for every email.

## 3. Required reading — what to read and where

### PEP 8 — Style Guide for Python Code

[Moodle PEP008 entry](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523822) / [Official Python text](https://peps.python.org/pep-0008/)

Moodle states **REQUIRED READING: Familiarise yourself with the pep008 standard**. The aim is to recognise common style conventions and apply them in code. No separate requirement to upload a reading reflection was found.

- [ ] Read code layout/indentation/line length.
- [ ] Read imports, whitespace and comments/docstrings.
- [ ] Read naming conventions and programming recommendations.
- [ ] Be able to distinguish style, readability and checks for correctness.

### Research Software Engineering with Python — Chapter 2

[Moodle reading page](https://moodle.ucl.ac.uk/mod/book/view.php?id=8523823) / [UCL Primo](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159) / [Authors' Chapter 2](https://third-bit.com/py-rse/bash-basics.html)

The authors are Damien Irving, Kate Hertweck, Luke Johnston, Joel Ostblom, Charlotte Wickham and Greg Wilson. The official title is **Research Software Engineering with Python**. The Moodle activity title uses “in Python”; the corresponding instruction is **Read Chapter 2**.

Chapter 2 is titled **The Basics of the Unix Shell**. Read it in this order:

1. **2.1–2.2 Exploring / moving around:** filesystem, current directory and absolute/relative paths.
2. **2.3–2.6 File operations:** creating, moving, copying and deleting.
3. **2.7–2.8 Wildcards / manual:** selecting files with patterns and consulting command documentation.
4. **2.9–2.11 Summary / exercises / key points:** checking whether you can predict a command's effects.

- [ ] Finish reading Chapter 2.
- [ ] Be able to explain `pwd`, `cd`, `.`, `..` and `~`.
- [ ] Be able to explain the difference between `cp` and `mv`, and understand which files a wildcard selects.
- [ ] Practise operations you do not understand; do not experiment with deletion commands on important data.

The Moodle book page displayed **No content has been added to this book yet**, but provided a Primo link in its description. The authors' version is available for reading. Moodle did not explicitly require submitting all the chapter exercise answers; the chapter-end exercises are not answered on the student's behalf here.

### Optional reference

[Unix in a Nutshell](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523819) is labelled **Extra reading** on Moodle. Use it as a reference when needed.

## 4. Learn Git Branching — four specified groups

[Moodle task entry](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523825)

Complete these groups in **Main**:

- [ ] **Introduction Sequence**
- [ ] **Ramping Up**
- [ ] **Moving Work Around**
- [ ] **A mixed bag**

Moodle says you may optionally complete all exercises; it does not make every level compulsory. The student's external website progress was not checked, so the items are not marked complete. Keep your own record of concepts you find confusing and completion dates. Do not treat AI-provided solutions as evidence that you have completed the work yourself.

**Deadline/submission:** Week 1 calls this the “exercise for this week”, but no exact deadline or requirement to upload a screenshot was found. Do not invent a compulsory screenshot submission requirement.

## 5. In-class / remedial practice — distinguish classroom activities from formal submission

Sources: [Remedial Software Engineering ODP](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523817) and [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270).

| Topic | Confirmed teaching-material requirement/activity | Personal answer |
| --- | --- | --- |
| **YAML intro** | Moodle provides a short MD about the basic structure of configuration data. The original file was not obtained during the review. | No record yet |
| **Good Python code** | PEP 8, Pythonic code and the classroom discussion of good code. | No invented discussion conclusions |
| **Unit testing** | The ODP asks for a unit test before implementing a function; no specific function task is available in the readable material. | No answer supplied for an unknown task |
| **GitHub pair exercise** | Person 1 creates a repository/adds working code to main; Person 2 changes code/opens a PR; Person 1 checks and approves. | No evidence of the student's pair exercise yet |
| **Refactoring** | Listed in the ODP as a subsequent software engineering topic. | No separate task/submission requirement yet |

Do not reconstruct unrecognisable commands in the later transcript as “commands the lecturer requires everyone to run”. No separate Week 1 submission portal or exact deadline was found for these items either.

## Completion record — update after completing the work

| Date | Completed item | Personal evidence or source link | Remaining questions |
| --- | --- | --- | --- |
| To be filled in | For the student to complete | To be filled in | To be filled in |

Moodle's **Mark as done/completion** indicates platform tracking conditions or a ticked status. It cannot, by itself, prove completion of offline reading, external Git levels or VM operations. Mark as done was not clicked manually while preparing these notes.

## Help and sources

- [Module Communication](https://moodle.ucl.ac.uk/course/section.php?id=1381264): Use the [Ask a Question forum](https://moodle.ucl.ac.uk/mod/hsuforum/view.php?id=8523791) for general module questions; contact the lecturer directly for personal/accessibility matters. If you cannot find your namespace, contact Daniel Buchan as instructed in the 6 October announcement.
- [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270) / [Announcements](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523790)
- [Unix Commands exercise](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523826) / [Git Branching exercise](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523825)
- [Asksia original class transcript](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43)
- [PEP 8](https://peps.python.org/pep-0008/) / [Irving et al. Chapter 2](https://third-bit.com/py-rse/bash-basics.html)

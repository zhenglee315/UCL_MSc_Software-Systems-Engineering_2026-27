# COMP0235 — Week 1 Study Notes

[繁體中文版](../README.md)

Personal answers and completion status in this document refer to the repository owner, not to every reader.

**Module:** Engineering for Data Analysis 1 (the folder retains the name Data Engineering)

**Moodle topic:** Course Welcome and Remedial Software Engineering Practice

**Class recording:** `Recording_20261007_1002` (2026-10-07)

**Compiled and checked:** 2026-10-12, Europe/London

This week establishes the shared foundations needed for later data analysis systems: logging into your own remote Linux VM, understanding files and commands, combining operations into repeatable workflows, and managing code through Python coding practice, testing and Git. At **18:37** in the recording, the lecturer emphasises that the most important outcome of Week 1 is successfully logging into a remote machine.

These are personal study notes that retain English technical terms; this edition provides the explanations in English. Assignment requirements and outstanding tasks are recorded separately in [coursework/README.md](../coursework/dict/README.md).

## Source coverage and reliability

| Source | Scope read and purpose |
| --- | --- |
| [Asksia original recording/transcript](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43) | With `Origin` selected in the source panel, all available English text was read section by section from **0:01–103:36**. The recording is labelled 106:22 long, but the last text in the panel ends at 103:36. The material at 60:20–75:46 is mainly conversation during the break and is excluded from the course notes. |
| Asksia summaries | After analysing the original transcript, two summaries about virtualisation management and Linux were checked for omissions. Details added by a summary must not be treated as the lecturer's own words. |
| [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270) | All resource names, reading requirements, the scope of the Git exercise and the Unix forum requirements were checked. |
| Original teaching materials | The complete `1.2 Rancher and ssh configuration` MD and `1.3 Remedial Software Engineering` ODP were read, as was the existing local `1.1 Welcome Slides` ODP. This document preserves personal notes rather than the original files or a full transcript. |
| [Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269), [Communication](https://moodle.ucl.ac.uk/course/section.php?id=1381264) | Environment requirements, the course GitHub and Etherpad links, and the channels for asking questions were read. |
| Lecturer announcements | The 5 October Welcome, 6 October Condenser fixes, 6 October namespace demonstration explanation and 7 October HTTP Hostnames announcements were read. More recent, specific settings take precedence over example values in the older MD. |
| Required reading | The [official PEP 8 guidance](https://peps.python.org/pep-0008/) was checked, and the authors' version of [Research Software Engineering with Python, Chapter 2](https://third-bit.com/py-rse/bash-basics.html) was read. |
| Teaching materials not obtained | The original files for `1.3.1 Intro to the Unix Commandline`, `1.3.2 Incredibly quick YAML intro`, `1.3.3 Intro to good python code` and `1.3.4 Intro to git and github` could not be obtained normally. The Unix MD download timed out; opening it caused Chrome to display “blocked by client”. Notes on these items rely only on the class material, ODP and Moodle descriptions that were read, together with explicitly labelled supplementary explanations. They do not claim that these original files were read. |

**Transcript limitations:** The transcript labels different contributions as Speaker 1 throughout. Many sentences in its later sections are fragmentary, so exact operational commands cannot be reconstructed reliably. Transcriptions such as `Armor 9 Linux` and `Cadenza` have been corrected to **AlmaLinux 9** and **Condenser** using Moodle materials and announcements. Do not turn incomplete text into complete commands supposedly given by the lecturer.

## Whole-week summary

1. **ML-Ops / systems administration:** The course ultimately aims to build systems that distribute data analysis, manage data, and monitor and secure services. Week 1 first ensures that everyone can operate the remote environment.
2. **Provisioning a VM:** Select the correct cluster and your own namespace, attach your SSH public key, choose an operating system image, disk and network, and wait for the VM to start and its IP address to be reported.
3. **SSH through a jump host:** The gateway and target VM have different roles. A connection that closes immediately after successful gateway authentication is not necessarily a failure. Logging into the VM itself requires the target user, IP address, identity and jump host.
4. **Linux command line:** Know which machine and directory you are using, and whose permissions your commands have. Be able to create, inspect, copy and move files, and read documentation and configuration.
5. **Streams and composition:** Distinguish stdin, stdout and stderr. Redirection writes output to a file; a pipe passes one program's output to another program.
6. **From manual work to automation:** The lecturer may first explore settings manually on one VM, then turn the confirmed operations into configuration files or an automation process. Repeatedly clicking through web interfaces and logging in to edit files does not scale easily to multiple consistently configured machines.
7. **Good software practice:** Moodle also requires foundations in YAML, Python style, unit testing and Git/GitHub this week. These topics work together to make configuration and analysis code readable, traceable and suitable for collaboration.

## Key Concepts

| English term | Explanation | Distinction to understand this week |
| --- | --- | --- |
| **Virtual Machine (VM)** | A virtual computer with its own operating system and CPU, memory and disk configuration. | Your local Terminal is the entry point; after an SSH login, commands run on the remote VM. |
| **Cluster** | A unit through which the platform manages a group of computing resources. | Students use the teaching cluster; the cluster shown in the lecturer's demonstration may have a different name. |
| **Namespace** | A named scope that separates resources and operations on the platform. | Select your own namespace before creating a VM. Adding your ID to the machine name is not a substitute. |
| **Image / Volume** | An image provides the operating system starting point; a volume provides storage used by the VM. | Image version and disk capacity are separate choices. Capacity must cover the OS, data and working space. |
| **Public / private key** | The public key enables remote identification; the private key proves your identity from your local machine. | Upload the PUBLIC key to Rancher. Do not upload the private key instead. |
| **SSH certificate / IdentityFile** | The course gateway configuration uses a signed certificate and a local identity key. | The material returned after signing a public key differs from the original key pair, and their paths are specified separately. |
| **Jump host / ProxyJump** | A gateway forwards the SSH connection to the target VM. | The gateway is not the VM you want to operate. `-J` specifies the jump host; the final `user@host` specifies the target. |
| **Host fingerprint / known_hosts** | The client remembers the server's host identity. | A rebuilt VM may reuse an IP address with a different identity from the stored record. Not every warning should be ignored. |
| **Terminal / shell / command** | The terminal displays and accepts text; the shell interprets commands; a command is the operation invoked. | Commands such as `cd` can be shell builtins. Not every command necessarily corresponds to a separate file in `/usr/bin`. |
| **Working directory / path** | The working directory is the current location; a path specifies where a file is located. | An absolute path starts at `/`; a relative path is interpreted from the current location. |
| **stdin / stdout / stderr** | A program's standard input, normal output and diagnostic/error output. | stdout and stderr remain separate streams even when both are displayed in the Terminal. |
| **Redirection / pipe** | Change a stream's destination or connect two programs. | `>` writes output to a file, `2>` writes error output, and `\|` passes the left program's stdout to the right program's stdin. |
| **Package / service / firewall** | A package provides installable software; a service is running software; a firewall controls traffic. | Installing Apache does not mean it is running or that it is reachable from a browser. |
| **Manifest / YAML / automation** | A configuration file describes resources or settings to create. | YAML is a data format; a Kubernetes manifest is a configuration with a specific structure. Having a YAML file does not mean the VM has been created. |
| **Git / GitHub / pull request** | Git records version history; GitHub provides a collaboration platform; a PR requests review of a set of changes. | Saving a file, committing, pushing, opening a PR and merging are separate stages. |

## VM setup — interpreting the older handout using updated announcements

### 1. Environment preparation

According to [Moodle Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269), you must have a Unix terminal. On a Mac, use Applications → Utilities → Terminal; Windows users are advised to use WSL. Prepare a code editor, review the shell and SSH keys, and check that you can access Condenser/Rancher on the UCL campus or through the UCL VPN.

The course code is available at [UCL-ARC/engineering-for-datascience](https://github.com/UCL-ARC/engineering-for-datascience), and collaborative notes are at [COMP0235 Etherpad](https://etherpad.wikimedia.org/p/COMP0235). Moodle says that the lecturer will indicate when to obtain code and when there are important updates.

### 2. Correct cluster and namespace

**The [Condenser fixes announcement of 6 October](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710) provides the updated settings verified in the review:**

- Students should be able to log into Condenser.
- The teaching cluster is **`sl-t01`**.
- Individual namespaces have the form **`<UCL-ID>-comp0235-ns`**. Use the actual namespace assigned to you by the platform.
- Two AlmaLinux image options should be visible under Volumes when creating a VM.
- The lecturer asks anyone unable to find their namespace to contact him immediately.

The older Rancher MD contains `sl-p01` and `ds4eng-ns/ds4eng`. These are example values that should not be copied directly. The lecturer also says in the recording that his namespace differs from those of the students. If you choose the wrong cluster or fail to activate your namespace, you may be unable to find resources even when the later steps appear correct.

If you are unsure how to select it, the [namespace demonstration announcement of 6 October](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808) includes a short video. The announcement and video link were checked, but the video itself was not played during the review.

### 3. SSH keys and gateway

The original Rancher MD gives this workflow: create a key pair → upload the public key to Rancher → sign the public key through the course's Vault/SSH entry point → save the certificate locally → specify the gateway, user, certificate and identity in `~/.ssh/config`.

Key generation, signing and uploading were not performed on the student's behalf while preparing these notes. Private keys, certificates, tokens and account credentials do not belong in the notes repository. The original handout mentions omitting a passphrase for the demonstration; this is a demonstration choice, not a requirement for everyone.

The MD says that `ssh condenser` may authenticate and immediately close the connection without an error. This tests the gateway credentials; it has not yet logged you into your VM. The recording at 11:45–15:34 explains the same distinction.

### 4. VM creation and SSH login

At 3:58–6:34, the demonstration uses **4 CPUs**, selects **AlmaLinux 9** to avoid small differences from the existing examples, and describes **20 GB** as a sensible size for a practice machine. A disk of 20–40 GB leaves room for files. These are demonstration values or recommendations, not fixed quotas for every assignment. The original MD separately demonstrates 4 GiB of memory and a 40 GiB disk. Follow any later requirements from the platform or lecturer if they change.

Select the network associated with your namespace, attach the public key you uploaded, and wait for the VM status and IP address to be reported. At 10:42–11:28, the lecturer notes that monitoring information may be delayed or briefly disappear. Do not immediately assume that creation failed merely because an IP address has not appeared yet.

The following **syntax template** is based on the teaching material. It is not an actual address you can paste unchanged:

```sh
ssh -i ~/.ssh/<identity-key> -J <gateway-alias> almalinux@<your-vm-ip>
```

Read it as: “Use this identity, through this jump host, to log into this VM as the `almalinux` user.” The gateway alias is the `Host` name you define in your SSH config.

### 5. HTTP access has several layers

```text
Browser → Condenser ingress / hostname → VM network / firewall → Apache httpd
SSH client → SSH gateway / jump host → VM SSH server → remote shell
```

**Supplementary analysis:** This is a conceptual diagram for understanding where a failure occurs; it is not a diagram from the original transcript. A successful SSH connection establishes that the SSH path works, not that the HTTP path works.

The [HTTP Hostnames announcement of 7 October](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852) adds two specific requirements:

```apache
# /etc/httpd/conf/httpd.conf
ServerName localhost:80
```

The browser address is `https://<hostname>.comp0235.condenser.arc.ucl.ac.uk/`, where `<hostname>` is the name you set in the VM's instance labels. At 8:29–9:00, the lecturer says hostnames must be unique and recommends adding your ID as a prefix or suffix. Do not use his name or a shared `test` hostname directly.

Apache, package dependencies, services and the firewall can be identified in the later recording, but many exact commands have missing words. The incomplete transcript is therefore not reconstructed as an executable installation script. Open the original materials and updated announcements to confirm the steps when carrying them out.

## Linux filesystem — know what you are operating on

The lecturer uses **Everything is a file** to explain a basic Unix idea: devices and many system interfaces, as well as ordinary data, are exposed through file interfaces (24:58–27:14). This helps explain `/dev`, `/proc` and `/sys`; it does not mean they are ordinary text files that can be edited freely.

| Path | Focus for this week |
| --- | --- |
| `/` | The root directory of the entire filesystem tree. |
| `/bin`, `/usr/bin` | Locations for common executables. In the lecturer's AlmaLinux demonstration, `/bin` can point to `/usr/bin`. |
| `/boot` | The kernel and data needed to boot. The lecturer warns against changing these casually. |
| `/dev` | Device files. You may need them to identify a device, but should not modify them casually during ordinary work. |
| `/etc` | System and package configuration files, which will be used repeatedly later in the course. |
| `/home` | Home directories for ordinary users. `~` refers to the current user's home directory. |
| `/root` | The root administrator's home directory, which differs from `/`. An ordinary user may not have permission to enter it. |
| `/lib`, `/lib64` | Shared libraries. The lecturer compares them to Windows DLLs. |
| `/run`, `/tmp` | Runtime/temporary data. Do not keep work that needs to persist only in these locations. |
| `/var` | Data that changes but usually needs to be retained, such as logs. |
| `/proc`, `/sys` | Kernel/process interfaces. Some statements in the transcript are incomplete, so these notes only identify their general roles. |

**Supplementary correction:** The actual cleanup policy for `/tmp` depends on the system configuration. Do not treat “every Linux machine always deletes everything in `/tmp` on every reboot” as a universal rule. The lecturer's main point is to distinguish temporary data from data that needs persistence.

## Command line — relationships and short examples

### Navigation and file operations

| Command | Purpose/distinction to remember |
| --- | --- |
| `pwd` | Show the current working directory. Use it first if you are lost. |
| `ls -l -a -h` | Long listing, hidden files and human-readable sizes. |
| `cd /` / `cd ~` | Go to the filesystem root/your home directory, respectively. |
| `cd ..` / `cd -` | Go to the parent directory/the previous working directory, respectively. |
| `mkdir` / `touch` | Create a directory/create a new file or update an existing file's timestamps. |
| `cat`, `more`, `less` | Inspect file contents. `more` and `less` are useful for paging. |
| `cp` / `mv` | Copying creates another copy; moving changes location and can also rename a file. |
| `file` | Identify a file's content type. Changing its extension does not convert its format. |
| `rm` | Delete files. Check the path and target before running it; do not assume there is a graphical recycle bin. |
| `man <command>` / `<command> --help` | Look up syntax, options and arguments. Check each command's documentation for its short and long option names. |

The following is a **supplementary teaching example**, not an assignment answer or a record of commands already run on your VM:

```sh
# Run these in your own practice directory.
pwd
mkdir week1-practice
cd week1-practice
touch notes.txt
cp notes.txt notes-copy.txt
mv notes-copy.txt draft.txt
ls -l -a -h
```

At each step, ask two questions: what is the current `pwd`, and where will this relative path resolve? Tab completion helps reduce spelling mistakes in paths (44:07–44:35).

### Streams, redirection and pipes

| Syntax | Meaning |
| --- | --- |
| `command > output.txt` | Write stdout to a file, normally overwriting its existing contents. |
| `command >> output.txt` | Append stdout to a file. |
| `command 2> errors.txt` | Write stderr to a separate file. |
| `left \| right` | Connect the left program's stdout to the right program's stdin. |

```sh
# Supplementary example: text output and filtering.
echo "hello" > notes.txt
cat notes.txt
cat notes.txt | grep "hello"
```

**Supplementary correction:** In `echo "hello"`, `hello` is a command argument. Do not infer from the transcript's wording that `echo` generally reads stdin. A typical interpretation of the pipe is that `cat` produces text and `grep` receives and filters it. At 79:03, the explanation of a pipe as “stdout → the next program's stdin” is clearly recognisable.

**Supplementary correction:** `ls -l` normally lists modification time. Do not treat the “creation date” description at 52:04 in the transcript as an accurate definition of the usual field. `touch` updates timestamps rather than emptying an existing file.

### Editor, privilege and services

The lecturer recommends becoming familiar with `vi` because it is usually easy to find on remote Linux machines (48:36–49:30). First learn how to insert text, return to command mode, save and exit. The Asksia summary mentions `i`, `Esc`, `:wq` and `:q!`, but the detailed transcript during the break is incomplete; check the editor's help for the actual keystrokes.

Ordinary users and root have different permissions. `sudo` runs a command with higher privileges when authorised; being able to log in through SSH does not mean you can change every system setting. The Apache example involves package dependencies, the service lifecycle, startup at boot and the firewall. Verify these separately instead of checking only whether installation succeeded once.

## Other Moodle topics this week: YAML, Python, testing and Git

This section is supported by the Moodle Week 1 activity list and the Remedial Software Engineering ODP. **It does not claim that the recording of 7 October covers every topic in detail.**

### YAML and configuration

Moodle includes `1.3.2 Incredibly quick YAML intro`. Its original file was not obtained during the review. **Supplementary study direction:** Recognise mappings, sequences, nested indentation and scalar values. Understand the structure expressed by a configuration before discussing how a tool uses it. Once settings are recorded in files, they can be reviewed in Git, compared between versions and deployed repeatedly.

### Good Python code and PEP 8

The ODP lists PEP 8, Pythonic code and “What is good code in your opinion?” as class discussion topics. No verbatim answers are available, so personal preferences are not presented as the lecturer's conclusions.

Focus when reading [PEP 8](https://peps.python.org/pep-0008/): four spaces, readable line breaks and whitespace, grouped imports, `snake_case` functions/variables, `CapWords` classes, uppercase constant names, docstrings, and avoiding overly broad exception handling that conceals problems. The standard line length is 79 characters, or 72 for long comments/docstrings. Existing consistency and compatibility within a project also matter; do not break behaviour merely to impose formatting.

**Supplementary analysis:** Style helps people read code, but does not prove that a calculation is correct. Clear explanations of a function's inputs, outputs and boundary cases must be supported by testing.

### Unit testing and refactoring

The Remedial ODP explicitly schedules writing a unit test for a function before implementing the function. The readable material does not specify a particular function task, so no implementation or test answers are supplied here on the student's behalf.

**Supplementary analysis:** A unit test turns expected behaviour into an example that can be checked. Refactoring should improve structure while preserving expected behaviour. This explains why testing, readability and version control should be considered together.

### Git, GitHub and collaboration

The ODP's pair exercise is: Person 1 creates a repository and adds working code to main; Person 2 changes the code and opens a pull request; Person 1 checks and approves it. This is a classroom collaboration activity, not a record of work completed on your behalf during the review.

This week's Moodle Git Branching task consists of four Main groups: **Introduction Sequence → Ramping Up → Moving Work Around → A mixed bag**. All other levels are optional. Understand branches, HEAD, merge/rebase and the effects of selectively moving changes on history, rather than simply memorising command names.

```text
Clear code/configuration → unit tests → commit history → pull request review
                                              ↓
                          Traceable analysis and deployment workflows
```

This is a **supplementary integration diagram**: Unix provides the operating interface; YAML represents configuration; Python expresses analysis; tests check behaviour; Git records and reviews changes. Together they support later automation across multiple machines.

## Required reading map

- [Official PEP 8 website](https://peps.python.org/pep-0008/): Moodle asks you to familiarise yourself with it. Read code layout → imports/whitespace → naming/docstrings → programming recommendations, and identify the guidance in your own small pieces of code. Do not just memorise “four spaces”.
- [Research Software Engineering with Python — Chapter 2: The Basics of the Unix Shell](https://third-bit.com/py-rse/bash-basics.html): The authors' Chapter 2 covers filesystem/navigation, creating/moving/copying/deleting, wildcards and manuals, followed by exercises. Moodle uses “in Python”, while the authors' official book title uses **with Python**. This week requires reading Chapter 2; no requirement to upload answers to all the chapter exercises was found.
- [Moodle book entry](https://moodle.ucl.ac.uk/mod/book/view.php?id=8523823): The page showed that no book content had been added. Its description links to the [UCL Primo ebook entry](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159). You can read the authors' website; an empty Moodle page does not mean the required reading is empty.
- `Unix in a Nutshell` is labelled **Extra reading** on Moodle. Use it as a reference; it is not a separate assignment to submit this week.

## Classroom Q&A — identifiable exchanges

The English questions below are **paraphrases** based on recognisable English in the original transcript, not verbatim quotations. Speaker labels are unreliable, so student names are not supplied.

| Time | English question | Lecturer's response/interpretation |
| --- | --- | --- |
| **16:01–16:21** | **Do I have to use the same connection command every time I access the VM?** | You need to provide the correct identity, jump host and target machine. The long command represents the information genuinely required for the connection. |
| **16:21–17:51** | **Can we put it in SSH config so that the command is shorter?** | You can create a `Host` entry for the VM, configure the identity/jump host and then use a short alias. The lecturer adds that repeatedly destroying/creating VMs with new IP addresses requires repeated config updates; fixed machines with fixed IPs are easier to maintain. |
| **51:17–52:38** | **What happens if I touch an existing file?** | Following a student's answer, the lecturer confirms that the timestamp is updated; a file is created if it does not exist. Do not confuse this with overwriting the contents. |

**Material not presented as a lecturer's answer:** The ODP contains questions about good code and the advantages/disadvantages of Git, but no reliable verbatim answers. Missing words in later commands are not reconstructed into invented Q&A either.

## Teacher emphasis and common pitfalls

1. **18:37 — First establish a working remote environment this week.** A VM appearing in the list does not mean you have logged in. Successfully reaching a remote shell through SSH is the most direct learning check.
2. **5:06–5:36 — Version consistency.** AlmaLinux 9 was chosen to maintain consistency with demonstrations. A newer version being “probably the same” does not mean it has been tested for complete compatibility.
3. **8:29–9:00 — Hostname uniqueness.** Use your individual ID to help avoid collisions; do not copy the lecturer's example name.
4. **14:23–15:34 — IP reuse.** A new VM may obtain an old IP address with a different host identity. **Supplementary operational principle:** First confirm the reason for the change and the target, then handle the corresponding known_hosts entry. Removing all host checks is not a general fix.
5. **33:51–34:08, 49:30–49:45 — Turn manual exploration into automation.** Logging in to make temporary manual edits may still happen in practice, but understood operations should gradually become repeatable configuration workflows.
6. **55:48–57:08 — Relative path depends on location.** The same relative string points to different locations in different directories. Check `pwd` first.
7. **57:28–59:52 — Consult help/manuals.** Options and the completeness of documentation vary between commands. Read the documentation for the version you are actually using before operating it.
8. **7 October HTTP announcement — Include corrections outside the teaching files.** ServerName, hostname/instance labels, services and the firewall can each affect reachability.

## Study checklist — check your own understanding

These are **supplementary self-check questions**, not new assignments from the lecturer or predictions of exam questions.

- Can I explain the difference between the gateway and my VM?
- Can I identify the active namespace and explain why the old MD example differs?
- Can I tell whether a command is running on my Mac or on the remote VM?
- Can I explain `/`, `/root`, `/home`, `~`, `..` and `cd -` without confusing them?
- Can I trace stdout/stderr through a redirection or pipe?
- Can I distinguish an installed package from a running service and an accessible website?
- Can I explain why a clear config file, a unit test and a Git commit help reproduce my work?

## Source links

- [All Week 1 materials](https://moodle.ucl.ac.uk/course/section.php?id=1381270)
- [1.1 Welcome Slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523815) / [1.2 Rancher and ssh configuration](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523816) / [1.3 Remedial Software Engineering](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523817)
- [1.3.1 Unix](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523818) / [1.3.2 YAML](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523820) / [1.3.3 Python](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523821) / [1.3.4 Git](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523824)
- [5 October Welcome](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1312114) / [6 October Condenser fixes](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710) / [6 October namespace](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808) / [7 October HTTP Hostnames](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852)
- [Asksia recording and original transcript](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43)
- [PEP 8](https://peps.python.org/pep-0008/); [Irving et al., Research Software Engineering with Python](https://third-bit.com/py-rse/) and its [Chapter 2](https://third-bit.com/py-rse/bash-basics.html) (the authors' version is labelled CC BY 4.0; this document provides notes and links).

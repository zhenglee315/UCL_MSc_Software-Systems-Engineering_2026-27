# Week 1 — Introduction to Research Methods in Software Engineering

[繁體中文版](../README.md)

**Class:** 9 October 2026 · **Lecturer:** Emmanuel Letier · **Module:** COMP0108

**Owner-specific records:** Group D and any recorded submission or completion status refer to the repository owner. Other readers should check their own group allocation and current Moodle status.

This week connects two topics: how to read, evaluate and communicate Software Engineering research, and how to apply these skills to the assessments this term. The Traditional Chinese version retains English technical terms with Traditional Chinese explanations; this version presents the same content in English. The notes were developed from the original English lecture transcript, then cross-checked against the Asksia summary and official Moodle materials.

## Sources and coverage

| Source | Coverage and use in these notes |
|---|---|
| [Asksia — Recording_20261009_1102](https://app.asksia.ai/pro/session?id=586f073f-f525-4973-b96b-4a2a0208a53e) | The original English transcript in the Origin column was read in order, from the first segment at `0:28` to the end of the teaching content at `107:11`, including the break and the final visible segments. The complete summary was then used as a second check. Timestamps are navigation aids, not corrected subtitles. |
| [Module Organisation](https://moodle.ucl.ac.uk/mod/resource/view.php?id=9433582) | The official `0. Course Organisation-2026.pptx`, with 32 slides, was used to check learning outcomes, AI policy, reading strategy, MIP groups and assessment dates. |
| [Software Engineering Research: Purpose, Practice and Areas](https://moodle.ucl.ac.uk/mod/resource/view.php?id=9437333) | The Week 1 lecture entry and filename, `1. Introduction-SE-Research.pptx`, were confirmed on Moodle. The attachment could not be downloaded during this check, so its PPTX content was not read. Notes on this part of the class are based on the original transcript; no unverified slide numbers are provided. |
| [Moodle course](https://moodle.ucl.ac.uk/course/view.php?id=56456) / [Lecture Slides](https://moodle.ucl.ac.uk/course/section.php?id=1519140) | Used to check the course introduction and the official Week 1 materials list. |
| [CW1 task and submission](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8834016) | The complete DOCX brief and online rubric were read. Detailed requirements are in the [coursework notes](../coursework/dict/README.md). |

**Source limitations:** The ASR transcript contains missing phrases, errors and misheard names. For example, references to `Google` in course administration contexts were checked against the official Moodle pages. The player displays `110:27`, but fragmented noise at the end is timestamped `122:59` and `123:10`; these fragments are not treated as teaching content. Most of the transcript uses a single speaker label. The Q&A below does not infer student identities or turn fragments into invented verbatim quotations. Checked on **12 October 2026**.

## Key takeaways

1. **Research methods are engineering skills.** Even without plans for a PhD, engineers need to evaluate claims about tools, practices and AI systems. Producing working code does not itself demonstrate effectiveness in a real setting.
2. **Critical, yet balanced evaluation** means identifying the strengths of the evidence, its weaknesses, applicable contexts and limitations, while recognising the work's actual contribution. It involves more than finding faults.
3. **Credibility and relevance are different questions.** A result may be trustworthy but unsuitable for a particular project. A topic may also be highly relevant while the evidence remains weak.
4. **Quantity is not a substitute for knowledge.** The lecturer discussed publication incentives and recent submission volumes: more papers do not necessarily produce stronger, more coherent knowledge.
5. **Read for a purpose.** Start with a bird's-eye view, then understand the methods and results, and examine assumptions when needed. CW1 still explicitly requires reading the full assigned paper.
6. **Own the reasoning and writing.** AI can have an assistive role, but the understanding, arguments and reflections submitted must be your own. You remain responsible for every word and source.

## Why research methods matter

Sources: transcript approximately `5:29–11:56`; Module Organisation slides **5–7**.

| Skill / learning outcome | Main points from the class |
|---|---|
| **Critical thinking** | Analyse claims about tools and engineering practices, recognise hype, and ask what evidence supports each claim. |
| **Empirical research methods** | Learn to design experiments and collect and interpret data. The lecturer particularly emphasised the importance of these skills when developing and evaluating AI-based systems. |
| **Working at the frontier of knowledge** | Many problems have no established solution. Engineers need to handle complexity, uncertainty and ambiguity, rather than only completing clearly defined coding tasks. |
| **Creativity** | Generate new ideas and design ways to evaluate them. Research involves more than criticism and error checking. |
| **Communication** | Explain papers at different levels of abstraction, clearly conveying the contribution, methods, problems and reasons. |
| **Research literacy** | Identify research areas, seminal problems and solution techniques; understand how conferences and journals review and accept papers. |

The lecturer described understanding the value to be created and using experiments to evaluate effectiveness as increasingly important engineering work. This is a view expressed in this class; it should not be expanded into a general claim that coding no longer matters.

## Key concepts

### Normative and descriptive definitions

Sources: transcript approximately `67:41–71:05` and `83:26–84:44`.

| Perspective | Software Engineering | Software Engineering Research |
|---|---|---|
| **Normative** | Describes how engineering should be done: developing, operating and maintaining software in a systematic, disciplined and quantifiable way. | Describes how research should be done: using scientific inquiry to understand engineering practices and explore improvements, seeking honest, unbiased and evidence-based knowledge. |
| **Descriptive** | Examines what software engineers actually do and which methods work in practice. | Examines how researchers actually conduct research. Their incentives and practices may differ from the ideal. |

**Relationship:** Comparing descriptive practice with normative aspirations reveals gaps. The lecturer argued that a healthy research community should continually reflect on these gaps. A practice being common does not establish that it is the best practice.

### Credibility and relevance

Source: transcript approximately `72:16–83:23`.

| Question | What to investigate |
|---|---|
| **Credibility — Can I trust this claim?** | How the evidence was obtained and measured, what the sample was, whether other studies support it, and whether the research was well designed and well conducted. |
| **Relevance — Does it apply here?** | Whether the context of the result resembles your system, team and constraints, and whether transferring the result is reasonable. |

Information sources discussed in class included personal experiments and proofs of concept, experience from past projects, books, A/B testing, senior developers, similar existing systems, university teaching, research papers, blogs and social media, and vendor content.

The lecturer described a typical difference in credibility: blogs, social media and vendor claims often require greater caution; well-conducted empirical studies may provide stronger evidence than individual anecdotes; and replicated studies across different contexts can produce stronger systematic evidence. However, he also explicitly cautioned that **not all empirical studies are credible, and source type alone does not determine quality.**

**Additional study aid — use the two dimensions from class when reading:** Write down separately why a claim is credible and why it is applicable. This is an organisational method for these notes, not a coursework field assigned by the lecturer.

### Individual, professional and societal knowledge

Source: transcript approximately `80:44–83:23`.

```text
Personal experience + experiments + research evidence + professional discussion
                               ↓
               Decisions within a project or team
                               ↓
        Shared professional practice / bodies of knowledge / standards
                               ↓
        Society's expectations, accountability and regulation
```

Research is one part of this relationship. The soundness of engineering methods affects team decisions, society's expectations of professional engineers, assessments of responsibility after incidents, and the development of standards. Privacy, AI and accessibility were mentioned as examples. These notes record their research and engineering context; the classroom examples are not presented as statements of legal rules.

### Knowledge areas, research areas and state of the art

Source: transcript approximately `98:45–105:56`.

| Term | Distinction made in class |
|---|---|
| **Knowledge areas** | Established knowledge and techniques commonly used today, organising the **state of practice**. The class used the Software Engineering Body of Knowledge's categories as an example. |
| **Research areas** | Unanswered questions, unresolved challenges and techniques being explored. |
| **State of practice** | Practices currently in common use and accepted in industry. |
| **State of the art** | The most advanced techniques. They may not yet be widely used, or the conditions under which they work may not yet be fully understood. |
| **AI for Software Engineering** | Applying AI to engineering activities such as coding, testing and analysis. |
| **Software Engineering for AI** | Studying how to develop, evaluate and maintain AI-based systems. |
| **Software analytics / repository mining** | Analysing practices and problems using engineering data, repositories and related sources. |

In the discussion of the ICSE charts shown in this class, the lecturer pointed to the large number of submissions and accepted papers on AI for SE, and the continuing importance of testing and analysis. These are observations about **that conference and those charts**, not a ranking of all research communities or a permanent ranking of topics.

## Research quality and the publication numbers game

Source: transcript approximately `84:44–95:34`.

The lecturer introduced criticism of publication metrics through David L. Parnas's **Stop the Numbers Game** (2007). The author and year were separately checked against [Parnas's own publication list](https://amadon.academia.edu/DavidParnas/CurriculumVitae). The discussion of its ideas here paraphrases this lecture; it does not claim that the full article was read.

The main classroom argument was that when hiring and promotion systems emphasise paper and citation counts, they can encourage smaller, repetitive research outputs that are easy to count, while difficult long-term problems remain unresolved. The lecturer framed this as a **systemic incentive problem**. He did not claim that every researcher is dishonest.

He then discussed how AI might accelerate paper writing and submission, but asked whether this produces more useful knowledge or simply more outputs. He also highlighted the volume of scattered results, the shortage of synthesis that integrates them into coherent knowledge, and the increased reviewing burden.

**Additional study aid — relationships between the concepts:**

```text
Publication incentives → researchers' choices → quantity and type of outputs
                                                   ↓
                      Evidence quality + synthesis + validation
                                                   ↓
                            Useful, transferable knowledge
```

This diagram organises the classroom argument; it is not an established causal model. It is a reminder not to use paper counts, conference prestige or fluent writing as substitutes for evidence quality.

## Core responsibilities of research

Source: transcript approximately `95:42–98:40`.

The class linked research responsibilities into a process: **knowledge creation → validation → dissemination**. Activities include empirically investigating engineering practices; proposing and evaluating techniques and tools; developing theories explaining what works and why; checking claims through peer review and other critical or empirical evaluation; and sharing knowledge with industry, students and society through papers, tools, education and training.

The lecturer also mentioned students and researchers entering industry as a route for research impact. Dissemination should not be reduced to publishing a paper, and validation should not be interpreted as conference acceptance making every conclusion fully reliable.

## Reading a research paper

Sources: transcript approximately `49:52–53:16`; Module Organisation slide **31**. The transcript has gaps in the reading-strategy discussion, so the steps and times were checked against the official slide.

| Pass | Purpose and actions | Time guidance in the slides |
|---|---|---|
| **Pass 1 — Bird’s-eye view** | Read the title, abstract, introduction, section headings, main figures and conclusions. Judge relevance and form an initial view of the type of paper. | 5–10 minutes |
| **Pass 2 — Grasp the content** | Read carefully and study figures and graphs. Temporarily skip proofs and fine detail, and mark important references. This helps establish the contribution and how it was achieved. | Up to an hour |
| **Pass 3 — Challenge every detail** | Follow each step of the method and argument, and check assumptions and claims against the evidence. Appropriate for an in-depth review or building directly on the work. | 4–5 hours; beginners may need longer |

The slide adapts S. Keshav's **How to Read a Paper** (2007). Choosing reading depth according to purpose does not mean that CW1 allows reading only the abstract: the brief explicitly requires the **full paper**.

### Seven elements and their relationships

Sources: transcript approximately `46:31–50:28`; Module Organisation slide **30**; CW1 brief.

```text
Topic → Research question/problem → Prior work and gap → Novelty/contribution
                                                            ↓
                                                   Research method
                                                            ↓
                                                         Results
                                                            ↓
                                                    Claimed significance
```

This is a framework for understanding and communicating a paper. The **problem** is narrower than the topic; the **gap** is a limitation of existing work at the time of publication; **novelty** is the new contribution; the **method** explains how the contribution was built or investigated; **results** are the concrete findings; and **claimed significance** is the authors' statement of the work's implications in that paper.

The easiest pairs to confuse are gap/novelty, method/results, results/significance, and significance claimed in the original paper/actual impact ten years later. The official CW1 table and word limits are in the [coursework README](../coursework/dict/README.md).

## Instructor warnings and common mistakes

Sources: transcript approximately `25:48–42:56`; Module Organisation slides **19–27**.

| Warning | How to interpret it |
|---|---|
| **Hallucinations and specious answers** | AI may invent papers or authors, or produce fluent but incorrect answers. Check the source, rather than only asking another AI whether it agrees. |
| **Generic, superficial content** | Experts look for specificity, substance and understanding of the paper. Fluency does not establish accuracy. |
| **Keep your own voice** | AI revisions are not always clearer. The lecturer warned that overly formulaic, verbose and repeatedly contrastive phrasing can weaken authentic expression. |
| **Translation does not transfer responsibility** | You may carefully translate your own draft, but must check the style, reasoning and every word. The lecturer encouraged thinking and writing directly in English where possible. |
| **Learning happens in the process** | Making notes, writing summaries and reviewing work are themselves learning activities. Merely obtaining polished output may remove this practice. |
| **Assistive use has boundaries** | Assistive use generally does not require declaration in this module, but AI-generated coursework cannot be submitted as your own. Class tests and presentations also have different restrictions; check each brief. |
| **No confidential material in external AI tools** | The lecturer used unpublished work and similar material as examples. |

**The more specific CW1 boundary:** You must develop the structured summary and personal reflection yourself. AI may improve grammar and style, but may not generate these two parts. This file contains lecture notes; it does not write a summary or reflection for the assigned MIP.

## Actual in-class questions and discussion

The following are identifiable exchanges from the actual class. **Both questions and responses are paraphrased.** The transcript does not reliably distinguish individual student speakers, so statements cannot be attributed to named students.

| Approx. time | Actual prompt / question | Recorded response or clarification |
|---|---|---|
| `44:03–44:45` | **Are Best Paper and Most Influential Paper awards the same?** While explaining MIP awards, the lecturer asked whether they would go to the same paper. | Not necessarily: Best Paper awards are selected at publication time; MIP awards look back at the influence on theory or practice roughly ten years later. |
| `67:41–69:44` | **What is Software Engineering? How would you explain it to friends/family?** | The class suggested development and maintenance, engineering applied to software, problem-solving and controlled product delivery. The lecturer explained the variety of definitions, then distinguished normative and descriptive perspectives. |
| `72:16–77:06` | **How do professional software engineers form opinions about what works? What are their information sources?** | Identifiable group responses included proofs of concept, books, A/B testing, senior developers and similar systems. The lecturer added experience and reflection, research papers, and blogs/vendor content, leading into credibility and relevance. |
| `92:33–93:39` | Clarification of whether publication metrics count **submitted or accepted papers**. | The lecturer clarified that accepted papers were meant here, and that the prestige of top conferences has a large influence. He also noted that practices differ between institutions. |
| `93:52–95:16` | Discussion of why there is still an incentive to increase submissions when only accepted papers count. | The lecturer discussed variation and uncertainty in reviewing, repeated feedback and revision, and desk rejection of clearly unsuitable submissions. He did not say that all accepted papers succeed by chance. |
| `100:49–104:47` | **What are current research areas? Which areas are most popular in this conference?** | The class mentioned AI, benchmarks, security and analytics. The lecturer used the ICSE charts shown that day to explain the large volume of research on AI for SE and the importance of testing and analysis. |

## Moodle alignment and assessment roadmap

The Moodle General section emphasises **close reading** and **critical, yet balanced analysis**. At the time of checking, the official Week 1 list contained the Module Organisation and Research Purpose/Practice/Areas slide decks. Announcements contained no posts. The main task after class was to begin reading the assigned MIP and prepare individually according to the CW1 brief.

The following is the official outline from Module Organisation slides **13–15 and 32**. Later assessments require their own published briefs; this week's spoken introduction does not replace them.

| Assessment | Published schedule | Weight | Relationship |
|---|---|---|---|
| **CW1 — Summary and Reflection** | 20 Oct 2026, 16:00 UK time | 10% | Individually read the assigned MIP and develop a structured summary and reflection. |
| **CW2 — 1 Paper Summary + 1 Paper Review** | 10 Nov 2026, 16:00 | 20% | Practise related reading and reviewing skills using other papers. |
| **Practical 1 — Mock PC Meeting** | 20 Nov 2026, in class | 10% | Paper discussion and participation are assessed. |
| **Practical 2 — Group Research Talk** | Slides + MCQ: 3 Dec 2026, 16:00; talks: 4 / 11 Dec | 20% | Agree a group summary, trace the MIP's influence and give a talk. |
| **In-Class Test** | 18 Dec 2026; Moodle activity previously confirmed 12:10–12:55 | 20% | MCQs, including one question from each group's talk; attendance is required. |
| **CW3 — Individual Report** | 7 Jan 2027; the slide does not specify a time | 20% | Critically analyse one research line building on the MIP. |

The module has **no end-of-year exam**, but it does have assessed coursework, in-class practicals and the December test. The slides require notifying the lecturer in advance if you cannot attend an in-class assessment. [Moodle assessments](https://moodle.ucl.ac.uk/course/section.php?id=1379254)

**Optional opportunities:** The SSE research seminars, held every other Wednesday, are strongly recommended. The first seminar listed in the slides is **21 Oct 2026, 13:00–14:00**; the slides identify the 09:00 timetable entry as an error. If you want a summer research project, Moodle recommends contacting potential supervisors **before the end of Term 1**. This is long-term planning, not a file due in Week 1. [Research Project / Group Industrial Project](https://moodle.ucl.ac.uk/course/section.php?id=1379265)

### Corrections from the Asksia summary cross-check

| Summary simplification / mismatch | Result of the checks used in these notes |
|---|---|
| Citation tracing was included as a CW1 task. | Official CW1 consists of a seven-element summary and three reflections. Citation tracing belongs to the later MIP impact/group-talk/report activities, rather than an additional CW1 submission component. |
| CW2 was described as an analysis of the evolution of research methods. | The official outline is **1 Paper Summary + 1 Paper Review**. The evolution of the research context is discussed separately in later MIP activities. |
| Assigned papers were conflated with Best Paper award winners. | The assigned papers are **MIP award papers**. The class distinguished the selection timing and purpose of the two awards. |
| Seven sentences were treated as an absolute formatting constraint. | The spoken introduction and slides aim for one sentence per element. The complete CW1 brief occasionally permits multiple sentences; the strict requirements are seven elements and a maximum of 100 words per element. |

## Review prompts — additional study aid

These are **additional self-check questions prepared for these notes**. They are not new questions assigned by the lecturer, an exam question bank or completed coursework answers:

- For a software tool claim, how would you separately assess credibility and relevance?
- What evidence can support faster code writing? What evidence would support a broader claim about engineering productivity?
- When normative aspirations and descriptive practice differ, how can research help identify the problem?
- How would you distinguish a paper's method, results, claimed significance and later actual impact?
- Why might polished writing still be low quality if it lacks concrete evidence or the writer's own reasoning?

Coursework requirements and group information: **[Week 1 coursework README](../coursework/dict/README.md)**.

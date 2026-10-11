# Week 1 Coursework — CW1 MIP Summary and Reflection

[English version](dict/README.md)

此檔記錄 **官方要求、分組及閱讀安排**。沒有為 assigned paper 生成 structured summary 或 personal reflection，也沒有學生答案。

## Official sources

- [CW1 task, attachment and submission](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8834016)：`COMP0108 Coursework 1 - Summary and Reflection.docx`（頁面列上傳日期 6 October 2026）及 grading rubric。
- [Module Organisation](https://moodle.ucl.ac.uk/mod/resource/view.php?id=9433582)：slides **29–32**（groups、CW1、reading strategy、assessment relationships）。
- [Moodle Participants](https://moodle.ucl.ac.uk/user/index.php?id=56456)：查核時 selected group 為 **Group D**，名單包含 Wilson Lee。
- [Asksia Recording_20261009_1102](https://app.asksia.ai/pro/session?id=586f073f-f525-4973-b96b-4a2a0208a53e)：約 `43:15–57:13` 的口述背景；正式要求以完整 brief 為準。

**Last checked: 12 October 2026.** Moodle 當時顯示 **No submissions have been made yet**；此狀態是查核紀錄，提交後需另行更新。

## Download materials

| Order | Material | How to use it |
|---|---|---|
| 1 | [Group D assigned ISSTA 2015 paper — 13 pages](materials/Qi-et-al-2015-ISSTA-Patch-Plausibility-and-Correctness.pdf) | **先讀此篇指定 paper**：Qi、Long、Achour、Rinard 四作者的 conference paper。來源是[作者提供的 MIT PDF](https://people.csail.mit.edu/zichaoqi/papers/kali-issta15/paper.pdf)，由[作者首頁](https://people.csail.mit.edu/zichaoqi/)連結；只核對首頁書目身分，沒有生成 paper 分析或作業答案。 |
| 2 | [CW1 作業說明（原始 Word assignment brief）](materials/COMP0108-CW1-Summary-and-Reflection.docx) | Moodle 官方附件的原始副本，包含要求、格式及示例；不是已完成的作業答案。 |
| 3 | [Related MIT thesis (84 pages; not the assigned conference paper)](materials/An%20Analysis%20of%20Patch%20Plausibility%20and%20Correctness%20for%20Generate-and-Validate%20Patch%20Generation%20Systems.pdf) | **僅補充**：repo owner 提供的同名檔案，實際是 **Zichao Qi 單作者、September 2015 的 MIT master's thesis**。[UCL Primo / ProQuest thesis record](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/447gj8/cdi_proquest_journals_3332470845) 是此 thesis 的館藏紀錄。 |

目前核對的官方 CW1 材料中，只找到這份 Word **assignment brief**，沒有另行提供的可填寫 worksheet/template。**最終提交仍是單一匿名 PDF**；下載老師的 Word 說明不等於完成或提交作業。

上述 **84-page thesis 與 Group D 指定的四作者 ISSTA 2015 conference paper 不同**。CW1 要讀上表第 1 項 assigned paper；完整 citation 列在「Group D and the assigned MIP」。這份 thesis 是額外保存的相關來源，不是本作業指定的 84 頁閱讀。

## At a glance

| Item | Confirmed requirement |
|---|---|
| Coursework | **CW1 — MIP Summary and Reflection** |
| Individual / group | **Individual**：自己閱讀、寫作及反思；brief 明說不要與其他同學 conferring。 |
| Weight | **10%** of the module |
| Deadline | **Tuesday 20 October 2026, 16:00 UK time** |
| Submission | **One document in PDF format**, submitted on Moodle |
| Anonymous marking | **Do not put your name or student number** on the document |
| First page | 最上方寫 assigned MIP 的 **full citation：authors、title、venue、year** |
| Contents | **Part 1: Structured Summary** + **Part 2: Personal Reflection** |
| Reading | **Read the full assigned paper**, not only the abstract |
| Timing | 可以在 Week 1 後開始讀；在 **Week 2 lectures**（Theories / Research Methods in SE）之後 finalise |

## Group D and the assigned MIP

Module Organisation slide **29** 對應的 paper 是：

**Zichao Qi, Fan Long, Sara Achour and Martin Rinard. 2015. _An Analysis of Patch Plausibility and Correctness for Generate-and-Validate Patch Generation Systems._ Proceedings of the 2015 International Symposium on Software Testing and Analysis (ISSTA 2015), 24–36.**

- [ACM publication record / DOI](https://doi.org/10.1145/2771783.2771791) — 本次只核對 bibliographic metadata，沒有分析 paper 本文或生成作業內容。
- Group D 分配以 Moodle Participants 與官方 slide 核對；作業不是任選一篇 paper。
- 本週 task 是個別 CW1。提交後的課堂活動才比較 groupmates 的理解、討論一致與差異，建立 group summary，供後續 MIP impact analysis 使用。

**MIP means Most Influential Paper.** 它是在 paper 發表約十年後回看對研究或實務的影響；不要與 publication-time Best Paper award 混同。

## Part 1 — Structured Summary

**Format:** exactly **seven elements**，按以下順序，以三欄 table 呈現：**`#` / `Element` / `Sentence`**，每元素一列。

| # | Element | What the brief asks for — 要回答的方向 |
|---|---|---|
| 1 | **Topic** | Paper 所在的 Software Engineering area/topic。 |
| 2 | **Research question or problem** | 比 topic 更窄、但在 paper 之外也存在的問題；不要提前寫該 paper 的 technique、tool 或 dataset。 |
| 3 | **Prior work and gap** | 在 paper **發表當時**已有的 state of the art 及不足；不是 paper 自己的 novelty 或後來的 research。 |
| 4 | **Novelty / contribution** | 新的 technique/tool、hypothesis/theoretical account 或 empirical angle；不把 method/results 混在此元素。 |
| 5 | **Research method** | 作者如何 investigate、build 或 evaluate contribution；在相關時包含 study design 與 scale。 |
| 6 | **Results** | Concrete outcomes/findings；paper 有 numbers/comparisons 時應反映它們。不是只寫「很重要」。 |
| 7 | **Claimed significance** | 作者在該 paper 中主張的 significance/implications；不是重複 results，也不是十年後 actual impact 或為何得 MIP。 |

### Length and writing rules

- 目標通常是 **one sentence per element**；brief 允許某些元素偶爾多句。嚴格要求不是無例外地恰好七句。
- 建議 **15–35 words per element**、整體約 **150–250 words**；這是 guidance，超出該建議範圍本身不扣分。
- **Strict maximum: 100 words per element**，包含該元素所有句子；超過即該元素 **0 marks**。
- 一個句子不能同時涵蓋多個元素，例如把 gap 與 novelty、method 與 results 混在一起。
- 雖各列分開，Sentence 欄由上到下仍應能讀成 **one coherent paragraph**；可自然使用 connectives/pronouns。
- Audience：知道該 field，但可能不熟悉 paper topic 最新研究的 professional engineers、master’s students 或其他 SE areas 的 researchers。
- 用自己的文字；不要 copy/paste paper 或其他網路來源的句子；不能只依賴 abstract。

## Part 2 — Personal Reflection

三個 **independent short answers**，不必連成一段：

1. **Most interesting:** What did you find most interesting or surprising about this paper, and why?
2. **Least interesting / least convincing:** What did you find least interesting, or where do you think the paper is weakest or least convincing?
3. **Unclear:** What was unclear or hard to follow in the writing, method or results? 如果沒有，說明什麼讓它容易理解，例如 particular figure、running example 或 method explanation。

- 每答建議 **30–60 words**，是 guidance。
- **Strict maximum: 100 words per answer**；超過即該答案 **0 marks**。
- 必須是自己閱讀的反應，指向 paper 的 particular claim、result、design choice 或其他具體部分，而非 reviewers/later citations 的意見摘要。
- 「nothing was unclear」不能只給空泛結論；需有具體說明。

## Marking and easy-to-miss distinctions

總分 **100**：Part 1 的七元素各10分，Part 2 的三答各10分；各項評為 **0 / 5 / 10**。

官方頁面與 brief 的提醒包括：

- Copying、serious inaccuracies、超過100-word limit 可使該項得0。
- **Problem** 不能只寫 paper aim；問題應有超出該篇特定 solution 的意義。
- **Prior work and gap** 必須以當時的 prior work 為準。
- **Method** 不只有 study type；相關時要有 design/scale。
- **Results** 要寫 concrete findings；**significance** 要保留作者在原文中的 claim，兩者分開。
- Reflection 評的是是否具體投入該 paper，不是 marker 是否同意自己的觀點。

## AI policy for this coursework

CW1 brief 明確允許 AI/tools 幫助改善 **grammar and style**，但明確說 **不要用 AI 生成 structured summary 或 personal reflection**。

Module Organisation slides **19–27** 的較一般原則是 assistive use、保留本人 authorship、核對 sources、對 accuracy/integrity 負責。不能把較寬的一般口述理解成可外包 CW1 的核心閱讀、摘要或反思。

此 README 的內容只提供 requirements/navigation；作業中的十個內容項目仍由本人閱讀後完成。

## Week 1 actions and later group work

### Required now

- 找到 Group D assigned MIP，開始讀 **全文**。
- 閱讀 CW1 brief 及 Moodle rubric，辨識 seven elements 與 reflection 的不同任務。
- 先形成自己的理解與 notes，再在 Week 2 lectures 後完成自己的兩部分與 PDF。
- 在 **20 October, 16:00 UK time** 前提交；上傳後以 Moodle 實際狀態確認完成，不能把只開 Add submission 表單當成已提交。

### Reading strategy taught in Week 1

官方 slide **31** 使用 three passes：bird’s-eye view → grasp the content → challenge details。這是一個 reading strategy，不是允許略過 CW1 的 full-paper requirement；詳見 [Week 1 notes](../README.md#reading-a-research-paper)。

### Later activities — do not add them to the CW1 submission

- **Group summary / tracing the MIP’s influence / research talk** 屬於後續 Practical 2 脈絡。
- **CW2** 官方 outline 是 one paper summary + one paper review，不把 Asksia summary 中的簡化描述當作正式 brief。
- **CW3** 是個別 critical analysis of one line of research building on the MIP。
- Citation tracing 是後續學期活動的一部分；**CW1 brief 沒有把它列成第三個提交部分**。

截至查核日，Moodle Week 1 Lecture Slides 區只有兩份講義，Announcements 沒有新公告，未見額外 Week 1 exercise submission 或獨立 group deliverable。Research seminar 是 **optional, highly recommended**；若想做 summer research project，Moodle 建議 Term 1 結束前聯絡 potential supervisors，屬長期規劃。

## Submission self-check — requirements only

- [ ] 使用正確的 Group D assigned paper，已閱讀全文。
- [ ] PDF 首頁有 authors/title/venue/year，沒有姓名或 student number。
- [ ] Part 1 有七元素、指定順序與三欄 table。
- [ ] 每元素不超過100 words；elements 不混在同一敘述中。
- [ ] Part 2 有三個具體、個人的答案；每答不超過100 words。
- [ ] Summary/reflections 為本人形成；AI use 符合該 brief。
- [ ] 在 deadline 前提交，並核對 Moodle 顯示的 submission status。

勾選清單僅列官方要求，沒有預先宣稱任何項目已完成。

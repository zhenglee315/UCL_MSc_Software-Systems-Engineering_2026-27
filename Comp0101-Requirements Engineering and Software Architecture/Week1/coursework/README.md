# COMP0101 — Week 1 Coursework, Reading and My Answers

[回到本週課堂筆記](../README.md) · [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384)

核對時間：**2026-10-12，Europe/London**。本文件區分 Moodle instructions、我的完成狀態，以及學習用作法建議。這次整理沒有替我提交任何 Moodle assignment／quiz。

## 1. 本週任務與完成順序

| Order | Task | Required / grading | Deadline / target | Verified status |
|---|---|---|---|---|
| 1 | Read Chapters 1–6，尤其 Chapters 5、6 | 必讀；未完整課講的內容 could be assessed | 10/15 上午下一堂課前；建議 10/14 下午前 | 閱讀完成狀態尚未確認；舊 book 連結不可開啟。 |
| 2 | Quiz — Requirements in the lifecycle | Chapter 5 self-check；pass 4/4；不是 module final mark 的來源 | 同上，未見另列本週 quiz hard deadline | **已完成：Finished，4/4 (100%)**。 |
| 3 | Radiation Therapy Controller exercise | Not marked，但要求 genuine attempt；exam-like practice | 同上 | **尚未提交**；Moodle 顯示 no submissions。 |
| 4 | Upload RTC answers → compare solution → correct mistakes | 提交後才解鎖 solution sheet／exercise forum | 課前完成並訂正 | 尚未進行；沒有自己的 RTC 答案可收錄。 |
| 5 | Martin Fowler talk，約 30 min | **Optional but highly recommended** | 本週補充閱讀時段 | 未確認觀看狀態。 |
| 6 | Preview context diagrams / domain conceptual models | 10/9 公告歡迎課前先讀；預習 | 10/15 課前，時間允許時 | 未確認。 |

**期限來源及衝突**：老師 [2026-10-09 公告](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1316380#p2355911) 要求 week 1 tasks 在 next Thursday morning class 前完成，即 **2026-10-15 上午課前**。AM 課堂也建議 Wednesday afternoon 提交，故 **10/14（三）下午**是預留訂正時間的建議目標，沒有精確鐘點。RTC assignment 頁仍顯示 **2025-10-09 09:00**，並計算 overdue 一年；這是與本學年公告不一致的舊日期，不能據此認定本學年 deadline 已過一年。

## 2. Read Chapters 1–6：讀什麼、在哪裡

官方路徑：**Moodle → COMP0101 → Week 1 → Your Tasks For Next Week → Reading: Chapter 1 to 6 — Foundations of Requirements Engineering**。

- [Reading activity](https://moodle.ucl.ac.uk/mod/url/view.php?id=8513323)：Moodle 明確要求 Chapters 1–6，特別是未在課上完整涵蓋的 Chapters 5、6。
- 舊 [lecture-notes book](http://www0.cs.ucl.ac.uk/staff/E.Letier/book/) 本次無法開啟；同一連結也列在 Moodle General 與 10/9 公告中。
- 已可讀的 [Foundations of Requirements Engineering slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8513321)：`1. Foundations.pptx`，是本週課件，可先補足概念與練習；不等同已完成 book 閱讀。
- [Moodle General Reading List](https://moodle.ucl.ac.uk/course/view.php?id=56463) 提供延伸書籍；老師說不用買書，也不需讀完整個 reading list。指定的 Chapters 1–6 指這份 foundations lecture notes，不能誤當整個 reading list 的任意書第 1–6 章。

**閱讀作法（我的建議）**：先對照 [Week 1 notes](../README.md) 建立概念，再回課件用自己的英文解釋下列問題。若 book 仍失效，可在課堂／office hours 詢問可用副本；本整理未代發訊息。

| Focus | Available slide sections | Self-check |
|---|---|---|
| Definition of RE | Slides 3–18 | Why is RE more than asking clients what they want? |
| World / Machine / Phenomena | Slides 19–31 | Can I classify W/I/O/M after stating the machine boundary? |
| G / R / D and correctness | Slides 32–50 | Can I explain `Req, Dom ⊢ Goals` and distinguish actual state from sensor data? |
| Requirements errors | Slides 51–69 | Can a system fail while the software meets its spec? Why? |
| Lifecycle | Slides 70–80 | Iterative vs incremental? Twin Peaks? Requirements and testing? |
| Wider context | Slides 81–96 | Client/product, brownfield, regulation, social responsibility, AI? |

上表是 **slides sections** 的閱讀導引，未用它來假定失效 book 每章的正式標題。

## 3. Quiz — Requirements in the lifecycle

[Quiz entry](https://moodle.ucl.ac.uk/mod/quiz/view.php?id=8513324) · [My finished attempt / feedback](https://moodle.ucl.ac.uk/mod/quiz/review.php?attempt=6460314&cmid=8513324)

**Moodle 已確認**：Attempt 1，Finished；2026-10-12 **00:26** 完成；**4 out of 4 (100%)**；Highest grade 4/4。Grading method 是 Highest grade，pass threshold 4/4。四題客觀題各 1 mark，第五題 reflection 為 Not graded。Moodle 的 Done 表示 receive a grade；這次也另外核對了實際分數，不只看完成徽章。

### Q1 — Agile software development

**Question:** In this course, what do we mean by agile software development?

**My submitted answer:** Any iterative and incremental development process.

**Feedback:** Correct，1/1。

**理解**：Iterative 改善既有內容；incremental 增加可交付內容。Agile 仍需要 vision、plan、collaboration 和 engineering discipline；不是 writing code without following a plan。

### Q2 — Iterative vs incremental

**Question:** Imagine you are writing a book that will have several chapters. Which of these activities is iterative, incremental, or neither?

| Activity | My submitted answer | Moodle feedback |
|---|---|---|
| Adding a new chapter | **Incremental** | Correct |
| Revising the text of an existing chapter | **Iterative** | Correct |

整題 **1/1**。記憶方式：add new = incremental；improve existing = iterative。

### Q3 — Twin Peaks model

**Question:** What does the Twin Peaks model mean?

**My submitted answer:** Requirements and architecture must be defined together.

**Feedback:** Correct，1/1。

**理解**：不是要求兩份文件在同一分鐘寫完，而是 requirements 與 architecture 互相影響、反覆深化。Architecture 可以揭露成本、限制、需求遺漏與新的可能性。

### Q4 — Ultimate quality criterion

**Question:** According to the lecture notes, what is the ultimate criteria for evaluating the quality of a software system?

**My submitted answer:** The extent to which it meets its stakeholders' goals.

**Feedback:** Correct，1/1。

**理解**：fast、few bugs、profitable 等可能很重要，但必須回到 stakeholder goals。技術品質很好、卻沒有解決真正問題的 system，仍可能不是高品質成果。

### Q5 — My reflection (Not graded)

**Question:** Do you agree with this claim? What criteria do you think are the ultimate criteria for evaluating the quality of a software system? All answers are good answers.

以下保留我提供的英文作答；已在 Moodle review 確認同一內容，**Complete / Not graded**：

> I agree that the quality of system depends on how well it meets its stakeholders' goals. A fast, profitable system with no bugs can still be poor if it does not solve the problem.
>
> I would also look at whether it helps users complete their tasks and delivers the intended value, while considering reliability, usability, security, accessibility and maintainability. These criteria matter because they support stakeholders' goals. Where goals conflict, the trade-offs should be explicit because stakeholders need to understand which goals are given priority and why.

**中文理解**：先同意 stakeholder goals 是最終判準，再說明 reliability、usability、security、accessibility、maintainability 如何支持這些 goals；衝突時須交代 priority 和理由。這是我的答案，沒有把它稱為唯一 model answer。

### Quiz 會不會考？

Moodle 說 quiz 用來檢查 Chapter 5 的理解；必讀內容 could be assessed。因此 **Agile、iterative/incremental、Twin Peaks、stakeholder goals 等概念要會**。沒有公告保證期末考會原封不動出這五題，也沒有說 quiz mark 算入 COMP0101 final mark。

老師說 exam-like／曾為 exam questions 的，是每週 exercise sheets 的整體說明，不能擴張成「每道 quiz 題都是期末題庫」。

## 4. Radiation Therapy Controller (RTC) Exercise

[Assignment entry](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8513326) → download **`1. Foundations-RTC.docx`**。

### 4.1 題目在做什麼

Machine 是 **Radiation Therapy Controller (RTC) software**，不是整台 **Radiation Therapy Machine (RTM)**，也不是整個 hospital。

RTC 從 external prescription database 讀取 doctor 的 prescription；therapist 在 RTC workstation 選擇 prescription，直接到 RTM 調整 machine settings 和 patient position。RTC 能 **sense settings but not control settings**，主要檢查 actual／prescribed settings 是否一致，控制自己的 interlock switch，顯示 readiness，並寫入 external radiation-session database。

START／STOP control panel 直接連到 RTM switch；RTC 只是感測該 switch 的狀態。Beam 還受 dosimeter、其他 safety programs／hardware 的 interlock switches 影響。不能假設 RTC 單獨決定 beam 是否開啟，或直接移動病人／調整 RTM。

正常情境：選 prescription → 顯示設定 → therapist 調整 RTM → settings match → RTC closes switch / indicates ready → therapist leaves room / presses START → beam on → dose reached / beam off → RTC logs session。也要讀 exceptions：可提前 STOP、其他 interlocks 開啟、beam on 時不得換 patient/prescription 等。

### 4.2 各題怎麼做（作答導引，非我的已交答案）

| Question | Task | 作法與檢查 |
|---|---|---|
| Q1 — Actors and Stakeholders | 對 9 個 terms 分別填 Actor Y/N、Stakeholder Y/N。 | 檢查是否能 action／change state，以及是否為受影響的人／群體；不要把 entity、prescription、session 自動當 actor。 |
| Q2 — Phenomena | 將情境中的 phenomena 分為 W/I/O/M，填最具體類型。 | 在表上先註明 machine = RTC；依 context diagram 檢查每個 event 的位置和 controller；therapist 與 RTM 的直接互動不自動是 RTC input。 |
| Q3 — Domain Goals | 比較 G1 Achieve [Radiation Session Delivered] 與 G2 Avoid [Incorrect Radiation Delivery]；找滿足一個但不滿足另一個的 behaviours；列涉及的 world phenomena。 | 分開 eventual delivery 與不發生 incorrect delivery；用具體 sequence 檢查兩個 properties 是否等價。 |
| Q3 optional subquestion | 用 temporal logic 表達 Achieve／Avoid patterns。 | **Optional；not assessed on formal specification**。有餘裕再做，目的為加深 phenomena／properties 理解。 |
| Q4 — G / D / R | 對 ID 3–9 的 properties 分類，並為每條 R 列出 I/O phenomena。 | 不只看關鍵字；問 RTC 自己能否保證，或是在預期 therapist、RTM、hardware 的行為。 |
| Q5 — Requirements Correctness | 分別列出支持 G1、G2 的 domain assumptions D 與 machine requirements R。 | 解釋 D、R 如何一起支持目標，只保留相關項目；不要單列 requirements 卻省略外部行為／sensor／interlock assumptions。 |

**題目編號小誤植**：Q3 子題沿用 2.x 且出現重複 2.2；Q5 第二小題印成 5.12，末句又寫不貢獻 G1 的項目。此題前半明確要求 `D, R ⊢ G2`，可按 G2 整理並在答案註明依題意解讀，仍可向老師確認。

### 4.3 如何提交及訂正

1. 在 downloaded exercise sheet 或自己的答案文件中，標好 Q1–Q5，完成 genuine attempt。
2. 卡住時寫短註記，說明卡在哪裡或哪些 assumptions 不確定。Moodle 允許留空，但解釋比空白更有用。
3. 開 [RTC assignment](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8513326)，選 **Add submission**，上傳答案並 **Save changes**；以頁面 Submission status 確認有實際提交記錄。若該表單另外要求 **Submit assignment**，也要完成，不只停在 Draft；本次未代操作或假定必定有該按鈕。先前可見限制為最多 1 file、500 MB；未見指定唯一 extension，提交時依表單顯示為準。
4. 回 Week 1 查看解鎖的 **Week 1 Exercise: Solution Sheet**，逐題比較。
5. 把錯誤分類、缺漏 assumptions、推理問題加到自己的訂正，不只閱讀答案。
6. 若仍不理解，到解鎖的 **Week 1 Exercise Forum**、class 或 office hours 提問。

**Current state**：Moodle 顯示 **No submissions have been made yet / Not graded**；本次沒有 RTC 個人作答可收錄，也未開啟受限 solution sheet。`Not marked` 不代表不需要做；老師特別要求先自己嘗試，避免看懂答案卻無法自行答題的 false confidence。

## 5. Optional 與 Exam relevance 的區別

| Item | 老師／Moodle 的規則 | 應如何安排 |
|---|---|---|
| Weekly exercise sheet | Not marked；many exam-like questions；some were exam questions；仍需課前 genuine attempt / upload。 | 放在本週主要工作，提交後訂正。 |
| RTC formal specification | Optional；明確說不 assessed on formal specification。 | 先完成核心分類與推理題；有餘裕用來加深理解。 |
| Martin Fowler talk | Optional but highly recommended；約 30 min。 | 核心閱讀與 RTC 完成後補看。 |
| Chapters 5、6 | Required reading；未完整課講也 could be assessed。 | 必須補讀，不能因課上略過而跳過。 |
| Lifecycle Quiz | Short self-check on Chapter 5；4/4 pass。 | 我已完成；複習時能解釋理由。 |

COMP0101 final assessment 是 **100% three-hour written exam**。Past papers 入口在 [Moodle General](https://moodle.ucl.ac.uk/course/view.php?id=56463) → Library links → [COMP0101 Past exam papers](https://ucl.primo.exlibrisgroup.com/discovery/search?query=any%2Ccontains%2Ccomp0101&tab=Exampapers&search_scope=Exampapers&vid=44UCL_INST%3AUCL_VU2&offset=0)。老師說格式相近但內容每年不同，不能把練習當保證重出的題庫。

## 6. Sources

- [Moodle My courses](https://moodle.ucl.ac.uk/my/courses.php) → [COMP0101](https://moodle.ucl.ac.uk/course/view.php?id=56463) → [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384)。
- [Reading](https://moodle.ucl.ac.uk/mod/url/view.php?id=8513323)、[Foundations slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8513321)、[optional Fowler talk](https://moodle.ucl.ac.uk/mod/url/view.php?id=8513325)。
- [Lifecycle Quiz](https://moodle.ucl.ac.uk/mod/quiz/view.php?id=8513324) 與只讀 [completed attempt review](https://moodle.ucl.ac.uk/mod/quiz/review.php?attempt=6460314&cmid=8513324)；另有我提供的 Q1–Q5 screenshots。
- [RTC assignment](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8513326) 與已讀 `1. Foundations-RTC.docx`。
- [2026-10-09 Week 1 Reading and Exercises announcement](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1316380#p2355911)。
- [Asksia 原始課堂來源](https://app.asksia.ai/pro/session?id=32744d41-52e6-4ccd-847e-d63797c258a3)：`Recording_20261008_0800`／`Recording_20261008_1609`；已讀範圍與 ASR 限度見 [weekly notes](../README.md#11-sources-and-coverage)。

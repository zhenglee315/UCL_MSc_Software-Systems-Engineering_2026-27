# Week 1 — Introduction to Research Methods in Software Engineering

[English version](dict/README.md)

**Class:** 9 October 2026 · **Lecturer:** Emmanuel Letier · **Module:** COMP0108

本週把兩個主題連在一起：如何閱讀、判斷與溝通 Software Engineering research，以及如何把這些能力用在本學期的 assessments。以下以英文 technical terms 為主、繁中解釋為輔；內容依原始英文課堂 transcript 整理，再核對 Asksia summary 與 Moodle 官方資料。

## Sources and coverage

| Source | 本次覆蓋與用途 |
|---|---|
| [Asksia — Recording_20261009_1102](https://app.asksia.ai/pro/session?id=586f073f-f525-4973-b96b-4a2a0208a53e) | 順序讀取 Origin 欄的原始英文 transcript，從第一段 `0:28` 到教學末端 `107:11`，包含中途休息及最後可見段落；再用完整 summary 二次核對。時間戳是定位線索，並非校訂字幕。 |
| [Module Organisation](https://moodle.ucl.ac.uk/mod/resource/view.php?id=9433582) | 官方 `0. Course Organisation-2026.pptx`，32 slides；核對 learning outcomes、AI policy、reading strategy、MIP groups 及 assessment dates。 |
| [Software Engineering Research: Purpose, Practice and Areas](https://moodle.ucl.ac.uk/mod/resource/view.php?id=9437333) | Moodle 已確認 Week 1 講義入口與檔名 `1. Introduction-SE-Research.pptx`；本次附件無法下載，未讀取其 PPTX 本文。此部分的課堂內容依原始 transcript 整理，不提供未核對的 slide numbers。 |
| [Moodle course](https://moodle.ucl.ac.uk/course/view.php?id=56456) / [Lecture Slides](https://moodle.ucl.ac.uk/course/section.php?id=1519140) | 核對課程介紹及 Week 1 官方材料清單。 |
| [CW1 task and submission](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8834016) | 完整 DOCX brief 與線上 rubric 已讀；具體要求另見 [coursework notes](coursework/README.md)。 |

**Source limitations:** ASR 有缺句、錯字及人名誤聽；例如 `Google` 在課程操作語境中以官方 Moodle 頁面核對。播放器顯示 `110:27`，末尾卻出現 `122:59`、`123:10` 的零碎噪音，這些不當作教學內容。原稿大多只標同一 speaker，以下 Q&A 不推定學生身分、不把零碎文字補成逐字引言。查核日期：**12 October 2026**。

## Key takeaways

1. **Research methods are engineering skills.** 即使沒有 PhD 計畫，仍需評估 tools、practices 與 AI systems 的 claims；能寫出程式，不代表已證明它在實際情境有效。
2. **Critical, yet balanced evaluation** 包含找出證據的強弱、適用情境及限制，也包含辨認工作的實際貢獻。它不是只找缺點。
3. **Credibility and relevance are different questions.** 一個結果可以值得信任，卻不適用於自己的 project；也可能題目很相關，但證據薄弱。
4. **Quantity is not a substitute for knowledge.** 教授用 publication incentives 與近年的投稿量討論：更多 papers 不一定等於更扎實、可整合的 knowledge。
5. **Read for a purpose.** 先建立 bird’s-eye view，再理解方法與結果，必要時檢查每個 assumption；CW1 仍明確要求讀 assigned paper 全文。
6. **Own the reasoning and writing.** AI 可有 assistive role；提交的理解、論證與反思必須由本人形成，且要對每個字及來源負責。

## Why research methods matter

來源：transcript 約 `5:29–11:56`；Module Organisation slides **5–7**。

| Skill / learning outcome | 課堂要點 |
|---|---|
| **Critical thinking** | 分析工具與工程實務的宣稱，辨認 hype，問清楚支持宣稱的 evidence。 |
| **Empirical research methods** | 學習設計 experiments、收集並解釋資料。教授特別強調 AI-based systems 的開發與評估需要這些能力。 |
| **Working at the frontier of knowledge** | 許多問題尚無既定解法；需要處理 complexity、uncertainty、ambiguity，而不只是完成已定義好的 coding task。 |
| **Creativity** | 提出新 ideas，並設計能評估它們的方法；研究不只有批判與查錯。 |
| **Communication** | 在不同 abstraction levels 解釋論文，清楚說明 contribution、方法、問題及原因。 |
| **Research literacy** | 辨識 research areas、seminal problems、solution techniques；理解 conferences/journals 的 review 與 acceptance process。 |

教授把「理解需要創造什麼價值」及「實驗能否證明它有效」視為工程師日益重要的工作。這是本次課堂的觀點，不把它延伸為 coding 已不重要的普遍結論。

## Key concepts

### Normative and descriptive definitions

來源：transcript 約 `67:41–71:05`、`83:26–84:44`。

| Perspective | Software Engineering | Software Engineering Research |
|---|---|---|
| **Normative** | 描述工程應如何進行：systematic、disciplined、quantifiable 地開發、運作及維護軟體。 | 描述研究應如何進行：以 scientific inquiry 理解工程實務並探索改進方式，追求 honest、unbiased、evidence-based 的知識。 |
| **Descriptive** | 觀察 software engineers 在實際工作中做什麼、什麼方法實際可行。 | 觀察 researchers 實際如何做研究；實際 incentive、practice 可能與理想不同。 |

**Relationship:** 用 normative aspirations 檢查 descriptive practice，才能發現差距；教授認為健康的研究社群應持續反省這個差距。不能只因某項 practice 常見，就推論它是最好的 practice。

### Credibility and relevance

來源：transcript 約 `72:16–83:23`。

| Question | 需要追問什麼 |
|---|---|
| **Credibility — Can I trust this claim?** | 證據如何取得、如何量測、sample 是什麼、是否有其他 studies 支持、研究是否 well designed / well conducted。 |
| **Relevance — Does it apply here?** | 結果的情境與自己的系統、團隊、限制是否相近；能否合理移用。 |

課堂討論的 information sources 包含自己的 experiments / proof of concept、past project experience、books、A/B testing、senior developers、similar existing systems、university teaching、research papers、blogs/social media、vendor content。

教授提出一個通常的可信度差異：blogs、social media、vendor claims 往往較需警惕；well-conducted empirical studies 可以比個別 anecdotes 提供更扎實的證據；多個不同情境下的 replicated studies 可形成較有力的 systematic evidence。但他也明確提醒：**不是所有 empirical studies 都可信，不能只用來源類型決定品質。**

**整理補充 — 用課堂兩個維度做閱讀檢查：** 分別寫下「它為何可信」和「它為何適用」。這是筆記的整理方法，不是老師指定的作業欄位。

### Individual, professional and societal knowledge

來源：transcript 約 `80:44–83:23`。

```text
Personal experience + experiments + research evidence + professional discussion
                               ↓
               Decisions within a project or team
                               ↓
        Shared professional practice / bodies of knowledge / standards
                               ↓
        Society's expectations, accountability and regulation
```

Research 是這個關係中的一部分。工程方法是否合理不只影響團隊決策，也影響 society 對 professional engineers 的期待、事故後的責任判斷及 standards 的形成。課堂提及 privacy、AI 與 accessibility 等例子；這裡只記錄其研究與工程脈絡，不將課堂舉例當作法律規則說明。

### Knowledge areas, research areas and state of the art

來源：transcript 約 `98:45–105:56`。

| Term | 課堂區分 |
|---|---|
| **Knowledge areas** | 已建立的知識與今日常用 techniques，整理 **state of practice**。課堂以 Software Engineering Body of Knowledge 的分類作例子。 |
| **Research areas** | 尚未回答的問題、未解決 challenges，以及探索中的 techniques。 |
| **State of practice** | 工業界目前普遍使用、接受的做法。 |
| **State of the art** | 最先進的 techniques；可能尚未普及，也可能尚未充分理解其有效條件。 |
| **AI for Software Engineering** | 用 AI 支援 coding、testing、analysis 等工程活動。 |
| **Software Engineering for AI** | 研究如何開發、評估及維護 AI-based systems。 |
| **Software analytics / repository mining** | 從工程資料、repositories 等分析 practices 與問題。 |

教授在當次課堂的 ICSE 圖表討論中指出 AI for SE 的投稿與接受論文很多，testing/analysis 也一直是重要領域。這是 **該會議、該次圖表** 的觀察，不等於所有研究社群的排序，也不把它寫成永久不變的排名。

## Research quality and the publication numbers game

來源：transcript 約 `84:44–95:34`。

教授以 David L. Parnas 的 **Stop the Numbers Game**（2007）引出對 publication metrics 的批評。作者與年份另以 [Parnas 本人的 publication list](https://amadon.academia.edu/DavidParnas/CurriculumVitae) 核對；本文觀點的筆記依本次課堂轉述，未當作已閱讀文章全文。

課堂的主要論點是：當 hiring、promotion 等制度偏重 papers/citations 數量，容易鼓勵容易計數、較小、重複的研究成果，而較難的長期問題可能仍未解決。教授把這視為 **systemic incentive problem**，並沒有說每位 researcher 都不誠實。

教授接著討論 AI 可能加速 papers 的撰寫與 submission，但提出的問題是：這是否產生更多有用 knowledge，或只是更多 outputs？他也強調目前有大量分散 results，卻缺少把結果整合成 coherent knowledge 的 synthesis，並增加 reviewing 的負擔。

**整理補充 — 概念關係：**

```text
Publication incentives → researchers' choices → quantity and type of outputs
                                                   ↓
                      Evidence quality + synthesis + validation
                                                   ↓
                            Useful, transferable knowledge
```

這張關係圖是對課堂論點的整理，不是已證明的因果模型；它提醒閱讀時不要把 paper count、conference prestige 或 fluent writing 當作 evidence quality 的替代品。

## Core responsibilities of research

來源：transcript 約 `95:42–98:40`。

課堂把研究責任連成一個過程：**knowledge creation → validation → dissemination**。具體工作包括對 engineering practices 進行 empirical investigation、提出並評估 techniques/tools、建立解釋何者有效及為何有效的 theories、透過 peer review 及其他 critical/empirical evaluation 檢查 claims，再藉 papers、tools、education/training 等把知識傳到 industry、students 與 society。

教授提到學生與研究人員進入 industry 也是 research impact 的管道。不要只把 dissemination 理解成「發表一篇論文」，或把 validation 理解成「conference 已接受，所以結論完全可靠」。

## Reading a research paper

來源：transcript 約 `49:52–53:16`；Module Organisation slide **31**。原稿中 reading strategy 有缺句，因此步驟與時間以官方 slide 核對。

| Pass | Purpose and actions | 講義給的時間指引 |
|---|---|---|
| **Pass 1 — Bird’s-eye view** | 看 title、abstract、introduction、section headings、main figures、conclusions；判斷是否 relevant，初步辨識 paper 類型。 | 5–10 minutes |
| **Pass 2 — Grasp the content** | 仔細讀內容、study figures/graphs；暫時略過 proofs/fine detail，標出重要 references。適合理解 contribution 與如何達成。 | Up to an hour |
| **Pass 3 — Challenge every detail** | 跟著 method/argument 每一步，檢查 assumptions 及 claims 是否有 evidence 支持。適合深入 review 或直接在此工作上延伸。 | 4–5 hours；初學者可能更久 |

講義改編自 S. Keshav, **How to Read a Paper**（2007）。「按用途決定讀多深」不等於 CW1 可以只看 abstract；CW1 brief 明確要求 **full paper**。

### Seven elements and their relationships

來源：transcript 約 `46:31–50:28`；Module Organisation slide **30**；CW1 brief。

```text
Topic → Research question/problem → Prior work and gap → Novelty/contribution
                                                            ↓
                                                   Research method
                                                            ↓
                                                         Results
                                                            ↓
                                                    Claimed significance
```

這是一個讀懂與溝通 paper 的框架。**Problem** 是比 topic 更窄的問題；**gap** 是發表當時已有工作的不足；**novelty** 是新貢獻；**method** 是如何建立或檢驗貢獻；**results** 是具體發現；**claimed significance** 是作者在該篇 paper 中對意義的主張。

最容易混淆的組合是 gap/novelty、method/results、results/significance，以及原文的 claimed significance/十年後的 actual impact。CW1 的正式表格與字數要求見 [coursework README](coursework/README.md)。

## Instructor warnings and common mistakes

來源：transcript 約 `25:48–42:56`；Module Organisation slides **19–27**。

| Warning | 如何理解 |
|---|---|
| **Hallucinations and specious answers** | AI 可產生不存在的 papers/authors，或流暢但錯誤的答案；回到 source 核對，而不只問另一個 AI 是否同意。 |
| **Generic, superficial content** | 專家會注意是否具體、有 substance、是否真的理解 paper；語言流暢不等於內容正確。 |
| **Keep your own voice** | AI revision 不一定更清楚。教授提醒過度公式化、冗長、反覆 contrastive phrasing 會削弱真實表達。 |
| **Translation does not transfer responsibility** | 可謹慎翻譯自己的 draft，但要檢查 style、reasoning 和每個字；教授鼓勵盡可能直接用 English 思考與寫作。 |
| **Learning happens in the process** | 製作筆記、摘要及 review 本身就是學習；只取得 polished output 可能失去這個練習。 |
| **Assistive use has boundaries** | 本模組 assistive role 一般不要求 declaration，但不能把 AI 生成的 coursework 當自己的；class test/presentation 也有不同限制，須看各 brief。 |
| **No confidential material in external AI tools** | 教授以 unpublished work 等作例子。 |

**CW1 更具體的界線：**本人形成 structured summary 與 personal reflection；AI 可以改善 grammar/style，不能生成這兩部分。此檔是課堂學習筆記，沒有替 assigned MIP 撰寫摘要或反思。

## Actual in-class questions and discussion

以下為可辨識的實際課堂 exchanges，**問題與回答皆為轉述**。原稿無法可靠標出個別學生 speaker；不能把每句話歸到具名學生。

| Approx. time | Actual prompt / question | Recorded response or clarification |
|---|---|---|
| `44:03–44:45` | **Are Best Paper and Most Influential Paper awards the same?** 教授在說明 MIP 時問大家是否會是同一篇。 | 不必相同：Best Paper 在發表當時評選；MIP 約十年後回看對 theory/practice 的影響。 |
| `67:41–69:44` | **What is Software Engineering? How would you explain it to friends/family?** | 班上提出 development/maintenance、engineering applied to software、解決問題及有控制地交付產品等想法；教授說明 definitions 的多樣性，進而區分 normative/descriptive。 |
| `72:16–77:06` | **How do professional software engineers form opinions about what works? What are their information sources?** | 小組回報可辨識的項目有 proof of concept、books、A/B testing、senior developers、similar systems。教授再補上 experience/reflection、research papers、blogs/vendor content，帶入 credibility/relevance。 |
| `92:33–93:39` | 關於 publication metrics 中計數的是 **submitted or accepted papers** 的澄清。 | 教授澄清此處指 accepted papers，且 top conferences 的 prestige 影響很大；他也指出不同 institutions 的做法並非一致。 |
| `93:52–95:16` | 關於既然只計 accepted papers，為何增加 submissions 仍有誘因的討論。 | 教授談到 reviewing 的差異與不確定性、反覆取得 feedback 再修改，以及明顯不合格 submissions 可能 desk rejected；沒有說所有 accepted papers 都是碰運氣。 |
| `100:49–104:47` | **What are current research areas? Which areas are most popular in this conference?** | 班上提及 AI、benchmarks、security、analytics；教授用當次 ICSE 圖表說明 AI for SE 的大量研究，以及 testing/analysis 的重要性。 |

## Moodle alignment and assessment roadmap

Moodle General 強調 **close reading** 及 **critical, yet balanced analysis**。截至查核日，Week 1 官方清單有 Module Organisation 和 Research Purpose/Practice/Areas 兩份講義；Announcements 尚無公告。核心課後任務是開始閱讀 assigned MIP，並按 CW1 brief 個別準備。

以下為 Module Organisation slides **13–15、32** 的正式 outline；後續作業仍要讀各自發布的 brief，不由本週口述替代：

| Assessment | Published schedule | Weight | Relationship |
|---|---|---|---|
| **CW1 — Summary and Reflection** | 20 Oct 2026, 16:00 UK time | 10% | 個別讀 assigned MIP，建立 structured summary 與 reflection。 |
| **CW2 — 1 Paper Summary + 1 Paper Review** | 10 Nov 2026, 16:00 | 20% | 用其他 papers 練習相關 reading/review skills。 |
| **Practical 1 — Mock PC Meeting** | 20 Nov 2026, in class | 10% | 論文討論與參與受評量。 |
| **Practical 2 — Group Research Talk** | Slides + MCQ: 3 Dec 2026, 16:00; talks: 4 / 11 Dec | 20% | Agree group summary、trace MIP influence、give a talk。 |
| **In-Class Test** | 18 Dec 2026; Moodle activity previously confirmed 12:10–12:55 | 20% | MCQs，包括每組 talk 的一題；必須到場。 |
| **CW3 — Individual Report** | 7 Jan 2027；講義未列時間 | 20% | Critical analysis of one research line building on the MIP。 |

本模組 **沒有 end-of-year exam**，仍有 assessed coursework、in-class practicals 及 December test。若不能出席 in-class assessments，講義要求預先告知老師。[Moodle assessments](https://moodle.ucl.ac.uk/course/section.php?id=1379254)

**Optional opportunities:** 每隔一個星期三的 SSE research seminar 強烈建議參加，第一場講義列為 **21 Oct 2026, 13:00–14:00**；09:00 timetable entry 在講義中被指為錯誤。若想做 summer research project，Moodle 建議 **Term 1 結束前**聯絡 potential supervisors；這是長期規劃，不是 Week 1 必交檔案。[Research Project / Group Industrial Project](https://moodle.ucl.ac.uk/course/section.php?id=1379265)

### Corrections from the Asksia summary cross-check

| Summary simplification / mismatch | 本筆記採用的核對結果 |
|---|---|
| 把追蹤 citations 放入 CW1 task | 官方 CW1 是 seven-element summary + three reflections；citation tracing 放在後續 MIP impact/group-talk/report 脈絡，並非 CW1 多出的一項 submission。 |
| 把 CW2 概括成「研究方法演變分析」 | 官方 outline 為 **1 Paper Summary + 1 Paper Review**；研究脈絡演變另在 MIP 後續 activities 中討論。 |
| 把 assigned papers 與 Best Paper 混在一起 | 本次分配的是 **MIP award papers**；課堂區分了兩種獎的評選時間與目的。 |
| 把「七句」當絕對格式限制 | 口述與 slide 是 one sentence per element 的目標；完整 CW1 brief 允許偶爾多句，嚴格限制是 seven elements、每元素不超過100 words。 |

## Review prompts — additional study aid

以下是**整理者補充的自我檢查問題**，不是新增的教授題目、考試題庫或已完成 coursework answers：

- 同一個 software tool claim，如何分別檢查 credibility 和 relevance？
- 哪些 evidence 能支持「更快寫程式」？哪些 evidence 才能支持更廣的 engineering productivity claim？
- Normative aspiration 與 descriptive practice 出現落差時，研究可以怎樣幫助辨識問題？
- 如何分清一篇 paper 的 method、results、claimed significance，以及後續 actual impact？
- 如果文字很 polished，但沒有具體 evidence 或自己的 reasoning，為什麼仍可能品質低？

課後作業要求與分組資訊：**[Week 1 coursework README](coursework/README.md)**。

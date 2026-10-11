# COMP0101 — Week 1: Foundations of Requirements Engineering

[English version](dict/README.md)

本週將 **2026-10-08 上午與下午兩堂課**整合，主線是：從 stakeholders 在真實世界想達成的 goals 出發，劃定 machine boundary，分清 phenomena、requirements 和 assumptions，再檢查軟體做對規格是否足以解決問題。

[本週作業、閱讀與我的 Quiz 答案](coursework/README.md) · [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384)

## 1. Weekly Summary

**Requirements Engineering (RE)** 是貫穿 software lifecycle 的一組活動：discover、analyse、communicate stakeholder needs、context、desired externally visible software behaviours and qualities；同時處理 trade-offs 與 changes。它不只在開發初期發生，也不只是把客戶說的功能記成 user stories。

本週最重要的推理是 **`Req, Dom ⊢ Goals`**：若 machine 滿足 requirements，且 world 的 domain assumptions 成立，才能推導 stakeholder goals 被滿足。因此「code 符合 specification」並不保證「整個 system 成功」。Aircraft ground braking 與 London Ambulance Service 的課堂案例都說明：錯誤的環境假設足以讓符合規格的軟體造成 system failure。

老師強調 modelling 與精確溝通：描述使用者從外部看到的行為，辨認真實狀態和感測器資料的差別，明確分配各 actor 的責任。英文答題時，要能用具體情境解釋分類理由，而不只是背名詞。

**本週需自行補讀** Requirements in the Software Lifecycle 與 Wider Context。老師沒有在課上完整講完這些內容，Moodle 明確說 Chapters 5、6 **could be assessed**。以下以已讀的 Foundations slides 補足概念；這不代表已取得或讀過失效連結中的講義書全文。

## 2. Requirements Engineering 的工作範圍

| Key idea | 中文理解與實務意義 |
|---|---|
| Stakeholder needs | 人們對軟體如何影響生活、工作、業務的期待；stakeholders 超過付款的 client 和直接 users。 |
| Context | 系統運作的真實環境、既有流程、其他 actors、技術及限制。不了解 context，容易做出不成立的假設。 |
| Software requirements | 為了滿足 needs，在特定 context 下，軟體應有的**外部可見**行為與品質。 |
| Trade-offs | stakeholders 之間可能衝突；需求也可能超出技術、預算或時間能力，需要共同決定優先順序。 |
| Change management | needs、context、behaviour 都會變；需管理 versions 與 product-family variants。 |
| Lifecycle activities | RE 持續進行。Developers 在補足未寫明的行為時，也在作 requirements decisions。 |

**課堂例子**：產業中的需求可能出現在 PRD、user stories、email、PowerPoint、Word、DrawIO、Excel、API specification 或 microservice interaction diagrams。沒有單一文件模板能取代對需求的理解。

**老師的比喻：restaurant waiter vs medical doctor。** RE 需要追問問題及原因、理解真正目的、提出 alternatives 和 trade-offs，不能只照客戶的點單實作。課堂學生提到客戶要求自己訓練 LLM；應先問所需 business value，評估其他方案能否達到目的，再決定技術。

品質需求也需要 **testable criteria**。例如「fast」不足以驗證；應交代在什麼輸入、負載及環境下，哪個 response 必須在什麼時間內發生。這是課堂對 performance requirements 討論的學習整理。

## 3. World, Machine and Phenomena

### 3.1 先劃定 Machine boundary

- **Machine**：本開發團隊負責建立或改進的產品／software-to-be。
- **World**：與 machine 有關、受其影響的 application domain／environment／context。
- **Phenomenon**：可觀察的 **state** 或 **event**。例如「ambulance 位於某地」是 state，「ambulance 抵達現場」是 event。
- **Entity** 與 **property** 不等同 phenomenon。「an ambulance」是 entity；「response time must be less than 14 minutes」是限制 behaviours 的 property。

| Type | Definition | 問自己什麼 |
|---|---|---|
| World phenomenon (W) | World 中的狀態或事件；分類題以最具體種類回答，W 通常指不在 machine interface 的 world phenomenon。 | 這是外界真的發生的事，還是 machine 收到的資訊？ |
| Machine input (I) | Shared phenomenon controlled by the World。 | 是否發生在 machine boundary，且由外部 actor 控制？ |
| Machine output (O) | Shared phenomenon controlled by the Machine。 | 是否由 machine 控制，並對外部可見或送到外界？ |
| Internal machine phenomenon (M) | 在 machine 內部發生的狀態／事件。 | 是否只是內部 function、variable 或 computation，未跨越 boundary？ |

**關鍵區別：actual state ≠ information about that state。** Ambulance 的真實位置與 GPS 發給 CAD 的位置訊息是不同 phenomena；車可能在 tunnel 中，定位訊息可能缺失或錯誤。同理，**wheels turning** 與 **sensor signals that wheels are turning** 不可混為一談。

### 3.2 課堂 CAD 分類練習

以下以課堂 context diagram 的 **Computer Aided Dispatch (CAD) software** 為 machine；MDT、GPS、call handler 都在外部。這些是課堂討論的整理，不可把同一分類直接套用到另一個 boundary。

| Phenomenon | Type | Reason |
|---|---|---|
| An incident occurs. | W | 世界中的事故，未直接跨越 CAD interface。 |
| A person calls emergency services. | W | 在此 diagram，public 打給 call handler，CAD 沒有直接接收這通電話。 |
| A call handler encodes incident details into CAD. | I | 外部 actor 經 CAD interface 輸入。 |
| An ambulance is at Buckingham Palace. | W | 這是實際位置；GPS location update 才是另一個 input。 |
| An ambulance is available. | W | 真實 availability 不等於 paramedics 回報或 MDT 傳入的 availability。 |
| `findNearestAvailableAmbulance()` returns an ID internally. | M | 內部 method return；若改成畫面顯示 list，顯示事件才是 O。 |
| CAD sends mobilisation instructions to MDT. | O | 從 CAD 送往外部 component。 |
| Ambulance crew accepts mobilisation on MDT. | W | crew 與外部 MDT 互動；MDT 再向 CAD 發送接受訊息，才是 CAD 的 I。 |
| An ambulance arrives at the incident scene. | W | 真實世界的抵達事件。 |

老師在上午約 81–99 分鐘反覆提醒：**input/output 永遠相對於某個 actor／component／machine**。Context diagram 不只是畫圖練習；它能揭露責任歸屬和溝通誤解。

### 3.3 Actors vs Stakeholders

| Term | Meaning | 常見易錯點 |
|---|---|---|
| Actor | 能發起 event、改變 state 或執行 action 的 entity；可為 person、organisation、device、software。 | Machine 本身也是 actor；不是只有 users。 |
| Stakeholder | 對 machine 有利益關係、或受到它影響的人／群體。 | Non-human actors 不是 stakeholders；受影響但不操作系統的人也可能是 stakeholder。 |

例如 sensor 可以是 actor，但不是 stakeholder；safety regulator 可能是 stakeholder，是否在特定 model 中作為 actor 則要看它是否參與該系統的 actions。

## 4. Behaviours, Properties, Goals, Requirements and Assumptions

**Behaviour / scenario** 是 phenomena 隨時間發生的 sequence。**Behavioural property** 是對 behaviours 的 condition，將許多可能的情境判定為符合或不符合；不必逐一列出所有 scenarios。

| Property type | Definition | Example |
|---|---|---|
| Domain goal (G) | Desired property of the World。通常是 stakeholders 在乎的結果，可能需要多個 actors 合作。 | Ambulance arrives within 14 minutes after the first emergency call。 |
| Machine requirement (R) | Desired property of the Machine at its interface with the World。以 shared input/output phenomena 描述，由 machine 負責保證。 | Handler enters incident details → CAD displays nearest available ambulances based on its information。 |
| Domain assumption (D) | Assumed property of the World，可能是物理條件或其他 actors 的預期行為。 | GPS sends correct locations；call handler correctly enters incident details。 |

**分類方法（學習整理）**：先找 property 中的 phenomena，再定位它們是否跨 machine boundary，最後判斷這個敘述是在要求 machine 行為、期望世界結果，或假設外部 actor／環境會怎樣。不能單憑句子中有 `must`、`should` 或 `will` 分類。

**Goal identified ≠ goal necessarily satisfied。** 應先辨認 stakeholder goals，之後再處理衝突、範圍、責任和可行性；不是列入清單就全部保證達成。

### 4.1 Requirements correctness: `Req, Dom ⊢ Goals`

`⊢` 是 **logical deduction**：可從前提推導結論。

課堂簡化的 ground braking example：

```text
D1: MovingOnRunway → WheelsTurning
D2: WheelsTurning → WheelsPulseOn
R1: WheelsPulseOn → BrakingEnabled
--------------------------------------
G1: MovingOnRunway → BrakingEnabled
```

若 D1、D2 真的成立，而且 software 滿足 R1，便可推導 G1。但濕滑跑道上的 skidding 可讓 D1 不成立，因此這份 reasoning 並不能保證現實中的安全。

**Program correctness** 是相對於 requirements；**requirements correctness** 是相對於 domain goals，且必須有有效的 domain assumptions。不能省略 `Dom`。

在實務中，辨認 Goals、Dom、Req 是互相影響、反覆修正的活動。老師下午約 14–17 分鐘回答：通常可以從 goal 向下分解，但也會由已知技術／requirements 反推；不要求固定「先 goals 全寫完，再 assumptions，再 requirements」的順序。

**Goal modelling（本週 preview）**：將 parent goal 分成 subgoals，逐步找出 actor responsibilities、requirements 和 assumptions，用來組織 satisfaction argument。詳細方法是後續課程內容。

### 4.2 理論的限制

公式本身不完整處理：何時 requirements 已經 good enough、goal conflicts、alternative designs、partial goal satisfaction、uncertainty，以及 technology／budget／time constraints。

實務上關心的是「達成得多好」及「建錯系統的風險是否受到充分控制」。例如安全、隱私、可靠度往往有程度差異；目標也可能是特定比例的事件在 response threshold 內完成。

## 5. Requirements Errors and Failures

| Term | Definition / distinction |
|---|---|
| Failure | 產品在某個情境沒有按預期運作。 |
| Defect | 產品中的 flaw，可能導致 failure。 |
| Error | 人為 mistake，促成 defect。 |
| Machine failure | Machine 沒有滿足自己的 requirements。 |
| System failure | Machine 和周圍 world actors 未達成 essential stakeholder goal。 |
| Implementation error | Coding mistake：程式未按 developer 原先想實作的方式運作。 |
| Requirements error | 在 requirements 的 definition、communication 或 understanding 中出錯。 |

**Machine failure 不一定造成 system failure；system failure 也可以在沒有 machine failure 時發生。** 例如 software 完全按規格執行，但規格依賴錯誤 assumptions，無法達到安全目標。

Developers 正確實作自己「誤解後的需求」時，仍可能犯 **requirements error**。不能只因為問題是在寫 code 時發生，就稱為 implementation error。Vague／incomplete／hard-to-read requirements 也會誘發 misunderstanding 和缺陷。

`Req, Dom ⊢ Goals` 對應三類 requirements errors：

1. **Misunderstanding stakeholder goals**：G 沒有反映 essential、agreed stakeholder goals。
2. **Invalid domain assumptions**：D 的部分假設在現實不成立。
3. **Inadequate requirements due to incorrect reasoning**：即使 D 成立，R 仍不足以達成 G。

### 5.1 Aircraft ground braking — Warsaw, 1993

課件的安全目標有兩個：飛行中不可啟用 ground braking；落地後應能立即啟用。需要兼顧 human errors、sensor failures 及不同 landing scenarios。

課堂用簡化例子說明 **invalid domain assumption**：以「plane moving on runway implies wheels turning」作假設，遇到 wet runway／skidding 就可能失效。實際案例還涉及單側 landing gear 接地、shock absorber compression、輪速等資訊；投影片說 ground spoilers 與 reverse thrust 曾被延遲啟用。學習重點是 requirement-level reasoning，不把簡化式當作飛機完整安全規格。

**摘要核正**：Asksia 上午摘要將投影片中的兩個啟用條件寫成 `AND`。Slide 11 寫的是 **at least one** condition，也就是兩大條件間的 `OR`；每個條件內則要求兩個 main landing gears 都符合。應以原課件為準。

### 5.2 London Ambulance Service — 1992

課件描述新 CAD 依賴 GPS location、MDT status 和 crew behaviour。幾個不成立的 assumptions：

- GPS 一直提供正確、最新的位置：實際可能 inaccurate 或 missing。
- Crew 一定駕駛被 allocation 的 ambulance：實際可能換另一台車。
- Crew 一定正確且依序回報狀態：實際可能按錯按鈕、漏回報。

軟體把 imperfect information 當 perfect information，可能誤判 availability 或重複調派；即使按照設計運作，整體仍失敗。課件還列出 ambitious scope、impossible timeline、低價導向採購、忽略風險建議、一次完整部署、使用者參與不足，以及 testing／resilience 不足。不要將整個事件單一歸因成「程式 bug」。

## 6. Requirements in the Software Lifecycle — 自讀重點

以下主要核對 **Foundations slides 70–80**，也對應本週 Lifecycle Quiz。

| Topic | 必須會說的英文概念 | 中文理解 |
|---|---|---|
| Waterfall | Upfront detailed requirements; formal change requests | 假設初期 goals／assumptions／requirements 已清楚且開發期間不變，導致價值與驗證較晚，修改較昂貴。 |
| Agile | **Iterative + incremental** | Iterative 改善已做內容；incremental 增加新內容。仍有 initial vision and plan。 |
| RE in agile | Prioritisation; just-in-time testable requirements | 先選下一步最有價值的工作，在需要時分析並溝通可測試需求，透過交付學習與修正。 |
| Twin Peaks model | Requirements and architecture are developed together | Requirements 指引 architecture；architecture 揭露 costs、trade-offs、omissions 和 opportunities，兩者來回深化。 |
| V-Model | Tests and verification are with respect to requirements | 不同層次的 requirements 提供不同層次 testing 的依據。 |
| Ultimate quality criterion | Extent to which stakeholder goals are satisfied | Performance、few bugs、maintainability 等需回到目的與 context 評價。 |

**Book analogy**：adding a new chapter = Incremental；revising an existing chapter = Iterative。

**Agile assumptions**：必須能分成有用的小 increments；初期 iteration 的 business／safety／security risk 可以接受；customer collaboration 足夠；團隊具有 CI、automated testing、modularity、refactoring 等能力。不能回答成「不用計畫、隨便寫 code」。

**V-Model 學習配對**：stakeholder goals ↔ acceptance tests；machine requirements ↔ system tests；component requirements ↔ integration tests；unit requirements ↔ unit tests。Testing 的成功仍須考慮 requirements／assumptions 是否有效。

## 7. Requirements in the Wider Context — 自讀與課堂補充

核對 **slides 81–96**；下午約 73 分鐘以後簡介 commercial contexts，約 76 分鐘以後較集中討論 AI。

| Context | 對 RE 的影響 |
|---|---|
| Client project | 為特定 client 開發；tender、proposal、contract 和 change requests 影響 requirements。Fixed scope/price 與 time-and-materials 對變更有不同限制。 |
| Product development | 面向 market；product owner／backlog／stakeholder feedback 影響 priorities，較自然適用 iterative、incremental delivery。 |
| Greenfield | 從頭建立新 software。 |
| Brownfield | 修改或替換 existing system；更需理解 legacy constraints、周圍 systems 和既有流程。 |
| Regulated environment | 需要 comprehensive documentation，以及 regulations → requirements → code → tests → results 的 traceability。 |
| Social responsibility | 納入 safety、security、privacy、environmental sustainability、fairness，以及所有受影響人的利益。 |
| Wicked problem | 沒有唯一且人人同意的問題定義；不同群體對利益和傷害的看法不同，影響也難預測／衡量。 |

### 7.1 Requirements and AI

AI component 只是較大 system 的一部分，仍須先理解 stakeholder goals、expected business value、functional requirements 和 quality requirements。AI 的 uncertainty、non-determinism、opacity 讓 trade-offs、risk analysis、fairness、accountability、transparency 更重要。

**AI alignment problem**：objective function／reward 可能與真正 stakeholder goals 不一致。不能把某個 surrogate metric 的增加直接等同於成功。

**AI for RE** 可支援 requirements quality analysis、user feedback analysis、process mining 等；但 AI 生成外表完整的 PRD 不等於其 goals、assumptions 和 requirements 正確。這是老師的課堂判斷，而不是本筆記對工具效能的獨立實測。

### 7.2 Spec-Driven Development (SDD)

Asksia 把此詞誤聽成 speculative／spectral development；依 **slide 93** 核正為 **Spec-Driven Development**。

| Level | Meaning |
|---|---|
| Spec-first | Spec 指引 AI 完成一次 task，之後不持續維護。 |
| Spec-anchored | Spec 保留，隨 feature 演進持續更新。 |
| Spec-as-source | 只修改 spec，由工具產生 code，humans 不直接改 code。 |

老師認為這仍在 early days，尤其複雜行為很難只靠 natural language 精確表述。無論採何種工具，仍要分開 **Goals、Dom、Req、implementation constraints**，分析 potential missing requirements，檢查 `Req, Dom ⊢ Goals`，並尋找 assumptions 被破壞的 obstacles。Coding agents 使 good functional／quality requirements 和 acceptance tests 更重要。

## 8. 教授提醒的易錯點

| Common mistake | Better reasoning |
|---|---|
| 把 RE 當固定的第一階段 | 它在整個 lifecycle 持續發生，包括 developers 實作時的 gap filling。 |
| 把 client wish list 當完整需求 | 追問需要解決什麼、哪些 stakeholders 受影響、alternatives 和 trade-offs。 |
| 不先定義 boundary 就分類 input/output | 先說清楚 machine 是哪個 component。 |
| 把 real state 與 sensor/database message 混在一起 | 明列兩個 phenomena，辨認可能失真、延遲或缺失的情境。 |
| 把 function return 都當 output | 看是否跨越 machine interface；內部 return 可以只是 M。 |
| 只用 what vs how 分 requirements／implementation | 本週採更精確的 **where**：world-visible interface vs machine internals。 |
| 認為 software matches spec 就成功 | 檢查 goals 和 domain assumptions，區分 machine／system failures。 |
| 以為 unmarked = optional／不必練 | 每週練習要認真作答，部分接近／曾為考題。 |
| 看過 model answer 就認為自己會 | 先 genuine attempt，再比較、訂正；空白上傳會產生 false confidence。 |
| 把摘要的考試相關度標籤當老師意見 | Asksia 的自動評語不等於 syllabus／assessment instructions。 |

## 9. Actual Classroom Q&A

以下英文問題為**依實際對話整理的問法**，不是逐字引用；時間碼為 Asksia 回查位置。沒有將自行練習題冒充學生提問。

| Question | Answer / 中文理解 | Recording reference |
|---|---|---|
| How do we check whether a performance requirement is feasible? | 需要把 response target 和 conditions 說清楚，再考慮 technology、cost/time、alternatives，與 stakeholder 協調可行需求。 | AM，約 9–14 min |
| Are product variants the same as development versions or configurations? | 本課強調同時存在的 product-family variants；configuration 可實現 variants，但不等同所有開發分支。 | AM，約 46–51 min |
| Is the ambulance's real location an input? | 此 CAD boundary 下不是。Real location 是 W；AVLS 傳給 CAD 的 location message 才是 I。 | AM，81:54–83:57 |
| Why is a function returning an ambulance ID internal rather than input/output? | 課堂指 CAD 內部 function call/return。是否 input/output 取決於 boundary 和 external visibility，而不是「第一次知道某資訊」。 | AM，86:34–96:46 |
| Are inputs only given by actors? | Input 是 World-controlled shared phenomenon，可能由 person、device 或另一個 software actor 產生，不限人類操作。 | AM，92:03–93:24 |
| Is accepting a mobilisation on the MDT an input to CAD? | 是 MDT 的 input；對 CAD 而言，crew 操作 MDT 是 W，MDT 向 CAD 送訊息才是 I。 | AM，97:31–99:36 |
| Should we identify requirements or domain assumptions first? | 通常從 goals 向下分解，亦可 bottom-up；三者 concurrent／iterative，不是固定順序。 | PM，14:13–17:06 |
| Isn't the call handler's work a requirement? | 對 handler 可是工作要求，但在 CAD machine specification 中，預期 handler 輸入正確資訊是 D，CAD 不負責替他完成這個 action。 | PM，36:45–37:56 |

## 10. Exam Preparation

**老師直接說明**：COMP0101 成績 **100% 來自 three-hour written examination**；weekly exercises **not marked**，但很多題目 exam-like，部分曾是 exam questions。沒有證據支持「所有考題都從這些作業抽選」。AM 19:12、19:32、19:37 和 23:16–24:20 可回查。

**Optional 的範圍要分清楚**：Moodle 的 Martin Fowler talk 是 optional but highly recommended；RTC 的 temporal-logic subquestion 明確 optional，且不 assessed on formal specification。這與整份 RTC exercise 不計分是不同規則。Lifecycle 和 wider-context 必讀內容仍可能被考。

**我的複習題（不是歷屆原題）**：

1. Define Requirements Engineering and explain why it is not merely the first phase of development.
2. Given a machine boundary, classify W/I/O/M and justify each answer.
3. Distinguish domain goals, machine requirements and domain assumptions.
4. Explain `Req, Dom ⊢ Goals` with an example and an invalid-assumption counterexample.
5. Explain how system failure can occur without machine failure.
6. Classify a misunderstanding during coding as a requirements or implementation error, with reasons.
7. Explain iterative vs incremental, Twin Peaks, and requirements-based testing.
8. Explain how brownfield, regulation and AI affect RE.

**Past papers 在哪裡**：[Moodle General](https://moodle.ucl.ac.uk/course/view.php?id=56463) → Library links → **COMP0101 Past exam papers** → [UCL Library exam-paper search](https://ucl.primo.exlibrisgroup.com/discovery/search?query=any%2Ccontains%2Ccomp0101&tab=Exampapers&search_scope=Exampapers&vid=44UCL_INST%3AUCL_VU2&offset=0)。已核對入口，未將未讀的歷屆卷內容編入本筆記。

## 11. Sources and Coverage

| Source | 本次處理範圍 |
|---|---|
| [Asksia COMP0101 session](https://app.asksia.ai/pro/session?id=32744d41-52e6-4ccd-847e-d63797c258a3) — `Recording_20261008_0800` | 可見 Origin 英文逐字稿從開頭讀到最底；正式上午教學到約 100:19，之後多為離場／雜談。來源尾段時間碼到 107:30，但 player 標 103:32，故時間碼只供定位。 |
| 同一 session — `Recording_20261008_1609` | 可見 Origin 全部讀到最底 95:59；player 標 114:51。逐字稿開頭已在 properties 討論中，且有誤聽／缺句，不能聲稱已補回缺失 audio。 |
| Asksia existing summary / Sia Note | 二次核對；修正 AND/OR、wheels/wings 和 SDD 等錯譯。下午休息時間的 ID／age 雜談被摘要列成 exam trap，已排除，不作課程知識。 |
| [Foundations slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8513321) | 本機下載的 `1. Foundations.pptx`，101 張文字內容已讀，用來核對定義、案例和自讀章節主題。 |
| [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379384)、[10/9 announcement](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1316380#p2355911) | 核對必讀／optional、exam relevance、作業步驟與課前完成要求。 |
| [RTC assignment](https://moodle.ucl.ac.uk/mod/assign/view.php?id=8513326) | 題目 DOCX 已讀；未提交、未取得受提交條件限制的 solution sheet。 |
| [Lifecycle Quiz](https://moodle.ucl.ac.uk/mod/quiz/view.php?id=8513324) | 2026-10-12 只讀核對現有 Finished attempt，4/4，五題答案收錄在 coursework 文件。 |

Moodle 指向的 lecture-notes book 舊連結 `http://www0.cs.ucl.ac.uk/staff/E.Letier/book/` 本次無法開啟；仍保留 [Reading activity](https://moodle.ucl.ac.uk/mod/url/view.php?id=8513323) 供回查。未假裝讀過失效 book，也未用 slides 的 section titles 斷言該 book 每章原始標題。

核對日期：**2026-10-12，Europe/London**。中文為學習整理；英文 technical terms 和推理應能獨立表述。

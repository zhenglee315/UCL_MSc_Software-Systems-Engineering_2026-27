# UCL MSc Software Systems Engineering — 2026–2027

[English version — full index and notes](dict/README.md)

Personal weekly lecture notes, course summaries, and coursework explanations for the MSc Software Systems Engineering programme at UCL.

本專案以 **English technical terms、English questions** 為主，使用繁體中文解釋概念、整理課堂問答與作業步驟，方便準備英文考試。各科依 Moodle 的 teaching topic／Week 分組，再按 Asksia 錄音日期整合當週內容。

## Week 1 索引

本次整理涵蓋 2026-10-06 至 2026-10-09 的可取得課堂記錄，並核對 2026-10-12 可讀的 Moodle Week 1 資料。

| Module | Weekly notes | Coursework |
|---|---|---|
| COMP0101 — Requirements Engineering and Software Architecture | [繁中](Comp0101-Requirements%20Engineering%20and%20Software%20Architecture/Week1/README.md) · [English](Comp0101-Requirements%20Engineering%20and%20Software%20Architecture/Week1/dict/README.md) | [繁中](Comp0101-Requirements%20Engineering%20and%20Software%20Architecture/Week1/coursework/README.md) · [English](Comp0101-Requirements%20Engineering%20and%20Software%20Architecture/Week1/coursework/dict/README.md) |
| COMP0104 — Software Development Practice | [繁中](Comp0104-Software%20Development%20Practice/Week1/README.md) · [English](Comp0104-Software%20Development%20Practice/Week1/dict/README.md) | [繁中](Comp0104-Software%20Development%20Practice/Week1/coursework/README.md) · [English](Comp0104-Software%20Development%20Practice/Week1/coursework/dict/README.md) |
| COMP0108 — Research Methods in Software Engineering | [繁中](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/README.md) · [English](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/dict/README.md) | [繁中](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/coursework/README.md) · [English](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/coursework/dict/README.md) |
| COMP0235 — Engineering for Data Analysis 1 | [繁中](Comp0235-Data%20Engineering/Week1/README.md) · [English](Comp0235-Data%20Engineering/Week1/dict/README.md) | [繁中](Comp0235-Data%20Engineering/Week1/coursework/README.md) · [English](Comp0235-Data%20Engineering/Week1/coursework/dict/README.md) |

## 每週文件怎麼讀

- `Week1/README.md`：整週重點、Key Concepts、教授提醒的易錯點、課堂 Q&A，以及英文備考重點。
- `Week1/coursework/README.md`：作業／閱讀／練習內容、來源、期限、提交方式、計分規則，以及已提供的個人作答。
- 每份原 README 都有 `English version` 入口，完整英文版放在同層 `dict/README.md`；英文版可切回繁中，並連到英文課堂／coursework 文件。
- **課堂觀點／Moodle 要求**：可核對的來源內容；錄音中的時間碼用於回查。
- **理解補充／分析**：為了學習而加入的說明，不作為教授逐字原話。
- **My answer**：學生自己的作答，不自動等同於官方答案、已提交內容或已取得分數。

Asksia 的自動轉錄可能有誤聽、缺句或翻譯錯位。筆記先分析可取得的英文原始逐字稿，再以既有摘要、Moodle 投影片與作業說明交叉核對；不確定的內容會標明。來源課件以連結列出。

## 本次錄音與 Moodle 範圍

已由 [Moodle My courses](https://moodle.ucl.ac.uk/my/courses.php) 核對四個本學期課程的正式名稱，並逐科讀取 Week 1 活動要求、可取得課件及相關公告。`Comp0235-Data Engineering` 資料夾沿用既有名稱；Moodle 正式名稱是 **Engineering for Data Analysis 1**。

| Module | Asksia recordings included |
|---|---|
| COMP0101 | `Recording_20261008_0800`、`Recording_20261008_1609`，同週上午與下午合併整理 |
| COMP0104 | `Recording_20261006_1404` |
| COMP0108 | `Recording_20261009_1102` |
| COMP0235 | `Recording_20261007_1002` |

五份錄音均已逐段讀到可見英文原始 transcript 末端，再核對既有摘要。部分開頭、句子或音訊未被轉錄，少數尾段時間碼超過播放器長度；每科文件各自列出限度。Moodle 中另有 programme、support、careers 與 T2/3 project 頁，沒有對應本次 Week 1 課堂 transcript 的頁面不虛構授課筆記。

另核對 [Programme](https://moodle.ucl.ac.uk/course/view.php?id=60677)、[COMP0111 Group Project](https://moodle.ucl.ac.uk/course/view.php?id=60913)、[Individual Research Project](https://moodle.ucl.ac.uk/course/view.php?id=60916) 的可見 sections／announcements，未見 10/6–10/12 新發布的必交項目或本週截止。較長期的待辦是 **Term 1 結束前選定 project route**；想做 research project 者應及早了解資格並聯絡 supervisor。詳細規則見 [Summer Projects](https://moodle.ucl.ac.uk/course/section.php?id=1464650)；本次未讀三頁各 project handbook 全文，不由一般 summer submission 說明猜測精確期限。

## 本週建議完成順序

以下是依課前準備、截止日期與後續依賴安排的**學習建議**，不是新增的教師期限。全部時間採 **UK time / Europe/London**。

| Priority | Next action | Deadline / reason |
|---|---|---|
| 1 | 完成 **COMP0101** Chapters 1–6（尤其 5、6），RTC genuine attempt → Moodle upload → 看解答並訂正 | **10/15 上午課前**；建議 **10/14 下午**先交以留訂正時間。Lifecycle Quiz 已確認 **4/4，Finished**，不用把它列為未完成任務。 |
| 2 | 確認 **COMP0235** 能 SSH 進自己的 VM；完成 Unix forum 自己的 command topic + 對另一位同學的問題 | 課程後續依賴環境；10/6 公告要求立即核查 namespace。Week 1 活動未列精確交件期限。 |
| 3 | 開始 **COMP0108 CW1** 的 Group D assigned paper 全文閱讀，形成自己的 seven-element summary / three reflections，在 Week 2 後完成 | **10/20（二）16:00**，佔10%；需留時間閱讀。此 repo 只整理要求，未生成該篇 paper 的作業答案。 |
| 4 | 完成 **COMP0104** Lab 1 → SVN required reading → Lab 2A；補足 **COMP0235** required readings / Main 四組 Git 關卡 | 兩科練習未核到精確硬性截止；COMP0104 labs 不計分，仍用來鞏固操作與考試推理。 |

**另行處理**：COMP0104 的 Starting Experience and Expectations questionnaire 已於 **10/9 16:00** 關閉，查核時仍是 To do。如尚未交，需向 module team 詢問是否能補做。

**來源異常**：COMP0101 RTC 作業頁沿用 2025 年日期，故採用 2026-10-09 最新公告的課前要求；部分 Moodle 附件／lecture-notes book 無法正常取得，文件明示未讀部分並提供官方入口。Quiz 已讀現有 review；RTC、其他 labs／forums／CW1 均沒有由這次整理代交。

## 閱讀檔案與作答截圖

- **COMP0108 Group D**：[指定 ISSTA 2015 paper，13 頁](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/coursework/materials/Qi-et-al-2015-ISSTA-Patch-Plausibility-and-Correctness.pdf) · [老師提供的 CW1 Word 作業說明](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/coursework/materials/COMP0108-CW1-Summary-and-Reflection.docx)。我原有的 84 頁 MIT 碩論已在 [coursework 資料區](Comp0108-Research%20Methods%20in%20Software%20Engineering/Week1/coursework/README.md) 另標為相關補充，避免與指定 conference paper 混淆。
- **COMP0101**：已提交答案與 review 截圖收錄在 [coursework README](Comp0101-Requirements%20Engineering%20and%20Software%20Architecture/Week1/coursework/README.md)。

## 官方入口

- [UCL Moodle — My courses](https://moodle.ucl.ac.uk/my/courses.php)
- [COMP0101](https://moodle.ucl.ac.uk/course/view.php?id=56463)
- [COMP0104](https://moodle.ucl.ac.uk/course/view.php?id=56459)
- [COMP0108](https://moodle.ucl.ac.uk/course/view.php?id=56456)
- [COMP0235](https://moodle.ucl.ac.uk/course/view.php?id=56560)

## 更新記錄

- **2026-10-12**：整合五份原始課堂 transcript、四科 Moodle Week 1 資料，完成八份 weekly/coursework README 與根目錄索引；收錄 COMP0101 Lifecycle Quiz 五題作答，並核對現有提交成績 4/4。
- **2026-10-12**：四科新增完整英文版與語言切換連結；加入 COMP0108 閱讀檔案／Word 作業說明及 COMP0101 作答截圖。

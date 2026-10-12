# COMP0235 — Week 1 任務與閱讀紀錄

[English version](dict/README.md)

**Topic:** Course Welcome and Remedial Software Engineering Practice

**核查日期:** 2026-10-12，Europe/London

**學習筆記:** [上一層 README](../README.md)

本頁記錄 Moodle 公布的要求、完成方式與可見狀態。**沒有代寫 Unix 論壇答案、發布討論／回覆、做 Git 關卡、建立 VM 或提交作業。** 沒有本人答案時只整理題意及 checklist，不把學習示例當作本人的實作證據。

## Task overview — 先做什麼

| 建議順序 | 任務 | 官方要求／完成產物 | Deadline / 狀態 |
| --- | --- | --- | --- |
| 1 | **Environment and SSH** | 能使用 Unix terminal、確認自己的 Condenser namespace／image、建立或使用練習 VM、SSH 登入遠端 Linux。 | 10/6 公告要求立即核查 namespace；沒公布交件截止。本人環境未在本次代操作或驗證。 |
| 2 | **Unix Commands forum** | 新增一個 command 介紹 discussion topic，另到一位同學 topic 問一個問題。 | 本週活動；未見精確日期或時刻。2026-10-12 查核時沒找到本人 topic／reply。 |
| 3 | **Required reading** | 熟悉 PEP 8；讀 Research Software Engineering with Python 的 Chapter 2。 | 未公布提交要求或精確期限；是否本人已讀完不由 Moodle 勾選推定。 |
| 4 | **Learn Git Branching** | Main 四組指定關卡。 | 本週 exercise；未見精確期限；外部網站完成進度未核。 |
| 5 | **Remedial materials / in-class practice** | YAML、Python code、unit testing、Git/GitHub pair exercise，按 Moodle 編號閱讀。 | 沒找到獨立 Week 1 上傳作業入口／額外截止時間；不要把課堂活動自動解讀為已交件。 |

這是安排工作的建議順序，**不是教師公布的新增 deadline**。Moodle 說材料編號代表理想學習順序；查看要求入口仍以 [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270) 為準。

## 1. Environment and SSH — 環境檢查

來源：[Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269)、[Rancher/SSH MD](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523816)、[10/6 Condenser fixes](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710)、10/7 課堂 18:37。

- [ ] 找得到 Unix terminal；Mac 的 Terminal 可在 Applications → Utilities 開啟，Windows 依課程建議使用 WSL。
- [ ] 有合適 code editor；理解基本 shell navigation。
- [ ] 在校園或 UCL VPN 下能開 [Rancher](https://rancher.condenser.arc.ucl.ac.uk/) 與 [SSH 入口](https://ssh.condenser.arc.ucl.ac.uk/)。
- [ ] 在 **`sl-t01`** 看到並 activate 自己的 **`<UCL-ID>-comp0235-ns`**。
- [ ] 建立 VM 時能看到 AlmaLinux images；選自己的 network，不複製教師 namespace。
- [ ] 理解 public key、private key 和 signed certificate 的區別；按講義完成所需設定。
- [ ] 能成功登入自己的 VM；看得懂 prompt 的 user／host／working directory。
- [ ] 如果有跟做 Apache 示範，另核 [HTTP Hostnames 修正](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852) 中的 `ServerName localhost:80` 與 hostname 地址。

**Source conflict：** 舊 MD 的 `sl-p01` 和 `ds4eng-ns/ds4eng` 是示範值；10/6 更新公告與當週課堂確認學生用 `sl-t01` 及個人 namespace。教師說找不到 namespace 要立即聯絡他。確認／activate 的 [示範影片入口](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808) 可輔助；本次未播放影片。

可保留自己的非敏感證據：操作日期、使用哪個 image、成功登入的簡短說明與遇到的問題。**不在 repo 寫私鑰、certificate、token、密碼或完整個人連線配置。**

### 本人操作紀錄

尚未在本次核實本人操作結果。以下由本人完成後填寫：

| 項目 | 本人紀錄 |
| --- | --- |
| 日期／環境 | 待填 |
| VM／image 選擇 | 待填非敏感說明 |
| SSH 是否成功 | 待填 |
| 問題與解法 | 待填 |

## 2. Unix Commands — 明確要做兩件事

[官方論壇入口](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523826)

### A. Add a discussion topic

原始題意是：選一個 Unix 或相關系統的 command，使用 man pages、網路與適當文件研究；新增一個 Discussion Topic 向同學解釋。

自己的發文需包括：

1. **What does the command do?** 指令的用途。
2. **Why / when would you need it?** 實際使用情境。
3. **A short example.** 一個簡短使用例子，自己能解釋各參數與結果。

### B. Ask a question on another student's topic

到 **另一位同學** 的 topic，針對對方介紹的 command 問一個問題。不能只新增自己的介紹就當作全部完成。

### Verification and personal answer

2026-10-12 查核論壇共 **6 個 discussion topics**；topic starters 沒有 Wilson Lee。另核有回覆的 systemctl、grep、find 三串所有可見 reply authors，亦沒有本人。其他三串當時為 0 replies。

因此本次**沒有找到可收錄的本人答案**。不複製其他同學的介紹或代填本人發文；以下只記待辦：

- [ ] 選 command，先讀自己的實際系統版本 man page／官方文件。
- [ ] 用自己的練習檔案測試例子，能說明輸入與預期輸出。
- [ ] 本人完成 command topic 並保存 permalink。
- [ ] 閱讀另一位同學 topic，提出本人問題並保存 permalink。

| 本人紀錄 | 內容 |
| --- | --- |
| 選擇的 command | 待本人選擇 |
| 本人 topic permalink | 尚未找到 |
| 本人提問 permalink | 尚未找到 |
| 本人答案／反思 | 尚無可核對內容 |

**Deadline：** 本次可讀論壇要求與 Week 1 頁沒有列精確截止日期／時刻。Moodle 郵件中的同學 command 名稱是同一論壇練習的通知，不是每則郵件都新增一份作業。

## 3. Required reading — 讀什麼、在哪裡

### PEP 8 — Style Guide for Python Code

[Moodle PEP008 入口](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523822)／[Python 官方全文](https://peps.python.org/pep-0008/)

Moodle 寫 **REQUIRED READING: Familiarise yourself with the pep008 standard**。閱讀目標是能認出常見 style 規範並在程式中運用；本次沒有看到另需上傳閱讀心得。

- [ ] 看 code layout／indentation／line length。
- [ ] 看 imports、whitespace、comments/docstrings。
- [ ] 看 naming conventions 和 programming recommendations。
- [ ] 能說明 style、可讀性與正確性檢查的區別。

### Research Software Engineering with Python — Chapter 2

[Moodle reading 頁](https://moodle.ucl.ac.uk/mod/book/view.php?id=8523823)／[UCL Primo](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159)／[作者版第 2 章](https://third-bit.com/py-rse/bash-basics.html)

作者為 Damien Irving、Kate Hertweck、Luke Johnston、Joel Ostblom、Charlotte Wickham、Greg Wilson。正式書名是 **Research Software Engineering with Python**；Moodle 活動名稱寫作「in Python」，對應的要求是 **Read Chapter 2**。

**2026-10-12 閱讀整理：** [Chapter 2 課業要求、大綱、重點與心得草稿](reading/README.md) · [English version](reading/dict/README.md)。已依本機 PDF 完整書頁 13–44 與作者版整理；本人閱讀／實作狀態仍分開記錄。

第 2 章標題是 **The Basics of the Unix Shell**，依序讀：

1. **2.1–2.2 Exploring / moving around:** filesystem、current directory、absolute／relative paths。
2. **2.3–2.6 File operations:** 建立、移動、複製、刪除。
3. **2.7–2.8 Wildcards / manual:** 用 patterns 選檔與查指令說明。
4. **2.9–2.11 Summary / exercises / key points:** 檢查自己能否預測命令效果。

- [ ] 讀完 Chapter 2。
- [ ] 能說明 `pwd`、`cd`、`.`、`..`、`~`。
- [ ] 能說明 `cp`／`mv` 差異，理解 wildcard 選到哪些檔案。
- [ ] 自己練習不理解的操作；不要在重要資料上試刪除命令。

本次 Moodle book 頁顯示 **No content has been added to this book yet**，但有 Primo 說明連結。作者版可供閱讀。Moodle 未明確要求交整章 exercise answers；本頁不代做章末題目。

### Optional reference

[Unix in a Nutshell](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523819) 在 Moodle 是 **Extra reading**，需要時當 reference 使用。

## 4. Learn Git Branching — 指定四組

[Moodle 任務入口](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523825)

完成 **Main** 的：

- [ ] **Introduction Sequence**
- [ ] **Ramping Up**
- [ ] **Moving Work Around**
- [ ] **A mixed bag**

Moodle 說可以 optionally 完成全部 exercises；沒有把全部關卡列成必做。外部網站的本人進度未核查，因此不勾選完成。建議自己記下容易混淆的關卡概念與完成日期；不用把 AI 給的解法當作本人完成證據。

**Deadline／交法：** Week 1 稱 exercise for this week，但本次沒看到精確截止或要求上傳 screenshot 的文字；不要自行新增必交 screenshot 規定。

## 5. In-class / remedial practice — 區別課堂活動與正式交件

來源：[Remedial Software Engineering ODP](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523817) 及 [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270)。

| 主題 | 可確認的課件要求／活動 | 本人答案 |
| --- | --- | --- |
| **YAML intro** | Moodle 提供短 MD；閱讀配置資料的基本結構。原檔本次未取得。 | 尚無紀錄 |
| **Good Python code** | PEP 8、Pythonic code，以及 good code 的課堂討論。 | 不編造討論結論 |
| **Unit testing** | ODP 要先寫 function 的 unit test，再 implement function；沒有可讀的具體 function 題目。 | 不代寫未知題目 |
| **GitHub pair exercise** | Person 1 建 repo／加 working code 到 main；Person 2 改 code／提出 PR；Person 1 檢查並 approve。 | 尚無本人 pair exercise 證據 |
| **Refactoring** | ODP 列為後續軟體工程主題。 | 尚無獨立題目／交件要求 |

不要把原稿無法辨認的後段 commands 補成「老師規定必跑」。本次也沒有找到以上項目另外的 Week 1 submission portal 或精確 deadline。

## Completion record — 完成後再更新

| 日期 | 完成項目 | 自己的證據或來源連結 | 仍不清楚的地方 |
| --- | --- | --- | --- |
| 2026-10-12 | Chapter 2 閱讀筆記與心得草稿已整理 | [Reading README](reading/README.md)；AI 協助整理，非本人實作完成證據 | 本人核對心得、練習尚不熟悉的指令 |

Moodle 的 **Mark as done／completion** 只表示平台追蹤條件或勾選狀態，不能單獨證明離線閱讀、外部 Git 關卡或 VM 操作已完成。本次整理沒有手動按 Mark as done。

## Help and sources

- [Module Communication](https://moodle.ucl.ac.uk/course/section.php?id=1381264)：一般 module 問題使用 [Ask a Question forum](https://moodle.ucl.ac.uk/mod/hsuforum/view.php?id=8523791)；個人／accessibility 問題直接聯絡教師。找不到 namespace 的情況依 10/6 公告聯絡 Daniel Buchan。
- [Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270)／[Announcements](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523790)
- [Unix Commands exercise](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8523826)／[Git Branching exercise](https://moodle.ucl.ac.uk/mod/url/view.php?id=8523825)
- [Asksia 課堂原文](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43)
- [PEP 8](https://peps.python.org/pep-0008/)／[Irving et al. Chapter 2](https://third-bit.com/py-rse/bash-basics.html)

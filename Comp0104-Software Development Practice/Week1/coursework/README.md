# COMP0104 Week 1 — Coursework and Practice Checklist

[English version](dict/README.md)

> 核對：2026-10-12（Europe/London）。本頁整理官方題目要求與本人可見狀態，不是已完成的 Lab 答案。課堂概念見 [Week 1 notes](../README.md)。

## What needs doing, and when?

| Item | What to do | Deadline / grading | Visible personal status |
|---|---|---|---|
| [Starting Experience and Expectations](https://moodle.ucl.ac.uk/mod/questionnaire/view.php?id=8512795) | 匿名填寫 prior tools / coursework / personal projects / work experience、interests / expectations；可答 none / not sure。 | **Friday 2026-10-09 16:00 UK**；非 test。Moodle completion 要求 submitted questionnaire。 | 目前顯示 **Closed** 和 **To do: Student must submit this questionnaire to complete it**。沒有可讀的本人答案；未代填。 |
| [Lab 1 — Preparations](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512843) | 完成 Exercises 0–5：diff、patch、diff3、AI 或 supplied-response evaluation。 | [Labs page](https://moodle.ucl.ac.uk/course/section.php?id=1379312) 明列 **not assessed**。PDF 建議在 online lab support 前先嘗試，之後繼續；未列硬性日期／鐘點或 upload deadline。 | Week 1 的 manual completion 按鈕仍未標示 done；這不能證明本人完全沒做過。repo 尚無可讀的 Lab 實作／反思。 |
| [Lab 2A — Subversion](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512848) | 完成 Setup、Exercises 1–9：GNU Hello / SVN changes、patch、history、rename、build repair。 | **Not assessed**；建議先嘗試整份，再在 support session 問問題。未找到交件截止日／上傳入口。 | 同上；未執行命令、未替本人 commit exercise results。 |
| [Required Reading](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512850) | 讀 *Version Control with Subversion* **Preface、Chapter 1、Chapter 2**。 | Week 1 明標 **Required Reading**，無具體日期／鐘點；不能因不計分就改寫成 optional。 | Moodle manual completion 尚未標示 done；本筆記已分析閱讀內容，但不代表使用者本人已讀完。 |

問卷 deadline 已過且平台已關閉；如本人沒有提交，需向 module team 查詢是否可補做。這裡沒有代寄訊息、代答或修改 completion。

## Lab 1 — Preparations

**Primary source：** [official Lab Sheet](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512843)，6 頁。要求做完整 worksheet；可用自己的電腦或 [departmental Linux environment](https://moodle.ucl.ac.uk/course/section.php?id=1379312)。

### Part I: Command-Line Tools

| Exercise | Required work | Evidence to retain / check |
|---|---|---|
| **0 — Questionnaire** | 尚未填的人先完成 Moodle 起始問卷；目前已 closed，見上表。 | 真實 submission 狀態；不把點入頁面當作已交。 |
| **1 — DIFF** | 建立 `lab01` 工作目錄及 worksheet 指定的 `be`、`ae` 兩份文字；比較 `diff be ae` 與反方向；再比較 normal、`-c`、`-u`、`-y` formats，讀 `man diff`。 | 兩個方向的輸出與各格式差異；在 diff 後立即用 `echo $?` 查 exit status。 |
| **2 — PATCH** | 將 `be → ae` 的 diff 存成 `DIFFS`；以 `patch --verbose --backup be < DIFFS` 套用；用 diff 檢查結果。 | `DIFFS`、修改後檔案及 backup；確認比較結果，不能只看 patch 沒有報錯。 |
| **3 — DIFF3** | 還原 `be`；複製成 `be2`，將 `approximately` 改成 `around`，以 `diff3 -m be2 be ae` 測試 automatic merge；存成 `merged` 並檢查。再從原始 `be` 複製成 `be3`，將 `the most` 改成 `some of the most`，觀察與 `ae` 合併時的 conflict markers。 | 非衝突 merged text 應同時保留兩邊的修改；保留衝突輸出、exit status、參數順序，確認 input files 沒被 `-m` 自動改寫。 |

**Exit-status traps（官方 PDF）：**

- `diff`：0 = identical，1 = differences found，2 = error。1 本身不是執行失敗。
- `diff3 -m`：0 = no conflicts，1 = conflicts found，2 = error。1 的輸出可能包含 conflict markers，仍需 resolution。
- 不同 lines 的修改若相鄰，也可能 conflict；要看工具實際輸出。

### Part II: Using AI Tools

可使用自己的 AI tool，或評估 PDF 第 6 頁的 **Supplied Responses for Evaluation**。不使用 AI 不免除 command-line、manual-resolution 與 reflection tasks。Supplied responses 是待評估材料，**不是 model answers**。

| Exercise | Required work | Evidence / reflection |
|---|---|---|
| **4 — AI for Understanding and Summarising Changes** | 產生 `diff -u be ae`；請 AI 解釋逐行 diff 及產生簡短 imperative commit message，或評估 supplied explanation/message。 | 保留 unified diff、評估過的 explanation、commit message、需要的 corrections；寫短段落分析準確度、易懂程度，以及 message 是否 concise / conventional。 |
| **5 — AI for Resolving Merge Conflicts** | 先用 `diff3 -m be3 be ae` 重現 conflict；**先自己解決**並儲存 `merged-manual`，之後才看 AI 或 supplied response。 | 保留 `merged-manual`、待評估 proposed merge、corrections。依 worksheet 核對保留 `ae` 的 American spellings、`be3` 的 `some of the most`、`ae` 的 currency note，且無 conflict markers；比較兩種 resolution 的 intent 與差異，說明是否會不經人工核對就信任輸出。 |

記錄所用 tool，或註明使用 supplied responses。每題 reflection 要用實際輸出作證據；保留檔案及 notes 供 online lab support discussion。本 repo 未找到可讀的個人作答，故不填寫「我觀察到……」或完成反思。

## Lab 2A — Subversion

**Primary source：** [official Lab Sheet](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8512848)，6 頁。需要 `svn`、`svnadmin`、`wget`、`tar`、`patch`、`make` 和 C compiler；worksheet 使用 **GNU Hello 2.12.1**。Lab 延續 Lab 1 的 command-line / patch 技能。

### Setup

1. 在練習環境建立 **repository** `svnrepos/helloworld`，並另外建立 **workspace** `lab02a`；兩者不能混為同一個資料夾。
2. Checkout empty repository，建立／add／commit `trunk`。
3. 依 worksheet 從 GNU archive 取得 Hello 2.12.1，保留 tarball，解壓到 trunk。
4. 用 `svn status` 看 untracked entries，再 `svn add` 並 commit 初始來源；確認 clean status。

已做過的人應換新 repository / workspace 名稱並一致修改 worksheet 路徑。示範 revision 1、2、3……只適用全新 repository；不要盲用固定 revision numbers。

### Exercises 1–9

| Exercise | Required work | What to verify / keep |
|---|---|---|
| **1 — Compile and Modify** | 執行 `./configure`、`make`、`LC_ALL=C ./hello`；依 worksheet 將 greeting 改成德文，再 build / run。 | Source change、實際 compile / run output；`LC_ALL=C` 用來固定此命令的語言環境。 |
| **2 — See Changes** | `svn status`；`svn diff src/hello.c` 比較 working file 與 checked-out base。 | `M` 與 diff 所顯示的修改；build outputs 可能是 `?`，此 Lab **不要 add** generated outputs。 |
| **3 — Commit Changes** | 只 commit 指定 source change，附有意義的 message；之後再檢查 diff。 | commit revision / log；plain `svn diff` 應不再顯示已提交的本機改動。 |
| **4 — Create a Patch** | 用 `svn log` 找原始／德文的實際 revisions；以 `svn diff -r OLD:NEW src/hello.c` 建立 patch，放在 working copy 外。另解壓乾淨 tarball，在 source-tree root 以 `patch -p0` 測試，再 build / run。 | patch、test copy 和輸出；再套用同一 patch 時觀察提示，依 worksheet 不 reverse／不強行套用，解釋為何不能直接重複套用。 |
| **5 — More Modifications** | 將 greeting 改成法文；build / run、diff、commit、log。 | French revision 及 diff/log 證據。 |
| **6 — Navigate History** | 依 log 確認 English / German / French revisions；對 source file 使用 `svn update -r` 逐一取回，必要時 rebuild；最後 update 到 latest。 | 舊 working revision 不是新的本機 edit，亦沒有 undo repository commits；確認最後 source 是最新法文版本。 |
| **7 — Rename Files** | 以 `svn move src/hello.c src/hallo.c` rename；看 status 後 commit。 | 舊 path scheduled delete、新 path add-with-history (`A +`)；rename 不會自動修正 build-system references。 |
| **8 — Investigate History** | 查 renamed file 的 `svn log`，找原名時的 commits；用 revision range diff 檢查 English-to-German change。 | 解釋比較兩個 repository revisions 與 working file/base 的差別；保留 log/diff，使用自己的 revision numbers。 |
| **9 — AI Task: Diagnose and Repair the Build** | Run `make` 並記錄 rename 後的錯誤；查 root generated `Makefile`、root `Makefile.am` 的 `hello_SOURCES` 及 `Makefile.in`。可用 AI 解釋，也可自己根據 evidence 分析。依 worksheet 恢復原 build system 預期的 filename，使用 `svn move` 保留 history；保留法文 greeting 和現有 build files。 | Review status/diff，build / run 確認成功，再 commit repair；`svn log` 應保留 translations 與兩次 rename 的歷史。 |

### Exercise 9 reflection and final checkpoint

Reflection 需根據自己的觀察回答：什麼 evidence 找到 failure cause？AI 解釋是否符合實際檔案？為何只改 generated Makefile 可能只是暫時修復？為何 plain SVN commit 不會保存 untracked Makefile？Compilation、running、history inspection 各驗證什麼？

最終 checkpoint：working copy 可成功 build，修好的 source 沒有 uncommitted changes；untracked build outputs 可保留。保留 repository、working copy、archive、patch 供參考。這是 worksheet 所述目標，不是本人已達成的結果。

## Required Reading and extra material

- **Required:** [Version Control with Subversion](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512850)，Preface + Chapters 1–2。重點對照：repository vs working copy、atomic/global revisions、copy-modify-merge、four file states、status/diff/commit/update、history / rename。
- **Extra, not required for the module:** [Miller and Myers — A file comparison program](https://moodle.ucl.ac.uk/mod/lti/view.php?id=9428318)、[SVN for Java Developers](https://moodle.ucl.ac.uk/mod/url/view.php?id=8512852)。

## Submission, marks and questions

- 本週兩份 Lab **不計分**，未看到指定 upload / submission deadline；PDF 建議先在 support session 前嘗試、之後繼續，不能自行換算成某個硬性星期或鐘點。
- [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1379313) 的 **Mark as done** 是 manual completion；點過資源或閱讀本筆記都不等於本人已完成 Lab。
- 起始問卷是另外一項有明確截止、以 submission 計 completion 的活動；不把它當作 assessed coursework。
- [Announcements](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8512798) 核對時尚無公告，沒有另找到本週 deadline。
- Worksheet 問題可在 [Questions on the Labs](https://moodle.ucl.ac.uk/mod/forum/view.php?id=8512836) 提問。此整理沒有代發文或提交任何內容。
- 本頁所有 unchecked / 未記錄狀態表示 **沒有足夠可讀證據**，不是斷言使用者從未做過。後續只有在看得到個人 command outputs / answers 時，才補上完成記錄與個人反思。

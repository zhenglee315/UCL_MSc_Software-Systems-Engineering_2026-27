# COMP0235 Week 1 Reading — Research Software Engineering with Python

[English version](dict/README.md) · [Week 1 coursework](../README.md) · [Week 1 學習筆記](../../README.md)

**指定章節：** Chapter 2 — *The Basics of the Unix Shell*

**書名：** *Research Software Engineering with Python: Building software that makes research possible*

**作者：** Damien Irving、Kate Hertweck、Luke Johnston、Joel Ostblom、Charlotte Wickham、Greg Wilson

**出版：** CRC Press / Taylor & Francis，2021

**整理日期：** 2026-10-12，Europe/London

本頁依本機 PDF 的完整 Chapter 2 整理，涵蓋**書頁 13–44（PDF 第 28–59 頁）**、Figures 2.1–2.5、17 題章末練習與 Key Points，並核對[作者公開版全文](https://third-bit.com/py-rse/bash-basics.html)。以下大綱與重點是改寫後的閱讀筆記；心得是 AI 協助撰寫、供本人核對修改的第一人稱草稿。

## 1. 課業要求與來源

![Moodle Week 1 指定閱讀：REQUIRED READING: Read Chapter 2](materials/week1-reading-requirement.png)

上圖為本次提供的課程要求截圖，保留在本頁資料夾供回查。

| 項目 | 可確認的內容 | 依據 |
| --- | --- | --- |
| 課程／週次 | COMP0235 — Engineering for Data Analysis 1，Week 1 | [既有 coursework 紀錄](../README.md)；資料夾沿用 Data Engineering 名稱 |
| 閱讀資源 | Moodle 活動名稱為 **READING: Research Software Engineering in Python, Irving et al**；正式書名使用 **with Python** | 本次提供的 Moodle 截圖及既有閱讀紀錄 |
| 教師明確要求 | **REQUIRED READING: Read Chapter 2** | 本次提供的 Moodle 截圖 |
| 指定入口 | UCL Primo 電子書連結 | [UCL Library permalink](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159) |
| 截止、字數、交法、評分 | 截圖未列出這些資訊；既有 coursework 紀錄亦未查到此閱讀的精確期限或獨立上傳要求 | 不從閱讀活動名稱推定額外規則 |
| 本次另外整理的產物 | Chapter 2 大綱、重點、指令速查、練習主題與心得，存入 `coursework/reading/README.md` 並提交至 GitHub | 本次使用者要求 |

**要求的區別：** 讀 Chapter 2 是截圖中的課程要求。書內請讀者跟做範例、完成練習，是作者的學習安排；目前提供的課程資訊沒有明確要求提交全部 17 題答案。大綱和心得是本次要求新增的學習紀錄。截圖中的 **Mark as done** 是平台完成狀態按鈕，本頁不把它當成作業提交或本人已掌握內容的證據。

## 2. 整章大綱

本章先解釋 CLI 與 shell 的用途，再建立「知道自己在哪裡 → 找到資料 → 操作檔案 → 一次選取多個檔案 → 查閱指令說明」的基本工作流程。[Chapter 2](https://third-bit.com/py-rse/bash-basics.html)

| 章節 | 主題 | 應抓住的重點 |
| --- | --- | --- |
| Introduction | GUI、CLI、REPL、shell | Shell 讀取命令並執行程式；CLI 的文字操作便於記錄與自動化。 |
| 2.1 Exploring Files and Directories | 探索檔案與目錄 | `whoami`、`pwd`、`ls`；理解 filesystem、root、home、options 和 arguments。 |
| 2.2 Moving Around | 在目錄間移動 | `cd`；absolute／relative paths；`.`、`..`、`~`、`cd -`；隱藏檔案。 |
| 2.3 Creating New Files and Directories | 建立目錄與文字檔 | `mkdir`、Nano；命名與 quoting；副檔名只是格式慣例。 |
| 2.4 Moving Files and Directories | 移動與改名 | `mv source destination`；目的地可為新檔名或目錄；注意覆寫。 |
| 2.5 Copying Files and Directories | 複製 | `cp` 保留來源；`cp -r` 複製目錄及內容；提及遠端傳檔的 `scp`。 |
| 2.6 Deleting Files and Directories | 刪除 | `rm`、`rm -r`、`-i`、`-v`；通常沒有垃圾桶復原機制。 |
| 2.7 Wildcards | 用 pattern 選取檔案 | Shell 先展開 wildcard，才執行指令；`*` 與 `wc` 的批次使用。 |
| 2.8 Reading the Manual | 查閱文件 | `man`、`less`、部分程式的 `--help`、TLDR；了解 `wc` 的選項。 |
| 2.9 Summary | 串接後續學習 | 後續 Chapter 3 再介紹組合、重複指令與 workflows。 |
| 2.10 Exercises | 17 題練習 | 預測路徑、選項、移動／複製結果及 wildcard 選取範圍。 |
| 2.11 Key Points | 概念回顧 | 確認能解釋指令與 filesystem 的共同規則。 |

## 3. 閱讀重點

### 3.1 Shell 是執行程式的介面

Shell 接收文字命令，透過 **read → evaluate → print → loop** 的方式與使用者互動。它能執行不同語言寫成的程式，因此也是日後從命令列執行 Python 分析的基礎。Bash 與 zsh 都是 shell；書中 `$`、`%` 表示 prompt，不是要一起輸入的指令。[章節開頭與 2.1](https://third-bit.com/py-rse/bash-basics.html#bash-basics-explore)

**理解補充：** 命令可以保存、重跑，但只有 command history 還不足以保證研究可重現；仍需記錄資料、執行順序、working directory 與環境。這是從本章推導出的研究工作習慣。

### 3.2 Working directory 決定 relative path 的意思

Filesystem 由檔案與可巢狀的目錄形成 directory tree。`pwd` 告訴我們目前位置，`ls` 查看內容，`cd` 改變 shell 的 current working directory；`ls data` 本身不會進入 `data`。[2.1–2.2](https://third-bit.com/py-rse/bash-basics.html#bash-basics-navigate)

| 寫法 | 意義 | 例子 |
| --- | --- | --- |
| `/` | 整個 filesystem 的 root | `cd /` |
| Absolute path | 從 root 開始的路徑 | `/Users/amira/zipf/data` |
| Relative path | 從 current working directory 開始的路徑 | `data`、`../docs` |
| `.` | 目前目錄 | `mv data/draft.txt .` |
| `..` | 上一層目錄 | `cd ..`、`cd ../..` |
| `~` | Shell 展開的 home directory 簡寫 | `cd ~`、`ls ~/Downloads` |
| `cd` | 沒有路徑參數時回到 home | `cd` |
| `cd -` | 回到上一個 working directory | `-` 在這裡是 `cd` 的特殊用法 |

若目前位於 `/Users/amira/zipf/docs`，`../data` 指向 `/Users/amira/zipf/data`；`data` 則指向 `docs` 下的 `data`。同一段 relative path 換了起點，結果就可能不同。

`.`、`..` 的路徑意義能用在不同指令中，書中稱這種規則一致性為 **orthogonality**。以 `.` 開頭的設定檔通常不會出現在一般 `ls` 結果中，`ls -a` 可顯示它們。

### 3.3 空格、選項與檔名需要分清楚

一般命令可用 **command + options + arguments** 理解，例如 `ls -F data`：`ls` 是指令，`-F` 控制顯示方式，`data` 是要處理的目錄。`ls-F` 會被當成另一個程式名稱。為了減少不同系統的差異，依書中建議把 options 放在檔案／目錄 arguments 前面。[2.1 與 2.3](https://third-bit.com/py-rse/bash-basics.html#bash-basics-filedir)

新檔名宜清楚、簡單，避免空格、特殊符號及開頭的 `-`；遇到既有的空格路徑則加引號，例如：

```sh
ls -F "Comp0235-Data Engineering/Week1/coursework"
```

副檔名幫助人和程式辨識格式，但把 `.png` 改成 `.txt` 並不會把圖片轉成文字。Nano 操作純文字；`Ctrl+O` 儲存、Enter 確認檔名、`Ctrl+X` 離開。

### 3.4 Move、copy、delete 造成不同結果

`mv` 改變位置或名稱，`cp` 建立副本並保留來源，`rm` 刪除檔案。`mv`、`cp` 的第一個 argument 是來源，最後一個是目的地；若有多個來源，目的地必須是目錄。`cp -r` 會連目錄內的內容一起複製，並非只建立空的資料夾結構。[2.4–2.6 與 2.10.11–2.10.14](https://third-bit.com/py-rse/bash-basics.html#bash-basics-move)

移動／複製可能覆寫目的地檔案，`-i` 用於互動確認；`-v` 只回報操作，不能阻止刪錯。`rm -r` 遞迴刪除目錄與內容，通常不經垃圾桶。練習時應先確認 `pwd` 與選到的檔案，再操作可丟棄的副本。

### 3.5 Wildcard 先由 shell 展開

`wc data/*.txt` 的流程是 shell 先把 `data/*.txt` 展開成符合的檔名清單，再將清單交給 `wc`；這不是 `wc` 自己去理解 `*`。因此相同 pattern 可以交給不同程式使用。[2.7、2.10.15、2.10.17](https://third-bit.com/py-rse/bash-basics.html#bash-basics-wildcard)

| Pattern | 選取規則 |
| --- | --- |
| `data/*.txt` | `data` 下檔名以 `.txt` 結尾的項目 |
| `data/s*.txt` | 以 `s` 開頭、以 `.txt` 結尾 |
| `data/*_*.txt` | 檔名含 `_` 且以 `.txt` 結尾 |
| `data/?.txt` | `.txt` 前恰有一個字元；`?` 不是「零個或一個」 |
| `data/[st]*.txt` | 第一個字元為 `s` 或 `t` |

`*` 配對零個或多個字元，通常不跨過路徑分隔 `/`，也不自動選到開頭為 `.` 的隱藏項目。一般 glob 是依檔名配對，並不驗證檔案內容或保證選到的都是一般檔案。[Bash Filename Expansion](https://www.gnu.org/s/bash/manual/html_node/Filename-Expansion.html)

章末的 `novel-????-[ab]*.{txt,pdf}` 結合了不同規則：`????` 是恰好四個字元，`[ab]` 是 `a` 或 `b`，後面 `*` 可為空；`{txt,pdf}` 是 **brace expansion**，先產生兩種副檔名 pattern，再做檔名配對。「四個字元」不一定是四位數年份。

**系統差異補充：** 在 Bash 的一般預設下，沒有匹配的 pattern 會原樣交給程式；zsh 在預設 `NOMATCH` 行為下通常直接報 `no matches found`。實際表現會隨 shell 選項而變化。[Bash 文件](https://www.gnu.org/s/bash/manual/html_node/Filename-Expansion.html)、[zsh 文件](https://zsh.sourceforge.io/Doc/Release/Expansion.html#Filename-Generation)

### 3.6 `wc` 的數字需要了解定義

`wc` 可以快速檢查文本規模，搭配 wildcard 一次處理多份輸入。**技術精確化：** 書中概括為 lines、words、characters；一般 `wc` 預設第三欄實際是 **bytes**，不能直接當作中文或其他多位元字元的字數。`-l` 計算 newline，最後一段若沒有換行不會再增加一行；`-w` 以 whitespace 分隔的片段計數，不是語言學的斷詞；`-m` 才是依 locale 解讀的 character count。[GNU `wc` 文件](https://www.gnu.org/s/coreutils/manual/html_node/wc-invocation.html)

因此 `wc -w` 可作粗略規模檢查，但不能直接代替書中 Zipf's Law 分析所需的完整詞頻統計。

### 3.7 查文件是解決問題的一部分

`man wc` 可查指令的 NAME、SYNOPSIS、DESCRIPTION、options 等；部分指令有 `--help`，不能假設每個平台的每個工具都支援。TLDR 提供精簡例子，可用來找起點，再用實際系統的 manual 確認參數。常見 `less` 操作包括 Space 下一頁、`b` 上一頁、`/word` 搜尋、`n` 下一個搜尋結果、`q` 離開。[2.8 Reading the Manual](https://third-bit.com/py-rse/bash-basics.html#bash-basics-help)

## 4. 指令速查

以下是各自獨立的示例，假設相關來源檔案與目錄存在；不是一整段要依序執行的 script。

| Command | 用途／注意事項 |
| --- | --- |
| `whoami` | 顯示目前執行身分。 |
| `pwd` | 顯示 current working directory。 |
| `ls -F -a` | 顯示隱藏項目，並以 `/` 等符號標示項目類型。 |
| `ls -l -h` | 詳細列表與易讀檔案大小；章末延伸選項。 |
| `ls -R -t` | 遞迴列出目錄，各層依修改時間排序；大小寫不同會改變意義。 |
| `cd ../data` | 往上一層，再進入 `data`。 |
| `mkdir docs` | 建立目錄；父目錄需已存在。 |
| `nano docs/draft.txt` | 用 Nano 開啟／編輯純文字檔。 |
| `touch draft.txt` | 檔案不存在時建立空檔；存在時更新時間戳，不清空內容。 |
| `mv -i docs/draft.txt docs/notes.txt` | 改名；覆寫前詢問。 |
| `cp -i docs/notes.txt backup/` | 複製檔案到既有目錄。 |
| `cp -r docs backup` | 遞迴複製；`backup` 若已存在，結果的層級可能不同。 |
| `rm -i scratch.txt` | 刪除指定練習檔前詢問。 |
| `rm -r -i scratch` | 遞迴刪除練習目錄與內容，互動確認。 |
| `ls data/*.txt` | 先檢查 pattern 配對的項目。 |
| `wc -l data/*.txt` | 計算每個匹配輸入的 newline 數，並在多檔時列總和。 |
| `wc -w data/novel.txt` | 計算 whitespace 分隔的 words。 |
| `wc -c data/novel.txt` | 計算 bytes。 |
| `wc -m data/novel.txt` | 依 locale 計算 characters。 |
| `man wc` | 查閱本機 `wc` manual。 |

`ls -r` 是反向排序，`ls -R` 才是 recursive listing；其他工具的 `-r` 不一定有相同意思。參數需要按指令查證。

## 5. 17 題章末練習的學習大綱

以下整理題目要訓練的能力，不將閱讀過題目記成已完成實作。[2.10 Exercises](https://third-bit.com/py-rse/bash-basics.html#bash-basics-exercises)

| 題號 | 核心練習 |
| --- | --- |
| 2.10.1–2.10.2 | 理解 `ls -l`、`-h`、`-R`、`-t`，區分詳細顯示、遞迴與排序。 |
| 2.10.3–2.10.5 | 從指定 working directory 解讀 absolute／relative paths，結合 Figure 2.5 預測 `ls`。 |
| 2.10.6–2.10.7 | 了解 `touch` 與 `rm -i`，分辨建立空檔、更新時間與刪除。 |
| 2.10.8–2.10.11 | 移動多個檔案、改名、追蹤 `cp`／`mv` 後檔案位置，理解目的地參數。 |
| 2.10.12 | 比較不同 wildcard pattern 是否選出同一組檔名。 |
| 2.10.13–2.10.14 | 把分析輸出放到 `results`；區分重建空目錄結構與複製舊資料。 |
| 2.10.15–2.10.17 | 比較 wildcard 表達式、考慮無匹配情況、精確選取待刪檔案、解讀混合 pattern。 |

**自我檢查：** 能否在執行前回答「目前在哪裡？shell 會產生哪些 arguments？程式會修改哪些來源與目的地？結果如何檢查？」這是本章值得練熟的推理方式。

## 6. 閱讀心得草稿

讀完這章，我對 research software engineering 的理解更具體了。研究結果依賴程式，也依賴程式外圍的一連串操作：資料放在哪裡、哪些檔案被選進來、輸出如何保存。CLI 讓這些操作可以寫成文字，方便檢查與重做。我認為本章最有價值的地方，是把平常容易省略的檔案操作變成可以清楚說明的研究步驟。

Working directory 和 relative path 讓我看到，指令的意思會受到執行位置影響。同一個 `data/*.txt`，換到另一個目錄就可能讀到不同資料，甚至完全沒有匹配。因此，日後寫 coursework 的 README 時，我會先說明從哪個目錄執行，再提供相對路徑指令。這能讓其他人理解流程，也避免把自己的電腦路徑當成所有人都能使用的設定。

Wildcard 則提醒我，簡短指令背後其實包含資料選擇的決定。它可以減少重複輸入，但選到哪些檔案會直接影響分析結果。副檔名只是一種命名慣例，不能單靠 `.txt` 或 `.csv` 判斷內容是否正確。尤其在刪除或批次處理前，我會先查看配對結果，分清 raw data 和 derived output，讓處理範圍與研究目的保持一致。

我也認為效率需要配合可檢查的操作習慣。`cp`、`mv` 和 `rm` 看起來都很短，卻分別涉及建立副本、改變位置與刪除；`-v` 能顯示做了什麼，但不會替我判斷是否做對。這讓我更重視在操作前確認來源與目的地，並在可丟棄的資料上練習。研究資料的管理方式會影響之後能否回查錯誤與重做分析。

最後，`wc` 的例子讓我注意到「產生一個數字」和「知道那個數字代表什麼」之間的差距。Bytes、characters、whitespace 分隔的 words 是不同概念，語言學研究所需的詞頻又需要另外定義。對我而言，讀 manual 是理解分析方法的一部分。接下來我希望把本章的路徑與檔案管理基礎用到 Python coursework，讓自己的分析流程能被說明、檢查和重新執行。

## 7. 整理狀態與參考資料

- [x] 已依完整 Chapter 2 建立大綱、重點、指令速查與章末練習主題。
- [x] 已依閱讀內容撰寫心得草稿，附繁中與英文版本。
- [ ] 本人核對心得並改成符合自己觀點的版本。
- [ ] 本人練習尚不熟悉的指令，確認能預測結果。

以上區分文件整理與本人的閱讀／實作狀態；本次未操作 Moodle completion。

1. Irving, D., Hertweck, K., Johnston, L., Ostblom, J., Wickham, C., & Wilson, G. (2021). *Research Software Engineering with Python: Building software that makes research possible*. CRC Press / Taylor & Francis. Chapter 2, pp. 13–44。
2. [作者公開版 Chapter 2](https://third-bit.com/py-rse/bash-basics.html)／[全書與授權說明](https://third-bit.com/py-rse/#contributing-and-re-use)／[作者原始碼 repo](https://github.com/merely-useful/py-rse)。本頁為摘要、翻譯與理解補充；原書文字採 CC BY 4.0，程式碼採 MIT 授權。
3. [UCL Library 指定入口](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159)／[Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270)。本次課業要求依提供的 Moodle 截圖辨識，未重新登入平台查核。
4. 技術補充：[GNU `wc`](https://www.gnu.org/s/coreutils/manual/html_node/wc-invocation.html)、[Bash Filename Expansion](https://www.gnu.org/s/bash/manual/html_node/Filename-Expansion.html)、[zsh Filename Generation](https://zsh.sourceforge.io/Doc/Release/Expansion.html#Filename-Generation)；另核對本機 `man wc`。

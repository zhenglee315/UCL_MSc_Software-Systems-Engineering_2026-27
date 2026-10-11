# COMP0235 — Week 1 輔助筆記

**Module:** Engineering for Data Analysis 1（資料夾沿用 Data Engineering 名稱）

**Moodle topic:** Course Welcome and Remedial Software Engineering Practice

**課堂錄音:** `Recording_20261007_1002`（2026-10-07）

**整理及核查日期:** 2026-10-12，Europe/London

這週先建立後續資料分析系統所需的共同基礎：能登入自己的遠端 Linux VM、讀懂檔案和指令、把操作組合成可重複執行的流程，再以 Python coding practice、testing 和 Git 管理程式。教師在錄音 **18:37** 強調：Week 1 最重要的成果是成功登入遠端機器。

本頁是個人學習整理，保留 English 術語並用繁體中文解釋；作業要求與尚待完成項目另見 [coursework/README.md](coursework/README.md)。

## Source coverage 與可信度

| 來源 | 本次讀取範圍與用途 |
| --- | --- |
| [Asksia 原始錄音／逐字稿](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43) | 在來源面板選 `Origin`，逐段讀取全部可取得英文文字 **0:01–103:36**；錄音標示總長 106:22，但面板最後文字停在 103:36。60:20–75:46 主要為課間聊天，不納入課程筆記。 |
| Asksia 摘要 | 原稿分析後再核對兩份「虛擬化管理與 Linux」摘要；用於查漏，不能把摘要新增細節當作教師原話。 |
| [Moodle Week 1](https://moodle.ucl.ac.uk/course/section.php?id=1381270) | 已核全部資源名稱、閱讀要求、Git 練習範圍及 Unix forum 要求。 |
| 原始課件 | 全讀 `1.2 Rancher and ssh configuration` MD、`1.3 Remedial Software Engineering` ODP；亦讀本機既有 `1.1 Welcome Slides` ODP。以下只保存自己的整理，不保存原件或逐字全文。 |
| [Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269)、[Communication](https://moodle.ucl.ac.uk/course/section.php?id=1381264) | 已讀環境要求、課程 GitHub 與 Etherpad 入口、提問管道。 |
| 教師公告 | 已讀 10/5 Welcome、10/6 Condenser fixes、10/6 namespace 示範說明、10/7 HTTP Hostnames。較新的具體設定優先於舊 MD 的示範值。 |
| 指定閱讀 | 核對 [PEP 8 官方規範](https://peps.python.org/pep-0008/)；讀作者版 [Research Software Engineering with Python，第 2 章](https://third-bit.com/py-rse/bash-basics.html)。 |
| 本次未取得的課件 | `1.3.1 Intro to the Unix Commandline`、`1.3.2 Incredibly quick YAML intro`、`1.3.3 Intro to good python code`、`1.3.4 Intro to git and github` 的原始檔未能正常取得；Unix MD 下載逾時，開啟後 Chrome 顯示 blocked by client。這些項目的筆記只依已讀課堂、ODP、Moodle 說明和明示的補充，不宣稱讀過該原始檔。 |

**逐字稿限制：** 全稿把不同發言都標為 Speaker 1；後段不少句子破碎，不能可靠還原操作命令。原文中的 `Armor 9 Linux`、`Cadenza` 等轉錄，依 Moodle 課件及公告校正為 **AlmaLinux 9**、**Condenser**。不要從破碎文字自行補成教師說過的完整指令。

## Whole-week summary — 整週重點

1. **ML-Ops / systems administration:** 課程最終要建立能分散執行資料分析、管理資料、監控與保護服務的系統。Week 1 先確保每個人能操作遠端環境。
2. **Provisioning a VM:** 選正確 cluster 和自己的 namespace，附加 SSH public key，選作業系統映像、磁碟及網路，等待 VM 啟動及 IP 回報。
3. **SSH through a jump host:** Gateway 與目標 VM 是兩個角色；認證 gateway 成功後連線立即關閉，未必是失敗。真正登入 VM 要指定目標使用者、IP、identity 和 jump host。
4. **Linux command line:** 知道目前在哪台機器、哪個目錄、以誰的權限執行；能建立、查看、複製、移動檔案，讀取說明和設定。
5. **Streams and composition:** 分清 stdin、stdout、stderr；redirection 將輸出寫到檔案，pipe 將一個程式的輸出交給下一個程式。
6. **From manual work to automation:** 教師可先在一台 VM 手動探索設定，再把已確認的操作轉成配置檔或自動化程序。每次靠網頁點選及登入改檔，難以擴展成多台一致的系統。
7. **Good software practice:** Moodle 同週要求補齊 YAML、Python style、unit testing、Git/GitHub；它們不是孤立主題，而是讓配置與分析程式可讀、可查、可協作的工具。

## Key Concepts — 核心概念

| English term | 中文解釋 | 本週要分清楚的關係 |
| --- | --- | --- |
| **Virtual Machine (VM)** | 具有自己的作業系統、CPU／記憶體／磁碟配置的虛擬電腦。 | 本機 Terminal 是操作入口；SSH 後指令是在遠端 VM 執行。 |
| **Cluster** | 平台管理一組運算資源的單位。 | 學生使用 teaching cluster；教師示範的 cluster 名稱不一定相同。 |
| **Namespace** | 平台中分隔資源與操作範圍的名稱空間。 | 先選自己的 namespace，再建立 VM；不是只在機器名稱中加入自己的 ID。 |
| **Image / Volume** | Image 提供作業系統起點；volume 是 VM 使用的儲存空間。 | 映像版本與磁碟容量是不同選項；容量要容納 OS、資料及工作空間。 |
| **Public / private key** | 公鑰供遠端識別；私鑰在本機證明身分。 | Rancher 上傳 PUBLIC key；不要把私鑰當作上傳材料。 |
| **SSH certificate / IdentityFile** | 課程 gateway 設定有簽署的 certificate 和本機 identity key。 | 簽署公鑰得到的材料與原始 key pair 不同，路徑也各自指定。 |
| **Jump host / ProxyJump** | 透過 gateway 轉送 SSH 到目標 VM。 | Gateway 不等於你要操作的 VM；`-J` 是跳板，最後的 `user@host` 才是目標。 |
| **Host fingerprint / known_hosts** | 用戶端記住伺服器的 host identity。 | VM 重建可能重用 IP，使新 identity 與舊記錄不同；不能把所有警告都當作可忽略。 |
| **Terminal / shell / command** | Terminal 顯示及輸入文字；shell 解讀命令；command 是被呼叫的操作。 | `cd` 等可以是 shell builtin，不是每個命令都必然對應 `/usr/bin` 的獨立檔案。 |
| **Working directory / path** | Working directory 是當前位置；path 指定檔案所在位置。 | Absolute path 從 `/` 開始；relative path 依當前位置解讀。 |
| **stdin / stdout / stderr** | 程式的標準輸入、正常輸出、診斷／錯誤輸出。 | stdout 與 stderr 即使都顯示在 Terminal，也仍是不同的 stream。 |
| **Redirection / pipe** | 改變 stream 的目的地或連接兩個程式。 | `>` 寫檔，`2>` 寫錯誤，`|` 把左邊 stdout 交給右邊 stdin。 |
| **Package / service / firewall** | 套件是安裝材料；service 是執行中的服務；firewall 控制流量。 | 安裝 Apache 不等於已啟動，也不等於已能從瀏覽器連到。 |
| **Manifest / YAML / automation** | 配置檔記述要建立的資源或設定。 | YAML 是資料格式；Kubernetes manifest 是有特定結構的配置。單有 YAML 檔不代表 VM 已建立。 |
| **Git / GitHub / pull request** | Git 保存版本歷史；GitHub 提供協作平台；PR 提請審查一組變更。 | 保存檔案、commit、push、提出 PR 與 merge 是不同階段。 |

## VM setup — 用更新公告解讀舊講義

### 1. Environment preparation

依 [Moodle Preparation](https://moodle.ucl.ac.uk/course/section.php?id=1381269)：必須有 Unix terminal；Mac 可用 Applications → Utilities → Terminal，Windows 建議 WSL。準備 code editor，複習 shell 和 SSH keys，並確認在 UCL 校園或 UCL VPN 下能開 Condenser／Rancher。

課程程式碼入口為 [UCL-ARC/engineering-for-datascience](https://github.com/UCL-ARC/engineering-for-datascience)，協作筆記入口為 [COMP0235 Etherpad](https://etherpad.wikimedia.org/p/COMP0235)。Moodle 說老師會指示何時抓取程式碼及重要更新。

### 2. Correct cluster and namespace

**10/6 的 [Condenser fixes 公告](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710) 才是本次核到的更新設定：**

- 學生應能登入 Condenser。
- Teaching cluster 為 **`sl-t01`**。
- 個人 namespace 的形式為 **`<UCL-ID>-comp0235-ns`**；實際值使用平台分配給自己的項目。
- 建立 VM 的 Volumes 應能看到兩個 AlmaLinux image 選項。
- 找不到自己的 namespace，教師要求立即聯絡他。

舊 Rancher MD 寫 `sl-p01`、`ds4eng-ns/ds4eng`，是不能直接照抄的示範值。錄音中教師亦說自己的 namespace 與學生不同。選錯 cluster 或未 activate namespace，後面即使步驟看似正確，仍可能找不到資源。

如不清楚如何選擇，10/6 的 [namespace 示範公告](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808) 附有短影片；本次只核到公告及影片入口，未播放影片內容。

### 3. SSH keys and gateway

原始 Rancher MD 的流程是：建立 key pair → 在 Rancher 上傳公鑰 → 經課程提供的 Vault／SSH 入口簽署公鑰 → 把 certificate 保存到本機 → 在 `~/.ssh/config` 指定 gateway、user、certificate 與 identity。

Key generation、簽署及上傳在本次整理中沒有代操作。私鑰、certificate、token 與帳密不屬於筆記 repo 內容。原始講義提到示範時省略 passphrase；這是示範選擇，不是要求所有人如此設定。

MD 說 `ssh condenser` 若認證正常，可立即關閉連線而不報錯：這是測試 gateway credentials，還沒登入你的 VM。錄音 11:45–15:34 同樣解釋這個區別。

### 4. VM creation and SSH login

錄音 3:58–6:34 示範 **4 CPUs**，為避免與既有例子出現小差異選 **AlmaLinux 9**，並說練習機器 **20 GB** 是合理大小；20–40 GB 可為檔案留餘裕。這些是示範／建議值，不是所有作業固定配額。原始 MD 另示範 4 GiB memory、40 GiB disk；若平台或老師後續有新要求，以更新內容為準。

選與自己 namespace 對應的網路，附加已上傳的公鑰，等待 VM 狀態和 IP 回報。錄音 10:42–11:28 指出平台的監控回報可能延遲或短暫消失；不要因 IP 尚未顯示就立即認定建立失敗。

下式是從課件整理的 **syntax template**，不是你可直接照貼的實際地址：

```sh
ssh -i ~/.ssh/<identity-key> -J <gateway-alias> almalinux@<your-vm-ip>
```

讀法是：「使用這個 identity，經這個 jump host，登入這台 VM 的 `almalinux` 使用者。」Gateway alias 是 SSH config 中自己定義的 `Host` 名稱。

### 5. HTTP access has several layers

```text
Browser → Condenser ingress / hostname → VM network / firewall → Apache httpd
SSH client → SSH gateway / jump host → VM SSH server → remote shell
```

**補充分析：** 這是理解故障位置的概念圖，並非原逐字稿中的圖。SSH 成功只證明 SSH 路徑可用，不能證明 HTTP 路徑可用。

10/7 的 [HTTP Hostnames 公告](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852) 補上兩個具體要求：

```apache
# /etc/httpd/conf/httpd.conf
ServerName localhost:80
```

瀏覽地址為 `https://<hostname>.comp0235.condenser.arc.ucl.ac.uk/`，`<hostname>` 使用你在 VM instance labels 設定的名稱。錄音 8:29–9:00 要求 hostname 唯一，建議用自己的 ID 作前綴或後綴。不要直接使用教師的名稱或共用的 `test` hostname。

錄音後段可辨認 Apache、套件相依、服務與 firewall 主題，但精確 commands 多有缺字；因此不把後段轉錄猜成可執行安裝腳本。操作時應開原始課件與更新公告確認。

## Linux filesystem — 先知道正在操作什麼

教師以 **Everything is a file** 說明 Unix 的基本觀點：普通資料以外，裝置與許多系統介面也用檔案介面呈現（24:58–27:14）。理解這點有助讀懂 `/dev`、`/proc`、`/sys`；並不表示它們都是可任意修改的普通文字檔。

| Path | 本週重點 |
| --- | --- |
| `/` | 整棵 filesystem tree 的 root directory。 |
| `/bin`, `/usr/bin` | 常用 executable 所在位置；教師的 AlmaLinux 示範中 `/bin` 可指向 `/usr/bin`。 |
| `/boot` | Kernel 與開機所需資料；教師提醒不要隨意更改。 |
| `/dev` | Device files；辨認裝置時可能需要，日常不必亂改。 |
| `/etc` | 系統及套件 configuration files，課程之後會反覆使用。 |
| `/home` | 一般使用者的 home directories；`~` 指目前使用者的家目錄。 |
| `/root` | 管理員 root 的家目錄；不同於 `/`。一般使用者可能無權進入。 |
| `/lib`, `/lib64` | Shared libraries；教師以 Windows DLL 類比。 |
| `/run`, `/tmp` | Runtime／temporary data；不把應長期保留的工作只存在這些位置。 |
| `/var` | 持續變動而通常需要保留的資料，例如 logs。 |
| `/proc`, `/sys` | Kernel／process 相關介面；逐字稿部分說法破碎，本頁只作位置辨認。 |

**補充校正：** `/tmp` 的實際清理政策依系統設定而異；不要把「每台 Linux 每次重開機必定刪除所有內容」當成通則。教師的重點是辨認 temporary 與需要 persistence 的資料。

## Command line — 概念關係與短例子

### Navigation and file operations

| Command | 用途／要記得的區別 |
| --- | --- |
| `pwd` | 查看 current working directory；迷路時先用它。 |
| `ls -l -a -h` | Long listing、hidden files、human-readable sizes。 |
| `cd /` / `cd ~` | 分別到 filesystem root／自己的 home。 |
| `cd ..` / `cd -` | 分別到 parent directory／上一個 working directory。 |
| `mkdir` / `touch` | 建目錄／新檔或更新既有檔案時間戳。 |
| `cat`, `more`, `less` | 查看檔案內容；`more`、`less` 適合分頁。 |
| `cp` / `mv` | 複製產生另一份；移動改位置，也可重新命名。 |
| `file` | 判斷檔案內容類型；更改副檔名不會轉換格式。 |
| `rm` | 刪除；確認 path 和目標再執行，不視為有圖形介面的垃圾桶。 |
| `man <command>` / `<command> --help` | 查語法、options、arguments；短／長 option 名稱以各命令說明為準。 |

以下是 **補充教學例子**，不是作業答案或已在你的 VM 執行的紀錄：

```sh
# 請在自己的練習目錄操作
pwd
mkdir week1-practice
cd week1-practice
touch notes.txt
cp notes.txt notes-copy.txt
mv notes-copy.txt draft.txt
ls -l -a -h
```

每步都思考兩件事：目前 `pwd` 是什麼？這個相對路徑會解析到哪個位置？Tab completion 可減少路徑拼錯（44:07–44:35）。

### Streams, redirection and pipes

| Syntax | 意義 |
| --- | --- |
| `command > output.txt` | 把 stdout 寫入檔案，通常覆蓋原內容。 |
| `command >> output.txt` | 把 stdout 追加到檔案。 |
| `command 2> errors.txt` | 把 stderr 寫入另一檔案。 |
| `left | right` | 把左邊 stdout 接到右邊 stdin。 |

```sh
# 補充例子：文字輸出與過濾
echo "hello" > notes.txt
cat notes.txt
cat notes.txt | grep "hello"
```

**補充校正：** `echo "hello"` 的 `hello` 是 command argument；不能因轉錄中的說法就記成 `echo` 一般會讀 stdin。Pipe 的典型讀法是 `cat` 產生文字，`grep` 接收文字再過濾。錄音 79:03 對 pipe 的「stdout → 下一個 stdin」解釋可清楚辨認。

**補充校正：** `ls -l` 一般列的是 modification time；不要將轉錄中 52:04 的 creation date 描述直接當作通常欄位的準確定義。`touch` 是更新 timestamps，並不是把既有檔案清空。

### Editor, privilege and services

教師建議熟悉 `vi`，理由是在遠端 Linux 通常容易找到它（48:36–49:30）。先掌握插入文字、回到 command mode、保存及退出；Asksia 摘要提到 `i`、`Esc`、`:wq`、`:q!`，但課間的細節轉錄不完整，因此實際按鍵可查 editor help。

一般使用者與 root 權限不同。`sudo` 是經授權以較高權限執行命令；不要以為能 SSH 登入就能修改所有系統設定。Apache 範例同時涉及 package dependencies、service lifecycle、開機啟動與 firewall。它們要分開驗證，而不是只看一次 install 是否成功。

## Moodle 同週主題：YAML、Python、testing、Git

這一部分由 Moodle Week 1 的活動清單與 Remedial Software Engineering ODP 確認；**不能宣稱 10/7 錄音已詳細講完所有主題**。

### YAML and configuration

Moodle 有 `1.3.2 Incredibly quick YAML intro`。原始檔本次未取得。**補充學習方向：** 能辨認 mapping、sequence、巢狀縮排及 scalar 值；先看懂配置表達的結構，再討論工具如何使用它。將設定寫成檔案後，才可一起接受 Git review、比較版本並重複部署。

### Good Python code and PEP 8

ODP 將 PEP 8、Pythonic code 和「What is good code in your opinion?」列為課堂討論。沒有可取得的逐字回答，不把自己的偏好寫成教師結論。

[PEP 8](https://peps.python.org/pep-0008/) 的閱讀重點：4 spaces、可讀的換行與空白、分組 imports、`snake_case` functions/variables、`CapWords` classes、constants 的大寫名稱、docstrings，以及避免隱藏問題的過寬 exception handling。標準行長為 79、長 comments/docstrings 為 72；project 內既有一致性和相容性亦重要，不能為套格式破壞行為。

**補充分析：** Style 幫助讀程式；它無法證明計算正確。能否清楚說明 function 的 inputs、outputs 和邊界情況，須再配合 testing。

### Unit testing and refactoring

Remedial ODP 明確安排：先寫一個 function 的 unit test，再 implement function。課件沒有在可讀內容中指定 function 題目，因此此處不代寫實作或測試答案。

**補充分析：** Unit test 將預期行為寫成可檢查例子；refactoring 改善結構時應保留預期行為。這說明為什麼 testing、可讀性、version control 應一起看。

### Git, GitHub and collaboration

ODP 的 pair exercise 是：Person 1 建 repo，將 working code 加到 main；Person 2 改程式並提出 pull request；Person 1 檢查並 approve。這是課堂協作活動，並非本次已替你完成的紀錄。

Moodle 的本週 Git Branching 任務是 Main 四組：**Introduction Sequence → Ramping Up → Moving Work Around → A mixed bag**，其他全部關卡為 optional。應理解 branch、HEAD、merge／rebase 和選擇性移動 changes 的歷史效果，不能只記指令名稱。

```text
清楚的程式／配置 → unit tests → commit history → pull request review
                                      ↓
                       可回溯的分析與部署流程
```

這是 **補充整合圖**：Unix 提供操作介面；YAML 表示配置；Python 表示分析；tests 檢查行為；Git 記錄和審查變更。它們一起支撐後續多台機器的 automation。

## Required reading map

- [PEP 8 官方網站](https://peps.python.org/pep-0008/)：Moodle 要求 familiarise yourself。按 code layout → imports/whitespace → naming/docstrings → programming recommendations 閱讀，用自己的小段程式辨認規範；不要只背 4 spaces。
- [Research Software Engineering with Python — Chapter 2: The Basics of the Unix Shell](https://third-bit.com/py-rse/bash-basics.html)：作者版第 2 章依序談 filesystem/navigation、建立／移動／複製／刪除、wildcards、manual，最後有練習。Moodle 寫作「in Python」，作者版正式書名為 **with Python**。本週要求讀 Chapter 2，未看到要求上傳整章練習答案。
- [Moodle book 入口](https://moodle.ucl.ac.uk/mod/book/view.php?id=8523823)：本次頁面顯示未加入 book content；其說明附 [UCL Primo 電子書入口](https://ucl.primo.exlibrisgroup.com/permalink/44UCL_INST/18kagqf/cdi_askewsholts_vlebooks_9781000417159)。可用作者網站閱讀，不必把 Moodle 空頁誤認成指定閱讀為空。
- `Unix in a Nutshell` 在 Moodle 標作 **Extra reading**，可當 reference，並非本週另外一份必交作業。

## Classroom Q&A — 實際可辨認的問答

以下 English 問題是按可辨認英文原文整理的 **paraphrase**，不是逐字引用。Speaker 標籤不可靠，因此不填學生姓名。

| Time | English question | 教師回應／中文理解 |
| --- | --- | --- |
| **16:01–16:21** | **Do I have to use the same connection command every time I access the VM?** | 要提供正確 identity、jump host 和目標機器；這個長指令反映真正需要的連線資訊。 |
| **16:21–17:51** | **Can we put it in SSH config so that the command is shorter?** | 可以為 VM 建 `Host` entry，配置 identity／jump host 後用簡短 alias。教師補充：反覆 destroy/create VM 而換 IP 時，config 也要反覆更新；固定機器與固定 IP 的環境較容易維護。 |
| **51:17–52:38** | **What happens if I touch an existing file?** | 課堂學生回答後教師確認：更新 timestamp；不存在的檔案則建立。不要誤記成覆蓋內容。 |

**沒有收錄為教師回答的內容：** ODP 中的 good code／Git 優缺點討論只有題目，沒有可靠逐字回答；後段命令缺字亦不補造 Q&A。

## Teacher emphasis and common pitfalls

1. **18:37 — 本週先取得可工作的遠端環境。** VM 已在清單中不代表已完成登入；以成功 SSH 進入 remote shell 作最直接的學習檢查。
2. **5:06–5:36 — 版本一致性。** 教師選 AlmaLinux 9 是為延續示範；較新版本「大概相同」不能當作已測過完全相容。
3. **8:29–9:00 — Hostname uniqueness。** 使用個人 ID 協助避免 collision；不要複製教師示範名稱。
4. **14:23–15:34 — IP reuse。** 新 VM 可能取得舊 IP，host identity 不同。**補充操作原則：** 先確認變更原因與目標，再處理對應 known_hosts entry；不把清除所有 host checks 當作一般修法。
5. **33:51–34:08、49:30–49:45 — 手動探索之後要整理成 automation。** 臨時登入改檔可能實務上仍會發生，但應逐步把已理解的操作變成可重複的配置流程。
6. **55:48–57:08 — Relative path depends on location。** 同一相對字串在不同 directory 會指不同地方；先看 `pwd`。
7. **57:28–59:52 — 查 help／manual。** 不同命令的 option、文件完整度不同；先閱讀實際版本的說明再操作。
8. **10/7 HTTP 公告 — 課件外的修正也要納入。** ServerName、hostname／instance label、service 和 firewall 每層都可能影響可達性。

## Study checklist — 自己驗證理解

這些是 **補充自查問題**，不是教師新增作業或考試預測。

- Can I explain the difference between the gateway and my VM?
- Can I identify the active namespace and explain why the old MD example differs?
- Can I tell whether a command is running on my Mac or on the remote VM?
- Can I explain `/`, `/root`, `/home`, `~`, `..` and `cd -` without混淆？
- Can I trace stdout/stderr through a redirection or pipe?
- Can I distinguish an installed package from a running service and an accessible website?
- Can I explain why a clear config file, a unit test and a Git commit help reproduce my work?

## Source links

- [Week 1 全部材料](https://moodle.ucl.ac.uk/course/section.php?id=1381270)
- [1.1 Welcome Slides](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523815)／[1.2 Rancher and ssh configuration](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523816)／[1.3 Remedial Software Engineering](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523817)
- [1.3.1 Unix](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523818)／[1.3.2 YAML](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523820)／[1.3.3 Python](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523821)／[1.3.4 Git](https://moodle.ucl.ac.uk/mod/resource/view.php?id=8523824)
- [10/5 Welcome](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1312114)／[10/6 Condenser fixes](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313710)／[10/6 namespace](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1313808)／[10/7 HTTP Hostnames](https://moodle.ucl.ac.uk/mod/forum/discuss.php?d=1314852)
- [Asksia 錄音與原文](https://app.asksia.ai/pro/session?id=d22c85b4-7388-4baf-bf3a-28f965efbc43)
- [PEP 8](https://peps.python.org/pep-0008/)；[Irving et al., Research Software Engineering with Python](https://third-bit.com/py-rse/) 及其 [Chapter 2](https://third-bit.com/py-rse/bash-basics.html)（作者版標示 CC BY 4.0，本文為摘要與連結）。

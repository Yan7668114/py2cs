# xv6 學習心得報告
### XV6簡介
Xv6是一個教學用的操作系統，它基於Unix第六版（Version 6 Unix）的設計。它由麻省理工學院（MIT）的教授和研究人員開發，旨在作為操作系統課程的教學工具。
Xv6的設計目標是簡化和精簡，以幫助學生更好地理解操作系統的基本原理和概念。它使用C語言編寫，並且代碼量相對較小，易於閱讀和理解。
Xv6在功能上模仿了Unix操作系統的一些核心概念和機制，包括進程管理、內存管理、文件系統和系統呼叫等。通過研究和分析Xv6的源代碼，學生可以深入了解操作系統的內部工作原理，例如進程調度、內存分配、文件系統操作等。
Xv6還提供了一些基本的命令行工具，例如文件管理命令（如ls、cp、rm）、進程管理命令（如ps、kill）和調試命令（如debug）等。這些工具可以幫助學生學習和實踐在操作系統中常見的任務和操作。
除了教學用途，Xv6還可以作為研究操作系統的基礎平台。學者和研究人員可以基於Xv6進行擴展和實驗，探索操作系統的新概念和技術。
xv6在MIT操作系統課程[6.828](https://pdos.csail.mit.edu/6.828/2012/xv6.html) 中使用。
### 與Linux OS的比較
LINUX與xv6操作系統有多處異曲同工之處，以下是一些比較:

1,設計目標：xv6是一個教學用的操作系統，它基於Unix第六版，旨在提供一個簡化而易於理解的操作系統實現。它的設計目標是幫助學生學習操作系統的基本概念和原理。而Linux則是一個完整、成熟的開源操作系統，被廣泛應用於各種場景，包括桌面、伺服器和嵌入式系統等。

2,複雜性：相對而言，xv6是一個相對簡化的操作系統。它只包含了操作系統的核心組件和一些基本功能，以保持簡潔和易於學習。而Linux則是一個非常複雜和功能強大的操作系統，它具有廣泛的功能集，支援多任務、多使用者、網絡通訊等複雜的操作系統特性。

3,軟體生態系統：由於Linux是一個開源操作系統，它具有龐大的軟體生態系統。有許多開發者和組織為Linux提供了大量的應用程式、工具和驅動程式，使其成為一個功能豐富且可擴展的操作系統。相比之下，xv6的軟體生態系統相對較小，主要側重於教學和研究。

4,支援平台：Linux是一個跨平台的操作系統，可以在各種硬體架構上運行，包括x86、ARM、PowerPC等。而xv6主要針對x86架構，特別是在模擬器（如QEMU）上運行。

5,開發和維護：xv6是一個教學項目，它的開發和維護主要由教育機構和研究人員進行。而Linux是一個由全球開發者社群維護的開源項目，擁有眾多的貢獻者和維護者。

### xv6安裝
##### step1:下載Git(推薦)、xv6、VSCode、freedom studio
Git [載點](https://git-scm.com/download/win):
`winget install --id Git.Git -e --source winget`
在 windows Powershell輸入這行指令也可以使用winget工具下載Git。
xv6[載點](https://github.com/riscv2os/riscv2os):
這邊為了方便，所以用老師的Github來Git clone
終端機輸入:
`git clone https://github.com/riscv2os/riscv2os.git`
記住你Git的位置
VSCode [載點](https://code.visualstudio.com/):
也不是一定要使用VScode，但是目前使用起來沒有比VScode更好用的文本編輯器，編輯、整合都非常方便。
freedom studio [載點](https://github.com/sifive/freedom-studio/releases)
這是啟動xv6的關鍵工具包
官網由於我找到死都沒找到載點，所以就去官方github下載壓縮檔。
**(重要動作)**
打開freedom studio資料夾，找到以下兩個檔案
> riscv64-unknown-elf-gcc-8.3.0-2020.04.1
> riscv-qemu-4.2.0-2020.04.0

點開各自的`bin`資料夾，將兩個路徑都複製到環境變數裡
且看以下步驟:
![](https://hackmd.io/_uploads/HkcxofDD2.png)
![](https://hackmd.io/_uploads/SJWzoMPDh.png)
![](https://hackmd.io/_uploads/BJ6Isfvw3.png)
![](https://hackmd.io/_uploads/B1qjifvwn.png)


##### step2:啟動並運行xv6
打開VSCode，開啟RISCV2OS資料夾，開啟Git Bash:
![](https://hackmd.io/_uploads/HkOVyXvP3.png)
導引到xv6，輸入`make`，運行完成後輸入`make qemu`。
![](https://hackmd.io/_uploads/By7nk7Dw3.png)
![](https://hackmd.io/_uploads/r13T17Pv3.png)
當看到顯示這個之後就表示成功了:
![](https://hackmd.io/_uploads/S1zJl7Dw2.png)
退出的話，按下ctrl + a ，然後在按x，即可退出qemu。
![](https://hackmd.io/_uploads/B1gHNxQwvh.png)

### 常用指令
`ls`列出當前目錄中的文件和子目錄
![](https://hackmd.io/_uploads/rJjneQPvn.png)
`mkdir`創建新目錄
![](https://hackmd.io/_uploads/Hyg7bXDD2.png)
`cd`
![](https://hackmd.io/_uploads/rJwc7XDP2.png)
`cd ..`返回上一個目錄
![](https://hackmd.io/_uploads/HJcbN7ww3.png)
`echo` 用於在終端上列印文字或將文字追加到檔案中
`cat` 顯示文件的內容
![](https://hackmd.io/_uploads/rywYvQwPh.png)
`echo >>`將文字追加到檔案
![](https://hackmd.io/_uploads/BJdbOmDDn.png)
`rm`删除文件
![](https://hackmd.io/_uploads/BkuuOQwD2.png)

(諸如此類的指令還有許多，由於是基於Unix系統開發，所以許多指令與Linux相似，但是如上面介紹所說，xv6只是MIT基於學生學習開發的系統，比起LINUX還有許多不完善的地方)




參考文獻:[維基百科](https://zh.wikipedia.org/zh-tw/Xv6)、[xv6中文文檔](https://th0ar.gitbooks.io/xv6-chinese/content/)、ChatGPT
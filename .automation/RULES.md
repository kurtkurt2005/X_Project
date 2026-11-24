# 開發操作規範
狀態：webhook、認證、工作鎖及 cloud-pause/cloud-resume 未實作、未驗證。
Desktop 只收集及安排。遊戲碼經 webhook 交 Claude Code CLI。
知識庫、世界觀、所有日常 Git 寫操作及專案記憶體寫入，經 webhook 交 grok -p。不用 Grok 互動 TUI。
Claude Code CLI 只在核准專案根目錄及指定功能分支寫遊戲碼。不自行 commit、push、切分支或合併，不寫專案記憶體。
main 只由用家在 Cursor 睇 diff 後親自合併。禁止自動推 main。Origin 只核對鏡像 SHA，本章不更改其設定。
整個倉庫同一時間只准一項寫檔或 Git 作業。用家在作業中亦不在 Cursor 或 Godot 改同一棵樹。
接收器必須核對認證、核准目錄、指定分支及鎖，自己不改遊戲檔。
在 main 或有 .automation/cloud.lock 時拒絕，不排隊偷跑。
只有 workspace.lock 被合法作業持有時，其他合法請求才可按 FIFO 等候；出隊須重新驗證。
workspace.lock 的取得必須是不可同時成功的獨佔操作，不能只先檢存在再寫檔。
崩潰或逾時要先確認原寫手已終止，才安全復原並釋放鎖，避免原寫手仍跑卻開第二項。逾時不預填。
Desktop 及 CLI 可讀專案記憶體，但不可寫。各工具獨立記憶各自私有，不放入共用 Skills 或專案記憶檔。
Skills 是操作指引，不是硬權限隔離。不用 /desktop 或 /resume 交寫入權。
不安裝 Desktop Commander、CMD MCP 或對準遊戲目錄的不受限制 shell。
密鑰不進 Git、不貼聊天。不在本規範記錄本機私密設定。
Grok Build 不寫或審查遊戲程式、不派工。世界觀定稿由用家批准。
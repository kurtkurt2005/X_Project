---
name: project-guardrails
description: 在此專案討論派工或準備寫檔前，核對角色、目錄、分支與工作鎖。
---
先讀專案根目錄的 .automation/RULES.md。只按已驗證的角色與範圍工作。
Desktop 只收集及安排。遊戲碼經 webhook 交 Claude Code CLI；Git 與專案記憶體寫入經 webhook 交 grok -p。
Claude Code CLI 只在核准根目錄的指定功能分支寫遊戲碼，不自行做 Git 寫操作，不寫專案記憶體。
若無接收器已驗證的目錄、分支及鎖資訊，只能討論，不開始寫檔。
main 或 cloud.lock 必須拒絕。workspace.lock 被佔只可等候，出隊須重新檢查。
各工具獨立記憶各自私有，不放入此 Skill 或專案記憶檔。
Skills 不是硬隔離。不用 /desktop 或 /resume 交寫入權，不繞過接收器。
若本指引與既有內容衝突，先停止並請用家核對。
# 雲端開發環境驗證

日期：2026-10-13（Asia/Taipei）。來源：使用者在雲端環境建立對話要求依本 repo 的 AGENTS.md 與 docs/guide.md 安裝、驗證工具及實測最小 PR 的寫入／合併能力。

## 實測結果

- 起始程式 commit：`c47eecf17b538443e8c8cc15f7de947ca0b4aa3d`；開始時工作目錄乾淨。
- 已執行 `bash scripts/setup.sh`。Node 24.21.0、npm 11.19.0、pnpm 12.11.2、Python 3.12.14、Git 2.52.0 可用。
- 本機沒有系統套件安裝權限；既有系統函式庫足以執行固定版本的 Playwright Chromium。Node 校驗、npm lockfile 與 pnpm 已審閱腳本校驗維持啟用，保留平台 proxy 與 CA。
- Playwright 1.64.0 配套的 Chromium Headless Shell 156.0.8078.4 成功安裝；repo 的 `node tools/browser-smoke.mjs` 實際通過 JavaScript 與點擊輸入驗證。
- `python3 scripts/template-check.py` 的 10 項範本測試全數通過。
- managed runtime 為 running，網路政策回報 unrestricted；必要的 Node／npm／瀏覽器下載及 GitHub Git／API 唯讀操作成功。不以政策的 unknown enforcement observation 推定所有目的地都已驗證。
- 沒有宣告新的秘密、部署 PAT 或付費服務；沒有輸出秘密值。
- repo 的 `.agents/skills/grilling/SKILL.md` 可直接讀取。本 chat 提供原生問題工具；本次環境設定不開始遊戲規格訪談。
- GitHub API 回報此 repo 具有 push 權限；實際推送／PR／合併結果以本文件所屬 PR 的狀態為準。分支保護與 Actions 管理設定查詢回傳 integration 403，不能據此聲稱管理 API 可用。

## 能力界線與下一步

- `.template/project.json` 尚未初始化，沒有遊戲服務；上述是工具與範本驗證，不是遊戲測試、正式部署或 Pages 驗收。
- 安裝快取保留在 `.cache/` 與 `tools/node_modules/`；每個新 shell 在 repo root 執行 `source scripts/env.sh`。
- 雲端安裝指令依 Linux／系統安裝權限選擇是否使用 `DEV_TEMPLATE_INSTALL_SYSTEM_DEPS=1`；Start skill 使用 `docs/cloud-start-skill.md`，並明定使用現有隔離 checkout、不自行建立 worktree。
- 草稿儲存不等於發布。環境分享權限 Only me 應由環境設定確認；目前設定工具未提供分享權限欄位。
- 完成草稿設定後由使用者 Publish；在新 chat 核對 Start skill、grilling 發現與工具版本／browser smoke，才可聲稱新任務恢復已驗證。

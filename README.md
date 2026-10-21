# Three.js Mixamo 角色導入

by Deep Frame Studio

將 Mixamo FBX 角色、貼圖及動畫接入既有 Three.js 遊戲的 Agent Skill。支援依遊戲狀態對應任意數量的動畫；Idle／Run 只是例子。不需要先轉成 GLB，也不綁定角色、檔名或遊戲。

這是給 AI 開發工具使用的實作與驗收指引，不是可直接執行的模型匯入外掛。需要提供有使用權的模型及動畫；不包含角色素材或自動綁骨架服務。

## 安裝

使用 Node.js 與 npm，選擇你的 AI 開發工具：

```sh
npx skills add 00vchannel/threejs-mixamo-character-00vchannel --skill threejs-mixamo-character-00vchannel -g
```

ZCode 可加上 `-a zcode`。CLI 用法見 [Skills CLI](https://github.com/vercel-labs/skills)。

也可用 **Code → Download ZIP**，將完整的 `skills/threejs-mixamo-character-00vchannel` 資料夾放進 ZCode 的 `~/.zcode/skills/`，或 Codex 的 `~/.agents/skills/`。保留 `SKILL.md`、`agents/` 和 `references/`。在工具中重新整理 Skill 清單；檔案已下載不等於工具已載入。

更新前保留舊版及自行修改的內容，不直接覆蓋有修改的同名資料夾。本儲存庫沒有自動更新器。

## 使用

選取 `threejs-mixamo-character-00vchannel`，提供模型、動畫與所需狀態。例如：

> 使用 threejs-mixamo-character-00vchannel，把我現有 Three.js 遊戲的玩家換成提供的 FBX 角色與貼圖。站立播放 Idle，移動播放 Run；保留原本操作、碰撞、鏡頭、名字和手持物。先檢查素材及既有程式，再導入並實測。

其他動畫可直接指定，例如「跳躍播放 Jump，攻擊播放 Attack，完成後回到原狀態」。檔名不必一致；AI 應讀取實際動畫內容，設定循環、單次播放、中斷及回退行為。不要為沒有提出的動畫自行新增玩法。

## 驗證範圍與限制

- 新版指引已用實際 Idle／Run FBX 的 Three.js 整合案例檢查，涵蓋貼圖載入、動畫切換、獨立骨架、失敗處理及資源清理；另有本機雙客戶端同步與窄畫面操作檢查。
- 尚未完成實體手機、真正瀏覽器背景事件、第三種實際 FBX 動畫的驗證。場景暫停測試、窄視窗及合成動畫不能取代這些驗證。
- 不保證所有角色／骨架直接相容；不同骨架可能需要動畫重定向。持物姿勢可能需要額外動畫或 IK。每個遊戲仍須依 [驗收指引](skills/threejs-mixamo-character-00vchannel/references/acceptance.md) 實測。
- 尚未完成本發布版本在 ZCode 的實際安裝與載入驗證。

## 檔案

- [SKILL.md](skills/threejs-mixamo-character-00vchannel/SKILL.md)：導入流程與相容性處理。
- [acceptance.md](skills/threejs-mixamo-character-00vchannel/references/acceptance.md)：實際遊戲的驗收要求。
- `agents/openai.yaml`：Codex 顯示資訊；其他工具可忽略。

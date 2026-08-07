# Rogue Legacy 金币管理器 / Rogue Legacy Gold Tool

一个仅允许附加 `RogueLegacy.exe` 的 Windows 单进程工具。它不注入 DLL，不安装服务或驱动，不创建子进程，也不后台常驻。

A single-process Windows tool that only attaches to `RogueLegacy.exe`. It does not inject DLLs, install services or drivers, create child processes, or remain resident in the background.

## 程序说明 / Program Notes

1. 双击运行 `RogueLegacyGoldTool.exe` 即可。
   Double-click `RogueLegacyGoldTool.exe` to run it.
2. 该程序 100% 由 Codex GPT-5.6 Terra 生成。
   This program was generated entirely by Codex GPT-5.6 Terra.
3. 相关提示词和对话参考 `conversation.md` 和 `history.md`。
   Refer to `conversation.md` and `history.md` for the relevant prompts and conversation.

## 使用 / Usage

1. 启动《盗贼遗产》，选择角色，进入城堡内部。
   Start Rogue Legacy, select a character, and enter the castle.
2. 打开本程序并点击“连接 RogueLegacy.exe”。
   Open this tool and click “连接 RogueLegacy.exe”.
3. 输入当前金币，点击“首次扫描”。
   Enter the current gold value in “当前金币” and click “首次扫描”.
4. 在城堡内部获得金币，输入新金币数，点击“再次扫描”。
   Earn gold inside the castle, enter the new gold value, and click “再次扫描”.
5. 重复第 4 步至候选很少（测试时，在城堡内部只需要“首次扫描”加一次“再次扫描”，就只剩下一个地址）。
   Repeat step 4 until only a few candidates remain. During testing, while inside the castle, one “首次扫描” and one “再次扫描” left only one address.
6. 选中正确地址，输入目标值，点击“写入数值”。回到游戏检查金币是否改变。
   Select the correct address, enter the desired value in “目标金币”, click “写入数值”, and return to the game to verify that the gold changed.
7. 忽视“锁定金币”，我也不知道那是干啥的。
   Ignore the button “锁定金币”.
8. 成功后点击“退出并清理”（或窗口右上角关闭）。程序会停止锁定定时器、清空扫描状态并关闭游戏进程句柄，然后结束自身。
   After succeeding, click “退出并清理” (or close the window). The tool stops the lock timer, clears scan state, closes the game-process handle, and terminates itself.

请只在单机《盗贼遗产》运行时使用。退出工具并确认其进程消失后，再启动任何带反作弊的多人游戏。

Use this tool only while playing the single-player game Rogue Legacy. Exit it and confirm that its process is gone before starting any multiplayer game protected by anti-cheat software.
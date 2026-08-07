# 这是steam游戏盗贼遗产的游戏文件夹，帮我找到用户数据存放的地方，告诉我怎么改金币

> 这是steam游戏盗贼遗产的游戏文件夹，帮我找到用户数据存放的地方，告诉我怎么改金币

<details><summary>1 previous message</summary>

> Stream error
>
> Reconnecting 2/5
> request timed out
</details>

Model changed

gpt-5.6-sol -> gpt-5.6-terra

> 这是steam游戏盗贼遗产的游戏文件夹，帮我找到用户数据存放的地方，告诉我怎么改金币

<details><summary>5 previous messages</summary>

> Stream error
>
> Reconnecting 5/5
> request timed out
>
> 我会先只读检查游戏目录和本机常见存档位置，确认实际存档格式；不会直接改动你的存档。
>
> <details><summary>Ran a command</summary>
>
> - Ran `$roots = @('C:\Program Files (x86)\Steam\steamapps\common\Rogue Legacy','C:\Users\hzx\Documents','C:\Users\hzx\AppData\Local','C:\Users\hzx\AppData\Roaming','C:\Program Files (x86)\Steam\userdata'); foreach ($r in $roots) { if (Test-Path -LiteralPath $r) { Write-Output "[$r]"; rg --files "$r" 2>$null | Where-Object { $_ -match '(?i)(RogueLegacy|save|profile|player|slot|.rld$|.sav$)' } | Select-Object -First 80 } }`
>
> </details>
>
> 已定位到两个存档档位（Profile1、Profile2）；金币应保存在各档位的 `RogueLegacyPlayer.rcdat` 中。接着我会确认它是否能直接用文本修改，避免给你错误操作。
>
> <details><summary>Ran 2 commands</summary>
>
> - Ran `$p='C:\Users\hzx\Documents\SavedGames\RogueLegacy\RogueLegacyStorageContainer\AllPlayers'; Get-ChildItem -LiteralPath $p -Directory | ForEach-Object { Get-ChildItem -LiteralPath $_.FullName -Filter '*Player.rcdat' | Select-Object FullName,Length,LastWriteTime }; $f=Join-Path $p 'Profile1\RogueLegacyPlayer.rcdat'; $b=[System.IO.File]::ReadAllBytes($f); 'first64: '+(($b[0..63] | ForEach-Object { $_.ToString('X2') }) -join ' '); 'ascii strings:'; [Text.Encoding]::ASCII.GetString($b) -split '[^ -~]+' | Where-Object { $_.Length -ge 4 } | Select-Object -First 30`
> - Ran `$p='C:\Users\hzx\Documents\SavedGames\RogueLegacy\RogueLegacyStorageContainer\AllPlayers'; Get-ChildItem -LiteralPath $p -Directory | ForEach-Object { $q=Get-ChildItem -LiteralPath $_.FullName -Filter '*Player.rcdat' | Where-Object { $_.Name -notlike 'AutoSave*' } | Select-Object -First 1; [PSCustomObject]@{Profile=$_.Name; PlayerSave=$q.Name; Bytes=$q.Length; Modified=$q.LastWriteTime} } | Format-Table -AutoSize`
>
> </details>
</details>

存档位置已经找到：

`C:\Users\hzx\Documents\SavedGames\RogueLegacy\RogueLegacyStorageContainer\AllPlayers\`

你当前有两个档位：

- `Profile1`（较新，应该是正在玩的档）
- `Profile2`

每个档的核心人物存档是：

`...\Profile1\RogueLegacyPlayer.rcdat`

这个 `.rcdat` 是二进制格式，不能用记事本直接把金币数字改掉。最稳妥的方法是用 Cheat Engine 改内存：

1. 完全退出游戏，并备份整个 `Profile1` 文件夹。
2. 启动游戏，记下当前金币数，例如 `1234`。
3. 打开 Cheat Engine，选择 `RogueLegacy.exe` 进程。
4. 搜索类型选 `4 Bytes`，输入当前金币 `1234`，点击“首次扫描”。
5. 回游戏赚或花一些金币，比如变成 `1300`。
6. 回 Cheat Engine 输入新数值 `1300`，点“再次扫描”。
7. 重复“改变金币 → 再次扫描”，直到剩下极少数地址。
8. 双击正确地址到下方列表，修改为想要的金币数（如 `999999`）；回游戏触发一次存档即可。

注意：不要在游戏运行时直接编辑 `.rcdat`；而且 Steam 云同步可能会把旧存档覆盖回来。建议改完后正常退出游戏，确认金币已保存。

> cheat engine是什么

Cheat Engine（简称 CE）是 Windows 上的一个内存修改工具。它能在游戏运行时找到“金币、血量、经验”等数值在内存中的位置，然后临时改成你输入的值。

对《盗贼遗产》这种单机游戏，它比直接编辑二进制存档简单很多。

基本用法就是：

1. 开着游戏，记下当前金币。
2. CE 选中 `RogueLegacy.exe`。
3. 搜当前金币数。
4. 回游戏让金币变化。
5. 搜新金币数，逐步筛到正确地址。
6. 改为想要的数值。

建议只从 [Cheat Engine 官方网站](https://www.cheatengine.org/) 下载；安装时留意取消不需要的附加软件选项。

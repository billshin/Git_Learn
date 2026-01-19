# Git 後悔藥大全（救回你 99% 的手滑）

這份文件是一張 **Git 後悔藥對照表**，目的只有一個：

> **當你做錯 Git 操作時，知道該吃哪一顆藥。**

不是背指令，而是「情境 → 解法」。

---

## Git 最重要的觀念（先記住）

> **只要 commit 還在，幾乎都救得回來。**

真正危險的只有兩種情況：

* `git reset --hard`
* `git push --force` 強制

但就算這樣，也還有機會（靠 `reflog`）。

---

## 後悔藥速查表（最常用）

| 情境                | 後悔藥                    | 說明              |
| ----------------- | ---------------------- | --------------- |
| commit message 打錯 | `git commit --amend`   | 改訊息，不產生新 commit |
| commit 太早         | `git reset HEAD~1`     | 退回重新挑檔案         |
| 想合併多個 commit      | `git reset --soft`     | 保留暫存內容          |
| 檔案不該被 add         | `git restore --staged` | 從 staging 拿掉    |
| 檔案改壞了             | `git restore`          | 回到上次 commit     |
| commit 已推上遠端      | `git revert`           | 安全反向提交          |
| reset 後後悔         | `git reflog`           | 找回消失的 commit    |

---

## 1️⃣ commit message 打錯

### 情境

* 剛 commit 完發現訊息寫錯
* 還沒 push

### 解法（最安全）

```bash
git commit --amend -m "修正訊息"
```

* 只修改最後一個 commit
* 不改內容、不改歷史結構

---

## 2️⃣ commit 太早，想重新選檔案

```bash
git reset HEAD~1
```

效果：

* commit 消失
* 檔案回到 Working Directory

📌 常用於：

* 忘了加檔案
* 加了不該加的檔案

---

## 3️⃣ 想把多個 commit 合併成一個

```bash
git reset --soft HEAD~3
git commit -m "one clean commit"
```

📌 適合：

* 發 PR 前整理 commit

---

## 4️⃣ 不小心把檔案 git add 了

```bash
git restore --staged file.txt
```

* 只影響 Staging Area
* 檔案內容不會消失

---

## 5️⃣ 檔案改壞了，想全部丟掉

```bash
git restore file.txt
```

或整個專案：

```bash
git restore .
```

⚠️ 未 commit 的修改會消失

---

## 6️⃣ commit 已經 push 出去了（⚠️ 重點）

### ❌ 不要做

```bash
git reset --hard
git push --force
```

### ✅ 正確做法

```bash
git revert <commit-id>
```

* 產生一個「反向 commit」
* 不破壞歷史
* 團隊安全

---

## 7️⃣ reset --hard 後後悔了（救命）

```bash
git reflog
```

找到你要的 commit：

```bash
git reset --hard <commit-id>
```

📌 `reflog` 是 Git 的黑盒子紀錄

---

## 8️⃣ pull 之後整個亂掉

```bash
git reflog
git reset --hard ORIG_HEAD
```

* 回到 pull 前狀態

---

## reset / revert / restore 怎麼選？

| 指令      | 改歷史 | 安全性 | 常用時機   |
| ------- | --- | --- | ------ |
| reset   | ✅   | ❌   | 本機整理   |
| revert  | ❌   | ✅   | 已 push |
| restore | ❌   | ✅   | 檔案層級   |

---

## 新手保命三守則

1. **還沒 push 前，reset 很自由**
2. **已 push，一律先想 revert**
3. **不確定時先 reflog**

---

📘 一句話總結

> **Git 不怕你做錯，只怕你不知道怎麼救。**


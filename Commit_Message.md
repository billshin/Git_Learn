# Commit Message 速查表（單人 → 團隊通用）

> 目的：讓你現在寫得順、未來進團隊也能直接用

---

## 最小可用格式（推薦）

```
<type>: <一句話描述>
```

範例：

```
feat: add user login validation
fix: handle empty config file
```

---

## 常用 type（先記這 6 個）

| type     | 用途       | 範例                                     |
| -------- | -------- | -------------------------------------- |
| feat     | 新功能      | feat: add export to csv                |
| fix      | 修 bug    | fix: prevent crash when config missing |
| refactor | 重構（功能不變） | refactor: simplify auth logic          |
| docs     | 文件 / 筆記  | docs: add git branch notes             |
| test     | 測試       | test: add login unit tests             |
| chore    | 雜事 / 設定  | chore: update gitignore                |

---

## 單人開發實用加碼（非標準，但好用）

```
experiment: try async approach
spike: explore new library
```

> 進團隊前可逐步淘汰，現在用來標示「嘗試性修改」很清楚

---

## 好 vs 壞對照

❌ 不推薦

```
update
fix bug
test
```

✅ 推薦

```
feat: add password length check
fix: handle null pointer in auth service
docs: add mermaid flow examples
```

---

## 撰寫原則（記住這 3 點）

1. **現在式、動詞開頭**

   * add / fix / update / remove / refactor
2. **描述「為什麼改」**，不是列檔名
3. **一行看得懂**（未來的你或同事）

---

## 常見情境範例

### 新增功能

```
feat: add user permission check
```

### 修 bug

```
fix: prevent login when token expired
```

### 重構

```
refactor: extract auth service
```

### 學習筆記（很適合你）

```
docs: add git reset vs revert notes
```

---

## 進團隊的自然升級（之後再用）

```
feat(auth): add login validation
fix(api): handle empty payload
```

> scope 是加分，不是必須

---

## 自我檢查一句話

> 「三個月後我回來，這句話我看得懂嗎？」

看不懂 → 重寫一次。

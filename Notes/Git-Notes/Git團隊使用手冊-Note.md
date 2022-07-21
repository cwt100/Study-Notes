# Git團隊使用手冊-筆記
Update：2022/07/21<br/>

* [CH10：GitHub上的開放原始碼專案](#ch10github上的開放原始碼專案)
* [CH11：Bitbucket上的私人團隊作業](#ch11bitbucket上的私人團隊作業)
* [CH12：自行代管GitLab](#ch12自行代管gitlab)

---

## CH10：GitHub上的開放原始碼專案

1. 回饋成果：
- 使用Fork
- 將修改後的結果Push到Remote Repository
- Create pull request

<br/>

---

## CH11：Bitbucket上的私人團隊作業

1. Fork：僅允許私有fork
(需接受邀請，才允許直接存取所有的程式碼)
2. 提供wiki頁面以及issue
3. 存取控制：(不允許直接存取控制專案repository)
- 專案repository -> fork -> 個人repository
- 個人repository -> clone -> 本機repository
- 本機repository -> checkout -> 異動
- 異動 -> commit -> 本機repository
- 本機repository -> push -> 個人repository
- 個人repository -> pull request -> 專案repository

<br/>

---

## CH12：自行代管GitLab

```
提供儲存庫管理功能的開放原始碼程式碼代管系統
```

> 專案存取權限
- Guest 訪客
- Reporter 回報者
- Developer 開發者：可以在指定的分支記錄程式碼
- Master 管理者
- Owner 所有者：可以刪除專案

> 專案可視範圍
- 私有 (Private)
- 內部 (Internal)：所有能登入的使用者都能clone專案
- 公開 (Public)

<br/>

---


# Android 最佳化實作 Note

Update: 2022/08/11 <font color=yellow><b>(Doing)</b></font>

<br/>

## 項次

### [分析Android核心框架](#分析android核心框架) (2022/08/09)

### [為什麼需要最佳化](#為什麼需要最佳化) (2022/08/11)

### [Reference](#reference) <font color=yellow><b>(Doing)</b></font> (2022/08/09)


<br/>

---

## 分析Android核心框架

<br/>

### 生命週期

    優先權：foreground > visibile > service

#### 前台處理程序 (foreground)
#### 可見處理程序 (visible) 

    onPause()

#### 服務處理程序 (service)
#### 後台處理程序 (background)

1. onStop()
2. 系統可以任意終止
3. 使用[LRU](#lru)列表，確保當記憶體不足時，使用者最近看到的處理程序最後一個被終止
    
#### 空處理程序 (empty)

    可以加快啟動速度


</br>

---

## 為什麼需要最佳化

### 使用者體驗是產品成功的關鍵

> UX (User Experience) 國際標準

- ISO 9241-210 Human-centred design for interactive systems
- 可交互系統以人為中心的設計

#### 影響使用者體驗的因素

- 使用者的狀態
- 系統性能
- 環境狀況

#### 使用者體驗設計目標

- 有用
- 好用
- 人性化
- 視覺設計
- 品牌

<br/>

---

## Reference

### LRU
https://josephjsf2.github.io/data/structure/and/algorithm/2020/05/09/LRU.html

    Least Recently Used Cache (LRU)

- 一種快取的實作方式
- 儲存最近的內容
- 實作：Hash Map + Double Linked List (雙向鏈結串列)
 
    - 使用的內容，會被移置List前方
    - 快取滿了，會從list末端開始移除    


<br/>

### Double Linked List
https://www.codingsusu.com/java-datastructure-linkedlist/
(未讀)

### Dalvik
https://chloe-thhsu.medium.com/android-art-vs-dalvik-%E5%B7%AE%E5%88%A5-c69df49f0b31
(未讀)

### UX ISO 9241-210
https://dyfocus.com/science-all/48695a.html
(未讀)

---
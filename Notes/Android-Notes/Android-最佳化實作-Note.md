# Android 最佳化實作 Note

Update: 2022/08/09

<br/>

## 項次

### [分析Android核心框架](#分析android核心框架) <font color=yellow><b>(Doing)</b></font> (2022/08/09)

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

## Reference

### LRU
https://josephjsf2.github.io/data/structure/and/algorithm/2020/05/09/LRU.html
(Doing)

    Least Recently Used Cache (LRU)

- 一種快取的實作方式
- 儲存最近的內容
- 實作：Hash Map + Double Linked List
 
    1. 使用的內容，會被移置List前方
    2. 快取滿了，會從list末端開始移除    


<br/>

### Dalvik
https://chloe-thhsu.medium.com/android-art-vs-dalvik-%E5%B7%AE%E5%88%A5-c69df49f0b31
(未讀)

---
# Android 最佳化實作 Note

Update: 2022/11/25 <font color=yellow><b>(Doing)</b></font>

<br/>

## 項次

### [分析Android核心框架](#分析android核心框架) (2022/08/09)

### [為什麼需要最佳化](#為什麼需要最佳化) (2022/08/11)

### [UI版面配置最佳化](#ui版面配置最佳化) (2022/11/25)

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

## UI版面配置最佳化

### \<merge/>

- 一個佈局(A)包含另外一個佈局(B)時，且佈局(B)root layout 與佈局(A)相同時，可使用merge標籤，可減少一層root layout
- 有助於消除圖層結構中多餘的視圖組

#### Example：
- 修改前
```
a.xml
<FrameLayout>
    <include layout=@"layout/b">
</FrameLayout>

b.xml
<FrameLayout>
    <ImageView/>
</FrameLayout>

實際：
<FrameLayout>
    <FrameLayout>
        <ImageView>
    </FrameLayout>
<FrameLayout>

```
- 修改後
```
a.xml
<FrameLayout>
    <include layout=@"layout/b">
</FrameLayout>

b.xml
<merge>
    <ImageView>
</merge>

實際：
<FrameLayout>
    <ImageView>
</FrameLyout>

```

### bitmap圖片

#### 取得圖片原始高度、寬度
- Options inJustDecodeBounds = true
- outHight 原始高度
- outWidth 原始寬度

#### 設定縮放值
- 計算縮放值
- inSampleSize 設定縮放值
- Options inJustDecodeBounds = false (設定縮放值後，設為false)

<br/>

### ViewStub 延遲載入

- 不可見的
- 大小為0的View
- inflate or setVisibility() 時，才會產生
- infalte 僅能使用一次，故使用時需用try/catch，發生exception時，採用setVisibility(VISIBILE) 設定顯示
    > PS. 因呼叫inflate後，ViewStub會被移除且置換為要顯示之layout
- 尚未支援\<merge>

#### 適用場景：
頁面狀態切換管理，如：加載中、加載失敗、空資料等狀態，通常需風格一致且共用

#### 使用方式：
1. Layout
- 原本頁面：使用 \<ViewStub>
```
<LinearLayout>
    <Button>...</Button>
    <ViewStub
        android:id="@+id/stub"
        android:layout="@layout/customLayout"
        android:layout_width="300dip"
        android:layout_height="300dip">
    </ViewStub>
</LinearLayout>
```
- 需置換之UI，另定義layout.xml，如：customLayout
```
<LinearLayout>
    <Image>
    </Image>
    <TextView>
    </TextView>
</LinearLayout>
```

2. Activity

- onCreate()：Init
```
setContentView(R.layout.activity_main);
button = findViewById(R.id.button)
viewStub = (ViewStub) findViewById(R.id.stub)
```

- onClick()：真的需要顯示時
```
try{
    View customView = viewStub.inflate();
    textView = customView.findViewById(R.id.text);
    textView.text = "show"
}
catch(Exception oExp) {
    viewStub.setVisibility(VISIBLE);
}
```

<br>

### 建議
- 單一Activity：自定義視圖 <= 20，層數少於四層

---

## Reference

### LRU
https://josephjsf2.github.io/data/structure/and/algorithm/2020/05/09/LRU.html (DONE)

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

### ViewStub
- https://www.jianshu.com/p/175096cd89ac
- https://juejin.cn/post/6844903967252545544
- https://www.796t.com/content/1546670557.html
- https://cloud.tencent.com/developer/article/1597134

### lint 檢查項目改善程式碼
- https://developer.android.com/studio/write/lint (未讀)

---
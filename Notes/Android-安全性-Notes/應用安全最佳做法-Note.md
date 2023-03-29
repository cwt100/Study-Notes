# Android 應用安全最佳做法 Note

Update: 2022/07/28 (Doing)

* [實現安全通信](#實現安全通信)
* [提供適當的權限](#提供適當的權限)
* [Reference](#reference)

---

## 實現安全通信

    自己的App與其他App或網站之間交換的數據採取保護措施


### 使用隱式intent

    使用隱式intent方式，讓使用者開啟指定的信任App操作

> 隱式intent
* 不直接指定class name
* 使用intent action，彈跳出選擇器做處理

```
Intent intent = new Intent(Intent.ACTION_SEND);
List<ResolveInfo> possibleActivitiesList = getPackageManager().queryIntentActivities(intent, PackageManager.MATCH_ALL);

if (possibleActivitiesList.size() > 1) {

    // 使用特定名稱，讓選擇器指定開啟的App
    String sTitle = getResources().getString(R.string.chooser_title);
    Intent chooser = Intent.createChooser(intent, sTitle);
    startActivity(chooser);
} else {
    startActivity(intent);
}
```

> 官方不建議使用顯式intent開啟特定APP

<br/>

> permission 設定 protection 為 signature

    此權限不需要user確認，使用簽名檔檢核雙方是否可以做數據共享

- AndroidManifest.xml
```
<permission
    android:name="xxx.xxx.xxx"
    android:protectionLevel="signature"
/>
```

> android:protectionLevel

* normal：低風險權限
(有申請就可以使用，不需要使用者確認)

* dangerous：高風險權限
(需要使用者確認)

* signature
(簽名檔相同可以使用，不需要使用者確認)

* signatureOrSystem


<br/>

> provider exported 設為 false

    禁止提供content-provider給其他App使用

- AndroidManifest.xml
```
<provider
    android:name="xxx"
    android:exported="false"
>
</provider>
```

<br/>

### 顯示敏感訊息前請求提出憑證識別
* PIN碼
* 密碼
* 生物識別 (如：指紋辨識、臉部辨識)

<br/>

### 應用網路安全措施

> 使用SSL

> 增加網路安全設定

    在Application中填寫網路安全設定

1. AndroidManifest.xml

```
<Application
    ...
    android:networkSecurityConfig="xml/network_security_config"
    ...>
</Application>
```

2. res/xml/network_security_config.xml

    禁用http，設定使用https

```
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">secure.example.com</domain>
    </domain-config>
</network-security-config>
```

<br/>

### 謹慎使用webview

    非信任的內容，不要開啟javascript

<br/>

---

## 提供適當的權限

    僅提供維持正常運行所需的最低數量權限

### 使用 intent 轉移權限



<br/>

---

## Reference

* https://developer.android.com/topic/security/best-practices?hl=zh-cn#java
(Android document)

* https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/696369/
(隱式 intent)

* https://kknews.cc/zh-tw/tech/bxkknmj.html
(Android 權限管理)

* https://developer.android.com/training/articles/security-config?hl=zh-cn
(網路安全設定)
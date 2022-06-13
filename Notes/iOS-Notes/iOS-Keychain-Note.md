# iOS Keychain note
Update 2022/06/13

* [Notes](#notes)
* [Reference](#reference)

---
## Notes

> 主要提供之功能
* Add (新增)
* Query (查詢)
* Update (更新)
* Delete (刪除)

> 常使用之設定
* When Unlocked<br/>
    kSecAttrAccessibleWhenUnlocked<br/>
    裝置解鎖或沒有密碼(預設使用)

* When Passcode Is Set - This Device Only<br/>
    kSecAttrAccessibleWhenPasscodeSetThisDeviceOnly<br/>
    最高級別保護(有設定密碼才可以使用，不會寫入iCould)

---
## Reference

> 相關說明
* https://developer.apple.com/documentation/security/ksecclass?language=objc
* https://www.kaotenforensic.com/ios/ios-keychain-overview/
* https://juejin.cn/post/6844903921765318669
* https://www.slideshare.net/happymanx/ios-keychain (可以先看這篇)

> Sample - objc
* https://github.com/auth0/SimpleKeychain
* https://github.com/Cloudox/KeyChainTest

> Demo self - objc
* https://github.com/cwt100/keychain-demo-for-objc/tree/master



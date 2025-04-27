# Cordova APP 環境建置-筆記 (macOS)
Update：2024/06/24<br/>

---



## Node.js

1. Node.js 官網 (https://nodejs.org/en/download/package-manager)

- 選取要下載的版本與作業系統，可複製類似於以下指令之內容
- 請至終端機執行

ps. 建議下載LTS版本（長期維護版）

```
# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# download and install Node.js (you may need to restart the terminal)
nvm install 20

# verifies the right Node.js version is in the environment
node -v # should print `v20.15.0`

# verifies the right NPM version is in the environment
npm -v # should print `10.7.0`

```

## 安裝 Cordova

1. 終端機執行

```
npm install -g cordova
```

2. 如果失敗，可能為權限問題，調整使用sudo
```
sudo npm install -g cordova
```

<br/>

## JDK

Jdk or OpenJdk 擇一安裝

> JDK 11
- 官網下載
https://www.oracle.com/java/technologies/downloads/#java11

> AdoptOpenJDK
- 官網下載
https://adoptium.net/temurin/releases/?os=mac&arch=x64&package=jdk


## Android Studio




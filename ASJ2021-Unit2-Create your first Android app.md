[![hackmd-github-sync-badge](https://hackmd.io/D5UfrWmvQd6PH7937SuJ4g/badge)](https://hackmd.io/D5UfrWmvQd6PH7937SuJ4g)
###### tags: `Android`
# [ASJ2021] 從零開始學 Android（二）Unit 1: Kotlin basics for Android

[TOC]

+ 活動首頁：[Android App 開發培訓計劃 2021](https://events.withgoogle.com/android-study-jam-twhk-2021/?fbclid=IwAR0xD3_fgtD-IFMBup5x2Ff7L17KX4PcIwusSBcD9p-ik4OxeyTdGe16JTY)
+ 學習指南：[Android Study Jams 2021 操作手冊](https://docs.google.com/presentation/d/1qq72U1C22zMKRthk0oHPBL2nOjrpot1X8duWPhV0_es/edit?usp=sharing)
+ 學習教材：[Android Basics in Kotlin](https://developer.android.com/courses/android-basics-kotlin/course)

---

## 學習目標

#### Unit 1: Kotlin basics for Android 

+ [Create your first Android app](https://developer.android.com/courses/pathways/android-basics-kotlin-two) - 學習在 Android Studio 中建立並執行您的第一個 Android app。


## Android Studio 環境建置

+ 安裝 [Android Studio](https://developer.android.com/studio/index.html)，進入下載頁面會自動偵測使用者裝置的作業系統
+ 測試環境：準備 Android 行動裝置或使用模擬器（Emulator）

### 建立第一個 App

1. 開啟 Android Studio，選擇開啟新專案

![](https://i.imgur.com/VQ5xmzM.png)

2. 接著可選擇 Android Studio 提供的專案模板，這裡我們選的是 Empty Activity

![](https://i.imgur.com/76tvjcp.png)

3. 輸入專案資訊

![](https://i.imgur.com/LsYGhfS.png)

+ Name 專案名稱：`Happy Birthday`
+ Package name 應用程式的名稱
  + 用來讓 Android 系統識別 App
  + 預設會是專案名稱的小寫組合：`happybirthday`
+ Save location 儲存路徑
+ Language 語言：選擇 `Kotlin`
+ Minimum SDK 代表程式最低相容版本
  + 選擇 `API 19: Android 4.4 (KitKat)`
  + 點選底下的 Help me choose，可查看相容版本資訊

![](https://i.imgur.com/5DPFyhV.png)

+ 注意「不要」勾選底下的 `Use legacy android.support libraries`，避免新舊版本產生相容性問題

4. 完成後點選 Finish 建立專案，畫面如下：

![](https://i.imgur.com/209KTYL.png)

由左至右三個區塊分別是：

+ Project window 顯示專案路徑
+ Editing window 編輯視窗
+ What's New window 顯示更新訊息

5. 當視窗左下角顯示 `Gradle sync finished...`，代表專案已建立完成：

![](https://i.imgur.com/9a5xP0p.png)

## 建立模擬器 Emulator

接著我們要透過 [Android Virtual Device (AVD) manager](https://developer.android.com/studio/run/managing-avds)，在電腦安裝 Andorid Emulator（模擬器），即可針對不同裝置、型號，模擬開發環境測試。

![](https://i.imgur.com/uBFe1Nc.png)

+ 點選視窗中的 Create Virtual Device 建立虛擬裝置：

![](https://i.imgur.com/QBf2WbC.png)

+ Select Hardware 視窗：選擇不同類別（Category）的裝置，這裡以 Phone 類別中的 `Pixel 3 XL` 為例，選好後點選 Next：

![](https://i.imgur.com/JQwdIiF.png)

+ System Image 視窗：選擇虛擬裝置要運行的 Android 版本
  + 可選擇 Recommended 中的推薦版本；點選 x86 Images 或 Other Images 可查看更多版本
  + 注意各版本必須先 Download 才能使用

![](https://i.imgur.com/1YP3akO.png)

+ 安裝完成後點選 Finish，並點選 Next 進入下一步

+ Android Virtual Device (AVD) 視窗：可設定裝置資訊，點選 Finish 完成

![](https://i.imgur.com/QJruewz.png)

+ Your Virtual Device 視窗就會出現剛才建立好的虛擬裝置，即可關閉視窗

![](https://i.imgur.com/xKCfeLv.png)

### 如何在模擬器運行 App 

+ 在 Android Studio 視窗上方的工具列，有個虛擬裝置下拉選單：

![](https://i.imgur.com/9FoZ2da.png)

+ 也可以點選上方狀態的 `Run > Select Device...` 同樣可以開啟運行裝置的下拉選單：

![](https://i.imgur.com/cItjnRc.png)

+ 接著即可點選右側的綠色開始圖示 或點選 `Run > Run app` 運行 app，可能會需要一點時間
+ 虛擬裝置運行後會出現下方視窗，標題是 `Happy Birthday`，並顯示文字 `Hello World!`：

![](https://i.imgur.com/CZFOXMO.png)

### 如何在行動裝置運行 App

#### 1. 要讓 Android Studio 和行動裝置連線，必須先設定開發者選項：

+ 在 Android 裝置選擇 Setting > About phone
+ 點選 About phone > Build number 輸入密碼或 pin 碼授權
+ 回到 Setting 點選 System
+ 點選 Developer options（開發者選項）> 開啟 USB debugging（偵錯模式）

#### 2. 安裝 Google USB Driver（Window only）：
  + 在 Android Studio 點選 Tools > SDK Manager
  + 點選 SDK Tools，將  Google USB Drive 打勾後完成

#### 3. 在 Android 裝置運行 App：

+ 透過 USB 傳輸線連線裝置，允許 USB 偵錯模式
+ 在 Android Studio 點選 Run 運行 App
+ 接著會出現 Select Deployment Target 視窗，選擇與裝置對應的模擬器，即可在行動裝置安裝 app 並運行

## Android 專案結構

在 Android Studio 左側視窗，可查看 Android 專案結構：

![](https://i.imgur.com/6ibqmEZ.png)

app 專案結構如下：

+ manifests：記錄應用程式詳細資訊
+ java：存放 Java 程式原始碼
+ res
  + drawable：存放圖片等檔案
  + layout：存放介面設定 XML 檔
  + mipmap：存放應用程式圖形檔
  + values：存放參數設定 XML 檔
+ Grandle Scripts：存放 Grandle 相關檔案

點選 Android 下拉選單可切換成 Project Source Files 原始碼路徑：

![](https://i.imgur.com/oJcUlJ1.png)

## 小結

+ 建立新專案：開啟 Android Studio，點選  `+ Start a new Android Studio project`，可選擇模板和編輯專案資訊。 
+ 建立 Android 虛擬裝置：點選上方狀態列的 Tools > AVD Manager 建立裝置。
+ 在虛擬裝置運行 app：在狀態列的下拉選單選擇該虛擬裝置，點選綠色箭頭運行。
+ 查看專案路徑：在專案視窗的下拉選單選擇 Project Source Files。

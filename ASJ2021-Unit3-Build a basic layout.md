###### tags: `Android` `layout`
# [ASJ2021] 從零開始學 Android（三）Unit 1: Kotlin basics for Android

[TOC]

+ 活動首頁：[Android App 開發培訓計劃 2021](https://events.withgoogle.com/android-study-jam-twhk-2021/?fbclid=IwAR0xD3_fgtD-IFMBup5x2Ff7L17KX4PcIwusSBcD9p-ik4OxeyTdGe16JTY)
+ 學習指南：[Android Study Jams 2021 操作手冊](https://docs.google.com/presentation/d/1qq72U1C22zMKRthk0oHPBL2nOjrpot1X8duWPhV0_es/edit?usp=sharing)
+ 學習教材：[Android Basics in Kotlin](https://developer.android.com/courses/android-basics-kotlin/course)

---

## 學習目標

#### Unit 1: Kotlin basics for Android 

+ [Build a basic layout](https://developer.android.com/courses/pathways/android-basics-kotlin-three) - 透過建立一個生日賀卡的 app 來瞭解 Android 中使用者界面排版的基礎！

## 使用者介面 User Interfaces

使用者介面（User Interfaces）簡稱 UI，是使用者實際接觸產品的部分，主要由技術功能和視覺元素組成。

在 Android App 中，所有的使用者介面元素，均由 View 和 ViewGroup 所構成：

+ View 是介面上能和使用者互動的對象，這些 View 彼此之間也能相互影響
+ ViewGroup 則是用來存放 View 的容器

可參考以下示意圖：

![](https://i.imgur.com/eu598Zp.png)

## 佈局編輯器 Layout Editor

但我們通常不會直接用 View 和 ViewGroup 調整佈局，而是藉由撰寫程式碼來達成。

Android Studio 中的 Layout Editor（佈局編輯器）就提供了多種佈局來協助排版，常見的有：

+ FrameLayout：框架佈局
  + 透過設定父層 View 的`android:layout_gravity` 屬性定位子層View
+ LinearLayout：線性佈局
  + 透過 `android:orientation` 屬性指定，不允許各 View 相互重疊
+ RelativeLayout：相對佈局
  + 透過相對位置設定各個元件位置
+ ConstraintLayout：約束佈局
  + 透過物件本身與其它物件之間的約束，來決定物件位置，不會因裝置不同有太大差異
  + 在新版 Andorid Studio 為預設佈局，效能較佳

![](https://i.imgur.com/5zfqEfJ.png)

接下來，我們要透過 Layout Editor，把 app 介面上的 "Hello World!" 修改成 "Happy Birthday!"，以及練習如何編輯文字樣式。

撰寫Android 程式，通常由「`.xml` + `.kt`」構成一組畫面，類似於 iOS 的「`.swift` + `.xib`」的組合，分別代表：

+ .xml 檔案：設計畫面
+ .kt 檔案：用來定義方法，設計程式功能

切換到 `.xml`，可以看到 Layout Editor 的基本配置如下：

![](https://i.imgur.com/nXcwHKP.png)

+ (1) Project Window：查看專案路徑，可切換專案的排列方式
+ (2) Palette：元件庫，像調色盤的概念，裡面的元件皆可放到畫面上
+ (3) Component Tree：元件樹
+ (4) Design View：視覺預覽
+ (5) Bluepring View：設計藍圖
+ (6) Attributes：元件屬性設定

參考閱讀：

+ [Android入門教程：ConstraintLayout約束佈局](https://www.mdeditor.tw/pl/2ElE/zh-tw)
+ [Day4-Android APP 佈局](https://ithelp.ithome.com.tw/articles/10238517)

## 實戰：修改顯示文字

1. 開啟 `activity_main.xml` 檔案，位在專案路徑中的 app > res > layout 資料夾

![](https://i.imgur.com/oqs09gG.png)

2. 在 Component Tree 欄位，預設為 ConstraintLayout 佈局，底下有個 TextView，顯示預設文字為 `"Hello World!"`
3. 點選 `TextView` 之後，可看到右側的 Attributes 欄位，顯示詳細資訊
4. 找到 Declared Attributes 欄位，裡面包含了 text 屬性為 `Hello World!`，代表顯示在 TextView 上的文字

![](https://i.imgur.com/lsr8HVn.png)

5. 點選 text 屬性，並修改為 `Happy Birthday!`，按下 Enter 完成修改。此外，可看到畫面上出現黃色警告文字，我們會在下一章節解決這個問題：


![](https://i.imgur.com/MdvqS4y.png)

6. Design View 可看到修改結果，執行 app 同樣可看到更新後的文字

![](https://i.imgur.com/sbXSw9v.png)

### 實戰：在佈局新增 TextViews

1. 在 Layout Editor 選取 TextView，並按下 delete 鍵後可刪除該 TextView，同時會反應在 ConstraintLayout 視窗

![](https://i.imgur.com/JALAljY.png)

2. 在 Palette 視窗找到 Common or Text > TextView，並直接點選拖曳到 Design View，即可新增一個 TextView

![](https://i.imgur.com/YKrIiTX.gif)

3. 在 Component Tree 的 TextView 會發現出現一個紅色警告圖示，這是因為還沒被約束的 View，會在每次運行程式時出現在不同位置

![](https://i.imgur.com/bTX3DoK.png)

4. 因此要來定位剛才新增的 TextView，在右側的 Attributes 視窗找到 Constraint Widget 區塊，正方形代表目前的 view
5. 設定 top margin 和 left margin 為 16 dp，並將 Text 改成 `Happy Birthday,OOO!`
![](https://i.imgur.com/W1EEhG5.png)

> dp（density-independent pixels）：密度專屬像素，Android 的度量單位，會根據 dp 量化 UI 的大小

6. 同樣可新增一個 Textview 在右下角，設定 bottom margin 和 right margin 為 16 dp

![](https://i.imgur.com/1aRteVB.png)

7. 運行結果如下：

![](https://i.imgur.com/I138Abx.png)

### 實戰：新增 text 樣式

1. 點選 Component View 的 TextView，可在右側的 Attributes 視窗下方找到 Common Attributes
2. 打開 textAppearance 選單，即可修改 text 樣式，例如 fontFamily、textSize、textColor

![](https://i.imgur.com/bUlXKaX.png)

3. 運行結果如下：

![](https://i.imgur.com/xyPtpTN.png)

### 小結

+ 透過 Layout Editor 建立 Android 中的 UI，我們在 app 畫面中看到的幾乎是 View。
+ TextView 是一個用來顯示文字的 UI 元素。
+ ConstraintLayout 是一個用來裝其他 UI 元素的容器，在 ConstraintLayout 中的 Views 需約束水平和垂直關係
+ 可透過 margin 調整 View 的位置，代表 View 與容器邊界的距離。
+ 在 TextView 的 Attributes 視窗，可設定字型、大小和顏色。

---

## 如何在 Android app 新增圖片

1. 先到 [Github](https://github.com/google-developer-training/android-basics-kotlin-birthday-card-with-image-app-solution/blob/master/androidparty.png) 下載圖片 androidparty
2. 回到 Android Studio，點選 View > Tool Windows > Resource Manager，或直接在左邊的 Project 點選下方的 Resource Manager 標籤

![](https://i.imgur.com/sxaXmaS.png)

3. 點選 + 開啟選單，選擇 Import Drawables 剛才下載的圖片，接著選 Next 再 Import

![](https://i.imgur.com/FuCVUrS.png)

4. 成功匯入圖片後，即可在 app 中使用
5. 回到 Project 視窗，在專案路徑 app > res > drawable 確認是否有出現圖片

![](https://i.imgur.com/zDWB5M2.png)

### 實戰：新增一個 ImageView

1. 要在 app 顯示圖片，需要新增一個 ImageView 來放圖片
2. 從 Palette 的 Common 拉取一個 ImageView 到 Design View 中央
3. 在 Pick a Resource 視窗找到 androidparty，點選 OK 建立

![](https://i.imgur.com/SoqiUma.gif)

### 實戰：修改圖片大小與定位

1. 點選拖曳圖片到正中央，使邊框和粉紅色邊線對齊

![](https://i.imgur.com/x3ts6Bg.gif)

2. 或直接設定 Constraint Widget，margin 上下左右均為 0，即可將圖片置中

![](https://i.imgur.com/CFlD8h7.png)

3. 接著在 Constraint Widget 往下拉看到 Constraints section，選取 layout_width to 0dp (match constraint) 和 layout_height to 0dp (match constraint)

![](https://i.imgur.com/1sM039b.png)

4. 這樣 ImageView 就會和 app 畫面等寬高，但上下仍留有大量空白
5. 找到 scaleType 屬性設定圖片如何顯示，選擇 centerCrop，讓圖片維持原比例縮放

![](https://i.imgur.com/2s73drP.png)

6. 此時會發現圖片佔滿整個畫面，並遮住了文字，我們將會在下一步驟調整

### 實戰：調整元素前後順序

1. Component Tree 視窗，點選 ImageView 並拖曳到 TextViews 上方
2. 顯示結果如下：
![](https://i.imgur.com/SinKxtK.png)

> 假如拖曳效果失敗，可能是 Android Studio 需要更新。在實作過程不知為何無法拖曳，更新後就正常了！

### 實戰：修正警告訊息

在前面幾個步驟，可以看到 Android Studio 會顯示黃色三角的警告訊息，接下來我們要來進行修正。

#### HardcodedText

當我們在撰寫 app 時，程式會程式碼轉譯成別種語言。

![](https://i.imgur.com/jDOu0SM.png)

但是像 Hardcoded string（硬編碼字串）這類的程式碼，會直接將字串或數字直接寫入程式，較難進行轉譯或更動。

1. 點選警告圖示，可查看更多詳細資訊，以及建議如何修改：

![](https://i.imgur.com/NINCtKH.png)

2. 點選 Fix 後，會出現 Extract Resource 視窗
3. 將 Resource name 改成 `happy_birthday_text`，String resources 必須統一為英文小寫，並使用底線連接

![](https://i.imgur.com/6BGaRKL.png)

可以把 Resource name 想像成變數，而 Resource value 則是這個變數所代表的值。

4. 點選 OK 後，找到 Attributes 視窗的 text 屬性，會自動修改成`@string/happy_birthday_text`

![](https://i.imgur.com/A8S23Vv.png)

5. 開啟 app > res > values > strings.xml 檔案路徑，建立了一個 string resource 叫做 `happy_birthday_text`

![](https://i.imgur.com/kbFn3u0.png)

透過 strings.xml 檔案，我們能夠統一管理程式出現的字串，可重複使用，同時也能避免多國語系產生的編碼問題。

6. 用同樣的步驟，為 TextView 建立 string resource `signature_text`，完成後程式碼如下：

```kotlin=
<resources>
    <string name="app_name">Happy Birthday</string>
    <string name="happy_birthday_text">Happy Birthday, Heidi!</string>
    <string name="signature_text">From Liu.</string>
</resources>
```

### 實戰：提供無障礙服務

為了建立無障礙服務，Android 提供許多工具給使用者。像是 [TalkBack](https://support.google.com/accessibility/android/answer/6283677?hl=en) 無障礙工具，提供視障者透過語音導覽方式操作裝置。

1. 在 ImageView 顯示的警告訊息，說明圖片缺少 `contentDescription` 屬性：

![](https://i.imgur.com/uAM9zKV.png)

透過 content description（內容描述），可輔助 TalkBack 工具說明 UI 元素詳細資訊。

但也需注意，這張圖片在 app 中只是裝飾用途，因此可以讓 TalkBack 忽略這個 ImageView，方法如下：

2. 在 Attributes 視窗，滑到最下方的 All Attributes 區塊，找到`importantForAccessibility` 屬性並設定為 no，警告樣式就會消失了！

![](https://i.imgur.com/NLrWefP.png)

3. 運行結果如下：

![](https://i.imgur.com/81PmRzj.png)

### 小結

+ 透過 Android Studio  中的Resource Manager，可幫助新增和管理圖片或其他資源。
+ ImageView 是用來顯示圖片的 UI 元素。
+ ImageView 應該要有內容描述，以建立無障礙服務。
+ Text 字串必須統一由 string resource 替換使用，方便程式轉譯成其他語言，以及後續管理。
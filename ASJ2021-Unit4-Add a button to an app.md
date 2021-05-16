###### tags: `Android` `class`
# [ASJ2021] 從零開始學 Android - Unit 1-4: Kotlin basics for Android

+ 活動首頁：[Android App 開發培訓計劃 2021](https://events.withgoogle.com/android-study-jam-twhk-2021/?fbclid=IwAR0xD3_fgtD-IFMBup5x2Ff7L17KX4PcIwusSBcD9p-ik4OxeyTdGe16JTY)
+ 學習指南：[Android Study Jams 2021 操作手冊](https://docs.google.com/presentation/d/1qq72U1C22zMKRthk0oHPBL2nOjrpot1X8duWPhV0_es/edit?usp=sharing)
+ 學習教材：[Android Basics in Kotlin](https://developer.android.com/courses/android-basics-kotlin/course)

---

## 學習目標

#### Unit 1: Kotlin basics for Android 

+ [Add a button to an app](https://developer.android.com/courses/pathways/android-basics-kotlin-four) - 學習如何使用類別 (classes)、物件 (objects)、以及條件式 (conditionals) 來建立互動式的擲骰子 app。

## 1. Classes and object instances in Kotlin 類別與物件實體

在這個章節，我們會實作一個 Dice Roller Android app，在使用者擲骰子後，這個六面骰會隨機出現一面數字。

結果示意圖：

![](https://i.imgur.com/YWj2pvR.png)

接下來，為了熟悉新的程式觀念，我們將會使用線上的 Kotlin 開發工具 [kotlinplayground](https://developer.android.com/training/kotlinplayground) 來練習，稍後再將輸出結果匯入 Android Studio 介面使用。

學習目標：

+ 如何用程式生成隨機的數字來模擬擲骰子
+ 如何透過程式碼建立一個 Dice 類別，並具備變數和方法
+ 如何建立一個類別的物件實體，定義其變數，以及呼叫方法

### Roll random numbers 建立隨機數字

1. 開啟 [kotlinplayground](https://developer.android.com/training/kotlinplayground)，和先前章節一樣，寫下入口函式

```kotlin=
fun main() {

}
```

2. 建立 random function

資料型別除了數字 `Int` 和字串 `String` 以外，還有像是代表數字起始範圍的 `IntRange`，用來代表骰子可能的值，寫法為 `1..6` 用兩個點連接，數字範圍是從 `1` 到 `6`：

```kotlin=
fun main() {
	val dicRange = 1..6	// Kotlin range
    // 等同於 val diceRange: IntRange = 1..6
}
```

> 在程式中建立數字或字串時，不需特別定義 IntRange、Int 或 String 等型別，因為系統通常可直接判別資料型態。

3. 在 main() 定義一個變數 randomNumber
4. 對 dicRange 使用 random()，隨機產生一個數字並賦值給變數 randomNumber

```kotlin=
fun main() {
	val dicRange = 1..6
    val randomNumber = dicRange.random() // 隨機產生一個數字
    // 等同於 val randomNumber = (1..6).random()
}
```

4. 用 println() 印出結果

```kotlin=
fun main() {
	val dicRange = 1..6
    val randomNumber = dicRange.random()
    println("Random Number: ${randomNumber}") // 印出結果
}
// 印出 Random Number: 1~6 隨機數字
```

### Create a Dice class 建立一個骰子類別

試著想像有一個六面骰，每面具備相同特性。接下來我們將透過程式碼，描繪能夠骰出一個隨機數字的藍圖，這個藍圖在程式中被稱作類別（class），這段過程又叫做封裝（encapsulation）。

根據類別，我們可以實作出骰子的物件實體（object instances）。舉例來說，我們可以建立十二面骰或是四面骰。

實作步驟如下：

1. 定義骰子類別，命名慣例為駝峰式（Camel case），例如：`Dice`、`CustomerRecord`

```kotlin=
// 入口函式
fun main() {

}

// 骰子類別
class Dice {

}
```

2. 在 Dice class 裡面宣告一個變數 sides 代表骰子面數

```kotlin=
// 骰子類別
class Dice {
  val sides = 6
}
```

3. 根據 Dice class，在 main() 函式中建立一個名為 myFirstDice 的物件實體

```kotlin=
fun main() {
	val myFirstDice = Dice()
}

class Dice {
    var sides = 6
}
```

4. 這樣就建立了 myFirstDice 這個物件，並具備 class Dice 的特性，可透過 println() 印出 myFirstDice.sides，代表骰子物件的面數：

```kotlin=
fun main() {
    val myFirstDice = Dice()
    println(myFirstDice.sides)  // 印出 6
}

class Dice {
    var sides = 6
}
```

5. 建立擲骰子這個動作，可用方法 fun roll() 來表示：

```kotlin=
class Dice {
    var sides = 6

    fun roll() {

    }
}
```

6. 在 fun roll() 中建立一個隨機變數 randomNumber，範圍是 1 到 6：

```kotlin=
fun roll() {
     val randomNumber = (1..6).random()
     println(randomNumber)
}
```

7. 在 main() 入口函式中呼叫 roll() 方法

```kotlin=
myFirstDice.roll()
```

8. 完成後程式碼如下：

```kotlin=
fun main() {
  val myFirstDice = Dice()
  println(myFirstDice.sides)	// 印出骰子面數為 6
  myFirstDice.roll()	
}

class Dice {
  var sides = 6
    
  fun roll() {
  val randomNumber = (1..6).random()
    println(randomNumber)      // 印出隨機 1~6 的數字
  }
}
// 6
// 4
```

### Return your dice roll's value 回傳骰子值

1. 宣告一個變數 diceRoll 來存取 roll() 的回傳值

```kotlin=
val diceRoll = myFirstDice.roll()
```

在先前章節中，我們學到輸入的參數要先宣告型別；而同理回傳值也是相同道理，寫法如下：

2. 這裡要加上 roll() 回傳值型別，randomNumber 為數字 Int

```kotlin=
fun roll(): Int { ...
```

3. 執行程式碼，會出現以下錯誤訊息：

```
A 'return' expression required in a function with a block body ('{...}')
```

4. 這是因為 roll() 函式並沒有真的回傳一個型別為數字的值，只需把 println() 改為 return 回傳即可：

```kotlin=
fun roll(): Int {
     val randomNumber = (1..6).random()
     return randomNumber
}
```

5. 接著修改 main() 程式碼如下：

```kotlin=
fun main() {
	val myFirstDice = Dice()
    val diceRoll = myFirstDice.roll()	
    println("Your ${myFirstDice.sides} sided dice rolled ${diceRoll}!")
}

class Dice {
    var sides = 6
    
    fun roll(): Int { 
     val randomNumber = (1..6).random()
     return randomNumber	// 回傳值
	}
}
// 印出 Your 6 sided dice rolled 2!
```

### Change the number of sides on your Dice 修改骰子面數

因為骰子不一定是六面，可能會有各種形狀和面數的骰子。

1. 我們可以用 sides 這個變數來表示最大面數，也就是修改 `1..6` 這段 hard code，讓程式碼更有彈性

```kotlin=
val randomNumber = (1..sides).random()
```
2. 修改

```kotlin=
fun main() {
	val myFirstDice = Dice()
    val diceRoll = myFirstDice.roll()	
    // 六面骰子
    println("Your ${myFirstDice.sides} sided dice rolled ${diceRoll}!")
    
    // 改成二十面骰子
    myFirstDice.sides = 20
    println("Your ${myFirstDice.sides} sided dice rolled ${myFirstDice.roll()}!")
}

class Dice {
    var sides = 6
    
    fun roll(): Int { 
      val randomNumber = (1..sides).random()
      return randomNumber	// 回傳值
	}
}

// Your 6 sided dice rolled 3!
// Your 20 sided dice rolled 17!
```

### Customize your dice 客製化骰子

在真實世界中，通常無法直接去改變骰子面數：因此在物件導向的程式語言，我們也不會直接去改變現存的 Dice 物件實體，而是會建立一個符合需求的 new dice 物件實體。

1. 透過修改 Dice class 定義，使其能夠自訂面數的值 numSides

```kotlin=
class Dice(val numSides: Int) {
   // ...
}
```

2. 用 numSides 來取代原有的 sides 變數，修改後如下

```kotlin=
class Dice(val numSides: Int) {
    
    fun roll(): Int { 
     val randomNumber = (1..numSides).random()
     return randomNumber
	}
}
```

3. 這時執行程式碼會出現錯誤，因為我們還沒修改 main()，必須要傳入參數到 Dice()

```kotlin=
 val myFirstDice = Dice(6)
```

4. 調整程式碼，把 sides 變數改為 numSides

```kotlin=
fun main() {
	val myFirstDice = Dice(6)
    val diceRoll = myFirstDice.roll()	
    println("Your ${myFirstDice.numSides} sided dice rolled ${diceRoll}!")
}
```

5. 建立第二個骰子 mySecondDice，具有二十面

```kotlin=
val mySecondDice = Dice(20)
```

6. 完成後如下

```kotlin=
fun main() {
	val myFirstDice = Dice(6)   // 六面骰
    val diceRoll = myFirstDice.roll()	
    println("Your ${myFirstDice.numSides} sided dice rolled ${diceRoll}!")
    
    val mySecondDice = Dice(20) // 二十面骰
    println("Your ${mySecondDice.numSides} sided dice rolled  ${mySecondDice.roll()}!")
}

class Dice(val numSides: Int) {
    
    fun roll(): Int { 
     val randomNumber = (1..numSides).random()
     return randomNumber
	}
}

// Your 6 sided dice rolled 4!
// Your 20 sided dice rolled  15!
```

7. 再稍微精簡程式碼，去除多餘的部分，例如直接回傳 randomNumber 的值：

```kotlin=
fun main() {
	val myFirstDice = Dice(6)
    println("Your ${myFirstDice.numSides} sided dice rolled ${myFirstDice.roll()}!")
    val mySecondDice = Dice(20)
    println("Your ${mySecondDice.numSides} sided dice rolled  ${mySecondDice.roll()}!")
}

class Dice(val numSides: Int) {
    
    fun roll(): Int { 
      return (1..numSides).random()
	}
}

// 和修改前的輸出不會有差別
```

### 小結

+ 在 IntRange 數字範圍後使用 random() 函式，可產生一個隨機數字。
  + 例如：`(1..6).random()`
+ 類別（Classes）就像是物件（object）的設計圖，會擁有特性與狀態，可實作變數和函式。
  + 例如：`val mySecondDice = Dice(20)`、`myFirstDice.roll()`
+ 用 class 實例來表現物件，通常會是物理物件，像是骰子。我們可以對這個物件做動作，或是改變及特性。
+ 建立實例時可賦予值。
  + 例如：`class Dice(val numSides: Int)`，在建立實例 `Dice(6)` 時賦值。
+ 函式可以回傳東西，在函式定義時可指定資料型別。
  + 例如：`fun example(): Int { return 5 }`

---

## 2. Create an interactive Dice Roller app 

在這個章節，我們會使用 Android Studio，建立一個 Dice Roller Android app，讓使用者點擊 `Button` 擲骰子，並將結果顯示在螢幕中的 `TextView`。

結果示意圖：

![](https://i.imgur.com/pz9Xc1l.png)

學習目標：

+ 如何新增一個 `Button`，並新增 `Button` 點擊事件
+ 如何開啟和修改 `Activity` 程式碼
+ 如何顯示 `Toast` 訊息
+ 如何在 app 運行時更新 TextView 訊息

### Set up your app 建立新專案

和前面章節一樣，先建立一個新專案：

![](https://i.imgur.com/ruvqntv.png)

### Create the layout for the app 建立佈局

接下來我們需要在 `TextView` 底下新增一個 `Button`，兩者均會是父層 `ConstraintLayout` 底下的子層：

![](https://i.imgur.com/xpnGkR2.png)

1. 從 Palette 選取 Button，並拖曳到畫面中的 TextView 底下
2. 確認 Button 和 TextView 是否均為 ConstraintLayout 的子層
![](https://i.imgur.com/BDINtLG.png)

3. 可以看到 Button 右側出現紅色警告，提示必須設定水平垂直位置，點選 Button 上方的白色圓點，並拖曳到 TextView 底部

![](https://i.imgur.com/DM3ry4E.gif)

4. 這樣可直接設定 Button 的 Top → BottomOf textView 為 0dp

![](https://i.imgur.com/u5sRutU.png)

5. 同理，將 Button 左右兩側的圓點，分別拉到左右兩側的邊界，使 Button 在 ConstraintLayout 的水平中央位置

![](https://i.imgur.com/rs4XWv9.png)

6. 修改 Button 的文字，也就是 text 屬性為 Roll
7. 但此時會發現 Button 右側還有個黃色警告，和前面章節的 TextView 相同，可透過程式來幫我們修正
8. 點擊後下方會開啟 Message 視窗，點選底下的 Fix 修改，跳出抽出字串來源視窗，點選 OK

![](https://i.imgur.com/UJE5T5k.png)

結果如下，text 屬性會變成 `@string/roll`：

![](https://i.imgur.com/YAFI7Ln.png)

9. 編輯 TextView 樣式，調整字體大小，刪去預設的 text 內容，在底下有個板手的 tool text 屬性輸入 1

![](https://i.imgur.com/oYaQ4eb.png)

這個屬性只會在開發時顯示，假裝骰到的數字為 1，目的是方便編輯，不會出現在運行的程式：

![](https://i.imgur.com/lmDq0yA.png)

### Introduction to Activities 互動功能介紹

Andorid 提供了 android.app.Activity 這個類別，讓開發者能夠控制畫面以加速開發。每個 app 至少會有一個或更多的 activities，而最主要或層級最高的被稱作 MainActivity，由專案 template 提供。

在 MainActivity 中的程式碼，需要提供 Activity 的佈局細節，以及該如何產生互動，每個 Activity 都會有個特定目的。

舉例來說，在一個照片圖廊 app，可以有幾種 Activity 形式：

+ Photo Gallery 顯示多張圖片
+ View Photo 顯示單一圖片
+ Edit Photo 編輯圖片功能

![](https://i.imgur.com/DWOZlpY.png)

1. 開啟專案中的 MainActivity.kt 檔，路徑是 app > java > com.example.diceroller > MainActivity.kt，預設程式碼如下：

```kotlin=
package com.example.diceroller

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

// MainActivity 類別
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        // onCreate(): 第一次運行 app 時執行
        super.onCreate(savedInstanceState)
        // 載入佈局
        setContentView(R.layout.activity_main)
    }
}
```

透過設定允許自動 imports 套件功能，可以省下手動加入 import 的時間，即使沒有使用了也會自動移除該程式碼。

設定步驟如下：

+ 在 Android Studio 上方狀態列，點選 File > Other Setting > Setting for New Projects
+ 接著點選 Other Settings > Auto Import，看到 Java 和 Kotlin 兩區塊，將下方兩個選項都打勾：
  + Add unambiguous imports on the fly 自動匯入
  + Optimize imports on the fly  移除任何未使用的程式碼

![](https://i.imgur.com/abLngFt.png)

### Make the Button interactive 切換按鈕功能

接下來我們要實作按鈕的切換功能，點擊後會出現訊息：

![](https://i.imgur.com/GL5BlnC.png)

步驟如下：

1. 在 fun Create() 裡面加上 findViewById，用來找到 Button 物件，這個物件的 resouce ID 是 R.id.button，把 Button 的參考值（reference）存到變數 rollButton：

```kotlin=
override fun onCreate(savedInstanceState: Bundle?) {
   super.onCreate(savedInstanceState)
   setContentView(R.layout.activity_main)

   // 取得 Button 參考值並存入變數
   val rollButton: Button = findViewById(R.id.button)
}
```

當我們指派物件到一個變數時，Kotlin 並不會複製完整的物件，而是儲存物件的參考值，就像身分證用來識別一個人，但身分證並不是那個人本身。

2. 這時會發現 Button 是紅色的，因為還沒引入 Button 使用

![](https://i.imgur.com/3WpKken.png)

3. 可以手動 import 或點選 Button 後按下 Option+Enter(Mac)或Alt+Enter(Windows) 引入

![](https://i.imgur.com/Z7EAbZN.png)

4. 使用 rollButton 物件，並使用 setOnClickListener{...} 方法來監聽點擊事件

```kotlin=
rollButton.setOnClickListener {
  // do something
}
```

![](https://i.imgur.com/xbC64oE.png)

5. 透過呼叫 Toast.makeText 來印出文字 `"Dice Rolled!"`，再呼叫 toast.show() 顯示，Toast 物件同樣要引入使用

```kotlin=
val toast = Toast.makeText(this, "Dice Rolled!", Toast.LENGTH_SHORT)
toast.show()

// 上面兩行也可省去宣告變數，直接精簡成一行
Toast.makeText(this, "Dice Rolled!", Toast.LENGTH_SHORT).show()
```

完成程式碼如下：

```kotlin=
package com.example.diceroller

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button  // 引入 Button
import android.widget.Toast   // 引入 Toast

class MainActivity : AppCompatActivity() {

  override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    val rollButton: Button = findViewById(R.id.button)
    // 對 rollButoton 進行監聽點擊事件
    rollButton.setOnClickListener {
      // 點擊後要執行的事情：印出文字
      Toast.makeText(this, "Dice Rolled!", Toast.LENGTH_SHORT).show()
    }
  }
}
```

點選 Button 結果如下：

> 這裡有稍微卡住，需注意版本問題可能會無法顯示 Toast 內容！後面實作還是能正常顯示~_~

![](https://i.imgur.com/AHRPKU8.png)

當 Button 被點擊時，應該要更新 TextView，而不是顯示固定內容，要修改的地方如下：

1. 切換到 activity_main.xml，點選 TextView，記下 id 屬性的值：textView
2. 回到 MainActivity.kt，刪去剛才的 Toast 程式碼

```kotlin=
rollButton.setOnClickListener {
  
}
```
3. 同樣使用 findViewById 來找到 TextView，宣告一個變數 resultTextView 來儲存 TextView

```kotlin=
val resultTextView: TextView = findViewById(R.id.textView)
```

4. 設定這個變數 text 為 6

```kotlin=
resultTextView.text = "6"
```

完成後的程式碼：

```kotlin=
package com.example.diceroller

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val rollButton: Button = findViewById(R.id.button)
        rollButton.setOnClickListener {
            val resultTextView: TextView = findViewById(R.id.textView)
            resultTextView.text = "6"
        }
    }
}
```

運行結果如下：

![](https://i.imgur.com/8UivnLi.png)

### Add the dice roll logic 加上擲骰子邏輯

接著要加上我們在 Kotlin Playground 實作的擲骰子邏輯。

1. 在 MainActivity class 中，建立 Dice class，裡面會有 fun roll() 方法

```kotlin=
class Dice(val numSides: Int) {

   fun roll(): Int {
       return (1..numSides).random()
   }
}
```

會看到 numSides 底下有波浪號，如果將 numSides 設為 private（私有），numSides 這個變數就只能在 Dice class 裡面使用：相對於 public，我們會在下一個章節會提到。

![](https://i.imgur.com/Ql62kSP.png)

2. 將點擊事件要執行的內容改為 rollDice()

```kotlin=
rollButton.setOnClickListener {
   rollDice()
}
```

3. 接著要實作 rollDice() 方法

```kotlin=
private fun rollDice() {
    TODO("Not yet implemented")
}
```

4. 在 rollDice() 中刪去 TODO()，建立新的 Dice 物件實體，以及擲骰子邏輯

```kotlin=
private fun rollDice() {
    val dice = Dice(6)          // 建立一個六面骰
    val diceRoll = dice.roll()  // 呼叫 roll() 來搖骰，並用變數儲存結果
    val resultTextView: TextView = findViewById(R.id.textView)  // 找到 TextView
    resultTextView.text = diceRoll.toString() // 把 diceRoll 的值轉成字串，並賦值給 textView 
}
```

### 精簡程式碼與加上註解

+ Reformat Code：選取所有程式碼，並點選狀態列的 Code > Reformat Code，可以格式化程式碼，去除不必要的空格。

完成的程式碼如下：

```kotlin=
package com.example.diceroller

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView

/**
 * activity：讓使用者能夠擲骰子和看到結果
 */
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val rollButton: Button = findViewById(R.id.button)
        rollButton.setOnClickListener { rollDice() }
    }

    /**
     * 擲骰子和更新畫面上的結果
     */
    private fun rollDice() {
        // 建立句有六面的 Dice 物件，並呼叫 class 裡面的 roll() 方法
        val dice = Dice(6)
        val diceRoll = dice.roll()

        // 將擲骰子結果更新到畫面
        val resultTextView: TextView = findViewById(R.id.textView)
        resultTextView.text = diceRoll.toString()
    }

    /**
     * Dice 會有固定的面數值
     */
    class Dice(val numSides: Int) {

        // 回傳一個隨機數字，介於 1 到 numSides 之間
        fun roll(): Int {
            return (1..numSides).random()
        }
    }
}
```

運行結果，點選 ROLL 會隨機出現數字 1~6：

![](https://i.imgur.com/dL8dE1q.png)

### 小結

+ 透過 Layout Editor 新增一個 Button。
+ 修改 MainActivity.kt clas，新增 app 互動關係。
+ 彈出短暫的 Toast 訊息，可用來驗證程式邏輯。
+ 在 Button 監聽點擊事件，點擊時會執行 setOnClickListener() 裡面的行為。
+ 在 app 運行時，可透過元素呼叫方法來更新畫面，
+ 撰寫註解、統一程式碼風格均有助於多人協作。

---

## Add conditional behavior in Kotlin 新增條件狀態

我們能根據條件判斷，指定 app 做出對應的動作：而在 Kotlin 中的邏輯判斷使用的語法為 if、else 以及 when，當條件判斷的布林值為 true 時，才會執行大括弧內的程式碼：

```kotlin=
if (condition-is-true) {
    execute-this-code
}
```

以下方程式碼為例，假設有個變數為 4，經條件判斷後會執行 `num == 4` 內的程式碼：

```kotlin=
fun main() {
    val num = 4
    if (num > 4) {
        println("The variable is greater than 4")
    } else if (num == 4) {
        println("The variable is equal to 4")
    } else {
        println("The variable is less than 4")
    }
}

// The variable is equal to 4
```

### Create the Lucky Dice Roll game 建立擲幸運骰子遊戲

1. 接續上一章節的程式碼，我們要進一步新增功能

```kotlin=
fun main() {
    val myFirstDice = Dice(6)
    val diceRoll = myFirstDice.roll()
    println("Your ${myFirstDice.numSides} sided dice rolled ${diceRoll}!")
}

class Dice (val numSides: Int) {

    fun roll(): Int {
        return (1..numSides).random()
    }
}
```

2. 宣告變數 luckyNumber，用 if / else 條件判斷是否有出現幸運數字

```kotlin=
fun main() {
    val myFirstDice = Dice(6)
    val rollResult = myFirstDice.roll()
    val luckyNumber = 4

    if (rollResult == luckyNumber) {
        println("You win!")
    } else {
        println("You didn't win, try again!")
    }
}

class Dice (val numSides: Int) {

    fun roll(): Int {
        return (1..numSides).random()
    }
}
```

3. 或使用多個 else if 來對應所有可能結果，但注意開頭和結尾的 if 和 else 只能各一個

```kotlin=
fun main() {
    val myFirstDice = Dice(6)
    val rollResult = myFirstDice.roll()
    val luckyNumber = 4

    if (rollResult == luckyNumber) {
        println("You win!")
    } else if (rollResult == 1) {
        println("So sorry! You rolled a 1. Try again!")
    } else if (rollResult == 2) {
        println("Sadly, you rolled a 2. Try again!")
    } else if (rollResult == 3) {
        println("Unfortunately, you rolled a 3. Try again!")
    } else if (rollResult == 4) {
        println("No luck! You rolled a 4. Try again!")
    } else if (rollResult == 5) {
        println("Don't cry! You rolled a 5. Try again!")
    } else {
        println("Apologies! you rolled a 6. Try again!")
    }
}

class Dice (val numSides: Int) {

    fun roll(): Int {
        return (1..numSides).random()
    }
}
```

### Use a when statement 使用 when 判斷

透過上方程式碼，可以發現一旦有更多結果，會使程式碼更加冗長，這時可以透過 when 判斷句來解決。

1. 把剛才的 if / else 判斷改成 when

```kotlin=
fun main() {
    val myFirstDice = Dice(6)
    val rollResult = myFirstDice.roll()
    val luckyNumber = 4

    when (rollResult) {
      // do something
    }
}
```

2. 變數加箭頭，代表當 rollResult 和 luckyNumber 的值相同時，就執行後面的程式碼

```kotlin=
when (rollResult) {
  luckyNumber -> println("You win!")
}
```

3. 用相同的形式，完成當結果為 1-6 的程式碼，但是當骰到幸運數字 4 時，可以發現印出的字串會是 "You won!"

```kotlin=
fun main() {
    val myFirstDice = Dice(6)
    val rollResult = myFirstDice.roll()
    val luckyNumber = 4

    when (rollResult) {
        luckyNumber -> println("You won!")
        1 -> println("So sorry! You rolled a 1. Try again!")
        2 -> println("Sadly, you rolled a 2. Try again!")
        3 -> println("Unfortunately, you rolled a 3. Try again!")
        4 -> println("No luck! You rolled a 4. Try again!")
        5 -> println("Don't cry! You rolled a 5. Try again!")
        6 -> println("Apologies! you rolled a 6. Try again!")
    }
}

class Dice(val numSides: Int) {
    fun roll(): Int {
        return (1..numSides).random()
    }
}
```

### 小結

+ 使用 if 條件判斷是否要執行某些指令。例如：骰中幸運數字就印出中獎訊息。
+ Boolean 布林值型別的 true 和 false 可用來判斷結果。
+ 使用運算子比較值：大於 `>`、小於 `<`、等於 `==`。
+ 可使用 else if 進行多種條件判斷。例如：針對不同骰子結果進出對應訊息。而最後的 else 會包含所有未被指定的結果。
+ 使用 when 以 compact form 形式比較變數的值。

if-else 條件判斷：

```kotlin=
if (condition-is-true) {
  execute-this-code
} else if (condition-is-true) {
  execute-this-code
} else {
  execute-this-code
}
```

when 條件判斷：

```kotlin=
when (variable) {
  matches-value -> execute-this-code
  matches-value -> execute-this-code
  ...
}
```

## Add images to the Dice Roller app 新增圖片

除了用 TextView 顯示骰子的值，接下來我們要搭配剛才的 when 條件句，並使用圖片來顯示結果：

![](https://i.imgur.com/sfvGcXx.png)

學習目標：

+ 如何在程式運動時更新 ImageView
+ 如何透過 when 判斷句，自訂 app 顯示畫面結果

### Update the layout for the app 更新佈局

接著把 TextView 換成 ImageView，使用圖片來顯示結果。

1. 從元件樹移除 TextView，並從 Palette 新增一個 ImageView
2. 在視窗選擇 avatars，稍後我們會換成骰子的圖片，點選 OK 建立
![](https://i.imgur.com/ilAAjHN.png)

3. 調整 ImageView 水平垂直位置

![](https://i.imgur.com/6vmnne8.png)

### Add the dice images 新增骰子圖片

1. 從這裡 [URL](https://github.com/google-developer-training/android-basics-kotlin-dice-roller-with-images-app-solution/raw/master/dice_images.zip) 下載圖片檔，包含骰子數 1~6 共六張圖片
2. 點選 View > Tool Windows > Resource Manager，再點選 + 符號下拉選單，開啟 Import Drawables

![](https://i.imgur.com/csJ1Oo6.png)

3. 選取剛才六張圖片匯入，圖片會出現在 Resource Manager，路徑是 app>res>drawable

這些圖片的 resource ID 分別是：

```
R.drawable.dice_1
R.drawable.dice_2
R.drawable.dice_3
R.drawable.dice_4
R.drawable.dice_5
R.drawable.dice_6
```

### Use the dice images 使用骰子圖

接下來要替換掉剛才的 avatar 範例圖。

1. 點選 ImageView，找到屬性欄位的 tools srcCompat 屬性，改成 dice_1 並點選 OK，會發現圖片佔滿整個螢幕

![](https://i.imgur.com/kcSW1lU.png)

2. 調整 ImageView 的寬高，找到屬性視窗的  layout_width 和 layout_height 屬性，現在的值為 wrap_content
3. 將寬高改為固定值，分別是 height: 200dp 和 width: 160dp

![](https://i.imgur.com/2JyGOvC.png)

4. 修改 Button 的 top 距離為 16dp

![](https://i.imgur.com/XlmXorH.png)

這時如果想運行程式，會看到 Build failed 錯誤訊息：

![](https://i.imgur.com/bn9QvJ8.png)


這是因為我們剛才把 TextView 從佈局中移除，但 MainActivity.kt 還沒有修改：

![](https://i.imgur.com/e7YEsFF.png)

5. 移除有使用到 textView 的兩行程式碼
6. 匯入 ImageView，測試點擊後圖片是否有變成 dice_2

```kotlin=
    private fun rollDice() {
        // 建立句有六面的 Dice 物件，並呼叫 class 裡面的 roll() 方法
        val dice = Dice(6)
        val diceRoll = dice.roll()
        // 更新骰子圖片
        val diceImage: ImageView = findViewById(R.id.imageView)
        // 先固定為 dice_2 測試結果
        diceImage.setImageResource(R.drawable.dice_2)
    }

```

7. 點擊 Button 時，骰子圖片會變成兩點 dice_2

### Display the correct dice image based on the dice roll 設定對應的骰子圖片

我們可以透過 pseudocode（虛擬碼）來模擬程式邏輯：

+ if 骰到數字 1 時，顯示 dice_1 圖片
+ if 骰到數字 2 時，顯示 dice_2 圖片
+ etc...

轉換成 if / else 語法如下：

```kotlin=
if (diceRoll == 1) {
   diceImage.setImageResource(R.drawable.dice_1)
} else if (diceRoll == 2) {
   diceImage.setImageResource(R.drawable.dice_2)
}
 ...
```

或是更精簡的 when 語法：

```kotlin=
when (diceRoll) {
   1 -> diceImage.setImageResource(R.drawable.dice_1)
   2 -> diceImage.setImageResource(R.drawable.dice_2)
   ...
```

1. 修改後程式碼如下

```kotlin=
private fun rollDice() {
    // 建立句有六面的 Dice 物件，並呼叫 class 裡面的 roll() 方法
    val dice = Dice(6)
    val diceRoll = dice.roll()
    // 更新骰子圖片
    val diceImage: ImageView = findViewById(R.id.imageView)
    // 用 when 條件判斷
    when (diceRoll) {
        1 -> diceImage.setImageResource(R.drawable.dice_1)
        2 -> diceImage.setImageResource(R.drawable.dice_2)
        3 -> diceImage.setImageResource(R.drawable.dice_3)
        4 -> diceImage.setImageResource(R.drawable.dice_4)
        5 -> diceImage.setImageResource(R.drawable.dice_5)
        6 -> diceImage.setImageResource(R.drawable.dice_6)
    }
}
```

運行程式結果，擲骰的數字會對應到圖片：

![](https://i.imgur.com/wLipaVq.gif)

2. 上方程式碼其實可以再精簡，透過宣告 drawableResource 變數來替換掉重複的 diceImage.setImageResource：

```kotlin=
val drawableResource = when (diceRoll) {
   1 -> R.drawable.dice_1
   2 -> R.drawable.dice_2
   3 -> R.drawable.dice_3
   4 -> R.drawable.dice_4
   5 -> R.drawable.dice_5
   6 -> R.drawable.dice_6
}

diceImage.setImageResource(drawableResource)
```

但會發現 when 底下出現紅色波浪的錯誤訊息：

![](https://i.imgur.com/2e5nsI1.png)

3. 把數字 6 改為 else，即可包括非 1~5 的結果：

```kotlin=
val drawableResource = when (diceRoll) {
   1 -> R.drawable.dice_1
   2 -> R.drawable.dice_2
   3 -> R.drawable.dice_3
   4 -> R.drawable.dice_4
   5 -> R.drawable.dice_5
   else -> R.drawable.dice_6
}

diceImage.setImageResource(drawableResource)
```

4. 隨著每次的 diceRoll 結果，更新 ImageView 的內容敘述

```kotlin=
diceImage.contentDescription = diceRoll.toString()
```

### 設定初始圖片

在 onCreate() 中加上 rollDice()，當程式初始化時就會先擲一次骰子

```kotlin=
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val rollButton: Button = findViewById(R.id.button)
        rollButton.setOnClickListener { rollDice() }
        // Do a dice roll when the app starts
        rollDice()
    }
```

參考完整程式碼：[GitHub Repo](https://github.com/heidiliu2020/android-basics-kotlin-dice-roller-app)

### 小結

+ 使用 setImageResource() 修改 ImageView 顯示的圖片。
+ 使用 if / else 或 when 條件判斷句，根據不同結果執行對應的程式碼。
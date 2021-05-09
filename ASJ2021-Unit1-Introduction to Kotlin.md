[![hackmd-github-sync-badge](https://hackmd.io/QYyl-PnBS_6qGdsgeRG7ag/badge)](https://hackmd.io/QYyl-PnBS_6qGdsgeRG7ag)
###### tags: `Android` `Kotlin`
# [ASJ2021] 從零開始學 Android（一）Unit 1: Kotlin basics for Android

[TOC]

## 前言

這是用來記錄參加《Android App 開發培訓計劃》的學習筆記，也是我第一次接觸 App 開發。

最近工作上也需要和 App Team 合作，Web 端會使用到有關 Native SDK 提供的功能，就藉這個機會把基本觀念給補起來，如有錯誤歡迎指正！

+ 活動首頁：[Android App 開發培訓計劃 2021](https://events.withgoogle.com/android-study-jam-twhk-2021/?fbclid=IwAR0xD3_fgtD-IFMBup5x2Ff7L17KX4PcIwusSBcD9p-ik4OxeyTdGe16JTY)
+ 學習指南：[Android Study Jams 2021 操作手冊](https://docs.google.com/presentation/d/1qq72U1C22zMKRthk0oHPBL2nOjrpot1X8duWPhV0_es/edit?usp=sharing)
+ 學習教材：[Android Basics in Kotlin](https://developer.android.com/courses/android-basics-kotlin/course)

---

## 學習目標

#### Unit 1: Kotlin basics for Android 

+ [Introduction to Kotlin](https://developer.android.com/courses/pathways/android-basics-kotlin-one) - 學習使用 Kotlin 這個先進、且能幫助開發人員提高生產力的程式語言來寫程式。

## 關於 Andorid App

+ Andorid App：使用 Java 程式語言設計
+ Kotlin：於 2017 年由 Google 宣布成為 Android 官方開發語言
+ Android Studio：是 Android 平台開發程式的整合式開發環境（IDE），支援 Java 和 Kotlin 兩種程式語言

## Kotlin 入門實戰

我們可透過 Web 的程式碼編輯器 [Kotlin Playground](https://developer.android.com/training/kotlinplayground) 來練習 Kotlin 語法：

![](https://i.imgur.com/xseWfrO.png)

點選頁面中的綠色箭頭，即可運行編輯器中的程式碼：

```kotlin=
fun main() {
  println("Hello, world!")
}
// 印出 Hello, world!
```

+ fun：function 函式。
+ fun main()：main 為函式名稱，是程式的唯一入口（入口函式），後面接 `{}` 填入要實作的方法。
+ println()：印出參數，若傳入參數為字串，則必須加引號，否則程式會報錯：

![](https://i.imgur.com/XYVFU32.png)

修正後的輸出為：

![](https://i.imgur.com/uiFOIlb.png)

### `//` 撰寫註解 

在開發過程，我們可透過 `//` 為程式碼加上註解，這些反灰的文字不會影響程式運作，目的是讓未來的自己或其他開發者快速理解，提高程式碼的可讀性。

```kotlin=
fun main() {
    println("Happy Birthday, Teru!")
    
    // Let's print a cake!.
    println("   ,,,,,   ")
    println("   |||||   ")
    println(" =========")
    println("@@@@@@@@@@@")
    println("{~@~@~@~@~}")
    println("@@@@@@@@@@@")
    
	// This prints an empty line.
    println("")
    
    println("You are already 30!")
    println("30 is the very best age to celebrate!")
}
```

輸出結果如下：

![](https://i.imgur.com/wbjIN6E.png)

### Variables 變數

Kotlin 和其他程式語言一樣，可透過宣告變數來取代重複出現、或想要替換的文字。

舉例來說，在上述 main() function 中，我們可建立一個變數 age，程式碼寫法如下：

```kotlin=
val age = 5
```

+ 代表宣告一個變數 age 並賦值為 5
+ 使用 val 宣告的變數只能賦值一次，之後不可再改變
+ 使用 var 宣告一個可改變的變數

若要在 println() 中放入變數，則需加上錢字號和大括弧 `${variable}`，如以下範例：

```kotlin=
fun main() {
  val age = 25
  println("You are already ${age}!")
}
// 印出 You are already 25!
```

### Coding Convention 命名慣例 

在開發過程中，函式名稱和變數皆依循命名慣例：camelCase（駝峰式命名），這是為了統一程式碼風格，並提高可讀性。

改寫先前的範例：

```kotlin=
fun main() {
    printBorder()
    println("Happy Birthday, Haru!")
    printBorder()
}

fun printBorder() {
    println("=======================")
}
```

輸出結果如下，這樣的改寫稱為「重構」，可避免重複撰寫同樣的程式碼：

![](https://i.imgur.com/ZFhw2fs.png)

+ 延伸閱讀：[Kotlin style guide](https://developer.android.com/kotlin/style-guide)

### repeat() 重複執行

我們也可透過 repeat() 函式來執行需要重複的程式碼，這樣程式碼就只需要寫一次 `=` 符號：

```kotlin=
fun printBorder() {
  repeat(23) {
    print("=")  // 在同一行輸出
  }
  println()     // 換行輸出
}
```

重構之後會得到相同輸出結果：

![](https://i.imgur.com/EaQU8v6.png)

### 傳入參數的型別

在 function 傳入參數時，必須註記參數的型別，例如 `border: String` 表示變數 border 是 String 型別，否則程式會報錯：

```kotlin=
fun main() {
 	val border = ":"
    printBorder(border)
    println("Happy Birthday, Haru!")
    printBorder(border)
}
fun printBorder(border: String) {
    repeat(23) {
        print(border)
    }
    println()
}
```

輸出結果如下：

![](https://i.imgur.com/R0iWBEb.png)

我們也可傳入一個以上的參數，同樣必須標註該參數的型別，以宣告 timesToRepeat 變數（型別是 Int），取代重複次數為例：

```kotlin=
fun main() {
  val border = "`-._,-'"
  val timesToRepeat = 4
  printBorder(border, timesToRepeat)
  println("    Happy Birthday, Haru!")
  printBorder(border, timesToRepeat)
}

fun printBorder(border: String, timesToRepeat: Int) {
  repeat(timesToRepeat) {
    print(border)
  }
  println()
}
```

輸出結果如下：

![](https://i.imgur.com/LnZV8on.png)

### Nesting Loops 巢狀迴圈

接著我們要繼續完成生日蛋糕，預計輸出會長這樣：

```
 ,,,,,,,,,,,,,,,,,,
 ||||||||||||||||||
====================
@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@
```

程式碼範例：

```kotlin=
// 入口函式
fun main() {
  val age = 18
  val layers = 3
  printCakeCandles(age)        // 蛋糕蠟燭
  printCakeTop(age)            // 蛋糕頂部
  printCakeBottom(age, layers) // 蛋糕底部
}

// 蛋糕蠟燭: 18 根蠟燭
fun printCakeCandles(age: Int) {
  print (" ")
  repeat(age) {
      print(",")
  }    
  println() // Print an empty line   

  print(" ") // Print the inset of the candles on the cake
  repeat(age) {
      print("|")
  }    
  println()
}

// 蛋糕頂部
fun printCakeTop(age: Int) {
  repeat(age + 2) {
      print("=")
  }
  println()
}

// 蛋糕底部：用兩個 repeat() 實作巢狀迴圈
fun printCakeBottom(age: Int, layers: Int) {
  repeat(layers) {
      repeat(age + 2) {
          print("@")
      }
      println()
  }    
}
```

## 小結

+ 透過模板表達式在字串中傳入變數：`print("Hello, ${name}")`。
+ 使用 `val` 宣告的變數，一旦賦值就不能再改變，如：`val name = "QQ"`。
+ 函式可以傳入一個或以上的參數，如：`fun printCakeBottom(age: Int, layers: Int) {}`。
+ 實作 loop：使用 `repeat()` 可重複輸出傳入的參數。
+ 實作 Nested loops：`repeat(layers)` 裡再一層 `repeat(age)` 可決定重複輸出傳入參數幾次。

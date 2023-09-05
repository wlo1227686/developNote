Java 8 新特性
==================
*   [Lambda 表達式](#ch01)
*   [Lambda 表達式基本介紹](#ch02)
*   [Java 8 內置四大核心函數式接口](#ch03)
*   [Java 8 內置其他函數式接口](#ch04)
*   [Java 8 強大的Stream API](#ch05)
*   [Java 8 串型流 與 並行流](#ch06)
*   [Optional<T>類](#ch07)
*   [Java 8 接口(Interface)中的默認方法與靜態方法](#ch08)
*   [Java 8 全新的時間日期API](#ch09)


* * *
<h2 id="ch01">1. Lambda 表達式</h2>

Lambda表達式 : 是一段可以傳遞的代碼(將代碼像數據一樣進行傳遞)可寫出更簡潔，靈活的代碼。

&nbsp;&nbsp;範例1.&nbsp;&nbsp;透過Lambda表達式，完成升冪排序。
<br>![](img/img01.png)<br>

&nbsp;&nbsp;範例2.&nbsp;&nbsp;取當前公司員工年紀大於35歲的員工訊息，獲取當前公司員工薪水大於500的員工訊息。

&nbsp;&nbsp;&nbsp;&nbsp;方法一:&nbsp;&nbsp;將每項條件寫成一個方法來做調用。
<br>![](img/img02.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;方法二:&nbsp;&nbsp;透過策略設計模式，各個條件實作一個過濾器的抽象類，將攏長且重複的代碼收整。
<br>![](img/img03.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;方法三:&nbsp;&nbsp;透過匿名內部類，來完成實作類的部分。
<br>![](img/img04.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;方法四:&nbsp;&nbsp;透過Lambda表達式來實作以下方法。
<br>![](img/img05.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;方法五:&nbsp;&nbsp;透過Stream API。
<br>![](img/img06.png)<br>

—————————————————————
<h2 id="ch02">2. Lambda 表達式基本介紹</h2>
—————————————————————

<br>![](img/img07.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;語法格式一：&nbsp;&nbsp;無參數無返回值。
<br>![](img/img08.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;語法格式二：&nbsp;&nbsp;一個參數，無返回值。
<br>![](img/img09.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;語法格式三：&nbsp;&nbsp;多個參數，有返回值(多條語句)。
<br>![](img/img10.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;語法格式四：&nbsp;&nbsp;Lambda表達式的參數列表內的數據類型可以省略不寫。JDK1.8有改善(類型推斷:JVM編譯器通過上下文推斷出數據類型)
<br>![](img/img11.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;函數式接口：&nbsp;&nbsp;
<br>![](img/img12.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;Lambda表達式相關練習題：&nbsp;&nbsp;
<br>![](img/img13.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;1.&nbsp;&nbsp;
<br>![](img/img14.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2.&nbsp;&nbsp;
<br>![](img/img15.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3.&nbsp;&nbsp;
<br>![](img/img16.png)<br>

—————————————————————
<h2 id="ch03">3. Java 8 內置四大核心函數式接口</h2>
—————————————————————

<br>![](img/img17.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;1:&nbsp;&nbsp;Consumer&lt;T&gt;
<br>![](img/img18.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2:&nbsp;&nbsp;Supplier&lt;T&gt;
<br>![](img/img19.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3:&nbsp;&nbsp;Function&lt;T&gt;
<br>![](img/img20.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;4:&nbsp;&nbsp;Predicate&lt;T&gt;
<br>![](img/img21.png)<br>

—————————————————————
<h2 id="ch04">4. Java 8 內置其他函數式接口</h2>
—————————————————————

<br>![](img/img22.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;1:&nbsp;&nbsp;Lambda體-方法引用
<br>![](img/img23.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2:&nbsp;&nbsp;Lambda體-構造器引用
<br>![](img/img24.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3:&nbsp;&nbsp;Lambda體-數組引用
<br>![](img/img25.png)<br>

—————————————————————
<h2 id="ch05">5. Java 8 強大的Stream API</h2>
—————————————————————

<br>![](img/img26.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;1:&nbsp;&nbsp;創建Stream
<br>![](img/img27.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2:&nbsp;&nbsp;中間操作<br>
&nbsp;&nbsp;&nbsp;&nbsp;2-1:&nbsp;&nbsp;篩選與切片
<br>![](img/img28.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2-2:&nbsp;&nbsp;映射<br>
&nbsp;&nbsp;&nbsp;&nbsp;2-2-1:&nbsp;&nbsp;map()映射
<br>![](img/img29.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2-2-2:&nbsp;&nbsp;flatMap()映射
<br>![](img/img30.png)<br>
<br>![](img/img31.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;2-3:&nbsp;&nbsp;排序<br>
<br>![](img/img32.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3:&nbsp;&nbsp;終止操作<br>
<br>![](img/img33.png)<br>
<br>![](img/img34.png)<br>
<br>![](img/img35.png)<br>
<br>![](img/img36.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3-2:&nbsp;&nbsp;歸約<br>
<br>![](img/img37.png)<br>

&nbsp;&nbsp;&nbsp;&nbsp;3-3:&nbsp;&nbsp;收集<br>
<br>![](img/img38.png)<br>
<br>![](img/img39.png)<br>

—————————————————————
<h2 id="ch06">6. Java 8 串行流 與 並行流</h2>
—————————————————————

<br>![](img/img40.png)<br>

—————————————————————
<h2 id="ch07">7. Optional&lt;T&gt; 類</h2>
—————————————————————

<br>![](img/img41.png)<br>
<br>![](img/img42.png)<br>

—————————————————————
<h2 id="ch08">8. Java 8 接口(Interface)中的默認方法與靜態方法</h2>
—————————————————————

接口(Interface)多實現，類別(class)單繼承

<br>![](img/img43.png)<br>

—————————————————————
<h2 id="ch09">9. Java 8 全新的時間日期API</h2>
—————————————————————

<br>![](img/img44.png)<br>
<br>![](img/img45.png)<br>
<br>![](img/img46.png)<br>
<br>![](img/img47.png)<br>

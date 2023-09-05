# Removable_USB_Drive_MacOS
製作一支ＭacOS USB :<br>
  1.準備一隻空的USB (至少8G)<br>
  2.MacOS 安裝程式<br>
<br><br>
步驟一：<br>
  開啟App Store 下載 mac os Sierra 安裝程式<br><br>
![](img/img01.jpg)<br><br>
步驟二：<br>
  製作一支USB<br>
  Launchpad -> 其他 -> 磁碟工具程式 -> 清除 <br>
  格式依照下圖（名稱隨意）<br><br>
![](img/img02.jpg)<br><br>
步驟三：<br>
  準備2個Finder視窗<br>
  <br>
   1.Finder -> 應用程式<br>
      (找到 安裝 macOS Sierra)<br> 
   2.安裝 macOS Sierra 對圖示按右鍵 -> 顯示套件內容 -> Contents -> Resources<br>
      (找到Createinstallmedia)<br>
   3.開啟終端機<br>
      <依照下圖排列視窗> <br>
![](img/img03.jpg)<br><br>
步驟四：<br>
 按下步驟在終端機輸入(不包含"")<br>
  1."sudo "<br>
  2.將Createinstallmedia 拖入終端機(路徑會自行輸入)<br>
  3." --volume "<br>
  4.將 USB 拖入終端機(路徑會自行輸入)<br>
  5." --applicationpath "<br>
  6.將 安裝 macOS Sierra 拖入終端機(路徑會自行輸入)<br>
  <結果如下圖><br>
![](img/img04.jpg)<br><br>
步驟五：<br>
  1.按下Enter送出<br>
  2.輸入密碼 <br>
  3.輸入 "y" <br>
  4.一直等待大約半小時(看電腦狀態)<br>
    <結果如下圖><br>
![](img/img05.jpg)<br><br>
步驟六：<br>
<完成的結果如下圖><br>
![](img/img06.jpg)<br><br>
ps:<br>
因為會等很久,你可以點開USB的簡介觀察已使用量慢慢的變大 <br><br>
![](img/img07.jpg)<br><br>
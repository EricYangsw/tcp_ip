# TCP/IP
本篇是基於以下這本好書為主軸，所紀錄的心得：

![TCP/IP Book](/image/tcp_ip_book.jpeg)


### 為什麼想看這本書：
---------------------
1. 現今IT發展已經脫離不了網路通訊，包含各種數據處理也是需要透過網路進行各種活動，而TCP/IP毫無疑問是現今最普遍的標準協定。


2. 處理資料的軟體工具(Kafka、Elastic Search、all kind of Data Base....等），大多是基於TCP/IP傳輸層上另外設計應用層的協定，雖然不了解網路協定還是可以使用這些工具，但了解網路協議有助於更深入了解這些工具，例如：

  * 案例1.Docker 的 Bridge 模式網路建立就是利用Sanbox的虛擬化技術在網路層(IP）建立一組虛擬IP，有這認知，在部屬多容器上可以更深入的理解。
[深入浅出”来解读Docker网络核心原理](http://blog.51cto.com/ganbing/2087598)
    
  * 案例2.Kafka就是基於TCP上另外建立應用層的通訊協定，以便達到"multiplex requests, the ability to simultaneously poll many connections"...等目的。    
[The Explanation Behind The Protocols That Kafka Is Using](https://streamdata.io/blog/explanation-behind-protocols-that-kafka-is-using/)
  
  
  
### 什麼是網路協定?
-----------------
  * 前導-網際網路(Internet)：已經變成是一個專有名詞，表示為連接全世界電腦的網路。      
  * 前導-網路的應用層：www、HTTP、FTP、Email...等都是建立在網際網路上最頂層的應用。        
  * 協定：網際網路能夠實現通訊，就是依靠大家都認同的機制來達成，這些機制統稱為協定，而協定因為作用不同也有分高低的層次,通訊兩方同層次會盡量作到可以
         獨立變動，但以整體通訊角度來看，上層的功能需要以下層功能為基礎才能達到網路通訊目的，以電話為例，電話互相連結機制是一種基礎的協定;聲音傳遞
         機制是層次較高的協定;語言(中文）是更高層次的溝通協定，語言層次可以隨意更換(中文換英文）而不影響
         下層電話本身的通訊，反之改用對講機的話也不影響語言的選定。
                 
  * OSI參考模型：分層架構有很多的好處，但網路通訊比電話複雜許多，而最理想化的理論模型就是OSI的7層架構，雖然目前所用的TCP/IP不是用此架構，TPC/IP
    可以當成是一種比較實務的分層架構，可以視為OSI 7層的簡化，但是每一層的功能大致可以互相對應。
 
![分層概念](/image/abc_layer.jpg)   
![OSI 7 layer](/image/osi_explain.jpg)
     
       
       
### 什麼是TCP/IP 網路協定?
------------------------
  * TCP/IP:基本上，就是以IP網路層協定為基礎，往上層另外延伸的協定群的集合總稱，所以其不只是某一個協定名稱而已。    
  ![OSI分層模型](/image/layer_fram.jpg)
  
  * 重要觀念-封包(Packet):因應充分運用網路線路，以及預防網路斷訊風險...等考量，網路傳輸放棄在兩端點的電路交換網絡，改而提出封包交換網絡，
     而TCP/IP協定就是採用封包交換來傳遞資料，也就是將資料分拆成無數個小片段，僅在資料片段開頭加上各層的重要資訊(又稱表頭)後,其讓端點負責重組封包並在遺失封包時提出要求，這大幅簡化網路本身功能的舉動反而成功整合了各種不同的網絡。
  
  * 網路層：IP(Internet Protocol)就是TCP/IP協議的重要基礎，IP讓網路任兩台電腦可以互相連結並傳遞封包，可以把IP想像成電話線路，IP號碼就是電話號碼，封包就是講話的音訊片段。
  
  * 傳送層：傳送層就是基於IP層上，進一步建立各種應用程式間的通訊協定（Email, HTTP, FTP...等），而連接埠(Port)就是用來辨別應用程式用的，本層最常見的協定就是TCP,UDP
  
  * 應用層：直接以HTTP為例，www所有網頁能夠隨時連結的重要系統，它讓網路上的資料以超文字(HyperText)提供資料的系統，其中HTML就是這系統上主要的共用資料形式，而HTTP就是以www為基礎的重要應用協定，讓所有使用者可以透過瀏覽器來獲取網路上的資訊，以上所述都是以TCP為基礎的應用層協定;另位當然還有E-mail,FTP...等不同的應用。
  
  
          
 ### 什麼是 Socket?
 -------------------
  * 學習網路通訊編程，常常是以Socket套件操作開始，其實Socket不是一個層，而是UNIX系統下利用網路通訊的一種接口,本質上就是一個介面程式(Interface)，介於TCP層和應用層之間，目的是把TCP/IP封裝好，讓應用層的協定可以方便快速的使用TCP/IP協定; 以一般的程式操作角度來看，大家可以把Socket當作是(抽象為)對於檔案I/O的一個操作

![socket](/image/socket.jpg)

以下是用Python的Socket模組建立簡單的Client & Server互動範例：
       
[Simple TCP server by Python Socket Module](https://github.com/EricYangsw/tcp_ip/blob/master/server_client/simple_tcp_server.ipynb)

[Simple TCP Client by Python Socket Module](https://github.com/EricYangsw/tcp_ip/blob/master/server_client/simple_tcp_client.ipynb)


### TCP/IP資料傳送流程：
---------------------
![TCP/IP Flow](/image/tcpip_flow.jpg)
      
以上圖為例，以下簡述TCP/IP資料傳送流程，
1. 最上層使用者注重的是文字內容的表達，而在按下傳送後，E-mail應用程式處理通訊部份就開始工作，應用程式會決定這封信該怎麼使用下層TCP的協定來傳送，例如：是整間公司累積5封信後一起傳送？還是一封一封各自傳送，Email是否要依照特定格式去寫...等，都是應用層的決定範圍。
2. 下層TCP協定接收到上層信件的資料後，開始將資料處理成封包並加上TCP的表頭後往下IP層傳遞，而TCP這裡主要的功用就是建立讓這資料可以在相通的E-mail程式去通訊，並且為了保證所有封包對方都可以收的到，TCP另外會先確認對方是否有連線，並且在最後確認封包都有收到沒有遺漏...等，這些動作都是IP層沒有作到的。
3. IP層接收到資料後會加上IP層的表頭，並且想辦法把資料送到對方的電腦(非應用程式），當中怎麼靠IP找到對方電腦都是IP層負責處理的，可以想像成IP層就像電話，其負責可以連到另一個電話，但聲音要怎麼保證清楚的傳過去則是靠上層的TCP協定處理。
4. IP層以下就是實際網路線跟電腦透過網卡將資料傳到網路現中可以接受的資料



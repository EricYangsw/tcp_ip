# TCP/IP
本篇是基於以下這本好書為主軸，所紀錄的心得：

![TCP/IP Book](/image/tcp_ip_book.jpeg)


### 為什麼我想看這本書：
---------------------
1. 現今IT發展已經脫離不了依靠網路來通訊，包含各種數據處理也是需要透過網路進行各種活動，而TCP/IP毫無疑問是現今最普遍的標準協定。


2. 處理資料的軟體工具(Kafka、Elastic Search、all kind of Data Base....等），很多是基於傳輸層上另外因應需求而設計應用層的協定（對比網頁使用的HTTP)，雖然不了解網路協定還是可以使用這些工具，但了解網路協議有助於更深入了解這些工具，例如以下的理解：


  * 案例1.Docker 的 Bridge 模式網路建立就是利用Sanbox的虛擬化技術在網路層(IP）建立一組虛擬IP，有這認知，在部屬多容器上可以更深入的理解。
[深入浅出”来解读Docker网络核心原理](http://blog.51cto.com/ganbing/2087598)
    
  * 案例2.Kafka就是基於TCP上建立自己的通訊協議，以便達到"multiplex requests, the ability to simultaneously poll many connections"...
[The Explanation Behind The Protocols That Kafka Is Using](https://streamdata.io/blog/explanation-behind-protocols-that-kafka-is-using/)
  
  
  
### 什麼是網路協定?
-----------------
  * 前導-網際網路(Internet)：已經變成是一個專有名詞，表示為連接全世界電腦的網路。      
  * 前導-頂層應用：www、HTTP、FTP、Email...等都是建立在網際網路上最頂層的應用。        
  * 協定：網際網路能夠實現，就是依靠大家都認同的機制來達成，這些機制統稱為協定，而協定因為作用不同也有分層次,
      類比：電話互相連結機制是一種基礎的協定; 聲音傳遞機制是層次較高的協定; 語言(中文）是更高層次的溝通協定;        
  * OSI參考模型：以上分層架構有很多的好處，例如語言層次可以隨意換，而不影響電話本身的通訊，反之改用對講機的話也不影響語言，套用在網路通訊上層次會複雜很多，最理想化的理論模型就是OSI的7層架構。
  * TPC/IP可以當成是一種比較實務的分層架構，可以視為OSI 7層的簡化，但是每一層的功能大致可以互相對應。

![分層概念](/image/abc_layer.jpg)   
![OSI 7 layer](/image/osi_explain.jpg)

### 什麼是TCP/IP 網路協定?
------------------------
  * TCP/IP:就是利用IP這個較低層次的協定來進行通訊，所需要使用到的各種協定的集合總稱。    
  ![OSI分層模型](/image/layer_fram.jpg)
  
  * 重要觀念-封包(Packet):為了充分運用網路線路，以及預防網路斷訊...等，網路傳輸放棄在兩端點的電路交換網絡，改而提出封包交換網絡，而TCP/IP協定就是採用封包交換來傳遞資料，也就是將資料分拆成無數個小片段，僅在資料片段開頭加上各層的重要資訊(又稱表頭),其讓端點負責重組封包並在遺失封包時提出要求，大幅簡化網路的功能，成功讓。
  
  * 網路層：IP(Internet Protocol)就是TCP/IP協議的重要骨幹，IP讓讓兩台電腦可以互相連結並傳遞封包，可以把IP想像成電話線路，IP號碼就是電話號碼，封包就是講話的音訊片段。
  
  * 傳送層：傳送成層就是基於IP架構上，進一步建立各種應用程式間的通訊協定，例如：Email, HTTP, FTP...等，而連接埠(Port)就是用來辨別應用程式用的，本層最常見的協定就是TCP,UDP
  
  
  
 ### 什麼是 Socket?
 -------------------
  * 常聽到的Socket不是一個層，而是UNIX系統下利用網路通訊的一種接口,本質上就是一個介面程式(Interface)，介於TCP層和應用層之間，目的是把TCP/IP隱藏，讓應用層可以方便快速的使用TCP/IP協議，一般的程式操作上，大家可以把Socket當作是(抽象為)對於檔案I/O的一個操作

![socket](/image/socket.jpg)

[Simple TCP server by Python Socket Module](https://github.com/EricYangsw/tcp_ip/blob/master/server_client/simple_tcp_server.ipynb)

[Simple TCP Client by Python Socket Module](https://github.com/EricYangsw/tcp_ip/blob/master/server_client/simple_tcp_client.ipynb)

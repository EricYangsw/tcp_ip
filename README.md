# TCP/IP
本篇是基於以下這本好書為主軸，所紀錄的心得：

![TCP/IP Book](/image/tcp_ip_book.jpeg)


### 為什麼我想看這本書：
1.現今IT發展已經脫離不了網路，包含處理各種數據也是需要透過網路進行各種活動，TCP/IP毫無疑問是現今網路協定的標準。

2.許多處理資料的軟體工具(Kafka、Elastic Search、all kind of Data Base....等），很多是基於傳輸層之上，然後另外因應需求而設計應用層的協定（對比網頁使用的HTTP)，雖然不了解網路協定還是可以使用這些工具，但了解網路協議有助於更深入了解這些工具，例如以下的理解：


  **案例1.Docker 的 Bridge 模式網路建立就是利用Sanbox的虛擬化技術在網路層(IP）建立一組虛擬IP，有這認知，在部屬多容器上可以更深入的理解。
[深入浅出”来解读Docker网络核心原理](http://blog.51cto.com/ganbing/2087598)
    
  **案例2.Kafka就是基於TCP上建立自己的通訊協議，以便達到"multiplex requests, the ability to simultaneously poll many connections"...
[The Explanation Behind The Protocols That Kafka Is Using](https://streamdata.io/blog/explanation-behind-protocols-that-kafka-is-using/)
  
  **案例3.Socket是UNIX系統下利用網路通訊的一種接口,本質上就是一個介面程式(Interface)，介於TCP層和應用層之間，目的是把TCP/IP隱藏，讓應用層可以方便快速的使用TCP/IP協議，一般的程式操作上，大家可以把Socket當作是(抽象為)對於檔案I/O的一個操作
  
  
### 什麼是TCP/IP 網路協定?
** 前導-網際網路(Internet)：已經變成是一個專有名詞，表示為連接全世界電腦的網路。      
** 前導-應用：www、HTTP、FTP...等常聽到的詞，都是建立在網際網路上的應用。        
** 前導-協定：網際網路能夠實現，就是依靠大家都認同的機制來達成，這些機制統稱為協定，而協定因為作用不同也有分層次,例如：電話互相連結機制是一種基礎的協定; 聲音傳遞機制是層次較高的協定; 語言(中文）是更高層次的溝通協定;        
** TCP/IP:就是利用IP這個較低層次的協定來進行通訊，所需要使用到的各種協定的集合總稱。        
![TCP/IP分層概念](/image/abc_layer.jpg)

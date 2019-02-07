# TCP/IP
![TCP/IP Book](/image/tcp_ip_book.jpeg)


### 為什麼我想看這本書：
1.就算不寫網頁，當今各種容器部屬或處理大量資料的新工具也都脫離不了網路，雖然在完全不了解網路協議的情況下還是可以使用這些工具，但是對很多細節會一知半解。

2.針對許多處理資料的工具(Kafka、Elastic Search、all kind of Data Base....等），很多是基於TCP之上後另外因應需求而設計的網路協議（對比網頁使用的HTTP），


案例1.Docker 的 Bridge 模式網路建立就是利用Sanbox的虛擬化技術在網路層(IP）建立一組虛擬IP，有這認知，在部屬多容器上可以更深入的理解。
[深入浅出”来解读Docker网络核心原理](http://blog.51cto.com/ganbing/2087598) link.

案例2.Kafka就是基於TCP上建立自己的通訊協議，以便達到"multiplex requests, the ability to simultaneously poll many connections"...

# 資料庫安全
- 資料庫基本觀念
- 資料庫類型:SQL 資料庫 vs NoSQL  資料庫
- 資料庫的安全威脅
- 資料庫的安全防護

## 資料庫基本觀念
## 資料庫模型
- [階層資料庫Hierarchical database model](https://zh.wikipedia.org/zh-tw/%E5%B1%82%E6%AC%A1%E6%A8%A1%E5%9E%8B)
  - 用樹形結構描述實體及其之間關係的數據模型
  - IBM於1968年推出的IMS（Information Management System）資料庫管理系統是第一個階層式資料庫模型管理系統，也是最典型的一個。 
- [網路資料庫(Network Database)](https://en.wikipedia.org/wiki/Network_model)
  - 網狀式資料庫是將每筆記錄當成一個節點。
  - 節點與節點之間可以建立關聯 (也就是建立記錄與記錄間的關聯), 形成一個複雜的網狀架構。
  - 優點: 避免了資料的重複性。
  - 缺點: 關聯性比較複雜, 尤其是當資料庫的內容愈來愈多的時候, 關聯性的維護會變得非常麻煩。
  - 範例:Computer Associates 公司曾經推出的 IDMS(Integrated Database Management System)
- OODB物件導向資料庫 [物件資料庫- 維基百科](https://zh.wikipedia.org/zh-tw/%E5%AF%B9%E8%B1%A1%E6%95%B0%E6%8D%AE%E5%BA%93)
  - 物件資料庫是一種以物件(object)形式表示信息的資料庫。
  - 物件資料庫的資料庫管理系統被稱為ODBMS或OODBMS。
  - [ODBMS.ORG](https://www.odbms.org/)
  - 範例
    - Computer Associates 公司的 Jasmine
    - Eastman Kodak 公司的 Alltalk
    - Servio 公司的 GemStone
    - O2 Technology 的 O2
    - 此外也有關聯式資料庫為主, 再於其上架設物件導向概念的資料庫, 如PostgreSQL 。
    - [ObjectDB - JPA Object Database for Java]()
      - https://en.wikipedia.org/wiki/ObjectDB
- SQL關聯式 [資料庫(relational database model)](https://en.wikipedia.org/wiki/Relational_model)
  - https://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%95%B0%E6%8D%AE%E5%BA%93
  - 範例
    - Oracle 資料庫
    - MSSQL(Microsoft SQL Server) 微軟推出的資料庫
    - MYSQL/MariaDB , Postgresql 資料庫 
- [NoSQL 資料庫](https://zh.wikipedia.org/zh-tw/NoSQL):
  - Redis
  - MongoDB
    - https://www.mongodb.com/zh-cn/docs/manual/
    - [自管理部署的安全檢查清單](https://www.mongodb.com/zh-cn/docs/manual/administration/security-checklist/) 
  - Neo4j圖形資料庫 
## 資料庫的安全威脅
- 參考資料
  - [Threats to Database Security]()
## 資料庫的安全防護
- 參考資料
  - [What Is Database Security?](https://www.comptia.org/content/articles/what-is-database-security)
  - [Database Security](https://www.imperva.com/learn/data-security/database-security/)
  - [OWASP Database Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Database_Security_Cheat_Sheet.html)
  - [OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
## 微軟MSSQL 資料庫
- [保護 SQL Server 的安全](https://learn.microsoft.com/zh-tw/sql/relational-databases/security/securing-sql-server?view=sql-server-ver16)
- [SQL Server 安全性最佳做法](https://learn.microsoft.com/zh-tw/sql/relational-databases/security/sql-server-security-best-practices?view=sql-server-ver16)
- [SQL Server 安全總體架構簡介](https://www.mentortrust.com/home/ArticleSQLSecurityOverall#:~:text=%E8%8B%A5%E6%80%95%E7%B6%B2%E8%B7%AF%E5%81%B7%E7%AA%BA,%E6%94%AF%E6%8F%B4TLS%201.3%E7%89%88%E5%8D%94%E5%AE%9A%E3%80%82)
- https://www.microsoft.com/zh-tw/evalcenter/download-sql-server-2022

# 參考資料
- [What is Database Security: Top 13 Best Practices](https://blog.netwrix.com/what-is-database-security)


### 資料庫平台
- [Online SQL Editor](https://www.programiz.com/sql/online-compiler/)
- [sqliteonline](https://sqliteonline.com/)
### MYSQL  MySQL 9.0 was released on July 1, 2024
- [MySQL 資料庫開發的樂趣 | Rick Silva 著 黃詩涵 譯](https://www.tenlong.com.tw/products/9786263247192?list_name=srh)
  - 官方網站[MySQL Crash Course: A Hands-on Introduction to Database Development]()
  - [github](https://nostarch.com/mysql-crash-course)
  - 資料庫範例:
    - 天氣資料庫
    - 選舉資料庫 ==>利用觸發器防止發生錯誤
    - 薪資資料庫 ==>使用檢視表來保護薪資資料庫內的敏感資料 
- [MySQL 新手入門超級手冊, 3/e (適用 MySQL 8.x 與 MariaDB 10.x) |張益裕]()

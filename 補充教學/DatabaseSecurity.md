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
- [網路資料庫(Network Database)]()
  - 網狀式資料庫是將每筆記錄當成一個節點。
  - 節點與節點之間可以建立關聯 (也就是建立記錄與記錄間的關聯), 形成一個複雜的網狀架構。
  - 優點: 避免了資料的重複性。
  - 缺點: 關聯性比較複雜, 尤其是當資料庫的內容愈來愈多的時候, 關聯性的維護會變得非常麻煩。
  - 範例:Computer Associates 公司曾經推出的 IDMS(Integrated Database Management System)
- OODB物件導向資料庫 [物件資料庫- 維基百科]()
  - 物件資料庫是一種以物件(object)形式表示信息的資料庫。
  - 物件資料庫的資料庫管理系統被稱為ODBMS或OODBMS。
  - [ODBMS.ORG](https://www.odbms.org/)
    - https://en.wikipedia.org/wiki/ObjectDB
  - 範例
    - Computer Associates 公司的 Jasmine
    - Eastman Kodak 公司的 Alltalk
    - Servio 公司的 GemStone
    - O2 Technology 的 O2 
此外也有關聯式資料庫為主, 再於其上架設物件導向概念的資料庫, 如PostgreSQL 。
    - [ObjectDB - JPA Object Database for Java]()

- SQL [資料庫(relational database model)](https://en.wikipedia.org/wiki/Relational_model)
  - Oracle 資料庫
  - MSSQL(Microsoft SQL Server) 微軟推出的資料庫
  - MYSQL/MariaDB , Postgresql 資料庫 
- NoSQL 資料庫: Redis, MongoDB, Neo4j圖形資料庫 
## 資料庫的安全威脅
## 資料庫的安全防護
## 微軟MSSQL 資料庫
- [保護 SQL Server 的安全]()
- [SQL Server 安全性最佳做法](https://learn.microsoft.com/zh-tw/sql/relational-databases/security/sql-server-security-best-practices?view=sql-server-ver16)

# 參考資料
- [What is Database Security: Top 13 Best Practices](https://blog.netwrix.com/what-is-database-security)

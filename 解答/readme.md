# 管理篇

# 技術篇

#### 17.提權
- Linux 提權
  - Dirty Cow 
- Windows提權
  - [Windows提權 - Juicy Potato (Windows privilege escalation-Juicy Potato )](https://ithelp.ithome.com.tw/articles/10334049)
#### 18.網路芳鄰
- 利用「電腦瀏覽服務（Computer Browser Service）」，讓我們可以在電腦上看到其他電腦、工作群組（workgroup）及網域（domain）以及各電腦上的分享資源。
- Server Message Block (SMB) protocol | 伺服器訊息區塊
  - SMB又稱網路檔案分享系統（Common Internet File System | CIFS ），一種應用層網路傳輸協定，由微軟開發
  - 主要功能是使網路上的機器能夠共享電腦檔案、印表機、序列埠和通訊等資源。
  - 它也提供經認證的行程間通訊機能。它主要用在裝有Microsoft Windows的機器上，在這樣的機器上被稱為Microsoft Windows Network。
- SMB可以以不同方式執行在對談層或者更低的網路層之上：
  - 直接執行在 TCP 上 port 445
  - 通過使用 NetBIOS API, 它可以執行在幾種不同的 transports:
    - 基於 UDP ports 137, 138 & TCP ports 137, 139 (NetBIOS over TCP/IP);
- Windows網路芳鄰基本上是使用 139，445 port
- Linux samba: UDP 137,138,  | TCP 139
  - Samba 可以讓 Linux 加入 Windows 的網芳支援，讓異質平台可以共用檔案系統！
  - Samba 也可以讓 Linux 上面的印表機成為印表機伺服器 (Printer Server) 
- [網路上的芳鄰](https://zh.wikipedia.org/zh-tw/%E7%B6%B2%E8%B7%AF%E4%B8%8A%E7%9A%84%E8%8A%B3%E9%84%B0)
- https://linux.vbird.org/linux_server/centos6/0370samba.php
- 網路芳鄰的設定
  - [Windows 10 網路芳鄰完整教學：如何共享資料夾？如何共用列表機？](https://kkplay3c.net/win10-smb/)
  - [Win11 網路芳鄰設定：3分鐘排除找不到電腦問題【圖文教學】](https://kkplay3c.net/win11-network-neighborhood-settings/)

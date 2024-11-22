# [技術篇解答](TEC_SOL.md)

### 113 年度第 1 次 資訊安全工程師能力鑑定能力鑑定 初級試題
# 管理篇錄影

# 技術篇錄影 
- [第43題錄影](https://youtu.be/2K8uJHVEvKg)

# 管理篇
#### 6. [Security of Network and Information Systems, NIS 2 Directive](https://www.enisa.europa.eu/topics/cybersecurity-policy/nis-directive-new)
- 盟第2022/2555號《於歐盟實施高度共通程度之資安措施指令》（Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union, NIS 2 Directive）於2023年1月16日正式生效
- 其於《網路與資訊系統安全指令》（Directive on Security of Network and Information Systems, NIS Directive）之基礎上，對監管範圍、成員國協調合作，以及資安風險管理措施面向進行補充。
- （1）監管範圍：NIS 2納入
  - 公共電子通訊網路或服務供應、
  - 特定關鍵產品（如藥品與醫療器材）製造、
  - 社交網路平台與資料中心相關數位服務、
  - 太空及公共行政等類型，
  - 並以企業規模進行區分，所有中大型企業皆須遵守NIS 2之規定，而個別具高度安全風險之小型企業是否需要遵守，則可由成員國自行規範。
#### 12.[GDPR](GDPR.md)
#### 32.[FIDO](FIDO.md)
#### 33.[零信任架構(ZTA)](ZTA.md)

# 技術篇 
#### 12. DNS Zone Transfer
- [DNS redundancy: What are secondary DNSs and zone transfers?](https://blogs.manageengine.com/clouddns/2023/01/11/dns-redundancy-what-are-secondary-dnss-and-zone-transfers.html)
- Zones(區域) and zone files(區域檔案)
  - DNS 伺服器中託管的網域稱為Zones(區域)。
  - zone files(區域檔案)是一個人類可讀的文字檔，其中包含不同類型的 DNS 記錄。
    - SOA 記錄|SOA (Start of Authority) DNS records：表示授權的開始
    - A records(記錄)：映射到網域或子網域的 IPv4 位址
    - AAAA records(記錄)：映射到域或子域的 IPv6 位址
    - CNAME 記錄：指向正式名稱的規範記錄
    - MX 記錄：指向郵件伺服器的郵件交換記錄
    - TXT 記錄：用於各種驗證
    - PTR 記錄：反向 DNS 查找記錄
- primary(主|首座) DNS server vs  secondary(二當家) DNS servers
  - 由主 DNS 伺服器託管和管理的區域檔稱為主 DNS 區域。
  - DNS 是核心基礎設施元件，它需要 100% 的可用性。為了獲得更高的可擴展性、安全性和可用性，使用了輔助 DNS 伺服器。
- zone transfers(區域傳輸)
  - Securi區域傳輸是一種機制，用於將託管區域的主 DNS 伺服器的最新資訊同步到輔助 DNS。
  - 區域傳輸包括兩種類型：
    - 1.全區轉移 （AXFR）：主 DNS 伺服器通知輔助 DNS 伺服器已對特定區域進行了更改，輔助 DNS 聯繫主 DNS 以檢查發生更改的區域的 SOA 記錄中的序號。如果主 DNS 上的序號大於該區域的輔助 DNS 伺服器的序號，則會將整個區域檔從主 DNS 伺服器複製到輔助 DNS 伺服器。
    - 2.增量區域傳輸 （IXFR）： 主 DNS 伺服器通知輔助 DNS 伺服器已對特定區域進行了更改，輔助 DNS 聯繫主 DNS 以檢查發生更改的區域的 SOA 記錄中的序號。如果主 DNS 上的序號大於該區域的輔助 DNS 伺服器的序號，則輔助 DNS 伺服器會將上次更改與現有版本進行比較，並僅從主 DNS 複製更改的記錄。
  - 次要伺服器會定期檢查主 DNS 伺服器是否有任何更改，並複製最新的區域檔。
  - 來自輔助 DNS 伺服器的定期檢查基於區域 SOA 記錄中設置的刷新間隔。
- Attacking zone transfers
  - 攻擊者可以使用 AXFR 請求將啟用了區域傳輸的區域下載到主 DNS 伺服器
- Securing(安全強化) zone transfers
  - 1.IP address restriction(IP 地址限制)：僅允許從輔助 DNS 伺服器的 IP 向主 DNS 伺服器發出區域傳輸請求
  - 2.DNS transfer signature(TSIG) :啟用 DNS TSIG。
    - TSIG 是主 DNS 伺服器和輔助 DNS 伺服器之間預共用的對稱加密金鑰。
    - 每當在啟用了 TSIG 的主 DNS 伺服器和輔助 DNS 伺服器之間啟動區域傳輸 （AXFR/IXFR） 時，都會使用 TSIG 金鑰驗證參與區域傳輸的兩個伺服器之間的通信，並且區域傳輸會安全地完成。

#### 17.提權
- Linux 提權
  - Dirty Cow
  - SetUID 
- Windows提權
  - [Windows提權 - Juicy Potato (Windows privilege escalation-Juicy Potato )](https://ithelp.ithome.com.tw/articles/10334049)
  - Bypass UAC
- [Chisel](https://github.com/jpillora/chisel)
  - Chisel is a fast TCP/UDP tunnel, transported over HTTP, secured via SSH.
  - Single executable including both client and server.
  - Written in Go (golang).
  - Chisel is mainly useful for passing through firewalls, though it can also be used to provide a secure endpoint into your network. 

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
#### 23. IP camera 安全串流
- SMTPS|SMTP Secure (SMTPS)
  - [SMTP Secure (SMTPS) 如何運作？](https://www.cloudflare.com/zh-tw/learning/email-security/smtp-port-25-587/)
  - SMTPS 比普通的 SMTP 更安全，因為它給電子郵件加密，對電子郵件進行驗證，防止資料篡改。
  - 它透過使用 Transport Layer Security (TLS) 通訊協定來實現這三點。
    - 加密：TLS 會在資料穿越網路時加密資料。加密過程旨在打亂資料，以便只有正確解密金鑰的擁有者才能解密並檢視資料。透過加密，資料在網際網路等不可信環境中傳輸時可保持安全。
    - 驗證：TLS 使用數位簽章來確保網路流量確實是來自其聲稱的來源。如果沒有這一步，電腦將接收來自假冒者、攻擊者或其他惡意方的資料。
    - 電子郵件完整性：數位簽名也有助於確保資料未遭到竄改。
  - SMTPS 的官方預設連接為連接埠 587。
  - SMTPS 連線以一個「STARTTLS」命令開始，告知郵件伺服器將透過 TLS 傳送 SMTP 流量。
  - 早期版本也使用連接埠 465
- email使用的協定:
  - SMTP：簡單郵件傳輸協定（Simple Mail Transfer Protocol），用於發送電子郵件的傳輸協定；主要用來從郵件用戶端向郵件伺服器發送郵件,也可以用來在郵件伺服器之間轉發郵件。
    - [簡單郵件傳輸協定](https://zh.wikipedia.org/zh-tw/%E7%AE%80%E5%8D%95%E9%82%AE%E4%BB%B6%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)
    - SMTP伺服器通常使用傳輸控制協定（TCP），在埠25（用於伺服器之間）和埠587（用於來自已認證客戶端的提交）上執行，支援加密與非加密兩種方式。
    - 提供SSL加密的SMTP協定被稱為SMTPS
  - POP3：Post Office Protocol，用於接收電子郵件的標準協定；
    - 未加密的 IMAP 使用連接埠 143，加密的 IMAP 則使用連接埠 993 
  - IMAP| Internet Message Access Protocol，互聯網消息協定，是POP3的代替協議；後兩者用來從郵件伺服器獲取郵件。
    - 未加密的 POP3 使用連接埠 110，加密的 POP3 則使用連接埠 995 
- RTSPS
  - Secure RTSP streaming - SRTP/RTSPS
    - [從零開始精通RTSP之加密 - CSDN博客](https://blog.csdn.net/hope_wisdom/article/details/138939858) 
  - RTSP|Real Time Streaming Protocol [30-13之 RTSP 傳輸協議](https://ithelp.ithome.com.tw/articles/10205976)
    - 被設計出來是為了可以控制串流媒體伺服器的協議  ==> Client-server架構
    - 定義了控制的方法與參數 如：暫停/繼續、後退、前進等。
    - 它是一個多媒體播放控制協議
    - 我們先發送一個觀看影片的請求給 Server，然後它就開始以串流型式來傳輸影片，然後這時我們可以用 RTSP 所提供的一些方法，來進行影片的快轉或暫停，為了能控制串流就是它被設計出來的原理。
    - [流媒體傳輸協議系列之--RTSP協議詳解](https://www.itread01.com/articles/1476115529.html)
    - [即時串流協定 - 維基百科](https://zh.wikipedia.org/zh-tw/%E5%8D%B3%E6%99%82%E4%B8%B2%E6%B5%81%E5%8D%94%E5%AE%9A)
- SFTP
  - FTP |File Transfer Protocol| [檔案傳輸協議](https://zh.wikipedia.org/zh-tw/%E6%96%87%E4%BB%B6%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)
    - 用於Internet上的控制文件的雙向傳輸。同時，它也是一個應用程式（Application）。
    - FTP的兩個概念：下載」（Download）和」上傳」（Upload）。
    - 下載文件  ==> 就是從遠程主機拷貝文件至自己的計算機上
    - 上傳文件  ==> 就是將文件從自己的計算機中拷貝至遠程主機上
    - FTP不是一項安全的協定，並且具有許多安全漏洞。1999年5月發布的RFC 2577中列出了以下幾個主要的漏洞：
      - 暴力破解 Brute-force attack
      - FTP反彈攻擊 FTP bounce attack
      - 封包擷取 Packet capture
      - 埠竊取（猜測下一個開放埠並篡奪合法連接） Port stealing
      - 欺騙攻擊 Spoofing attack
      - 使用者名稱列舉 Username enumeration
      - DoS or DDoS
    - 通過FTP傳輸的流量不會被加密，所有傳輸通過明文進行的。
    - 任何能夠在網路上執行封包擷取（嗅探wireshark）的人都可以讀取使用者名稱、密碼、命令內容和資料。
  - SFTP | SSH 文件傳輸協議 |SSH File Transfer Protocol |安全文件傳輸協議（Secure File Transfer Protocol）
    - 技術教學
      - [手把手教你使用 SFTP 安全地傳輸文件]()
      - WinSCP :: Official Site :: Free SFTP and FTP client
      - [如何在 Windows 架設高安全性的 SFTP (SSH File Transfer Protocol) 伺服器](https://blog.miniasp.com/post/2021/12/12/Enhanced-Security-for-SFTP-SSH-File-Transfer-Protocol-on-Windows)
  - ftps |FTP Secure
    - SFTP（SSH File Transfer Protocol）：
  - FTP (File Transfer Protocol) uses the following ports:
    - FTP
      - 資料連接埠
        - 埠 20 是 FTP 最常見的資料連接埠。
        - 埠 989 是 FTPS 的預設資料連接埠。
      - control port: TCP port 21
    - TFTP (Trivial File Transfer Protocol): UDP port 69
    - SFTP (Secure File Transfer Protocol): TCP port 22
    - SCP (Secure Copy Protocol): TCP port 22
    - FTPS (FTP Secure): TCP port 990
SFTP 不同於FTP和FTPS，它是基於SSH協議的一個子協議，用於安全文件傳輸。 
- RDP |遠端桌面通訊協定 |Remote Desktop Protocol
  - 遠端桌面通訊協定 (RDP) 是用於遠端使用桌上型電腦的通訊協定或技術標準。
  - 遠端桌面軟體可以使用幾種不同的通訊協定，包括 RDP、獨立運算架構 (ICA) 和虛擬網路運算 (VNC)
  - RDP 是最常用的通訊協定。RDP 最初由 Microsoft 發佈，可用於大多數 Windows 作業系統，但它也可以與 Mac 作業系統一起使用。
  - 預設 「TCP 3389」連接埠

#### 29.惡意程式
- archive.org:Internet Archive is a non-profit library of millions of free texts, movies, software, music, websites, and more.
- VirusTotal
- [ANY.RUN](https://any.run/)
  - Innovative cloud-based sandbox with full interactive acces 
- vx-underground.org
  - vx-underground, also known as VXUG, is an educational website about malware and cybersecurity.
  - It claims to have the largest online repository of malware.
  - The site was launched in May, 2019 and has grown to host over 35 million pieces of malware samples.
  - On their account on Twitter, VXUG reports on and verifies cybersecurity breaches.[ 

#### 34.數位版權管理| Digital rights management| DRM

#### 40.IIS Log File
- [Day24. 凡走過必留下痕跡 - Logging, IIS Log](https://ithelp.ithome.com.tw/articles/10305315)

#### 43. [RFC 5424: The Syslog Protocol](https://www.rfc-editor.org/rfc/rfc5424)
- [Syslog 和 RFC 5424 分類的實際用途](https://hackmd.io/@hiiii/SklQV_JtR)
- PRI = Facility * 8 + Severity
- 165 = 20* 8 + 5 
  - 說明
    - PRI：優先級值（0-191）
    - Facility：設施碼（0-23）  ==> 16-23	local use 0-7 (local0-local7)	本地使用 0-7
    - Severity：嚴重程度（0-7）  ==> 5	==>Notice: normal but significant condition	注意：正常但重要的狀況

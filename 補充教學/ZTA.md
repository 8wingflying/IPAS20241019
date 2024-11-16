# 零信任架構|Zero Trust Architecture|ZTA
- 定義
- 歷史發展
- 零信任基本原則 | Tenets of Zero Trust
- 零信任模型
  - 邏輯元件 | ZTA邏輯元件組成 | Logical Components of Zero Trust Architecture
  - 信賴評估演算法
- 部屬模式 Multiple ZTA deployment models
- 零信任架構可能面臨的威脅挑戰

# 零信任架構|Zero Trust Architecture|ZTA
- 定義
  - `零信任`是一種網路資安的架構和目標，它的假設前提是：任何交易、個體與身分在獲得信任並持續維持信任之前，全都不可信任。
  - 這種安全模型只是基於「信任最小化」的基本原則進行設計
  - 零信任架構的理念強調「永不信任，始終驗證」
  - 各種別名
    - 零信任安全模型
    - Zero trust security model|零信任架構|零信任網路架構|ZTA |ZTNA
    - 無邊界安全perimeterless security
  - 傳統安全模式(傳統信任模型) vs 零信任架構
    - 傳統的信任模型是「內外有別」 ==> 內網 | 外網 ,網路邊界, 縱深防禦(depth in defense)
      - 對於內部和外部的信任程度並不一樣，這種方式在過去也主導了網路安全的策略。
        - 內網 ==> 彼此信任
        - 外部 ==> 不信任
      - 一般企業組織會用一條無形的分界線，來區分內部及外部的數位資料和財產，並使用防火牆及各式各樣的資安防護軟硬體設備，來保護分界線安全：來自內部員工如果要存取資料，資通系統通常預設相當高的權限（信任度）。
      - 隨著內部網路和外部攻擊者的界限逐漸模糊，傳統的信任模型已經無法有效應對日益複雜的網路威脅。
      - 內部威脅 
        - 內部威脅者，原本是系統中的「可信用戶」，擁有多重身分驗證措施，但由於缺乏對資料流量的監控，他們最終成功竊取大量敏感資料
        - 曼寧（Chelsea Manning）|將超過70萬份美國國防部和國務院的機密文件，洩露給維基解密（WikiLeaks）
        - 斯諾登（Edward Snowden）|向《衛報》和《華盛頓郵報》的記者洩露了大量的機密文件，揭露美國國家安全局針對全球互聯網通信和電話記錄的全球監控計畫。
        - [John Kindervag說](https://www.ithome.com.tw/news/165397)「這些案例揭露了傳統網路安全模式中的致命漏洞，意即進入系統後就可以自由存取的權限。」。
    - 零信任架構
      - 每一個數位行為──無論是來自內部還是外部──都被視為潛在的風險
      - 這意味著所有的流量、設備和用戶，都必須被持續監控和驗證。 
  - [保護面（Protect Surface） vs 攻擊面（Attack Surface）](https://www.ithome.com.tw/news/165397)
    - 傳統 ==> 攻擊面（Attack Surface）==> 網路安全討論都集中在如何管理「攻擊面」
      - 但攻擊面不斷擴大，幾乎無法完全控制。 
    - 零信任 ==>  保護面（Protect Surface）
      - 與其嘗試縮小攻擊面，不如將焦點轉向保護面
      - 這一思路轉變，有助於企業集中力量保護最核心的資產，避免資源分散。
    - 案例:特勤局的保護
      - 特勤局的保護對象並非每位民眾或整個城市，而僅限於總統及其家人
      - 這樣的保護策略，非常類似零信任的做法，重點在於精準保護，而不是試圖一網打盡，避免所有風險。

## 歷史發展:
- 1994年4月，Stephen Paul Marsh在其博士論文中提出了「零信任zero trust」一詞
- 2003年 Jericho Forum強調了為組織IT系統定義邊界的挑戰性，討論了當時稱為「去邊界化」的趨勢。
- 2009年 Google實施了BeyondCorp的零信任架構 [資料來源](https://www.webcomm.com.tw/blog/zero-trust-security-model/?srsltid=AfmBOoox4cy_h3xgnnau2NruZ59pCeiAXLmPWm5Piw34A_mq0voJXUp3)
  - 過去 Google 採用 VPN 的方式讓員工遠端連線，充滿了不確定性。
  - 為了解決這個困擾，從了解員工使用裝置開始，Google 逐漸轉化為零信任安全架構 BeyondCorp
  - 其構成採取了無密碼驗證的概念，相關的原則如下：
    - 服務存取權非由連線的網路決定
    - 根據使用者及其裝置的相關要素授予服務存取權
    - 不論存取任何服務，都必須經過驗證、授權及加密程序
  - BeyondCorp 的出現讓 Google 員工能夠在任何地方快速工作，在提高安全性的同時提高生產力，
  - 一開始只在 Google 內部使用，但隨著零信任的需求高漲也開始作為 Google 的服務推行到全世界供人使用
  - BeyondCorp 的零信任安全架構，所有對企業資源的訪問都是根據設備狀態和使用者憑證進行完全認證、授權和加密的。 
- 2010年 Forrester Research的分析師John Kindervag使用術語「零信任模型」表示更嚴格的公司內部網路安全計劃和存取控制。
  - 4大核心
    - 1.使用整合的分割閘道器（Segmentation gateway）為網路核心
    - 2.建立平行且安全的網路分隔
    - 3.需考慮網路後臺的集中管理
    - 4.建立資料蒐集網路，以掌握網路的完整狀況。 
- 2018年末，美國國家標準與技術研究院 (NIST) 和美國國家網絡安全卓越中心 (NCCoE) 的網絡安全研究人員發行 NIST SP 800-207 Zero Trust Architecture
- 2019年，英國國家網路安全中心NCSC建議網路架構師考慮對新增IT部署採用零信任措施，尤其是計劃大量使用雲服務時

## NIST 零信任架構|Zero Trust Architecture|ZTA
- 參考資料:
  - NIST SP 800-207 Zero Trust Architecture
  - NIST CSWP 20:Planning for a Zero Trust Architecture:A Planning Guide for Federal Administrators(2022)
- Tenets of Zero Trust | 零信任基本原則
  - （一）所有的資料來源與運算服務都要被當作是`資源resources` All data sources and computing services are considered `resources`
  - （二）不管適合哪個位置的裝置通訊，都需要確保安全 All communication is secured regardless of location
  - （三）對於個別企業資源的存取要求，應該要以`每次連線`為基礎去許可Access to individual enterprise resources is granted on a `per-session` basis
  - （四）資源的存取應該要基於客戶端識別、應用服務，以及要求存取資安可觀察到的狀態，以及可能包括的行為或環境屬性，去動態決定Access to resources is determined by dynamic policy
  - （五）企業監控與衡量所有擁有與相關資訊資產的正確性與安全狀態；All owned and associated devices are in the most secure state possible
  - （六）在允許存取之前，所有的資源的身分鑑別與授權機制，都要是依監控結果動態決定，並且嚴格落實；All resource authentication and authorization are `dynamic` and `strictly enforced`
  - （七）企業應該要盡可能收集有關資訊資產、網路架構、骨幹，以及通訊的現況，並用這些資訊來增進安全狀態。Collect as much information as possible on current state of network infrastructure to improve security posture 

## 零信任模型
- ZTA邏輯元件組成 | Logical Components of Zero Trust Architecture | 零信任模型的邏輯元件
  - 政策引擎 Policy Engine (PE)– PE 負責根據政策和 CDM 系統與威脅情報服務的輸入來判斷是否該授予存取權限。
  - 政策管理員 Policy Administrator (PA)– PA 負責根據 PE 的決策來建立或關閉通訊。
  - 政策落實點 Policy Enforcement Point (PEP)– PEP 負責准許、監控和終止連線
- 信賴評估演算法 | The trust algorithm (TA)
  - the process used by the policy engine to ultimately grant or deny access to a resource
  - 類型:
    - 第一種: Criteria- versus score-based
    - 第二種: Singular versus contextual
## ZTA 模式
- 完整的零信任方案應包含3個要素
  - 參考資料: NIST NIST SP 800-207| 3.1 Variations of Zero Trust Architecture Approaches
    - 3.1.1 ZTA Using Enhanced Identity Governance(增強的身分治理)
    - 3.1.2 ZTA Using Micro-Segmentation(微分段)
      - 在零信任架構下，對於特定資產、資料或應用，要設置更精細化的安全邊界，以確保更嚴格的存取控制。 
    - 3.1.3 ZTA Using Network Infrastructure and Software Defined Perimeters (網路基礎架構與軟體定義邊界)
- 我國政府機關所採取的模型  
  - 參考 NIST SP 800-207 文件的 ZTA 部署模型，我國政府機關所採取的模型為資源門戶部署（Resource Portal-Based Deployment）方式
  - 對於任何對資通系統之存取皆須透過存取閘道，並將`身分鑑別`、`設備鑑別`與`信任推斷`列為三大核心機制。
## 部屬模式 Multiple ZTA deployment models
  - 參考資料: NIST NIST SP 800-207| 3.2 Deployed Variations of the Abstract Architecture
    - 3.2.1 Device Agent/Gateway-Based Deployment
    - 3.2.2 Enclave-Based Deployment
    - 3.2.3 Resource Portal-Based Deployment
    - 3.2.4 Device Application Sandboxing
## 導入`零信任架構`步驟 ==> 階段式導入
- [John Kindervag|導入零信任架構的五步驟](https://www.ithome.com.tw/news/165398)
  - 零信任的實施可以分成五個步驟，這些步驟目的在於在簡化安全流程，確保系統的每個保護面得到充分保護
    - 步驟1：定義保護面，確認DAS元素(DAS元素，包括：資料、應用、資產和服務的縮寫。)
    - 步驟2：繪製交易流
      - 在實施零信任之前，必須全面了解系統的交易流
      - 因為只有在理解這些流動的基礎上，才能準確地設計出合適的安全策略，以保護每個保護面
    - 步驟3：設計零信任環境
    - 步驟4：制定零信任策略(Create Zero Trust Policy)
      - 零信任的核心原則 ==>「永不信任，始終驗證」
      - 目的就是通過設計一套精細、動態且基於風險的存取控制政策，來確保組織內部所有的資料、資產和應用的安全性。 
    - 步驟5：持續監控與維護（Monitor and Maintain）
      - 通過不斷的監控、資料收集和分析確保系統的安全策略能夠動態應對各種威脅，並且根據新的風險情況對策略，進行調整和維護，以保持整個系統的安全。 

## 零信任架構可能面臨的威脅挑戰
  - 參考資料: NIST NIST SP 800-207| ch 5. Threats Associated with Zero Trust Architecture
  - 5.1 Subversion of ZTA Decision Process  顛覆決策過程
  - 5.2 Denial-of-Service or Network Disruption  拒絕服務或網絡中斷
  - 5.3 Stolen Credentials/Insider Threat  憑證被盜/內部威脅
  - 5.4 Visibility on the Network  網絡可見性 == > 加密流量encrypted traffic
  - 5.5 Storage of System and Network Information 系統和網絡信息的儲存
  - 5.6 Reliance on Proprietary Data Formats or Solutions 專有數據格式或解決方案
  - 5.7 Use of Non-person Entities (NPE) in ZTA Administration 非個人實體 (NPE)   
    - 基於機器學習/人工智慧的自動化正在部署來管理網絡運營。
    - 這些組件與 ZTA 的管理組件（例如策略引擎、策略管理員）交互，並可能面臨其他風險：
      - 驗證非個人實體
      - 誤報的可能性

## 思科3W評估模式 [ITHOME](https://www.ithome.com.tw/news/144408)
- 分別從工作力（Workforce）、工作負載（Workloads）、工作場所（Workplace）來進行探討與對應
  - 工作力：員工身分識別與連網設備的存取控管
  - 工作負載：應用程式的活動監控、分隔與安全偵測
  - 工作場所：連網設備管理、用戶與設備的網路存取控制、持續資安健康狀態偵測 
- 實施方式:零信任是一個不斷循環下列3個步驟的過程，分別是：
  - 建立信任（Establish trust）
  - 執行基於信任的存取（Enforce trust-based access）
  - 持續驗證（Continuously verify trust）

## 推薦閱讀
- [零信任網路｜在不受信任的網路中建構安全系統 (Zero Trust Networks)](https://www.tenlong.com.tw/products/9789865026332?list_name=srh)
- [零信任安全架構設計與實現 Zero Trust Security: An Enterprise Guide](https://www.tenlong.com.tw/products/9787302631507?list_name=srh)

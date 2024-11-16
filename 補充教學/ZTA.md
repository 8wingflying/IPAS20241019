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
  - 零信任架構的理念強調「永不信任，始終驗證」 Never Trust, Always Verify
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
## 各國推動
- 美國  
  - 2020年8月，NIST已公布SP 800-207標準文件，成為美國政府採用ZTA的指南
  - 從2021年5月總統拜登提出行政命令（EO 14028），要求聯邦政府推動零信任架構，美國政府發表零信任架構安全原則
  - 基於該原則，美國總務署GSA提出零信任採購指引
  - 國防部DOD提出零信任策略
  - 美國網路暨基礎設施安全局（CISA）也提出零信任成熟度模型。
  - 美國國家標準暨技術研究院（NIST）也發布零信任架構SP 800-207、實施指引草案，以及SP 800-63身分與存取管理指引第四版草案等。
- 韓國
  - 2023年6月由科學技術情報通訊部（MSIT）發表零信任準則1.0 
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
- 信任推斷| 信賴評估演算法 | The trust algorithm (TA)
  - the process used by the policy engine to ultimately grant or deny access to a resource
  - 類型:
    - 第一種: Criteria(情境)- versus score(分數)-based
    - 第二種: Singular(單一) versus contextual(上下文本)

## ZTA的3項必要技術
- 完整的零信任方案應包含3個要素
  - 參考資料: NIST NIST SP 800-207| 3.1 Variations of Zero Trust Architecture Approaches
    - 3.1.1 ZTA Using Enhanced Identity Governance(增強的身分治理)
    - 3.1.2 ZTA Using Micro-Segmentation(微分段)
      - 在零信任架構下，對於特定資產、資料或應用，要設置更精細化的安全邊界，以確保更嚴格的存取控制。 
    - 3.1.3 ZTA Using Network Infrastructure and Software Defined Perimeters (網路基礎架構與軟體定義邊界)
- 我國政府機關所採取的模型  
  - 參考資料
    - [資安院：政府推動零信任架構，今年完成A級機關導入身分鑑別，2機關將先導入信任推斷機制](https://www.ithome.com.tw/news/163079)
    - [資料來源](https://moda.gov.tw/press/multimedia/blog/9773) 
  - 參考 NIST SP 800-207 文件的 ZTA 部署模型，我國政府機關所採取的模型為資源門戶部署（Resource Portal-Based Deployment）方式
  - 對於任何對資通系統之存取皆須透過存取閘道，並將`身分鑑別`、`設備鑑別`與`信任推斷`列為三大核心機制。
    - 身分鑑別 ==> 採用多因子身分鑑別（例如FIDO無密碼驗證）與鑑別聲明；
      - 採無密碼雙因子，例如FIDO2鑑別使用者的身分
      - 依照NIST SP800-63-3，該標準建立的身分鑑別機制，將身分鑑的嚴謹度定義為身分保證等級（IAL）、鑑別保證等級（AAL）、聯邦保護等級（FAL），每個身分鑑別等級的嚴謹程度又分為3個1、2、3等級（數字愈高，等級愈高）
      - 我國採用基準概念，政府公部門推動零信任架構，至少需滿足IAL2、AAL3及FAL2
    - 設備鑑別 ==>  則是鑑別使用設備、設備健康管理；
      - 採用公開金鑰技術作為設備鑑別，由設備上的TPM安全晶片或代理程式產生金鑰憑證，完成設備註冊及鑑別；
      - 同時也持續監控設備的健康狀態，依據設備健康狀態計算對該設備的健康信任等級。
      - 設備健康狀態包含作業系統更新、防毒更新、應用軟體更新、組態合規等，根據不同的狀態評分，計算使用設備的健康信任等級。 
    - 信任推斷 ==> 則是綜合使用者的身分、設備及行為各方面，作為信任推斷的依據。
      - 基於信任推斷來決定存取權限，信任推斷機制可能制定規則、分數，或是混合規則與分數。
      - 以分數為例，依使用情境計算每次存取的信任分數，綜合參考身分鑑別、設備鑑別、設備健康、IP位址、登入時間，還有外部情資如CVSS評分、EPSS漏洞利用評分等等，根據上述資料計算信任等級，再依權重、信任等級計算出信任分數，依不同的信任分數允許或是拒絕存取。 

## 部屬模式 Multiple ZTA deployment models |4種ZTA部署方式
  - 參考資料: NIST NIST SP 800-207| 3.2 Deployed Variations of the Abstract Architecture
    - 3.2.1 Device Agent/Gateway-Based Deployment
    - 3.2.2 Enclave-Based Deployment
    - 3.2.3 Resource Portal-Based Deployment資源門戶的部署方式
      - 零信任架構分為核心組件、支援組件
      - 核心組件控制資源的存取，負責鑑別、授權、管理連線
      - 支援組件則是支援存取決策的周邊系統，例如身分管理、活動日誌、威脅情資、資料存取政策等等。
    - 3.2.4 Device Application Sandboxing

## 導入`零信任架構`步驟 ==> 階段式導入
- [John Kindervag|導入零信任架構的五步驟](https://www.ithome.com.tw/news/165398)
  - 零信任的實施可以分成五個步驟，這些步驟目的在於在簡化安全流程，確保系統的每個保護面得到充分保護
    - 步驟1：定義保護面，確認DAS元素(DAS元素，包括：資料、應用、資產和服務的縮寫。)
    - 步驟2：繪製交易流
      - 在實施零信任之前，必須全面了解系統的交易流
      - 因為只有在理解這些流動的基礎上，才能準確地設計出合適的安全策略，以保護每個保護面
    - 步驟3：設計零信任環境
      - 如何針對不同保護面，設計不同的保護方案呢？
        - 1.可以在每個「保護面」周圍設計微型周界（Micro-Perimeters），將保護目標和周邊的其他系統隔離開來，對每一個保護面進行精細的控制和保護，以減少不必要的攻擊面。
        - 2.選擇合適技術來實現安全控制，包括多因素身分驗證（MFA）、微分割（Micro-Segmentation）、加密技術、身分與存取管理（IAM）等，來確保每個資產和交易流都得到了合適的保護。
        - 3.設計一個政策自動化與應用的架構，使得系統能夠基於預定的安全政策，自動做出允許或拒絕的決定。這樣的政策應根據每個保護面的特定需求，結合對用戶、設備、應用程序的存取需求和風險評估，進行精細化設計。
        - 4.確保所有的保護面都能夠被持續地監控，並且可以即時反應異常活動或潛在的威脅，讓這些管理和監控系統，能夠提供完整的可視性，並能根據即時資料，快速應對網路事件。 
    - 步驟4：制定零信任策略(Create Zero Trust Policy)
      - 零信任的核心原則 ==>「永不信任，始終驗證」
        - 目的就是通過設計一套精細、動態且基於風險的存取控制政策，來確保組織內部所有的資料、資產和應用的安全性。
      - 零信任是一組粒度細緻的允許規則，組織或企業則會根據個人的工作職能角色，來允許他們可以存取的資源。
        - 這個步驟目的是，為組織內的資料、應用、資產或服務（DAS元素），按照最小權限（Least Privilege）和「始終驗證」的原則，建立一套嚴格且細緻的存取控制政策，從而最大限度地減少安全風險，並且提高網絡的整體安全性，以保護每一個「保護面」。 
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
## 參考資料
- 2024[【回歸根本定義，捍衛網路戰爭的無形防線】零信任之父第一手導讀零信任架構](https://www.ithome.com.tw/news/165397)
- [企業如何導入零信任架構？專家由淺入深剖析上手關鍵](https://www.ithome.com.tw/news/157027)
- [【搞懂零信任，從理解NIST SP 800-207著手】打造以零信任原則的企業網路安全環境](https://www.ithome.com.tw/news/145709)
- [【臺灣資安大會直擊】看懂零信任架構，先釐清對於ZTA常見的3大迷思](https://www.ithome.com.tw/news/144551)

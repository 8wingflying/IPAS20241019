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
  - 零信任安全模型|Zero trust security model|零信任架構|零信任網路架構|ZTA |ZTNA|無邊界安全perimeterless security
## 歷史發展:
- 1994年4月，Stephen Paul Marsh在其博士論文中提出了「零信任zero trust」一詞
- 2003年 Jericho Forum強調了為組織IT系統定義邊界的挑戰性，討論了當時稱為「去邊界化」的趨勢。
- 2009年 Google實施了BeyondCorp的零信任架構
- 2010年 Forrester Research的分析師John Kindervag使用術語「零信任模型」表示更嚴格的公司內部網路安全計劃和存取控制。
  - 4大核心
    - 1.使用整合的分割閘道器（Segmentation gateway）為網路核心
    - 2.建立平行且安全的網路分隔
    - 3.需考慮網路後臺的集中管理
    - 4.建立資料蒐集網路，以掌握網路的完整狀況。 
- 2018年末，美國國家標準與技術研究院 (NIST) 和美國國家網絡安全卓越中心 (NCCoE) 的網絡安全研究人員發行 NIST SP 800-207 Zero Trust Architecture
- 2019年，英國國家網路安全中心NCSC建議網路架構師考慮對新增IT部署採用零信任措施，尤其是計劃大量使用雲服務時

## NIST 零信任架構|Zero Trust Architecture|ZTA
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
- 參考資料: NIST NIST SP 800-207| 3.1 Variations of Zero Trust Architecture Approaches
    - 3.1.1 ZTA Using Enhanced Identity Governance(增強的身分治理)
    - 3.1.2 ZTA Using Micro-Segmentation(微分段)
    - 3.1.3 ZTA Using Network Infrastructure and Software Defined Perimeters (網路基礎架構與軟體定義邊界)
## 部屬模式 Multiple ZTA deployment models
  - 參考資料: NIST NIST SP 800-207| 3.2 Deployed Variations of the Abstract Architecture
    - 3.2.1 Device Agent/Gateway-Based Deployment
    - 3.2.2 Enclave-Based Deployment
    - 3.2.3 Resource Portal-Based Deployment
    - 3.2.4 Device Application Sandboxing
## 導入`零信任架構`步驟 ==> 階段式導入

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

# FIDO(Fast IDentity Online)
- 非營利組織FIDO聯盟(FIDO Alliance)所訂定的網路識別標準，確保登入流程中伺服器及終端裝置協定的安全性
- 使用特定硬體或生物特徵取代傳統密碼，進行身分認證。
- 安全機制：
  - 1.使用非對稱式公鑰私鑰機制。
  - 2.伺服器端僅儲存相對應公鑰。
  - 3.私鑰皆只保存在裝置端，風險分散。
- 三大認證協議：
  - FIDO UAF ==>用裝置上的生物辨識器取代密碼，各裝置分別註冊身分，需分別整合各應用系統，適用於網銀App。
  - FIDO U2F==>使用USB裝置儲存公私鑰，使用者的登入，皆需要插入USB裝置，需分別整合各應用系統，適用在可存取USB的應用系統。
  - FIDO2 ==>支援Web應用，呼叫API即可透用各種載具(Token)驗證，包括UAF及U2F載具，不同網頁URL需註冊不同金鑰，經常搭配SSO Web Portal使用。

 
# FIDO Alliance
- FIDO Device Onboard（FDO）安全標準規範
- 2021年4月，針對物聯網設備所公布的IoT開放標準協定，名為FIDO Device Onboard（FDO），裡面定義簡易與安全的身分識別方式，IoT裝置無論連至雲端或企業內部網路的後端管理平臺，均可適用這樣的驗證方式。
- 2022年4月19發布的FIDO Device Onboard Specification 1.1中，完整說明了這項裝置連入標準的規範，並圖解FDO的傳輸介面
- 裝置註冊（Device onboarding），指以將包含金鑰的機密資料及配置資料的設定安裝過程，使設備能與物聯網平臺安全地連接與互動。基本上，物聯網平臺就是設備擁有者用來管理裝置的系統，包括修補安全漏洞、安裝或更新軟體、檢視感測器資料，以及與執行器互動。
- 2024/10/14 發表一組新規範，包括憑證交換協定（Credential Exchange Protocol，CXP）與憑證交換格式（Credential Exchange Format，CXF），以推動憑證的可攜，包括通行密鑰（Passkey）與其它憑證。[FIDO聯盟發表新規範以推動憑證可攜](https://www.ithome.com.tw/news/165496)

# 重要推動
- 2016年，英國政府的電子化政府入口網站（gov.uk）就提供U2F的支援
- 2018年，美國政府部門間共享的認證平臺Login.gov網站，也開始新增提供FIDO2支援，讓民眾能應用這種新一代的線上驗證方式，登入當地政府提供的服務。
- [2020內政部資訊中心打造的TW FidO臺灣行動身分識別](https://www.ithome.com.tw/news/141254)
- [【金融業FIDO應用實例】行動銀行安全性提升，更多臺灣金融業建置FIDO](https://www.ithome.com.tw/news/141253)

# 參考資料

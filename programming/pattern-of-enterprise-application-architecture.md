# Pattern of Enterprise Application Architecture 摘要與心得

## Layering (分層)

分層架構經常被用在處理複雜的應用上

### 常見的分層架構案例

- Network OSI layer
  - HTTP是base在TCP
  - TCP又在base在IP network上
- MVC Pattern
    - model負責商業邏輯
    - view負責畫面的呈現
    - controller負責連接model與view


### 為什麼要分層 ###

- 只需要了解單一層的東西, 不需要知道其他底層的細節
- 元件間的相依性比較清楚
- 容易替換底層的實做(只要上下層間的溝通界面維持一致)

### 分層的缺點 ###

- 如果最上層需要一個來自很底層的資訊, 這樣的改動會影響到每一層
  - 例如: database新增了一個欄位, UI上需要呈現這個資訊
- 過度分層會衍生效能問題

### 分層的基本原則

- 上層不知道會有誰依賴(或者直接理解為"使用")它
- (通常)上層只能依賴下一層, 但不會知道下層的依賴


### 三層法

- Presentation: 負責軟體與人的溝通, 包含接受輸入, 呈現資訊
  - 例如: GUI, CLI
- Domain Login(Business Logic): 負責處理具體的商業問題
  - 位於Presentation與Data Source中間 
- Data Source: 負責傳遞或是保存訊息 
  - 位於最底層
  - 例如: message queue, database
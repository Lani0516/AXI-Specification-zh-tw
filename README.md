**AXI Specification**
- 

- [1. 簡介](#簡介)
  - [1.1. AXI 協定概述](#axi-協定概述)
    - [1.1.1. 特色](#特色)
    - [1.1.2. 主要特色](#主要特色)
    - [1.1.3. 涵蓋內容](#涵蓋內容)
  - [1.2. AXI 架構](#axi-架構)
    - [1.2.1. 說明](#說明)
    - [1.2.2. 通道定義](#通道定義)
    - [1.2.3. 介面與互連](#介面與互連)
    - [1.2.4. 暫存器切片](#暫存器切片)
  - [1.3. 術語](#術語)
    - [1.3.1. 元件與拓撲](#元件與拓撲)
    - [1.3.2. 事務](#事務)
    - [1.3.3. 快取與快取操作](#快取與快取操作)
    - [1.3.4. 時間描述](#時間描述)
- [2. 訊號說明](#訊號說明)
  - [2.1. 全域訊號](#全域訊號)
  - [2.2. 寫入位址通道訊號](#寫入位址通道訊號)
    - [2.2.1. 由主端提供](#由主端提供)
    - [2.2.2. 由從端提供](#由從端提供)
  - [2.3. 寫入資料通道訊號](#寫入資料通道訊號)
    - [2.3.1. 由主端提供](#由主端提供)
    - [2.3.2. 由從端提供](#由從端提供)
  - [2.4. 寫入回應通道訊號](#寫入回應通道訊號)
    - [2.4.1. 由從端提供](#由從端提供)
    - [2.4.2. 由主端提供](#由主端提供)
  - [2.5. 讀取位址通道訊號](#讀取位址通道訊號)
    - [2.5.1. 由主端提供](#由主端提供)
    - [2.5.2. 由從端提供](#由從端提供)
  - [2.6. 讀取資料通道訊號](#讀取資料通道訊號)
    - [2.6.1. 由從端提供](#由從端提供)
    - [2.6.2. 由主端提供](#由主端提供)
  - [2.7. 低功耗介面訊號](#低功耗介面訊號)
- [3. 單一介面需求](#單一介面需求)
  - [3.1. 時鐘與重置](#時鐘與重置)
  - [3.2. 基本讀寫事務](#基本讀寫事務)
    - [3.2.1. 握手流程](#握手流程)
    - [3.2.2. 通道訊號要求](#通道訊號要求)
  - [3.3. 通道間的關係](#通道間的關係)
    - [3.3.1. 關係](#關係)
    - [3.3.2. 通道握手訊號間的相依性](#通道握手訊號間的相依性)
    - [3.3.3. 舊版相容性考量](#舊版相容性考量)
  - [3.4. 事務結構](#事務結構)
    - [3.4.1. 位址結構](#位址結構)
    - [3.4.2. 傳輸的偽程式碼描述](#傳輸的偽程式碼描述)
    - [3.4.3. 資料讀寫結構](#資料讀寫結構)
    - [3.4.4. 讀寫回應結構](#讀寫回應結構)
- [4. 事務屬性](#事務屬性)
  - [4.1. 事務類型與屬性](#事務類型與屬性)
  - [4.2. AXI3 記憶體屬性訊號](#axi3-記憶體屬性訊號)
    - [4.2.1. 事務屬性編碼](#事務屬性編碼)
  - [4.3. AXI4 記憶體屬性訊號的變更](#axi4-記憶體屬性訊號的變更)
    - [4.3.1. *AxCACHE[1], Modifiable*](#431-axcache1-modifiable)
    - [4.3.2. Read-Allocate 與 Write-Allocate 的新定義](#read-allocate-與-write-allocate-的新定義)
  - [4.4. 記憶體類型](#記憶體類型)
    - [4.4.1. 記憶體類型編碼](#記憶體類型編碼)
    - [4.4.2. 記憶體類型需求](#記憶體類型需求)
  - [4.5. 不一致的記憶體屬性](#不一致的記憶體屬性)
    - [4.5.1. 不一致的記憶體屬性](#不一致的記憶體屬性)
    - [4.5.2. 變更記憶體屬性](#變更記憶體屬性)
  - [4.6. 事務緩衝](#事務緩衝)
    - [4.6.1. 寫入事務](#寫入事務)
    - [4.6.2. 讀取事務](#讀取事務)
  - [4.7. 存取權限](#存取權限)
    - [4.7.1. 訊號](#訊號)
    - [4.7.2. 保護屬性](#保護屬性)
- [5. 事務識別碼](#事務識別碼)
  - [5.1. AXI 事務識別碼](#axi-事務識別碼)
  - [5.2. ID 訊號](#id-訊號)
    - [5.2.1. 通道事務 ID](#通道事務-id)
    - [5.2.2. 讀取資料排序](#讀取資料排序)
    - [5.2.3. 寫入資料排序](#寫入資料排序)
    - [5.2.4. 互連對事務識別碼的使用](#互連對事務識別碼的使用)
- [6. AXI 排序模型](#axi-排序模型)
  - [6.1. AXI 排序模型概述](#axi-排序模型概述)
  - [6.2. 記憶體位置與周邊區域](#記憶體位置與周邊區域)
  - [6.3. 事務與排序](#事務與排序)
  - [6.4. 觀察與完成的定義](#觀察與完成的定義)
    - [6.4.1. 觀察](#觀察)
    - [6.4.2. 完成](#完成)
  - [6.5. 主端排序保證](#主端排序保證)
    - [6.5.1. 收到完成回應前的保證](#收到完成回應前的保證)
    - [6.5.2. 完成回應所提供的保證](#完成回應所提供的保證)
    - [6.5.3. 回應排序保證](#回應排序保證)
  - [6.6. 排序要求](#排序要求)
    - [6.6.1. 從端排序要求](#從端排序要求)
    - [6.6.2. 互連排序要求](#互連排序要求)
  - [6.7. 端點前的回應](#端點前的回應)
    - [6.7.1. 提前讀取回應](#提前讀取回應)
    - [6.7.2. 提前寫入回應](#提前寫入回應)
  - [6.8. 有序寫入觀察](#有序寫入觀察)
    - [6.8.1. 有序寫入觀察](#有序寫入觀察)
    - [6.8.2. Ordered_Write_Observation](#ordered_write_observation)
- [7. 原子存取](#原子存取)
  - [7.1. 單一複本原子性大小](#單一複本原子性大小)
    - [7.1.1. 單一複本原子性大小](#單一複本原子性大小)
    - [7.1.2. 多複本寫入原子性](#多複本寫入原子性)
  - [7.2. 獨占存取](#獨占存取)
    - [7.2.1. 獨占存取流程](#獨占存取流程)
    - [7.2.2. 從主端角度看獨占存取](#從主端角度看獨占存取)
    - [7.2.3. 從從端角度看獨占存取](#從從端角度看獨占存取)
    - [7.2.4. 獨占存取限制](#獨占存取限制)
    - [7.2.5. 獨占存取的回應](#獨占存取的回應)
  - [7.3. 鎖定存取](#鎖定存取)
  - [7.4. 原子存取訊號](#原子存取訊號)
    - [7.4.1. AXI3 原子存取編碼](#axi3-原子存取編碼)
    - [7.4.2. AXI4 原子存取編碼](#axi4-原子存取編碼)
    - [7.4.3. 舊版相容性考量](#舊版相容性考量)
- [8. AMBA 4 附加訊號](#amba-4-附加訊號)
  - [8.1. QoS 訊號](#qos-訊號)
    - [8.1.1. QoS 介面訊號](#qos-介面訊號)
    - [8.1.2. 主端考量](#主端考量)
    - [8.1.3. 系統考量](#系統考量)
  - [8.2. 多區域訊號](#多區域訊號)
    - [8.2.1. 附加介面訊號](#附加介面訊號)
  - [8.3. 使用者定義訊號](#使用者定義訊號)
    - [8.3.1. 使用者定義訊號組態](#使用者定義訊號組態)
    - [8.3.2. 訊號傳遞](#訊號傳遞)
    - [8.3.3. 使用考量](#使用考量)
- [9. 預設訊號與互通性](#預設訊號與互通性)
  - [9.1. 互通性原則](#互通性原則)
  - [9.2. 主要介面類別](#主要介面類別)
    - [9.2.1. 讀寫介面](#讀寫介面)
    - [9.2.2. 唯讀介面](#唯讀介面)
    - [9.2.3. 唯寫介面](#唯寫介面)
    - [9.2.4. 記憶體從端與周邊從端](#記憶體從端與周邊從端)
  - [9.3. 預設訊號值](#預設訊號值)
    - [9.3.1. 預設訊號值](#預設訊號值)
    - [9.3.2. 預設訊號要求](#預設訊號要求)

# 1. 簡介

## 1.1. AXI 協定概述 

### 1.1.1. 特色

- 高性能、低延遲
- 高頻通信、結構簡單
- 滿足各種組件的接口要求
- 適用於具有較高初始訪問延遲的內存控制器
- 互聯架構實施高度靈活
- 兼容AHB&APB接口

### 1.1.2. 主要特色

- 地址/控制信息和數據單獨傳輸
- 支持非對齊數據傳輸，使用寫選通信號（按字節）
- 使用突發為基礎的事務傳輸，主機僅需發出首地址
- 獨立的讀寫數據通道，提供低開銷的直接數據訪問
- 支持outstanding操作，即Master不用等待上一個事務傳輸完成就可發送下一個事務的地址
- 支持out of order操作，即Slave返回數據時可不必按照Master發送的地址順序
- 允許添加寄存器級以提供時序收斂

### 1.1.3. 涵蓋內容

- AXI4 Lite
- AXI5 Lite
  
## 1.2. AXI 架構

### 1.2.1. 說明

- **Transaction channels**
  - Write address，寫地址通道，信號以AW開頭
  - Write data，寫數據通道，信號以W開頭
  - Write response，寫回應通道，信號以B開頭
  - Read address，讀地址通道，信號以AR開頭
  - Read data，讀數據通道，信號以R開頭

- **Channel architecture of transaction**
  - 寫入事務的通道架構 
    ![寫事務的通道架構](README.assets/1.jpg)
  - 讀取事務的通道架構 
    ![讀事務的通道架構](README.assets/2.jpg)


### 1.2.2. 通道定義

五個獨立的通道都採用VALID和READY的握手協議，此外讀寫數據通道還包括一個LAST信號
- **Read&Write Address Channels**  
    讀寫事務擁有自己的地址通道，地址通道可以攜帶所需的地址和控制信息
- **Read Data Channel**  
    包括數據總線（可支持8－1024位）和一個讀響應信號
- **Write Data Channel**  
    1、包括數據總線（可支持8－1024位）和一個字節大小的通道選通信號（每八個數據位一個字節通道選通信號，指示數據總線的哪個字節有效）    
    2、寫數據通道信息始終被視為已緩衝，因此主機可以執行寫事務，而無需從機確認先前的寫事務
- **Write Data Channel**  
    1、主要支持從機返回響應信號，表示傳輸完成
    2、每個burst傳輸僅需一個完成信號

### 1.2.3. 介面與互連

- **Interface**  
    主機和Interconnect、從機和Interconnect以及主從機之間均需要接口

- **Interconnect Approaches**
    - **共用位址與資料匯流排**   
        地址和數據總線均共享
    - **共用位址匯流排與多組資料匯流排**  
        地址總線共享、數據總線私有
    - **多層架構，使用多組位址與資料匯流排**  
        多層結構，數據和地址總線均私有

### 1.2.4. 暫存器切片

- 寄存器切片對AXI總線的關鍵路徑進行切斷和分割，以獲得更好的時序性能

## 1.3. 術語

### 1.3.1. 元件與拓撲

- Component
- Master component
- Slave component
    - Memory slave component
    - Peripheral slave component
- Interconnect component

### 1.3.2. 事務

- Transaction
- Burst
- Beats

### 1.3.3. 快取與快取操作

- Cache
- Cache line

### 1.3.4. 時間描述

- The AXI specification uses the term in a timely manner.

# 2. 訊號說明

## 2.1. 全域訊號

- **ACLK**
    時鐘來源

- **ARESETn**  
    重置來源   
    低電位有效

## 2.2. 寫入位址通道訊號

### 2.2.1. 由主端提供

- **AWID**  
    Write address ID，寫地址ID，用來標誌一組寫信號
- **AWADDR**   
    Write address，寫地址，突發傳輸首地址
- **AWLEN**   
    Burst length，突發傳輸的傳輸次數
- **AWSIZE**   
    Burst size，每次傳輸的字節數
- **AWBURST**   
    Burst type，加上size信息用來計算突發傳輸內每次傳輸的地址
- **AWLOCK**   
    Lock type，總線鎖信號，可提供操作的原子性
- **AWCACHE**   
    Cache type，內存類型，表明一次傳輸是怎樣通過系統的
- **AWPROT**  
    Protection type，指示事務的保護級別（正常、特權、安全）以及事務是數據訪問還是指令訪問
- **AWQOS**   
    寫事務服務質量
- **AWREDION**   
    區域標誌，能實現單一物理接口提供多個邏輯接口
- **AWUSER**   
    用戶自定義信號
- **AWVALID**   
    1、Write address valid，指示寫地址總線和控制信息是否有效，高電平有效  
    2、在AWREADY變高前一直保持

### 2.2.2. 由從端提供

- **AWREADY**   
    Write address ready，指示從機可以接收地址和控制信息，高電平有效

## 2.3. 寫入資料通道訊號

### 2.3.1. 由主端提供

- **WID**  
    Write ID tag，寫過程ID，一次寫傳輸的ID，必須和AWID相匹配
    *AXI4中已取消*
- **WDATA**  
    Write data，可支持8-1024位數據傳輸
- **WSTRB**  
    Write strobes（寫選通信號），指示當前傳輸的有效數據段,每一位對應一個字節
- **WLAST**  
    Write last，表明突發傳輸的最後一次傳輸
- **WUSER**  
    用戶自定義信號
- **WVALID**  
    Write valid，指示寫數據和寫跳變信息有效與否，高有效

### 2.3.2. 由從端提供

- **WREADY**  
    Write ready，高電平時才可進行寫數據

## 2.4. 寫入回應通道訊號

### 2.4.1. 由從端提供

- **BID**  
    Response ID，寫響應ID標籤，和AWID相對應
- **BRESP**  
    1、Write response，表示寫事務的狀態       
    2、包括4種狀態：OKAY、EXOKAY、SLVERR、DECERR
- **BUSER**  
    用戶自定義信號
- **BVALID**  
    Write response valid，高電平時寫響應信號有效

### 2.4.2. 由主端提供

- **BREADY**    
    Response ready，高電平時表示主機可接受響應信號

## 2.5. 讀取位址通道訊號

### 2.5.1. 由主端提供
- **ARID**  
    Write address ID，用來標誌一組讀信號
- **ARADDR**  
    Write address，給出一次讀突發傳輸的讀地址
- **ARLEN**  
    Burst length，給出突發傳輸的次數
- **ARSIZE**  
    Burst size，給出每次傳輸的字節數
- **ARBURST**  
    Burst type
- **ARLOCK**  
    Lock type，總線鎖信號，可提供操作的原子性
- **ARCACHE**  
    Cache type，內存類型，表明一次傳輸是怎樣通過系統的
- **ARPROT**  
    Protection type，表明一次傳輸的特權級及安全等級
- **ARQOS**  
    服務質量
- **ARREGION**  
    區域標誌，能實現單一物理接口對應的多個邏輯接口
- **ARUSER**  
    用戶自定義信號
- **ARVALID**  
    有效信號，表明此通道的地址控制信號有效

### 2.5.2. 由從端提供

- **ARREADY**  
    表明Slave可以接收地址和對應的控制信號

## 2.6. 讀取資料通道訊號

### 2.6.1. 由從端提供

- **RID**  
    Read ID tag，一次讀傳輸的ID
- **RDATA**  
    Read data，可支持8-1024位數據傳輸
- **RRESP**  
    Read response，表明讀傳輸的狀態
- **RLAST**  
    Indicating last data transfer in a read transaction
- **RUSER**  
    用戶自定義信號
- **RVALID**  
    Read valid，表明此通道信號有效

### 2.6.2. 由主端提供

- **RREADY**  
    Read ready，表明主機能夠接收讀數據和響應信息

## 2.7. 低功耗介面訊號

- **CSYSREQ**  
    1、System low-power request  
    ​2、Clock controller --> Peripheral device
- **CSYSACK**  
    1、Low-power request acknowlegement  
    2、Peripheral device --> Clock controller
- **CACTIVE**  
    1、Clock active   
    2、Peripheral device --> Clock controller

# 3. 單一介面需求

## 3.1. 時鐘與重置

- **Clock**
    - 每個AXI接口都有一個單獨的時鐘信號 *ACLK* 
    - 所有輸入信號均在 *ACLK* 的上升沿進行採樣 
    - 所有輸出信號必須在 *ACLK* 上升沿之後改變 
- **Reset**
    - **特點**  
        - 低電平有效，異步復位、同步釋放
    - **復位期間對個接口信號要求**  
        - 主接口信號 *ARVALID*、*AWVALID* 和 *WVALID* 必須拉低  
        - 從接口信號 *RVALID* 和 *BVALID* 必須拉低

## 3.2. 基本讀寫事務

### 3.2.1. 握手流程

- **特點**  
    - 每個通道均採用以VALID/READY為握手信號的流控機制  
    - Master和Slave都可以控制數據的傳輸速率  
    - VALID信號由源設備產生，READY信號由目的設備產生  
    - 當VALID和READY均為高時數據才可傳輸

- **示例**    
    - VALID before READY handshake 
        ![VbR](README.assets/3.jpg)
    - READY before VALID handshake 
        ![RbV](README.assets/4.jpg)
    - VALID with READY handshake   
        ![VwR](README.assets/5.jpg)   

### 3.2.2. 通道訊號要求

- **Write address channel**  
    - 僅當地址和控制信息有效時主機才可拉高 *AWVALID*，並一直保持到從機拉高 *AWREADY*  
    - *AWREADY* 缺省值可高可低，但一般為高，否則至少需要兩個時鐘週期才能完成數據傳輸

- **Write data channel**  
    - 僅當地址和控制信息有效時主機才可拉高 *WVALID* ，並一直保持到從機 *WREADY*   
    - 僅當從機在一個週期內可接受寫數據時，*WREADY* 可缺省為高  
    - 最後一次寫傳輸時主機需要把 *WLAS* T拉高  
    - *WVALID* 為低時，寫選通信號可為任意值，但一般為低或保持之前的值  
    - 無效字節一般保持為0

- **Write response channel**  
    - 僅當寫響應信號有效時從機才可拉高 *BVALID*，並一直保持到主機拉高 *BREADY*  
    - 僅當主機在一個週期內可接受寫響應信號時，*BREADY* 可缺省為高

- **Read address channel**  
    - 僅當地址和控制信息有效時主機才可拉高 *ARVALID*，並一直保持到從機拉高 *ARREADY*  
    - *ARREADY* 缺省值可高可低，但一般為高，否則至少需要兩個時鐘週期才能完成數據傳輸  

- **Read data channel**  
    - 僅當地址和控制信息有效時主機才可拉高 *RVALID*，並一直保持到從*RREADY*  
    - 僅當從機在一個週期內可接受寫數據時，*RREADY* 可缺省為高  
    - 最後一次寫傳輸時主機需要把 *RLAST* 拉高  
    - 無效字節一般保持為0 

## 3.3. 通道間的關係

### 3.3.1. 關係

- 寫響應必須在寫事務中的最後一次傳輸後
- 讀數據跟隨讀地址
- 通道間的握手信號存在依賴關係
- Note
    - Master發出讀寫請求之後，必須能夠提供或接收相關數據，並且在事務傳輸期間不依賴於來自該Master的其他事務
    - Master可以依賴從使用相同ID的事務按順序返回的讀取數據，因此，Master僅需要足夠的存儲空間來存儲來自具有不同ID的事務的讀取數據。
  
### 3.3.2. 通道握手訊號間的相依性

- **In Any Transanction**  
    - 不同AXI組件之間的VALID和READY信號沒有依賴關係  
    - READY信號可以等待VALID信號置位  
- **In Read Transanction**  
    ![讀通道握手信號依賴關係](README.assets/6.jpg)  
    - 從機在拉高ARREADY之前可以等待ARVALID  
    - 從機在拉高RVALID之前必須等待ARVALID和ARREADY
- **In Write Transanction**
    - AXI3 
        ![AXI3寫通道握手信號依賴關係](README.assets/7.jpg)  
        - 主機在拉高AWVALID或WVALID之前不必等待AWREADY或WREADY
            WVALID不必等待AWREADY可以防止在從機拉高AWREADY之前等待WVALID的情況下造成死鎖    
        - 從機可以在拉高AWREADY或WREADY之前等待AWVALID或WVALID  
        - 從機在拉高BVALID之前必須等待WVALID和WREADY以及WLAST
    - AXI4&AXI5     
        ![AXI4寫通道握手信號依賴關係](README.assets/8.jpg) 
        - 從機在拉高BVALID之前必須等待AWVALID、AWREADY、WVALID和WREADY以及WLAST  
        - 其他同AXI3

### 3.3.3. 舊版相容性考量

- AXI4&AXI5較AXI3的區別  
    Slave在接收正確的地址之前不返回給Master寫響應信號

## 3.4. 事務結構

### 3.4.1. 位址結構  
    
突發傳輸不得跨越 4KB 位址邊界。  

- **Burst length**  
    - **Definition**  
        - *AxLEN[3:0]* for AXI3，*AxLEN[7:0]* for AXI4 
          - *ARLEN[7:0]*，for read transfers
          - *AWLEN[7:0]*，for write transfers  
        - Burst_length = AxLEN + 1  
        
    - **Burst lengths supported**  
        1、AXI3對所有突發類型均支持1-16次傳輸長度  
        2、AXI4對INCR類型支持1-256次傳輸長度，對其他類型僅支持1-16次傳輸長度

    - **Rules**  
        1、對於WRAP類型，長度必須是2、4、8或16  
        2、一次Burst傳輸不能跨越4KB邊界  
        3、不支持提前終止Burst傳輸
        - 可以通過禁止進一步的寫操作或者忽略後續數據 來達到減少傳輸次數，但是在此情況下仍然需要完成後續的傳輸。
        - 訪問一些對讀操作敏感的設備如FIFO等，忽略後續數據會造成數據丟失
        - 可將長Burst打成多個短Burst
        - 
- **Burst size**
    - **Definition**  
        1、*AxSIZE[2:0]*，表示在Burst傳輸中，一次傳輸可支持的最大字節數  
        2、*ARSIZE[2:0]*，for read transfers  
        3、*AWSIZE[2:0]*，for write transfers

    - **Encoding**  
        | AxSIZE[2:0] | Bytes in transfer |
        |-|-|
        |000|**1**|
        |001|**2**|
        |010|**4**|
        |011|**8**|
        |100|**16**|
        |101|**32**|
        |110|**64**|
        |111|**128**|
    - ***Burst大小不能超過數據總線寬度*** 

- **Burst type**
    - **Types**  
        ***FIXED***  
        傳輸過程中地址固定，用於FIFO訪問 

        ***INCR***  
        增量突發，傳輸過程中，地址遞增，增加量取決於AxSIZE的值 

        ***WRAP***    
        1、回環突發，和增量突發類似，但會在特定高地址的邊界處回到低地址處。回環突發的長度只能是2,4,8,16次傳輸，傳輸首地址和每次傳輸的大小對齊。最低的地址與整個傳輸的數據大小對齊。回環邊界等於（AxSIZE*AxLEN）  
        2、用於訪問Cache line

    - **Definition**
        1、*AWBURST[1:0]*，for write tranfers  
        2、*ARBURST[1:0]*，for read tranfers  
        3、Encoding  
        | AxBURST[1:0] | Burst type |
        |-|-|
        |000|*FIXED*|
        |001|*INCR*|
        |010|*WRAP*|
        |011|*Reserved*|

- **Burst address**
    - **Variables**  
        - $Start\_Address$  
        首地址  
        - $Number\_Bytes$  
        每次傳輸可以支持的最大字節數  
        - $Data\_Bus\_Bytes$  
        在數據總線中的字節通道數  
        - $Aligned\_Address$  
        首地址的對其形式  
        - $Burst\_Length$  
        在一個Burst傳輸中總傳輸次數  
        - $Address\_N$  
        在一個Burst傳輸中第N次傳輸的地址  
        - $Wrap\_Boundary$  
        在WRAP Burst中的地址下邊界   
        - $Lower\_Byte\_Lane$  
        在一次傳輸中的最低尋址字節的字節通道  
        - $Upper\_Byte\_Lane$  
        在一次傳輸中的最高尋址字節的字節通道 
        - $INT(x)$  
        向下取整 

    - **Equations**
        - *Address* 
            - 首地址  
              $Start\_Adress = AxADDR$
            - 數據包字節數  
              $Number\_Bytes = 2^{AxSIZE}$
            - 傳輸長度
              $Burst\_Length = AxLEN + 1$
            - 對齊地址
              $Aligned\_Address = (INT(Start\_Address / Number\_Bytes)) \times Number\_Bytes$
            - 第一次傳輸地址
              $Address\_1 = Start\_Address$
          
            - INCR burst和地址未到達邊界的WRAP burst
                - 第N次傳輸地址
                  $Address\_N = Aligned\_Address + (N-1) \times Number\_bytes$
            
            - WRAP burst   
                - 回環邊界  
                  $Wrap\_Boundary = (INT(Start\_Address / (Number\_Bytes \times Burst\_Length))) \times (Number\_Bytes \times Burst\_Length)$   
                - 當地址遞增至$Wrap\_Boundary + (Number\_Bytes \times Burst\_Length)$  
                    - 當前傳輸地址  
                      $Address\_N = Wrap\_Boundary$
                    - 下一傳輸地址
                      $Address\_ = Start\_Adress + (N-1)\times Number\_Bytes - (Number\_Bytes \times Burst\_Length)$  
        - *Byte lane*
            - For first transfer
              - 最低尋址字節通道
                - $Lower\_Byte\_Lane = Start\_Address – (INT(Start\_Address / Data\_Bus\_Bytes)) \times Data\_Bus\_Bytes$
              - 最高尋址字節通道
                - $Upper\_Byte\_Lane = Aligned\_Address + (Number\_Bytes – 1) – (INT(Start\_Address / Data\_Bus\_Bytes)) \times Data\_Bus\_Bytes$
            - For other transfers
              - 最低尋址字節通道
                - $Lower\_Byte\_Lane = Address\_N – (INT(Address\_N / Data\_Bus\_Bytes)) \times Data\_Bus\_Bytes$
              - 最高尋址字節通道
                - $Upper\_Byte\_Lane = Lower\_Byte\_Lane + Number\_Bytes - 1$
            - Data is transferred on:
              - $DATA((8 \times Upper\_Byte\_Lane) + 7: (8 \times Lower\_Byte\_Lane))$  
        - *Transaction Container*
          - $Container\_Size = Number\_Bytes \times Burst\_Length$
          - For INCR bursts
            - $Container\_Lower = Aligned\_Adress$
            - $Container\_Upper = Aligned\_Adress + Container\_Size$
          - For WRAP bursts
            - $Container\_Lower = Wrap\_Boundary$
            - $Container\_Upper = Wrap\_Boundary + Container\_Size$

### 3.4.2. 傳輸的偽程式碼描述

```text
//DataTransfer()
//=============

DataTransfer(Start_Address, Number_Bytes, Burst_Length, Data_Bus_Bytes, Mode, IsWrite)
// Data_Bus_Bytes is the number of 8-bit byte lanes in the bus
// Mode is the AXI transfer mode
// IsWrite is TRUE for a write, and FALSE for a read

assert Mode IN {FIXED, WRAP, INCR};   
addr = Start_Address;     // Variable for current address    
Aligned_Address = (INT(addr/Number_Bytes) * Number_Bytes);    
aligned = (Aligned_Address == addr);    // Check whether addr is aligned to nbytes   
dtsize = Number_Bytes * Burst_Length;   // Maximum total data transaction size 

if mode == WRAP then        
    Lower_Wrap_Boundary = (INT(addr/dtsize) * dtsize);        
    // addr must be aligned for a wrapping burst        
    Upper_Wrap_Boundary = Lower_Wrap_Boundary + dtsize;    
for n = 1 to Burst_Length        
    Lower_Byte_Lane = addr - (INT(addr/Data_Bus_Bytes)) * Data_Bus_Bytes;        
    if aligned then            
        Upper_Byte_Lane = Lower_Byte_Lane + Number_Bytes - 1        
    else            
        Upper_Byte_Lane = Aligned_Address + Number_Bytes - 1 - (INT(addr/Data_Bus_Bytes)) * Data_Bus_Bytes;         
        
    // Peform data transfer        
    if IsWrite then            
        dwrite(addr, low_byte, high_byte);
    else            
        dread(addr, low_byte, high_byte);        
        
    // Increment address if necessary        
    if mode != FIXED then            
        if aligned then
            addr = addr + Number_Bytes;                
            if mode == WRAP then                    
                //WRAP mode is always aligned                    
                if addr >= Upper_Wrap_Boundary then 
                    addr = Lower_Wrap_Boundary;           
        else                
            addr = Aligned_Address + Number_Bytes;                
            aligned = TRUE;            // All transfers after the first are aligned    
return;


```

### 3.4.3. 資料讀寫結構

- **Write strobes**
  - *WSTRB[n]* 對應WDATA[(8n)+7:(8n)],每一位選通信號對應8位數據位，即1個字節
  - *WSTRB[n]* 為高表示WDATA[(8n)+7:(8n)]包含的數據有效，且僅當對應數據位中的數據有效時主機才能拉高WSTRB
  - WVALID為低時，WSTRB可以是任意值

- **Narrow transfers**
  - Burst Size小於總線位寬時即發生窄傳輸，進行窄傳輸時需要選擇數據傳輸的字節通道(Byte Lane)
    - 對於增量和回環突發傳輸，每一次傳輸所用到的字節通道不盡相同
    - 對於固定突發傳輸，每一次傳輸用到的字節通道是一樣的
  - 示例
    - 8-bit transfers on 32-bit bus  
        ![8-bit](README.assets/9.jpg)
    - 32-bit transfers on 64-bit bus 
        ![32-bit](README.assets/10.jpg)

- **Byte invariance**
  - 即字節所在的位置與大小端定義無關。完全按照其地址所對應的偏移來決定其採用哪一個字節通道(byte lane)來傳輸，換句話說，在AXI中，認為所有的傳輸都是以byte為單位的，每次傳輸都是傳了多少個byte
  - 字節不變性保證了大小端數據存儲在同一個Memory中不會會互相影響

- **Unaligned transfers**
  - 使用低位地址線表示未對齊的起始地址。
  - **提供一個對齊的地址，並使用字節通道選通信號指示未對齊的起始地址。**

### 3.4.4. 讀寫回應結構

- **Response signals**
  - **讀事務**
    - *RRSEP[1:0]*
    - 通過讀數據通道返回給Master
  - **寫事務**
    - *BRESP[1:0]*
    - 通過寫響應通道返回給Master
  - **xRESP Encoding**
    | xRESP[1:0] | Response |
    |--|--|
    |00|*OKAY*|
    |01|*EXOKAY*|
    |10|*SLVERR*|
    |11|*DECERR*|

- **Response indication**
  - ***OKAY, normal access success***
    - 普通訪問成功
    - 獨佔訪問失敗
    - 對不支持獨佔訪問的Slave進行獨佔訪問
  - ***EXOKAY, exclusive access success***
    - 獨佔訪問成功
  - ***SLVERR, slave error***
    - 事務傳輸失敗
    - **Slave發生錯誤的情況**
      - FIFO或緩存溢出
      - 傳輸大小不支持
      - 對只讀區域進行寫操作
      - Slave響應超時
      - 訪問禁用或掉電功能
  - ***DECERR, decode error***
    - Interconnect無法解碼

# 4. 事務屬性

## 4.1. 事務類型與屬性

- **Slave**
  - **Memory slave**
  - **Periphral slave**

- **Attributes**
  - **相關信號**
    - *AWCACHE*
    - *ARCACHE*
  - **作用**
    - 控制事務傳輸在系統中如何進行
    - 控制系統級緩存如何處理事務

## 4.2. AXI3 記憶體屬性訊號

### 4.2.1. 事務屬性編碼

- **Encoding** 
<table>
    <tr>
        <th>AxCACHE[n]</th>
        <th>Value</th>
        <th>Transaction Attribute</th>
    </tr>
    <tr>
        <td rowspan="2">0</td>
        <td>0</td>
        <td><em>Non-bufferable</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Bufferable</em></td>
    </tr>
    <tr>
        <td rowspan="2">1</td>
        <td>0</td>
        <td><em>Non-cacheable</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Cacheable</em></td>
    </tr>
    <tr>
        <td rowspan="2">2</td>
        <td>0</td>
        <td><em>No Read-Allocate</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Read-Allocate</em></td>
    </tr>
    <tr>
        <td rowspan="2">3</td>
        <td>0</td>
        <td><em>No Write-Allocate</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Write-Allocate</em></td>
    </tr>
</table>

- ***AxCACHE***
  - *AxCACHE[0], Bufferable(B)bit*
    - 此位拉高時，該傳輸事務在到達目的地之前可以被Interconnect或者任何AXI組件緩存、延遲若干週期
    - 一般只用於寫事務 
  - *AxCACHE[1], Cacheable(C)bit*
    - 拉高時允許對傳輸事務進行分配，其他相關信息由RA和WA提供
    - 最終目的地的事務屬性不必與原事務屬性匹配
      - 寫事務可以聚合
      - 讀事務可以預取數據或者一次取數據可以用於多次傳輸
  - *AxCACHE[2], Read-Allocate(RA)bit*
    - 讀分配策略
  - *AxCACHE[3], Write-Allocate(WA)bit*
    - 寫分配策略

## 4.3. AXI4 記憶體屬性訊號的變更

### 4.3.1. *AxCACHE[1], Modifiable*

- **Non-modifiable transactions**
  - *AxCACHE[1]* 為低表示傳輸事務傳輸特性**不可修改**
  - 傳輸事務不能被分割或聚合，但當突發長度大於16時可以被分割，分割後的事務仍然遵守本小節的規則
  - 以下參數不可修改
    |Parameter|訊號|
    |--|--|
    |Transfer Address|*AxADDR、AxREGION*|
    |Burst size|*AxSIZE*|
    |Burst length|*AxLEN*|
    |Burst type|*AxBURST*|
    |Lock type|*AxLOCK*|
    |Protection type|*AxPORT*|
  - *AxCACHE* 僅可修改Bufferable位使其屬性從Bufferable變為Non-bufferable
  - 事務ID和QoS值可以修改
  - **注意**
    當Burst size大於數據總線位寬時，事務可不遵循上述規則

- **Modifiable transactions**
  - *AxCACHE[1]* 為高表示傳輸事務傳輸特性**可修改**
  - 傳輸事務可以分割或聚合
  - 讀傳輸事務中，可以預取相鄰地址上的讀數據，目的地址可以返回比主機需求更多的數據
  - 寫傳輸事務中，可以訪問比需求地址跨度更大的區域，其中使用 *WSTRB* 信號防止更新無關地址
  - 可修改的參數
    - **Transfer address**
    - **Burst size**
    - **Burst length**
    - **Burst type**
    - **Transaction ID**
    - **QoS value**
  - 不可修改的參數
    - **Lock type**
    - **Protection Type**
  - **內存屬性也可修改**，只是保證其他組件對事務的可見性不被降低，例如阻止事務傳輸到指定的位置或更改在緩存中查找事務的需求。另外對同一地址範圍內的所有事務，對內存屬性的任何更改必須保持一致
  - **注意：兩種情況下，事務屬性不可修改**
    - 修改地址後若超過KB邊界
    - 導致對單拷貝原子大小區域的單次訪問被作為多次訪問執行

### 4.3.2. Read-Allocate 與 Write-Allocate 的新定義

- **Redefining**
  - **讀傳輸事務**
    - *WA*位拉高表示當前地址的數據因為寫傳輸事務或者其他主機的傳輸已經緩存在Cache中
  - **寫傳輸事務**
    - *RA*位拉高表示當前地址的數據因為讀傳輸事務或者其他主機的傳輸已經緩存在Cache中

- **Cache Allocate**
  - *AWCACHE bit allocations* 
    ![Write-Allocate](README.assets/11.jpg)
  - *ARCACHE bit allocations* 
    ![Read-Allocate](README.assets/12.jpg)

## 4.4. 記憶體類型

### 4.4.1. 記憶體類型編碼

<table>
    <tr>
        <th>ARCACHE[3:0]</th>
        <th>AWCACHE[3:0]</th>
        <th>Memory type</th>
    </tr>
    <tr>
        <td>0b0000</td>
        <td>0b0000</td>
        <td><em>Device Non-bufferable</em></td>
    </tr>
    <tr>
        <td>0b0001</td>
        <td>0b0001</td>
        <td><em>Device Bufferable</em></td>
    </tr>
    <tr>
        <td>0b0010</td>
        <td>0b0010</td>
        <td><em>Normal Non-cacheable Non-bufferable</em></td>
    </tr>
    <tr>
        <td>0b0011</td>
        <td>0b0011</td>
        <td><em>Normal Non-cacheable Bufferable</em></td>
    </tr>
    <tr>
        <td>0b1010</td>
        <td>0b0110</td>
        <td><em>Write-Through No-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1110(0b0110)</td>
        <td>0b0110</td>
        <td><em>Write-Through Read-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1010</td>
        <td>0b1110(0b1010)</td>
        <td><em>Write-Through Write-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1110</td>
        <td>0b1110</td>
        <td><em>Write-Through Read and Write-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1011</td>
        <td>0b0111</td>
        <td><em>Write-Back No-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1111(0b0111)</td>
        <td>0b0111</td>
        <td><em>Write-Back Read-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1011</td>
        <td>0b1111(0b1011)</td>
        <td><em>Write-Back Write-Allocate</em></td>
    </tr>
    <tr>
        <td>0b1111</td>
        <td>0b1111</td>
        <td><em>Write-Back Read and Write-Allocate</em></td>
    </tr>
</table>
 
- **表中未出現的值均保留**

### 4.4.2. 記憶體類型需求

- **Device訪問**
  - 在訪問 Device 時，*AxCACHE[3:1] = 3'b000*,傳輸事務在中間節點不能被修改。具體地說，不能預讀數據（Prefetch read）和匯聚寫數據（Merge write）。這是因為在訪問非存儲外設時，讀寫的是寄存器值，預取數據是沒有必要的。而將不同的寫事務聚集則容易造成預期之外的問題，比如會導致相鄰寄存器操作的先後順序無法滿足。
  - 根據 *AxCACHE[0]* 決定 Device 訪問是否可以被中間節點緩存，決定*bufferable*性質。
    - **Non-bufferable**，*AxCACHE[0] = 0*，不可以被中間節點緩存
    - **Bufferable**，*AxCACHE[0] = 1*，可以被中間節點緩存

- **Normal Non-cacheable訪問**
  - Normal 訪問指正常地訪問存儲介質，而不會查找緩存，*AxCACHE[3:1] = 3'b001*。Normal 非緩存訪問中，中間組件可以對傳輸事務信息進行修改，支持寫事務聚合。
  - 根據*AxCACHE[0]* 決定 normal 訪問是否可以被中間節點緩存，決定bufferable性質。
    - **Non-bufferable**，*AxCACHE[0] = 0*，不可以被中間節點緩存
    - **Bufferable**，*AxCACHE[0] = 1*，可以被中間節點緩存

- **Write-Through訪問**
  - *Write-through* 指緩存的寫入策略為直寫，即數據寫入緩存的同時，也寫入主存儲中。此時*AxCache[1:0] = 2'b10*，即中間組件可以修改傳輸事務，實現寫聚合與讀預取。*AxCache[0]* 置低，每個寫事務最終必須寫入目的地址。
  - 此類訪問啓用緩存，讀數據可以來自緩存，並且每次讀寫操作都需要查找緩存，尋找匹配表項。
  - 根據*AxCache[3:2]* 不同，從圖中得到共有 4 種情況，分別代表不同的分派提示。不過這都只是代表處理器從性能出發給出的建議，由緩存控制器視情況執行。
    - **No-Allocate**，*ARCACHE[3:2] = 2'b10*、*AWCACHE[3:2] = 2'b01*，代表建議不要為該事務分派緩存空間。
    - **Read-Allocate**，*ARCACHE[3:2] = 2'bx1*、*AWCACHE[3:2] = 2'b01*，代表建議為讀事務分派緩存，但不建議為寫事務分派緩存。
    - **Write-Allocate**，*ARCACHE[3:2] = 2'b10*、*AWCACHE[3:2] = 2'b1x*，代表建議為寫事務分派緩存，但不建議為讀事務分派緩存。
    - **Read and Write-Allocate**，*ARCACHE[3:2] = 2'b11*、*AWCACHE[3:2] = 2'b11*，代表建議為讀寫事務均分派緩存。

- **Write-Back訪問**
  - *Write-Back* 指緩存的寫入策略為寫回，數據僅寫入緩存，修改的緩存只在被替換時寫入主存儲。
  - *AxCache[1:0] = 2'b11*，即中間組件可以修改傳輸事務，並且進行緩存。
  - 與 Wirte-through 訪問相比，區別在於由於寫回策略中並不是每次寫事務後都需要更新主緩存，因此無需將每個寫事務傳輸至其本來的目的地（即主存儲）。
  - 和*Write-Through* 相同，根據*AxCache[3:2]* 不同，從圖中得到共有 4 種情況，分別代表不同的分派提示。不過這都只是代表處理器從性能出發給出的建議，由緩存控制器視情況執行。
    - **No-Allocate**，*ARCACHE[3:2] = 2'b10*、*AWCACHE[3:2] = 2'b01*，代表建議不要為該事務分派緩存空間。
    - **Read-Allocate**，*ARCACHE[3:2] = 2'bx1*、*AWCACHE[3:2] = 2'b01*，代表建議為讀事務分派緩存，但不建議為寫事務分派緩存。
    - **Write-Allocate**，*ARCACHE[3:2] = 2'b10*、*AWCACHE[3:2] = 2'b1x*，代表建議為寫事務分派緩存，但不建議為讀事務分派緩存。
    - **Read and Write-Allocate**，*ARCACHE[3:2] = 2'b11*、*AWCACHE[3:2] = 2'b11*，代表建議為讀寫事務均分派緩存。
 
## 4.5. 不一致的記憶體屬性

### 4.5.1. 不一致的記憶體屬性

- 所謂**內存屬性不匹配**指的是多個Master可採用不同的內存屬性去訪問同一內存區域。但必須遵循以下准則：
  - 所有訪問同一內存區域的的Master需要考慮任何層次內存區域的緩存一致性問題:
    - 訪問**不可緩存**地址區域：所有傳輸事務的AxCACHE[3:2]必須為2'b00;
    - 訪問**可緩存**地址區域：所有傳輸事務的AxCACHE[3:2]必須**不**為2'b00。
- 不同的Master可以採用不同的**緩存分派策略**
- 訪問具有**正常不緩存**屬性的尋址區域時，可採用**Device**訪問，即可把此塊存儲區域視為外設
- 如果尋址區域具有Bufferable屬性，則任何Master都可以使用不允許進行緩衝行為的事務來訪問

### 4.5.2. 變更記憶體屬性

- 一些特殊的內存區域可以修改內存屬性，比如從**直寫**改為**寫回**。
- 執行更改時需要合理的流程：
  - 所有主機停止訪問該內存區域
  - 單個主機執行緩存維護操作
  - 所有主機採用新的屬性重新訪問

## 4.6. 事務緩衝

### 4.6.1. 寫入事務

- 對以下內存類型，寫事務具有相同的要求：即事務的響應可以來自中間節點，而非目的地；另外寫事務必須對目的地及時可見（寫事務必須最終到達目的地，而不能一直緩存在Buffer中）。
  - **Device Bufferable**
  - **Normal Non-cacheable Bufferable**
  - **Write-Through**

- 可以保存和合併寫事務的**中間緩衝區**必須確保事務不會無限期地保留在其緩衝區中。 例如，合併寫事務不得重置確定何時將寫事務傳輸到最終目的地的機制。

### 4.6.2. 讀取事務

- 對於不同的內存類型，讀事務具有不同的要求：
  - **Device Bufferable：** 讀數據必須從目的地獲取
  - **Normal Non-cacheable Bufferable：** 讀數據要麼從目的地獲取，要麼從目的地相同的寫事務中獲取。從寫事務獲取讀數據時必須保證寫事務是最新版本，同時由此得來的數據不能被緩存
  - **Write-Through：** 讀數據可以從中間的Cache中獲得

- 可以響應事務的**中間緩衝區**必須確保對*Normal Non-cacheable Bufferable* 內存的任何讀事務最終都將到達其目的地。這就意味著中間緩衝區對事務的緩衝不可能一直持續下去。該協議未定義任何機制來確定用於轉發讀取事務的數據可以保留多長時間。但是，在這種機制下，讀取數據的行為一定不能重置數據超時時間。

## 4.7. 存取權限

### 4.7.1. 訊號

- **AxPORT**
    為了阻止惡意程序越權訪問的關鍵外設，AXI 協議設計了訪問權限控制信號 AxPROT，配合其他安全機制，限定不同應用的訪問權限。
  - ARPORT[2:0]，定義了讀事務的訪問權限
  - AWPORT[2:0]，定義了寫事務的訪問權限

- **Protection encoding**
<table>
    <tr>
        <th>AxPORT[n]</th>
        <th>Value</th>
        <th>Function</th>
    </tr>
    <tr>
        <td rowspan = '2'>0</td>
        <td>0</td>
        <td><em>Unprivileged access</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Privileged access</em></td>
    </tr>
    <tr>
        <td rowspan = "2">1</td>
        <td>0</td>
        <td><em>Secure access</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Non-secure access</em></td>
    </tr>
    <tr>
        <td rowspan = "2">2</td>
        <td>0</td>
        <td><em>Data access</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Instruction access</em></td>
    </tr>
</table> 

### 4.7.2. 保護屬性

- **Unprivileged access**
- **Privileged access**
- **Secure access**
- **Non-secure access**
- **Data access**
- **Instruction access**

# 5. 事務識別碼

## 5.1. AXI 事務識別碼

- **Identifiers**
  - AXI提供事務標識符（ID）來標識必須按順序返回給Master的單個事務。
  - 具有給定ID的所有事務必須按照特定的順序進行傳輸，具有不同ID的事務則沒有順序上的限制。
  - 一個物理接口可以被多個邏輯接口復用，從而實現事務的亂序傳輸。但對於每個邏輯接口而言，事務的傳輸必須按照特定的順序。
- **注意**
  - AXI協議並未要求必須使用ID。Master和Slave可以按照事務發出的順序一次只處理一個事務。
  - Slave在作出響應時須在信號*BID* 或*RID*上要包含標誌發出事務的Master的ID信息

## 5.2. ID 訊號

### 5.2.1. 通道事務 ID
<table>
    <tr>
        <th>Transaction channel</th>
        <th>Transaction ID</th>
    </tr>
    <tr>
        <td>Write address channel</td>
        <td><em>AWID</em></td>
    </tr>
    <tr>
        <td>Write data channel(AXI3 only)</td>
        <td><em>WID</em></td>
    </tr>
    <tr>
        <td>Write response channel</td>
        <td><em>BID</em></td>
    </tr>
    <tr>
        <td>Read address channel</td>
        <td><em>ARID</em></td>
    </tr>
    <tr>
        <td>Read data channel</td>
        <td><em>RID</em></td>
    </tr>
</table>

- *WID*僅在AXI3中支持，此時寫地址和寫數據通道的順序是任意的。但是在AXI4中*WID*被取消，寫數據通道只能緊接著寫地址通道，因此就不存在*數據超前於地址*的傳輸，此種情況下，寫地址和寫數據通道的傳輸順序是一致的。

### 5.2.2. 讀取資料排序

- Slave返回數據時必須確保RID值與響應的地址的ARID值相匹配
- 在具有不同目的Slave但是具有相同ARID值的讀事務序列傳輸中，Interconnect必須確保主機是按照發送地址的順序來獲取讀數據的
- 數據重排序
  - 讀取數據的重排序深度取決於Slave中重排序緩存區的大小。
  - 按順序處理所有事務的Slave的重排序深度為1。
  - 重排序深度相當於Slave的一個屬性，是個靜態值，由設計者指定。

### 5.2.3. 寫入資料排序

- Master發送數據的順序必須和發送地址的順序是一致的。
- Interconnect可以合併來自於不同Master的寫傳輸事務，但是數據的傳輸必須遵循地址順序。
- 在AXI3中就已經允許**寫數據重排序**，但是在AXI4中並不建議使用寫數據重排序。

### 5.2.4. 互連對事務識別碼的使用

- 當Master和Interconnect相連時，Interconnect會向該主機端口的唯一標識符AWID、WID、ARID添加附加信息：
  - Master不必知道其他Master使用哪些ID值，因為Interconnect通過將主機號附加到原始標識符上，使每個Master使用的ID值唯一。
  - 從接口的ID標識符比主接口的ID標識符寬。
- 對於讀數據，Interconnect使用RID標識符的附加位來確定讀數據的目標主機端口。在將RID值傳遞到正確的主端口之前，Interconnect模塊會刪除RID標識符的附加位。
- 對於寫響應，Interconnect使用BID標識符的附加位來確定寫響應的目標主機端口。在將BID值傳遞到正確的主端口之前，Interconnect模塊會刪除BID標識符的附加位。

# 6. AXI 排序模型

## 6.1. AXI 排序模型概述

- AXI排序模型是基於事務標識符實現的，事務標識符通過*AWID*和ARID*發出。
- 同一通道上具有相同ID和目的地的事務請求要保持發出的順序。
- 具有相同ID的事務響應要按照Master發出的順序返回。
- 以下情況沒有順序限制：
  - 事務來自不同的Master
  - 讀寫事務之間
  - 具有不同ID的事務
  - 事務到達不同外設區域
  - 事務到達不同內存單元
- 如果Master要求無順序保證的事務按順序執行，則其必須等待接收上一個事務的響應後才能發出下一個事務。

## 6.2. 記憶體位置與周邊區域

- AMBA的地址映射包括存儲單元和外設區域：
  - **內存單元**：
    - 從內存單元讀取一個字節時返回的是該字節位置的最新值
    - 向內存單元寫入一個字節會將該位置的值更新為一個新值，該值是通過對該位置的後續讀取獲得的
    - 對任何內存單元的讀寫操作都不會影響其他單元
    - 內存單元的每個位置都提供“觀察保證”
    - 內存單元的大小等於該組件的單拷貝原子性大小。
  - **外設區域**：
    - 從外設區域中讀取數據時並不一定返回該位置的最新值
    - 向外設區域中寫入數據時不一定會將該地址上的值更新為通過後續讀取獲得的新值
    - 訪問外設區域中的地址可能會對該區域的其他地址造成影響
    - 每塊外設區域都為外設提供了“觀察保證”
    - 外設區域的大小是在設計外設時定義的，但無論設計多大它都代表一個從組件

## 6.3. 事務與排序

- 所謂事務就是對一個或多個地址的讀寫，訪問的地址由*AxADDR*和相關的限定詞決定，例如*AxPORT*中的*Non-Secure*位
  - 僅在訪問相同的內存單元或外設區域之間提供排序保證
  - 外設區域的事務傳輸必須完全包含在該區域之內
  - 目的節點囊括多個內存單元的事務具有多個順序保證

- 事務可以分為*Device*訪問和*Normal*訪問
  - *Device*
    - *AxCACHE[1] = 0*
    - 設備事務可以用來訪問外設區域或內存單元
  - *Normal*
    - *AxCACHE[1] = 1*
    - 普通事務可以用來訪問內存單元，不希望用於訪問外設區域
    - 普通事務訪問外設區域必須以符合協議的方式完成，但是具體結果還是要在設計Slave時實現

- 寫事務可以分為*Bufferable*和*Non-Bufferable*
  - 寫事務類型為*Bufferable*時，可以在到達目的節點之前返回事務響應
  - *Buffeable：AxCACHE[0] = 1*; *Non-Bufferable：AXCACHE[0] = 0*
 
## 6.4. 觀察與完成的定義

### 6.4.1. 觀察

- **外設區域**
  - 對於外設區域的訪問，讀寫早到的設備讀寫事務DRW1受到晚到的設備設備讀寫事務DRW2的觀察

- **內存單元**
  - 寫事務W1對在其之後生效的寫事務W2可見
  - 讀事務R1從寫事務W3獲取數據，而寫事務W2發生在W3之後，則R1對W2可見
  - 如果讀事務R2從寫事務W1或W3獲取數據，且W3在W1之後，則W1對R2可見
  - 讀寫事務類型可以是*Device*或*Normal*

### 6.4.2. 完成

- **Write completion response**
  - 當*BVALID*和*BREADY*有效時，給出關聯的*BRESP*握手信號的週期即標誌著寫事務的完成
- **Read conpletion response**
  - 當*RVALID*、*RLAST*和*RREADY*有效時，給出最後關聯的*RDATA*握手信號的週期即標誌著讀事務的完成

## 6.5. 主端排序保證

- **順序模型保證**
  - 收到完成響應之前的可見性保證
  - 來源於完成響應的可見性保證
  - 響應順序保證

### 6.5.1. 收到完成回應前的保證

- 下面所述**順序保證**的情況均是來源於同一Master，使用相同ID：
  - 訪問同一外設區域的兩個設備寫事務DW1和DW2，DW1先於DW2發出，則順序模型保證DW1是先於DW2到達指定區域
  - 設備讀事務同設備寫事務
  - 訪問同一內存單元的兩寫事務，前一事務對後一事務可見
  - 寫事務W1對讀事務R2可見，W1仍然對在R2之後發出且與R2訪問同一內存單元的讀事務可見
- 上述保證意味著訪問同一內存單元的設備訪問和普通訪問之間存在順序保證

### 6.5.2. 完成回應所提供的保證

- 完成響應保證以下條件：
  - 對讀請求的完成響應保證了對來自任何Master的後續讀取或寫入請求均可見。
  - 對寫請求的完成響應保證了對來自任何Master的後續讀取或寫入請求均可見。這種可見性是多拷貝原子系統的要求。
- 包含符合ARM架構體系的處理器的系統必須是具有多拷貝原子性。
- 可緩衝寫事務的響應可以由中間節點發出。它不能保證在目的節點上已完成寫入，但是對之後的事務可見。

### 6.5.3. 回應排序保證

- 事務響應遵循以下順序：
  - 由同一Master發出並且具有相同ID的兩個讀事務，讀響應的返回順序與讀請求的發出順序一致。
  - 由同一Master發出並且具有相同ID的兩個寫事務，寫響應的返回順序與寫請求的發出順序一致。

## 6.6. 排序要求

### 6.6.1. 從端排序要求

- **外設區域**
  - 訪問外設區域的事務的執行順序在設計外設時確定。
  - 一般上述的執行順序是與事務到來的順序匹配的。

- **內存單元**
  - 訪問同一內存單元並且具有相同事務ID的寫事務，Slave按照接收的順序進行處理。
  - 訪問同一內存單元的寫事務，Slave在接收事務W2之前就已經給出事務W1的響應時，W1的順序必須排在W2之前。
  - 訪問同一內存單元的讀寫事務W1和R2，Slave在給出W1的響應之後接收R2，則W1必須排在R2之前。
  - 訪問同一內存單元的讀寫事務R1和W2，Slave在給出R1的響應之後接收W2，則R1必須排在W2之前。

- **響應順序**
  - 具有相同事務ID的讀寫事務，返回響應的順序按照接收的順序
 
### 6.6.2. 互連排序要求

- **互聯組件的屬性**
  - 在一個端口上接收到請求，該請求在另一個端口上被發出或被響應。
  - 在一個端口上接收到響應，該響應在另一個端口上被發出或被使用。

- **互連發出請求或響應時，遵循以下條件**
  - 訪問同一或者具有重疊的內存單元並且具有相同事務ID的讀寫事務，請求的發出順序同接收順序。
  - 訪問同一外設區域且具有相同事務ID的讀寫事務，請求的發出順序同接收順序。
  - 具有相同事務ID的讀寫事務，請求的發出順序同接收順序。
- **注意**
  - 當互連表現為一個從組件時，此時遵循Slave的順序要求。
  - 任何關於事務ID值的操作都必須確保維持原始ID值的順序要求。

## 6.7. 端點前的回應

- **Early response**
  - 為了提高系統性能，一些事務可以由中間組件響應，這種行為被稱為*Early response*。這種情況下中間組件必須保證事務的可見性和保序性。

### 6.7.1. 提前讀取回應

- 對於普通讀事務，如果中間組件的本地內存中的數據相對於之前對相同或重疊地址的寫入是最新的，則該中間組件可以用本地內存中的數據進行響應。
- 中間組件按必須遵循ID排序規則，具有相同ID的事務返回響應時，必須按照接收時的順序。

### 6.7.2. 提前寫入回應

- 對於可緩衝寫事務，對下游沒有觀察者的事務，中間組件可以發送*提前寫入回應*。這種情況下中間組件可以將數據備份到本地緩存中，但在丟棄該數據之前需要將事務傳輸到下游。
- 中間組件按必須遵循ID排序規則，具有相同ID的事務返回響應時，必須按照接收時的順序。
- 發送*提前寫入回應*之後，在事務傳輸到下游並收到寫響應之前，中間組件要保證事務的保序性和可見性。
- 在發送*提前寫入回應*與接收到下游的寫響應期間，中間組件必須保證以下情況：
  - 如果對普通事務給出*提前寫入回應*，則訪問相同或具有重疊的內存單元的後續事務都須排在該事務之後。
  - 如果對設備事務給出*提前寫入回應*，則訪問相同外設區域的後續事務都須排在該事務之後。
- 當為可緩衝的設備事務提供*提前寫入回應*，中間組件傳播該寫事務時不依賴於其他事務。中間組件在傳播先前的設備寫事務之前不能等待其他讀寫事務的到來。

## 6.8. 有序寫入觀察

### 6.8.1. 有序寫入觀察

- 為了提高支持不同排序模型的接口協議的兼容性，從接口可以為寫事務提供更有力的順序保證。 更有力的順序保證被稱為*有序寫入觀察*。
- *有序寫入觀察*保證來自同一Master並且具有相同ID的事務，前一事務對後一事務可見。
- 使用*Producer-Consumer*順序模型的Master與具有*有序寫入觀察*的從接口連接時，Master發送寫事務時不須等待之前的事務響應。

### 6.8.2. Ordered_Write_Observation 
- *Ordered_Write_Observation*屬性用來定義接口是否提供*有序寫入觀察*
  - **TRUE**：提供
  - **FALSE**：不提供
  - 默認為*不提供*

# 7. 原子存取

## 7.1. 單一複本原子性大小

### 7.1.1. 單一複本原子性大小

- AXI4協議引入了單拷貝原子大小的概念。該術語定義事務自動更新的最小字節數。AXI4協議要求的事務大小大於單拷貝原子性大小，必須以至少單拷貝原子性大小的塊更新內存。
- 注意
  - 原子性並沒有定義數據更新的確切時間。必須確保的是，沒有任何Master能夠觀察到原子數據的部分更新形式。例如，在許多系統中，數據結構（例如鏈表）由32位原子元素組成。對這些元素之一進行原子更新需要同時更新整個32位值。不接受任何Master一次只觀察16位的更新，然後再觀察其他16位的更新是不可接受的。
- 更複雜的系統需要支持更大的原子元素，尤其是64位原子元素，以便Master可以使用基於這些更大原子元素的數據結構進行通信。
- 系統中支持的單拷貝原子性大小很重要，因為給定通信中涉及的所有組件都必須支持所需的原子元素大小。如果兩個Master通過一個互連和一個Slave進行通信，則所有涉及的組件必須確保以原子性處理所需大小的事務。
- AXI4協議不要求特定的單拷貝原子性大小，並且系統可以設計為支持不同的單拷貝原子性大小。
- 不同組的組件可以具有不同的單拷貝原子性大小，以在組內進行通信。 在AXI4中，術語“單拷貝原子組”描述了可以以特定原子性進行通信的一組組件。 例如，圖7-1顯示了一個系統，其中：
  - 處理器，數字信號處理器（DSP），DRAM控制器，DMA控制器，外設，SRAM存儲器和相關的互連位於32位單拷貝原子組中。
  - 處理器，DSP，DRAM控制器和相關的互連也位於64位單拷貝原子組中。
  ![圖7-1](README.assets/13.jpg "圖7-1")
- :grey_question:事務的原子性保證永遠不會大於其起始地址的對齊形式。例如，未與8字節邊界對齊的64位單拷貝原子組中的突發傳輸沒有任何64位單拷貝原子保證。
- 與事務相關的字節選通信號不影響單拷貝原子性的大小。

### 7.1.2. 多複本寫入原子性 

- **Multi_Copy_Atomicity**
  - **True**：支持多拷貝原子性
  - **False**：不支持多拷貝原子性
  - 默認不支持

- 以下情況系統具有多拷貝原子性：
  - 所有Agents都已相同的順序對訪問相同位置的寫事務。
  - 一個寫事務對一個Agent可見，則對所有的Agents可見。

- 可以通過以下方式確保多拷貝原子性：
  - 對給定地址使用單個序列化點，以便對同一位置的所有訪問進行排序。這必須確保該位置的所有一致性緩存副本在使該位置的新值對任何Agent可見之前都無效。
  - 避免使用任何Agent上游的轉發緩衝區。這可以防止某個位置的緩衝寫事務在對所有Agent可見之前對某些Agent可見。
  - 對於本發行版G和更高版本，要求Multi_Copy_Atomicity屬性為True。

## 7.2. 獨占存取

- 獨佔訪問機制使得信號量類型操作（semaphore type operations）的開發不需要總線在操作期間保持對某一個特定主機的鎖定。
- 這意味著信號量類型的操作不會影響總線訪問延遲或最大可達到的帶寬。
- AxLOCK信號選擇獨佔訪問，RRESP和BRESP信號表示獨佔訪問的成功或失敗。
- Slave需要額外的邏輯來支持獨佔訪問。AXI協議提供了一種用於指示Master何時嘗試對不支持它的Slave進行獨佔訪問的機制。本節的其餘部分描述了AXI Exclusive訪問機制。

### 7.2.1. 獨占存取流程

- **獨佔訪問的基本過程**
1. Master對一個地址執行獨佔讀取。
2. 之後，Master嘗試通過對同一地址執行獨佔寫入，並使用與用於獨佔讀取的ARID匹配的AWID來結束獨佔操作。
3. 此獨佔寫入訪問結果可以表示為：
   - 在讀和寫訪問之間，如果沒有其他Master對該位置進行寫訪問，則獨佔訪問成功,這種情況下，地址位置被該獨佔寫訪問更新。
   - 在讀和寫訪問之間，如果任何Master對該位置進行寫訪問，則獨佔訪問失敗，在這種情況下，地址位置不會被更新。

- **注意**
  - 一個主機可能還沒有完成一個獨佔操作的寫操作部分。獨佔訪問的監視硬件，只能監視每個事務ID的一個地址。
  - 如果一個Master沒有完成獨佔操作的寫操作部分，則接下來的一個獨佔讀訪問會改變正在被獨佔地監視的地址。

### 7.2.2. 從主端角度看獨占存取

- 主機通過執行一個獨佔讀操作來開始一個獨佔操作，獨佔操作通常從從機返回一個EXOKAY響應，表示從機記錄了要被監視的地址。
- 注意
  - 如果主機嘗試從一個不支持獨佔訪問的從機執行一個獨佔讀操作，則從機返回OKAY響應，而不是EXOKAY響應，表示獨佔訪問失敗。
  - 主機可將這種情況當做錯誤條件，表示不支持獨佔訪問，推薦主機在這種情況下，不執行該獨佔操作的寫操作部分。
- 獨佔讀操作之後通常會對同一地址進行獨佔寫操作：
  - 如果地址位置沒有發生改變，則獨佔寫成功，從機返回EXOKAY響應，並且更新內存位置。
  - 如果地址位置發生了改變，則獨佔寫失敗，從機返回OKAY響應，且不會更新內存位置。
- 一個主機可能無法完成獨佔訪問的寫操作部分。如果發生這種情況，則從機繼續監視獨佔的地址，直到另一個獨佔讀操作開始一個新的獨佔訪問。
- 在獨佔訪問的讀操作完成之前，主機不能開始獨佔訪問的寫操作部分。

### 7.2.3. 從從端角度看獨占存取

-  一個不支持獨佔訪問的從機可以忽視 *ARLOCK[1:0]/AWLOCK[1:0]* 信號，從機必須為正常訪問和獨佔訪問提供一個OKAY響應。

- 一個支持獨佔訪問的從機必須具有監控硬件，一般具有一個監控單元，用來監控可訪問該從機的每個可獨佔訪問的主機ID。一個單端口從機可以具有一個從機外部的標準獨佔訪問監控器，但是多端口的從機可能需要內部監控器。

- 獨佔訪問監控器記錄任何獨佔讀操作的地址和ARID值，之後監控器一直監控該位置，直到一個到該位置的寫操作發生，或者直到相同的ARID值的另一個獨佔讀操作將監控器復位到一個不同的地址；

- 當一個具有給定的AWID值的獨佔寫操作發生，則監控器會檢查該地址是否正在被獨佔監控;
  - 如果是，則表示獨佔寫操作之前，該位置沒有發生寫操作，獨佔寫操作會繼續執行，來完成獨佔訪問。從機返回EXOKAY響應到主機。
  - 如果獨佔寫發生時，地址不再被監控，則表示以下情況：
    - 從機獨佔讀之後，位置被更新
    - 監控器已經被復位到另一個位置
    - 主機未發出具有與獨佔寫操作相同屬性的獨佔讀操作
    - 以上情況下，獨佔寫操作都不能更新地址位置，並且從機必須返回OKAY響應，代替EXOKAY響應

### 7.2.4. 獨占存取限制

- **獨佔訪問約束**
  - 獨佔訪問的地址必須與事務中的字節總數對齊，即突發大小和突發長度的乘積。
  - 獨佔訪問突發中要傳輸的字節數必須是2的指數次方，即1、2、4、8、16、32、64或128個字節。
  - 獨佔突發中可以傳輸的最大字節數為128。
  - 獨佔訪問的突發長度不能超過16。
  - *AxCACHE*信號的值必須確保事務到達正在監視獨佔訪問的從設備。如果有緩衝區或緩存區可能會在到達監視器之前響應獨佔訪問，因此獨佔訪問必須是不可緩衝的和不可緩存的。
  - 地址域要麼是不可共享的要麼是系統可共享的。
  - 事務類型必須為 *ReadNoSnoop* 或 *WriteNoSnoop*。
  - **不遵循上述約束會產生無法預料的行為。**

- 獨佔訪問可以分為獨佔讀操作和獨佔寫操作，對於兩次傳輸，下列信號必須保持一致：
  - *AxID*
  - *AxADDR*
  - *AxREGION*
  - *AxLEN*
  - *AxSIZE*
  - *AxBURST*
  - *AxLOCK*
  - *AxCACHE*
  - *AxPORT*
  - *AxDOMAIN*
  - *AxSNOOP*
  - *AxMMUSECSID*
  - *AxMMUSID*
  - *AxMMUSSIDV*
  - *AxMMUSSID*
  - *AxMMUATST*

- 獨佔操作期間要監視的最小字節數由事務的突發長度和突發大小定義。但從機可以監視更多的字節，最大為128，這是獨佔訪問的最大大小。但是，這可能導致成功的獨佔訪問被指示為失敗，因為相鄰字節被更新。

### 7.2.5. 獨占存取的回應

- 響應信號 *BRESP* 和 *RRESP*中包含一個用於指示正常訪問成功的*OKAY* 信號，以及一個用於指示獨佔訪問成功的 *EXOKAY* 信號。同時，*OKAY* 信號還可以指示獨佔訪問失敗。
- 注意
  - 對不支持獨佔訪問的從屬設備的獨佔寫操作始終會更新內存位置。
  - 僅當獨佔寫入操作成功時，對支持獨佔訪問的從屬設備進行獨佔寫入才更新內存位置。
- 獨佔寫入使用BRESP進行單個響應，可以是OKAY，EXOKAY，SLVERR或DECERR。
- 獨佔讀取具有一個或多個響應節拍。這些可以是EXOKAY，SLVERR和DECERR的混合，也可以是OKAY，SLVERR和DECERR的混合。但是不允許在同一事務中混合使用EXOKAY和OKAY響應。
 
## 7.3. 鎖定存取

- AXI4不支持鎖定訪問，但AXI3中必須支持鎖定訪問。
- AXI4取消鎖定訪問的原因：
  - 大多數組件不需要鎖定的事務傳輸
  - 鎖定的事務傳輸的實現會有重大影響：
    - 互連的複雜性
    - 做出QoS保證的能力

## 7.4. 原子存取訊號

### 7.4.1. AXI3 原子存取編碼
<table>
    <tr>
        <th>AxLOCK[1:0]</th>
        <th>Access type</th>
    </tr>
    <tr>
        <td>00</td>
        <td><em>Normal access</em></td>
    </tr>
    <tr>
        <td>01</td>
        <td><em>Exclusive access</em></td>
    </tr>
    <tr>
        <td>10</td>
        <td><em>Locked access</em></td>
    </tr>
    <tr>
        <td>11</td>
        <td><em>Reserved</em></td>
    </tr>
</table>

### 7.4.2. AXI4 原子存取編碼
<table>
    <tr>
        <th>AxLOCK</th>
        <th>Access type</th>
    </tr>
    <tr>
        <td>0</td>
        <td><em>Normal access</em></td>
    </tr>
    <tr>
        <td>1</td>
        <td><em>Exclusive access</em></td>
    </tr>
</table>

### 7.4.3. 舊版相容性考量
<table>
    <tr>
        <th>AXI3</th>
        <th>AXI4</th>
    </tr>
    <tr>
        <td><em>AWLOCK[1:0] = 2'b10</em></td>
        <td><em>AWLOCK = 0</em></td>
    </tr>
    <tr>
        <td><em>ARLOCK[1:0] = 2'b10</em></td>
        <td><em>ARLOCK = 0</em></td>
    </tr>
</table>

# 8. AMBA 4 附加訊號

## 8.1. QoS 訊號

### 8.1.1. QoS 介面訊號

- *AxQoS*
  - *ARQoS*：4位QoS信號，每個讀事務均通過讀地址通道發送。
  - *AWQoS*：4位QoS信號，每個寫事務均通過寫地址通道發送。
- 作用
  - 該協議未指定QoS標識符的確切用法。但一般會將 *AxQOS* 用作讀寫事務的優先級指示符，較高的值表示事務優先級較高。缺省值 *0b0000* 表示接口未參與任何QoS方案。
- 注意
  - 也可以使用QoS的其他解釋。

### 8.1.2. 主端考量

- 主機可以產生自己 *AxQOS* 值，如果主機可以發出多個事務流，則它可以給不同的事物流以不同的QoS值。
- 支持QoS代表著要對所使用的QoS方案有著系統的瞭解，並且所有參與的組件要相互配合協作。因此，主機一般要具有可編程性，以控制在不同場景下QoS的確切值。
- 如果主組件不支持可編程的QoS方案，則它可以使用QoS值來表示其生成的事務的相對優先級。並且在適當的情況下可以將這些值映射到替代的系統級QoS值。
- 無法產生自己的*AxQOS*值的主機必須使用默認值。
- 注意
  - 該協議書期望多數互連組件將支持可編程寄存器，用於將QoS值分配給連接的主機。這些值取代了主機提供的QoS值（已編程或默認）。

### 8.1.3. 系統考量

- 如AXI4中定義的QoS信令可與任何兼容的系統級QoS方法一起使用。
- QoS的默認系統級實現是：僅當沒有其他AXI約束要求以特定順序處理事務時，首先處理QoS值高的事務。即AXI的排序規則的優先級要高於QoS。
- 可以實現與此默認方案兼容的更複雜的QoS方案。

## 8.2. 多區域訊號

### 8.2.1. 附加介面訊號

- **AxREGION信號**
  - *AWREGION*：4-bits地址區域標識符，每個寫事務通過寫地址通道發送。
  - *ARREGION*：4-bits地址區域標識符，每個讀事務通過讀地址通道發送。

- 4-bits的區域標識符最多可唯一標識16個不同的區域。區域標識符可以提供地址的高位解碼。在某4KB地址空間中保持不變。
- 區域標識符的使用使得從機上的單個物理接口可以提供多個邏輯接口，每個邏輯接口在系統地址映射中具有不同的地址位置，而從機就不必支持不同邏輯接口之間的地址解碼。
- 當對具有多個邏輯接口的單個從設備執行地址解碼時，此協議期望互連使用*AxREGION*信號。如果從站在系統地址映射中只有一個物理接口，則互連必須使用默認的*AxREGION*值。

- **區域標識符使用模式**（不限於以下兩種）
  - 外設可以將其主數據路徑和控制寄存器放置在地址映射中的不同位置，並且可以通過單個接口進行訪問，而無需從機執行地址解碼。
  - 從機可以在不同的存儲區域中表現出不同的行為。例如，從設備可能在一個區域中提供讀寫訪問，而在另一區域中提供只讀訪問。

- **注意**
  - 從機必須確保正確的協議信號傳遞以及維持正確的事務順序。
  - 從機必須確保以正確的順序為ID相同但訪問區域不同的兩個事務提供響應。
  - 從機必須確保任何*AxREGION*值具有正確的協議信號傳遞。
  - 如果從機內部的地址劃分區域少於16個，則在訪問不受支持的區域時，從機必須確保正確的信號傳遞。具體如何實現由設計從機時決定，例如：
    - 為訪問不受支持的區域的任何訪問都提供錯誤響應
    - :grey_question: 在所有不受支持的區域中對受支持的區域進行別名處理，以確保對所有訪問均給出符合協議的響應。
  - *AxREGION* 信號僅提供現有地址空間的地址解碼，從機可以使用它來消除對地址解碼功能的需求。信號不會創建新的獨立地址空間。 *AxREGION* 只存在於地址解碼功能下游的接口上

## 8.3. 使用者定義訊號

- 在AMBA 4中引入了用戶定義的信號。對於AMBA 5，這些信號的用法和配置在協議中得到了進一步的闡明和統一。AXI接口可以包括一組用戶定義的信號，稱為用戶信號。這些信號可用於將信息擴展到現有AMBA規範未涵蓋的要求的事務中。擴展信息可添加到：
  - 事務請求
  - 事務響應
  - 內部的每個讀寫數據節拍 
- 通常，本規範建議不要使用用戶信號。AXI協議未定義這些信號的功能，如果兩個組件以不兼容的方式使用相同的用戶信號，則可能導致互操作性問題

### 8.3.1. 使用者定義訊號組態

- **User signals properties**
  - 如果屬性值為零，則接口上不存在相關信號。
  - 最大值僅具有指導意義，以便為可配置接口設置合理的最大值。 
<table>
    <tr>
        <th>Name</th>
        <th>Min</th>
        <th>Max</th>
        <th>Applies to</th>
    </tr>
    <tr>
        <td><em>USER_REQ_WIDTH</em></td>
        <td>0</td>
        <td>128</td>
        <td><strong>AWUSER，ARUSER</strong></td>
    </tr>
    <tr>
        <td><em>USER_DATA_WIDTH</em></td>
        <td>0</td>
        <td>DATA_WIDTH/2</td>
        <td><strong>WUSER，RUSER</strong></td>
    </tr>
    <tr>
        <td><em>USER_RESP_WIDTH</em></td>
        <td>0</td>
        <td>16</td>
        <td><strong>BUSER，RUSER</strong></td>
    </tr>
</table>


- **以下接口類型可以包括自定義信號：**
  - ACE5
  - ACE5-Lite
  - ACE5-LiteDVM
  - ACE5-LiteACP
  - AXI5
  - AXI5-Lite

### 8.3.2. 訊號傳遞

- **User-defined signals** 
<table>
    <tr>
        <th>訊號</th>
        <th>寬度</th>
        <th>說明</th>
    </tr>
    <tr>
        <td><strong>ARUSER</strong></td>
        <td><em>USER_REQ_WIDTH</em></td>
        <td>
            用戶自定義讀請求屬性
            其有效性同其他讀地址通道信號
        </td>
    </tr>
    <tr>
        <td><strong>AWUSER</strong></td>
        <td><em>USER_REQ_WIDTH</em></td>
        <td>
            用戶自定義寫請求屬性
            其有效性同其他寫地址通道信號
        </td>
    </tr>
    <tr>
        <td><strong>WUSER</strong></td>
        <td><em>USER_DATA_WIDTH</em></td>
        <td>
            用戶自定義寫數據屬性
            其有效性同其他寫數據通道信號
        </td>
    </tr>
    <tr>
        <td><strong>RUSER</strong></td>
        <td><em>USER_RESP_WIDTH＋USER_RESP_WIDTH</em></td>
        <td>
            用戶自定義讀數據和讀響應屬性
            其有效性同其他讀數據通道信號
        </td>
    </tr>
    <tr>
        <td><strong>BUSER</strong></td>
        <td><em>USER_RESP_WIDTH</em></td>
        <td>
            用戶自定義寫響應屬性
            其有效性同其他寫響應通道信號
        </td>
    </tr>
</table> 

### 8.3.3. 使用考量

- 在使用用戶信號的情況下，並不需要所有通道都支持用戶信號。是否包括用戶信號的設計對請求，數據和響應通道是獨立的。
- 為了幫助數據寬度和協議轉換，本規範建議：
  - USER_DATA_WIDTH是數據總線寬度的整數倍（以字節為單位）。
  - 用戶響應位對於讀取或寫入響應的每個節拍都是相同的值。
  - RUSER的低位用於傳輸每個事務的響應信息。 
  - RUSER的高位用於傳輸逐拍讀取的數據信息。

# 9. 預設訊號與互通性

- 本章介紹了默認信號指令和AXI接口的互操作性。
- AXI協議不需要組件使用AXI接口上可用的全部信號集。為了幫助連接不使用每種信號的組件，本章定義了接口的主要類別以及適用於每種類別的限制。

## 9.1. 互通性原則
  
- 下面所述互操作性原則適用於所有的AXI3和AXI4組件。
- 作為一般原則，組件必須支持所有輸入組合，但不必生成所有輸出組合。例如，從設備必須支持所有可能的不同長度的突發傳輸，而主設備僅生成其使用的突發類型。此策略可確保所有組件與其他組件一起使用。
- AXI接口可以省略信號的情形：
  - **輸出可選**
    - 如果一個組件要求某信號的值不是默認值，則該組件必須輸出該信號。
    - 如果一個組件對某信號的值不做要求，即為默認值，則該組件不需要輸出該信號。
  - **輸入可選** 
    - 當主機或從機不需要觀察某輸入信號就可進行正確的功能操作時，該輸入信號即可省略。
- **注意**：在適當的時機，互連組件也可以省略信號
  - 當信號被驅動為其默認值時，就不需要跨互連傳輸該信號，可以在其目的地創建該信號。 
  - 如果在任何目的地均未使用某信號，則無需跨互連傳輸該信號。

## 9.2. 主要介面類別

### 9.2.1. 讀寫介面

- 讀寫接口包含以下AXI通道：
  - 讀地址
  - 讀數據
  - 寫地址
  - 寫數據
  - 寫響應

### 9.2.2. 唯讀介面

- 只讀接口僅支持讀事務並且包含以下AXI通道：
  - 讀地址
  - 讀數據 
- **注意**
  - 只讀接口不支持獨佔訪問。
 
### 9.2.3. 唯寫介面

- 只寫接口僅支持寫事務並且包含以下AXI通道：
  - 寫地址
  - 寫數據
  - 寫響應
- **注意**
  - 只寫接口不支持獨佔訪問。

### 9.2.4. 記憶體從端與周邊從端

- AXI從機可分為存儲從機和外設從機：
  - 存儲從機必須能夠正確處理所有事物類型。
  - 外設從機應具有自己定義的訪問方法，該方法可用於確定訪問設備的事務類型，以及是否對設備的訪問方式有任何限制。
    - 通常，在組件的數據表中描述了定義的訪問方法。任何不是定義的訪問方法的訪問都可能導致外設發生故障，但該訪問應以符合協議的故障安全方式完成，以防止系統死鎖。在此情況下外設並不需要繼續正確的操作。
    - 由於外設僅針對其定義的訪問方法才能正常工作，因此外設的接口信號集會大大減少。

- **注意**
  - 期望所有外設都支持事務的子集，該子集允許使用可以在C代碼中指定的訪問來控制外圍設備。例如，可能支持單個8位，單個16位或單個32位對齊的事務。
  - 未定義最小子集，因為所支持事務的子集在外設之間可能有所不同。例如，一個外設可能僅支持16位訪問，而另一個外設可能僅支持32位訪問。

## 9.3. 預設訊號值

- 通常，為了最大程度地實現IP重用，AXI組件接口應包括所有信號，這樣降低了在設計流程的系統集成階段出錯的風險，並且還可以支持某些不能有效支持省略信號的默認值的設計流程。

### 9.3.1. 預設訊號值

- **主接口寫通道信號及其默認值**
<table>
    <tr align="left">
        <th>訊號</th>
        <th>方向</th>
        <th>必要？</th>
        <th>預設</th>
    </tr>
    <tr>
        <td><strong>ACLK</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARESETn</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWID</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零</td>
    </tr>
    <tr>
        <td><strong>AWADDR</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWREGION</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零</td>
    </tr>
    <tr>
        <td><strong>AWLEN</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零, 長度 1</td>
    </tr>
    <tr>
        <td><strong>AWSIZE</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>資料匯流排寬度</td>
    </tr>
    <tr>
        <td><strong>AWBURST</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b01, INCR</td>
    </tr>
    <tr>
        <td><strong>AWLOCK</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零, Normal access</td>
    </tr>
    <tr>
        <td><strong>AWCACHE</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b0000</td>
    </tr>
    <tr>
        <td><strong>AWPROT</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWQOS</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b0000</td>
    </tr>
    <tr>
        <td><strong>AWVALID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWREADY</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WDATA</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WSTRB</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>All ones</td>
    </tr>
    <tr>
        <td><strong>WLAST</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WVALID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WREADY</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BID</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BRESP</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BVALID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BREADY</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
</table> 

- **存儲從接口寫通道信號及其默認值**
<table>
    <tr align="left">
        <th>訊號</th>
        <th>方向</th>
        <th>必要？</th>
        <th>預設</th>
    </tr>
    <tr>
        <td><strong>ACLK</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARESETn</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWADDR</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWREGION</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWLEN</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWSIZE</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWBURST</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWLOCK</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWCACHE</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWPROT</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWQOS</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>0b0000</td>
    </tr>
    <tr>
        <td><strong>AWVALID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>AWREADY</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WDATA</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WSTRB</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WLAST</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WVALID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>WREADY</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BRESP</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b00,OKAY</td>
    </tr>
    <tr>
        <td><strong>BVALID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>BREADY</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
</table>

- **主接口讀通道信號及其默認值**
<table>
    <tr align="left">
        <th>訊號</th>
        <th>方向</th>
        <th>必要？</th>
        <th>預設</th>
    </tr>
    <tr>
        <td><strong>ARID</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零</td>
    </tr>
    <tr>
        <td><strong>ARADDR</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARREGION</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0x0</td>
    </tr>
    <tr>
        <td><strong>ARLEN</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零, 長度 1</td>
    </tr>
    <tr>
        <td><strong>ARSIZE</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>資料匯流排寬度</td>
    </tr>
    <tr>
        <td><strong>ARBURST</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b01, INCR</td>
    </tr>
    <tr>
        <td><strong>ARLOCK</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>全零, Normal access</td>
    </tr>
    <tr>
        <td><strong>ARCACHE</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b0000</td>
    </tr>
    <tr>
        <td><strong>ARPROT</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARQOS</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b0000</td>
    </tr>
    <tr>
        <td><strong>ARVALID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARREADY</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RID</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RDATA</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RRESP</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RLAST</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RVALID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RREADY</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
</table>

- **存儲從接口讀通道信號及其默認值**
<table>
    <tr align="left">
        <th>訊號</th>
        <th>方向</th>
        <th>必要？</th>
        <th>預設</th>
    </tr>
    <tr>
        <td><strong>ARID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARADDR</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARREGION</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARLEN</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARSIZE</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARBURST</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARLOCK</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARCACHE</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARPROT</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARQOS</strong></td>
        <td>輸入</td>
        <td>選用</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARVALID</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>ARREADY</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RDATA</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RRESP</strong></td>
        <td>輸出</td>
        <td>選用</td>
        <td>0b00,OKAY</td>
    </tr>
    <tr>
        <td><strong>RLAST</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RVALID</strong></td>
        <td>輸出</td>
        <td>必要</td>
        <td>-</td>
    </tr>
    <tr>
        <td><strong>RREADY</strong></td>
        <td>輸入</td>
        <td>必要</td>
        <td>-</td>
    </tr>
</table> 

### 9.3.2. 預設訊號要求

- **Master address**
  - 對主機提供的地址位數沒有最低要求。如果主機連接的系統的地址總線寬度與主機提供的地址總線寬度不同：
    - 系統地址比主機提供的地址寬，則必須給主機的高位地址位附加全零值。
    - 系統地址比主機提供的地址窄，則必須斷開主機的高位地址位。
  - 注意
    - 通常，主機提供32位尋址。但有時候主機可以支持64位尋址。

- **Memory slaves**
  - 存儲從機對 *AxLOCK* 輸入信號的使用不做要求，但是對於支持獨佔訪問的存儲從機則需要此信號。
  - 存儲從機對 *AxCACHE* 輸入信號的使用不做要求。在以下情形存儲從機不需要此信號：
    - 無緩存行為
    - 以相同方式緩存所有事務

- **寫入事務**
  - 如果主機始終以完整的數據總線位寬執行寫事務，則不需要主機使用寫選通信號WSTRB。寫選通的默認值是全為高。
  - 從機對 *WLAST* 信號的使用不做要求。由於定義了寫突發傳輸的長度，因此從機可以根據突發傳輸長度 *AWLEN[7：0]* 信號計算最後一次寫數據的傳輸。

- **讀取事務**
  - 主機對 *RLAST* 信號的使用不做要求。由於定義了讀突發傳輸的長度，因此主機可以根據突發傳輸長度 *AWLEN[7：0]* 信號計算最後一次讀數據的傳輸。

- **Response signaling**
  - 如果主機同時滿足以下條件，則不需要 *RRESP* 和 *BRESP* 輸入信號：
    - 不執行獨佔訪問
    - 不需要通知事務錯誤
  - 如果從機同時滿足以下條件，則不需要 *RRESP* 和 *BRESP* 輸出信號：
    - 不支持獨佔訪問
    - 不生成錯誤響應

- **Non-secure and Secure accesses**
  - 不需要區分非安全訪問和安全訪問的從機，並且不需要任何其他保護支持，則不需要 *AxPROT* 輸入信號。
  - **注意**
    - 請特別注意 *AxPROT信號* 。*AxPROT[1]* 信號指示事務的安全性或非安全性，並且錯誤分配這些位可能導致錯誤的系統行為。
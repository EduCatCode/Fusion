# Fusion 安裝與使用手冊

## 專案介紹與背景
Fusion 是一個專為慣性測量單元（IMU）設計的感測融合庫，優化了嵌入式系統的應用。IMU 是一種包含陀螺儀、加速度計和磁力計的裝置，用於測量物體的方位和運動。Fusion 庫通過融合這些感測器的數據，提供精確且穩定的方位測量，廣泛應用於導航、機器人、自動駕駛等領域。

## 演算法介紹
Fusion 使用 Attitude And Heading Reference System (AHRS) 演算法來融合來自陀螺儀、加速度計和磁力計的數據，計算出相對於地球的方位。這個演算法基於 Madgwick 博士在其博士論文第七章中提出的修正版 AHRS 演算法。該演算法與更知名的第三章中提出的初版 AHRS 演算法有所不同。

## 背後原理與物理意義
AHRS 演算法將陀螺儀數據的積分結果與來自其他感測器的方位誤差作為反饋項結合起來，這個反饋項乘上一個增益後與陀螺儀數據相加，形成一個互補濾波器。濾波器高通部分處理陀螺儀數據，低通部分處理加速度計和磁力計數據，角頻率由增益決定。低增益會更信任陀螺儀，容易產生漂移；高增益會增加其他感測器的影響，容易受到加速和磁場失真的干擾。

## 初始設定
演算法啟動時會進行初始化，並在角速度恢復期間再次初始化。初始化期間，加速度和磁力拒斥功能會被禁用，增益從 10 降到最終值，持續 3 秒鐘，使方位測量快速收斂到感測器指示的值。

## 加速度與磁場拒斥
加速度拒斥功能通過計算即時測得的傾斜角度與演算法輸出的傾斜角度之間的誤差來減少加速運動引起的錯誤。如果誤差超過閾值，演算法會忽略加速度計數據。類似地，磁場拒斥功能通過比較磁力計測得的方位與演算法輸出的方位來減少磁場失真引起的錯誤。

## 演算法輸出
演算法輸出四元數、線性加速度和地球加速度。四元數描述了傳感器相對於地球的方位，可以轉換成旋轉矩陣或歐拉角。線性加速度是去除重力後的加速度計數據，地球加速度是去除重力並轉換到地球坐標系後的數據。演算法支持 NWU、ENU 和 NED 軸系。

這些範例程式展示了如何使用 Fusion 庫來處理 IMU 數據並計算方位，讓學生可以更深入地了解和應用這個強大的工具。如果有任何問題，請參考 [Fusion 的官方文件](https://github.com/xioTechnologies/Fusion.git)







## 下載 Fusion Project

```bash=
git clone https://github.com/xioTechnologies/Fusion.git
```
## 下載並安裝 Anaconda (使用虛擬環境)

### 步驟 1: 下載 Anaconda
前往 [Anaconda 官網](https://www.anaconda.com/download/) 下載適合使用者作業系統的 Anaconda 版本。

### 步驟 2: 安裝 Anaconda
- 開啟下載的安裝程式。
- 遵循安裝精靈的指示完成安裝。
- 建議將 Anaconda 加入至您的 PATH 環境變數。

![螢幕擷取畫面 2023-12-29 110324](https://hackmd.io/_uploads/rkFXw3iPa.png)

### 驗證安裝
開啟命令提示字元或終端機，輸入以下命令以確認安裝成功(顯示版本編號)：

```bash
conda --version
```

## 下載並安裝 Build Tools
### 步驟 1: 下載 Build Tools

[Microsoft 官網](https://visualstudio.microsoft.com/zh-hant/visual-cpp-build-tools/)


### 步驟 2: 安裝 Build Tools
- 在安裝過程中，確保選擇 “C++ build tools”。
- 在 “Installation details” 中選擇 “MSVC v143 - VS 2022 C++” 或 “MSVC v142 - VS 2019 C++ x64/x86 build tools” 和 “Windows 10 or 11 SDK”。
- 完成安裝後，重啟電腦。

![螢幕擷取畫面 2023-12-29 111517](https://hackmd.io/_uploads/SJ-793oPp.png)

## 創建虛擬環境
### 使用 YAML 檔案創建環境
我有已設定好的環境 yaml 檔案，可直接使用以下命令創建虛擬環境：

![螢幕擷取畫面 2023-12-29 110705](https://hackmd.io/_uploads/B14Dhniva.png)


```bash=
conda env create -f Fusion_Environment.yaml
```

![image](https://hackmd.io/_uploads/rJ8zu3ovT.png)

### 啟動虛擬環境
啟動創建的虛擬環境：

```bash=
conda activate Fusion
```

![image](https://hackmd.io/_uploads/SJC692ov6.png)


## 開啟 Visual Studio Code

### 步驟 1: 安裝 Visual Studio Code (安裝可以跳過此步驟) 
如果尚未安裝 Visual Studio Code，請前往 [Visual Studio Code 官網](https://www.bing.com/search?pglt=643&q=vs+code&cvid=f0f823c569944db98cd0ca9159aff00d&gs_lcrp=EgZjaHJvbWUqBggAEAAYQDIGCAAQABhAMgYIARBFGDsyBggCEEUYOzIGCAMQABhAMgYIBBAAGEAyBggFEAAYQDIGCAYQABhAMgYIBxAAGEAyBggIEAAYQNIBCDM5OTVqMGoxqAIAsAIA&FORM=ANNTA1&PC=ASTS) 下載並安裝。


### 步驟 2: 虛擬環境中啟動 Visual Studio Code

在虛擬環境中使用以下命令啟動 Visual Studio Code：


```bash=
code .
```
![image](https://hackmd.io/_uploads/BJ6UbTswa.png)


## 執行範例程式
### 步驟 1: 開啟範例程式
在 Visual Studio Code 中打開範例程式檔案。

![image](https://hackmd.io/_uploads/HJBvohjvp.png)

### 步驟 2: 執行程式

![image](https://hackmd.io/_uploads/HJmtihoDT.png)






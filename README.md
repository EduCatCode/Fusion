# Fusion 安裝與使用手冊

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






# GCP 部署機器學習 API
此範例使用鳶尾花朵資料集進行 `XGBoost` 分類器模型訓練。將模型儲存起來，並使用 Flask 建置 API 介面提供輸入值預測。最後並部署到 Google Cloud Platform。


## GCP 設定
### 建立一個虛擬機器
每個Google帳號都有免費一年300美金額度的試用，啟用後首先一開始點選 Compute Enging 並新增建立 VM 執行個體。

![](https://i.imgur.com/5BDeg41.png)

新建一個虛擬機需要注意以下幾個事情：

1. 主機區域 (通常主機離你越遠相對的費用就會比較便宜，相對的速度會比較慢)
2. 機器規格設定 (各位可以依據需求配置你的虛擬機)
3. 系統 (今天的範例使用 Ubuntu18.04 LTS)
4. 防火牆 (開啟 HTTP 流量，也就是 80 PORT 被允許存取)

![](https://i.imgur.com/2iyJT0z.png)
![](https://i.imgur.com/v7GKCf4.png)

### SSH 進入虛擬主機
邊教學使用 Google 瀏覽器開啟 SSH 進入虛擬機的方式，一方面也比較簡單，若你是長期使用的資深的玩家可以考慮利用金鑰的方式直接從本機電腦的終端機進行連線存取雲端伺服器的方式。

![](https://i.imgur.com/1Rl4haK.png)
![](https://i.imgur.com/9IQ3DpR.png)


### 安裝 Python
要在 Linux 環境中安裝 Python 3，請安裝相對應的套件。[python3](https://packages.debian.org/stable/python3)、[python3-dev](https://packages.debian.org/stable/python3-dev)、 [python3-venv](https://packages.debian.org/stable/python3-venv)。

```
sudo apt update
sudo apt install python3 python3-dev python3-venv build-essential
```

輸入以下指令安裝 Python 以及 PIP 管理工具。

```
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
```

## 執行 API
你可以直接 Fork 此專案到你自己的 GitHub 帳號中，或是直接 clone 專案到你的 GCP 中。

```
git clone https://github.com/1010code/Flask-API-example-with-ML-model-GCP.git
cd Flask-API-example-with-ML-model-GCP
```

### 安裝必要套件
使用 `pip3` 指令安裝必要的套件。

```
pip3 install -r requirements.txt
```

### 執行
使用 `python3` 指令且在 `sudo` 環境下執行程式，即可監聽 80 PORT。

```
sudo python3 run.py
```
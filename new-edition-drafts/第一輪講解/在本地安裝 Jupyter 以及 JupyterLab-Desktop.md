## 在本地安裝 Jupyter 以及 JupyterLab-Desktop

[Windows 使用者安裝方法點這裡](#Windows使用者)

### macOS 使用者

macOS 系統自帶的 Python 版本是 2.7，路徑（path）通常是 `/usr/local/bin/python`；想要使用更高版本的 Python，必須自己動手安裝。

### 1. 安裝 Homebrew

先在 Terminal 裡安裝 `Homebrew`，以便將來用 `brew` 命令安裝更多的軟體：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. 安裝 Miniconda

隨後，就去可以用 `brew` 安裝 Miniconda 了，它是一個小型的 Python 管理工具。

```bash
brew install miniconda
```

安裝完成之後，還要在 Terminal 執行以下命令：

```bash
conda init "$(basename "${SHELL}")"
```

這一步很重要，這個命令會更改一些必要的系統檔案，以便 `conda` 能夠正常使用。在我的機器上，以上的命令更改了我的 `~/.zshrc` 檔案，新增了以下內容（你也可以手動新增）：

```bash
# conda init "$(basename "${SHELL}")"
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/homebrew/Caskroom/miniconda/base/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/homebrew/Caskroom/miniconda/base/etc/profile.d/conda.sh" ]; then
        . "/opt/homebrew/Caskroom/miniconda/base/etc/profile.d/conda.sh"
    else
        export PATH="/opt/homebrew/Caskroom/miniconda/base/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

隨後，可以檢查一下當前的 `conda` 狀態：

```bash
which conda
conda --version
```

### 3. 確認 Python 版本

```bash
which -a python
# 應該可以看到至少兩個 Python 的位置
# 將來用 JupyterLab-Desktop 安裝的 Python 版本（目前預設是 v3.8.17）不會被檢索到
# ~/Library/jupyterlab-desktop/jlab_server/bin/python
python --version
# 應該給出的是 Miniconda 安裝的版本，比如，Python 3.11.5
```

在一臺機器上，可以安裝很多個 Python 版本，本質上來看，只不過是 “把某個版本及其相關的元件都放到同一個 ‘資料夾’（或者 ‘目錄’）之下”，而後，處於該目錄下的 ptyhon 直譯器會呼叫該目錄下的各種元件。

例如，`/opt/homebrew/Caskroom/miniconda/base/bin/python` 這個 python 直譯器，呼叫的就是 `/opt/homebrew/Caskroom/miniconda/base/` 這個目錄下的 Python 元件，而這個 “環境” 的名稱就是 `base`，可以用 `conda activate base` 啟用。

### 4. 安裝 Jupyterlab Module

```bash
python -m pip install jupyterlab
```

### 5. 安裝 JupyterLab-Desktop

```bash
brew install --cask jupyterlab
```

在 macOS 上，由於系統許可權設定，Jupyterlab-Desktop 自帶的命令列工具 `jlab` 需要手動安裝：

```bash
sudo chmod 755 /Applications/JupyterLab.app/Contents/Resources/app/jlab
sudo ln -s /Applications/JupyterLab.app/Contents/Resources/app/jlab /usr/local/bin/jlab
```

可以選擇使用 Jupyterlab-Desktop 自帶的 “Bundled Python environment”，不過，它的 Python 版本是 3.8.17。這個 “Bundle” 中，Python 直譯器是 `~/Library/jupyterlab-desktop/jlab_server/bin/python`；所有相關元件安裝在 `~/Library/jupyterlab-desktop/jlab_server/` 資料夾之內。

![](../images/jld-3.8.png)

想要使用更高版本的 Python 及其環境，比如，Python 3.11.5，就得用我們自己在系統上使用 `conda` 安裝的 Python 環境。

開啟 JupyterLab-Desktop 之後，右上角會顯示當前使用的 Python 環境名稱，比如，最初的時候，預設是 `conda: jlab_server`…… 點選這個字串，會跳出一個帶有輸入框的下拉選單：

![](../images/jld-change-env.png)

在輸入框裡輸入我們用 `conda` 安裝的 Python 路徑而後按 `Enter` 鍵即可：

```bash
# 用以下命令獲取當前系統預設 Python 的路徑：
which python
# 輸出是：/opt/homebrew/Caskroom/miniconda/base/bin/python
# 把 "/opt/homebrew/Caskroom/miniconda/base/bin/python" 複製貼上到輸入框裡
```

而後我們就可以在 JupyterLab-Destop 裡面使用自己選擇的 Python 版本了：

![](../images/jld-3.11.5.png)

有必要的話，可以在 JupyterLab-Desktop 的 `Settings > Server` 對話方塊裡，把某個 Python 環境設定成 “預設”：

![](../images/jld-default-env.png)

### 6. jlab 命令使用

在 Terminal 裡，使用以下命令 “以當前路徑為工作路徑開啟 JupyterLab Desktop”（注意末尾的 `&`）：

```bash
jlab . &
```

如果忽略了末尾的 `&`，那麼在使用 JupyterLab-Desktop 的時候，Terminal 就得一直開啟著。

使用以下命令 “用 JupyterLab Desktop 開啟某個 `.ipynb` 檔案”，比如：

```bash
jlab sample.ipynb &
```

### 7. 使用 JupyterLab-Desktop 圖形介面

當然，普通使用者最適應的是 “圖形介面”，JupyterLab-Desktop 的圖形介面相對比較直觀，很快就可以學會。最基礎的，無非是幾個最常用操作：

* `Shift+Enter`：執行某個單元格的程式碼；
* 連續按 `d` 兩次：刪除某個單元格；
* 指標拖拽：可以移動某個單元格，改變程式碼執行順序；
* ……

### 8. 關於 Python 的基本使用

可以參照《[自學是門手藝](https://github.com/selfteaching/the-craft-of-selfteaching)》，也可以參照 [Python Cheatshee in Jupyter Notebookst](https://github.com/xiaolai/Python-Cheatsheets-in-Jupyter-Notebooks)。

### Windows使用者

準備工作：網路通訊正常

### 1、下載安裝檔案

1.[下載 Anaconda Python 環境管理器](https://www.anaconda.com/download#downloads)

點選 Windows 圖示下面的 `64-Bit Graphical Installer ......` 下載檔案

2.[下載 JupyterLab Desktop](https://github.com/jupyterlab/jupyterlab-desktop/releases)

點選  `...... Setup-Windows.exe` 下載檔案

### 2、安裝 Anaconda

找到下載的檔案 `Anaconda3 ...... .exe` 雙擊執行安裝嚮導，需要注意的是**下面這幾個地方不要選錯**：

![installJL-2](../images/win-installJL-2.png)

![installJL-3](../images/win-installJL-3.png)

確認無誤再點選 Install 安裝：

![installJL-4](../images/win-installJL-4.png)

> 在安裝過程的最後一小段，電腦反應可能會變慢，感覺好像是卡住了，無需緊張，靜靜等待就好，因為安裝過程中會執行各種解壓、下載和安裝命令。

當出現 Completed 字樣，說明安裝成功，我們 Next ：

![installJL-6](../images/win-installJL-5.png)

最後 Finish 的時候記得取消這個對勾：

![installJL-6](../images/win-installJL-6.png)

點選 Finish

### 3、配置 Anaconda Python 環境

安裝完成後，系統會自動啟動 Anaconda Navigator：

![installJL-7](../images/win-installJL-7.png)

Anaconda Navigator 提示有新版本，點選 No, remind me later 暫不升級：

![installJL-8](../images/win-installJL-8.png)

> 如果你對你的網路很有信心，你也可以現在升級，無論你是否升級，都不影響後續操作

點選視窗左側的 Environments 進入環境配置：

![installJL-9](../images/win-installJL-9.png)

點選螢幕左下部分的 Create 按鈕，新建一個新的 Python 環境，專門用於英語訓練：

![installJL-10](../images/win-installJL-10.png)

> 儘可能不要破壞系統的 Python 環境，以防其他使用Python 的 APP 出問題

在彈出的對話方塊中，在 Name 這一行輸入這個虛擬環境的名稱  EnTrainEVM ：

![installJL-11](../images/win-installJL-11.png)

> 這個名稱隨便填啥都可以，只要自己看著順眼即可；只是**不能**整成**中文或者純數字**
>

在 Packages 選擇 **Python 3.11.7**

點選 Create 建立環境

![installJL-12](../images/win-installJL-12.png)

這個時候你會看到右下角的進度條在蠕動，說明你建立的 Python 環境正在建立中

> 需要注意的是，整個建立過程中都需要通暢的網路連結，如果建立失敗，99.9999% 都是網的問題。

看到下面這樣的畫面，說明環境建立成功！

![installJL-13](../images/win-installJL-13.png)

> 如果一開始你沒有更新 Anaconda Navigator 可能會彈出新版本提示，我們同樣點選 No, remind me later 暫不升級
>
> ![installJL-8](../images/win-installJL-8.png)

點選視窗左邊的 Home 進入主頁，往下滑，找到 Jupyter Lab 點選 Install 安裝：

![installJL-17](../images/win-installJL-17.png)

![installJL-18](../images/win-installJL-19.png)

等右下角的進度條走完，說明安裝成功！可以關閉 Anaconda Navigator 程式了。

此時，你用於英語訓練的 Python 環境就**配置完成啦！**

### 4、安裝 JupyterLab Desktop

找到下載目錄，雙擊 `JupyterLab-Setup-Windows` 執行安裝嚮導，此時系統會提示安裝程式需要管理員許可權，我們點 `是` 授權執行：

![installJL-15](../images/win-installJL-15.png)

點選我同意，安裝立即開始

![installJL-14](../images/win-installJL-14.png)

安裝完成，點選完成

### 5、配置 JupyterLab Desktop

系統會自動執行 JupyterLab Desktop 程式：

![installJL-16](../images/win-installJL-16.png)

我們點選 Open Folder 開啟資料夾，找到存放學習資料的地方，點選 Open：

![installJL-21](../images/win-installJL-21.png)

在視窗的右上方，有一個藍色的圖示，點一下：

![installJL-23](../images/win-installJL-23.png)

在彈出的選單裡，選擇我們剛才建立的 EnTrainEVM 英語練習環境：

![installJL-24](../images/win-installJL-24.png)

看到這個畫面需要稍微等一下：

![installJL-25](../images/win-installJL-25.png)

當你看到這個畫面，說明 JupyterLab Desktop 已經安裝成功啦！

![installJL-26](../images/win-installJL-26.png)

### 6. jlab 命令使用

在 PowerShell 裡，使用以下命令 “以當前路徑為工作路徑開啟 JupyterLab Desktop” ：

```bash
jlab .
```

注意，用 PowerShell 裡用 `jlab` 命令開啟 JupyterLab-Desktop 的時候，PowerShell 視窗不能關閉（可以最小化）。

使用以下命令 “用 JupyterLab Desktop 開啟某個 `.ipynb` 檔案”，比如：

```bash
jlab sample.ipynb
```

### 7. 使用 JupyterLab-Desktop 圖形介面

當然，普通使用者最適應的是 “圖形介面”，JupyterLab-Desktop 的圖形介面相對比較直觀，很快就可以學會。最基礎的，無非是幾個最常用操作：

* `Shift+Enter`：執行某個單元格的程式碼；
* 連續按 `d` 兩次：刪除某個單元格；
* 指標拖拽：可以移動某個單元格，改變程式碼執行順序；
* ……

### 8. 關於 Python 的基本使用

可以參照《[自學是門手藝](https://github.com/selfteaching/the-craft-of-selfteaching)》，也可以參照 [Python Cheatshee in Jupyter Notebookst](https://github.com/xiaolai/Python-Cheatsheets-in-Jupyter-Notebooks)。

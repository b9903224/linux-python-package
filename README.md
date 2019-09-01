# linux-python-package
ref.
* [linux下无root权限使用yum安装的方法](https://blog.csdn.net/GreenHandCGL/article/details/83055151)
* [ubuntu18.04.1无root权限在user目录下安装python及pip](https://blog.csdn.net/lfs666666/article/details/88901543)
* [Python: CentOS7 安裝 Python ](https://medium.com/@CCstruggled/python-centos7-%E5%AE%89%E8%A3%9D-python-rpm-source-15045893f680)

## 安裝Python
* 下載Python-3.7.4.tgz，解壓縮(執行tar -zxvf Python-3.7.4.tgz)
* 建立一個之後放Python的目錄(執行mkdir Python_file)
* 檢查OS中是否有安裝Python3.7必備三個套件: Development Tools, zlib, libffi-devel

### 不存在
#### 有網路有權限情況下安裝
* yum group install "Development Tools"
* yum -y install zlib
* yum -y install libffi-devel

#### 無網路無權限情況下安裝
##### 方法1
將套件安裝在自己建的python目錄下，之後安裝python時需指定套件位置
1. 分別下載所有套件的tar檔案，並分別解壓縮完成step2~5(執行tar -zxvf (package name))
2. ./configure --prefix=(python file path)
3. 執行 make
4. 執行 make install
5. 執行完畢後可移除暫存檔(執行 make clean)

##### 方法2
套件只能暫時安裝(暫時性的修改環境變數)，重新開機後就無法使用了
1. 分別下載rpm檔案(可以下載此repo的檔案)，解壓縮(執行rpm2cpio (rpm檔案名稱) | cpio -idvm)
2. 假設再~data/目錄下解壓縮，編輯 ~/.bashrc 檔案(修改export PATH=$PATH:$HOME/data/usr/bin/) 
3. source ~/.bashrc

### 開始安裝Python
1. 進入解壓縮過的Python-3.7.4目錄中
2. 執行 ./configure --prefix=(python file path) **如果使用方法1必須指定套件路徑: ./configure --prefix=(python file path) --with-(package)=(path)**
3. 執行 make
4. 執行 make install
5. 執行完畢後可移除暫存檔(執行 make clean)

## Python執行方式
(python file path)/bin/python3
## pip執行方式
(python file path)/bin/pip3

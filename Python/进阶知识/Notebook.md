# 1 使用
- 记得要保证你开启的虚拟环境是你需要的那个
```
conda activate env_name
```
- 在虚拟环境内先进行其安装（注意，若是使用pip，需要安装，`conda install pip`）
```
conda install notebook
```
- 自此可以在vscode上使用，安装插件即可
- 若是想在浏览器操作，切换到你的工程目录，若是在D盘则需要先切换盘符
```
//切换盘符到D盘
D:
//切换到工程路径
cd your_dir
```
- 直接输入指令即可在浏览器使用notebook，命令行需要保持开启，不然进程会被中断
```
jupyter notebook
```
# 2 软件包
- 如果需要进行持久化安装, 需要使用持久化路径, 如下方代码示例
```Python
#创建目录，用于存放额外的库或者依赖项
!mkdir /home/aistudio/external-libraries
#-t选项指定了安装路径
!pip install beautifulsoup4 -t /home/aistudio/external-libraries
!pip install bs4
```
- 同时添加如下代码, 这样每次环境(kernel)启动的时候只要运行下方代码即可
```Python
import sys
sys.path.append('/home/aistudio/external-libraries')
```
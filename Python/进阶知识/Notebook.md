  
# 1 软件包
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
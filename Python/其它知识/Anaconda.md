# 1 虚拟环境管理
- 展示虚拟环境列表
```Python
conda env list
```
- 激活虚拟环境
```Python
conda activate env_name
```
- 退出当前虚拟环境
```Python
conda deactivate
# 这里相当于缺省当下环境名
conda activate
# 这里相当于缺省base环境
```
- 创建/删除虚拟环境
```Python
conda create -n env_name python=ver_number
conda remove -n env_name --all
```
# 2 包的管理
- 查询当下环境的包列表
```Python
conda list
```
- 使用conda安装需要的包，注意选择版本的等号是一个，且周围不能有空格
```Python
conda install package_name=ver_number
```
- 若是conda下不下来，则可以使用pip/pip3，但是要先下载
```Python
conda install pip
# 注意此处是两个等号，和conda的一个不一样，但周围都不能有空格
pip install package_name==ver_number
```
- 卸载包
```Python
conda uninstall package_name
# 这样会将依赖于这个包的所有其它包也同时卸载
conda uninstall package_name --force
# 仅仅删除选定的包
```
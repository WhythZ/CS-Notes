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
//这里相当于缺省当下环境名
conda activate
//这里相当于缺省base环境
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
- 安装需要的包
```Python
conda install package_name=ver_number
```
- 卸载包
```Python
conda uninstall package_name
//这样会将依赖于这个包的所有其它包也同时卸载
conda uninstall package_name --force
//仅仅删除选定的包
```
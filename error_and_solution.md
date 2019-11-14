
# cmd安装 python -m pip install tensorflow

```bash
ERROR: Cannot uninstall 'wrapt'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.
```
办法1：输入 pip install -U --ignore-installed wrapt enum34 simplejson netaddr

[参考](https://www.cnblogs.com/xiaowei2092/p/11025155.html)

 
---
```bash
ERROR: tensorboard 1.14.0 has requirement setuptools>=41.0.0, but you'll have setuptools 39.1.0 which is incompatible.
```
原因： setuptools 版本太低

办法：更新setuptools版本 输入 
```bash
python -m pip install --upgrade setuptools
```
[参考](https://www.cnblogs.com/conver/p/11141176.html)

---

```python
>>> import tensorflow as tf
d:\ProgramData\Anaconda3\lib\site-packages\h5py\__init__.py:36: FutureWarning: Conversion of the second argument of issubdtype from `float` to `np.floating` is deprecated. In future, it will be treated as `np.float64 == np.dtype(float).type`.
  from ._conv import register_converters as _register_converters

```
问题原因：   

包内出错，是h5py包

尝试：
```bash
python -m  pip install --user h5py==2.8.0rc1
```
[参考-成功解决：FutureWarning: Conversion of the second argument of issubdtype from `float` to `np.floating` is](https://www.cnblogs.com/guohaoblog/p/9391929.html)



---
# anaconda报错

CondaHTTPError: HTTP 404 NOT FOUND for url https://pypi.tuna.tsinghua.edu.cn/simple/ 错误
二、解决方式
参考的是github上给出的一个解决方法，地址如下：
https://github.com/conda/conda/issues/7695

具体就两个步骤：

删除之前的镜像通道
重新添加默认的镜像通道
```bash
conda config --remove-key channels
conda config --append channels conda-forge --append channels bioconda --append channels defaults
```
[参考](https://blog.csdn.net/weixin_41010198/article/details/88740150)



## pip安装慢


- 修改pip源：

Linux系统：
```bash
mkdir ~/.pip
cd ~/.pip
vim pip.conf
```

```bash
[global]
index-url = https://pypi.mirrors.ustc.edu.cn/simple/
```

windows系统：
```bash
mkdir pip
cd pip
vim pip.ini
```
```bash
[global]
index-url = https://pypi.mirrors.ustc.edu.cn/simple/
```



- Conda修改镜像源 
Linux和Windows对于conda修改镜像源的方法一样：
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
查看是否添加
```bash
vim ~/.condarc
```
查看是否有新增
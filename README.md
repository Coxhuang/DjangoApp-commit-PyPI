
[TOC]

# PyPI发布 Django App

## #0 GitHub

```
https://github.com/Coxhuang/DjangoApp-commit-PyPI
```

## #1 环境

```
Python3.6
```

## #2 开始

### #2.1 安装twine

```
pip3 install twine
```

### #2.2 新建包(我的包名叫django-google-auth)


```
.django-google-auth

├── LICENSE 
├── MANIFEST.in 
├── README.md
├── django_google_auth2 # django App
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── google
│   ├── migrations
│   ├── models.py
│   ├── templates
│   ├── templatetags
│   ├── tests.py
│   ├── urls.py
│   ├── utils
│   └── views.py
└── setup.py
```

- 把django app拷贝到django-google-auth目录下
- 在django-google-auth目录下新建以下文件

```
LICENSE  # 许可证
MANIFEST.in # 把不是.py结尾的文件一起打包(如果没有该文件,默认只打包py文件)
README.md # 项目描述 
setup.py # 配置文件 
```

### #2.3 MANIFEST.in

```
include LICENSE 
include README.md
recursive-include django_google_auth2/google * # django_google_auth2/google * 下的所有文件全部打包
recursive-include django_google_auth2/utils *
recursive-include django_google_auth2/templatetags *
recursive-include django_google_auth2/migrations *
recursive-include django_google_auth2/templates *

```

### #2.4 setup.py

```
import os
from setuptools import find_packages, setup

with open(os.path.join(os.path.dirname(__file__), 'README.md')) as readme:
    README = readme.read()

# allow setup.py to be run from any path
os.chdir(os.path.normpath(os.path.join(os.path.abspath(__file__), os.pardir)))

setup(
    name='django-google-auth2',
    version='0.0.8',
    packages=find_packages(),
    include_package_data=True,
    license='BSD License', # example license
    description='django-google-auth2 project is demo application for google auth ',
    long_description=README,
    url='https://github.com/Coxhuang/django-google-auth',
    author='黄民航',
    author_email='gmhesat@gmail.com',
    classifiers=[
        'Environment :: Web Environment',
        'Framework :: Django',
        'Framework :: Django :: 2.0', # replace "X.Y" as appropriate
        'Intended Audience :: Developers',
        'License :: OSI Approved :: BSD License', # example license
        'Operating System :: OS Independent',
        'Programming Language :: Python',
        # Replace these appropriately if you are stuck on Python 2.
        'Programming Language :: Python :: 2',
        'Programming Language :: Python :: 3.6',
    ],
)
```

## #3 发布

- 回到包的目录下

```
# 打包
python3 setup.py sdist
```

```
# 发布
twine upload dist/*
```

![20190403101203-image.png](https://raw.githubusercontent.com/Coxhuang/yosoro/master/20190403101203-image.png)


# 下载

```
pip3 install django-google-auth2==0.0.8
```














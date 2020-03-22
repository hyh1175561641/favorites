



# 和Python的交互

安装Redis包

Pip3 install redis

pip freeze 

安装好Redis的python包之后，有许多命令可以和Redis交互，函数类似于Redis命令

```python
import redis
>>> r = redis.Redis(host='localhost', port=6379, db=0)
>>> r.set('foo', 'bar')
True
>>> r.get('foo')
'bar'
```



[redis PyPl首页](https://pypi.org/project/redis/#description)

[作者github首页](https://github.com/andymccurdy/redis-py)

[手册](https://redis-py.readthedocs.io/en/latest/)

手册还可以在pydoc命令中找到



Strict  严格的，绝对的，精确的，详细的
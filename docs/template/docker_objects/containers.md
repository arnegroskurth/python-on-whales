# Containers

Don't use the constructor directly. Instead use 
```python
from python_on_whales import docker

my_container = docker.container.inspect("my-container-name")

# for example:
if my_container.state.running:
    my_container.kill()

```
For type hints, use this

```python
from python_on_whales import Container

def print_dodo(container: Container):
    print(container.execute(["echo", "dodo"]))
```

## Attributes

It attributes are the same that you get with the command line:
`docker container inspect ...`

If you want to know the exact structure, you can go to the 
[`docker container inspect` reference page](https://docs.docker.com/engine/api/v1.40/#operation/ContainerInspect)
and click on "200 no error".
An example is worth many lines of descriptions.


```
In [1]: from python_on_whales import docker

In [2]: container = docker.run("ubuntu", ["sleep", "infinity"], detach=True)

In [4]: def super_print(obj):
   ...:     print(f"type={type(obj)}, value={obj}")
   ...:

In [5]: super_print(container.id)
type=<class 'str'>, value=1fb602d9292492846a395c7d7c8400a796c6b49eecdf83ae38875feb08728071

In [6]: super_print(container.created)
type=<class 'datetime.datetime'>, value=2020-10-24 13:49:55.050922+00:00

In [7]: super_print(container.image)
type=<class 'python_on_whales.Image'>, value=sha256:9140108b62dc87d9b278bb0d4fd6a3e44c2959646eb966b86531306faa81b09b

In [8]: super_print(container.name)
type=<class 'str'>, value=charming_burnell

In [9]: super_print(container.state.status)
type=<class 'str'>, value=running

In [10]: super_print(container.state.running)
type=<class 'bool'>, value=True

In [11]: super_print(container.state.paused)
type=<class 'bool'>, value=False

In [12]: super_print(container.state.restarting)
type=<class 'bool'>, value=False

In [13]: super_print(container.state.OOM_killed)
type=<class 'bool'>, value=False

In [14]: super_print(container.state.dead)
type=<class 'bool'>, value=False

In [15]: super_print(container.state.pid)
type=<class 'int'>, value=5565

In [16]: super_print(container.state.exit_code)
type=<class 'int'>, value=0

In [17]: super_print(container.state.error)
type=<class 'str'>, value=

In [18]: super_print(container.state.started_at)
type=<class 'datetime.datetime'>, value=2020-10-24 13:49:55.325651+00:00

In [19]: super_print(container.state.finished_at)
type=<class 'datetime.datetime'>, value=0001-01-01 00:00:00+00:00

In [20]: super_print(container.host_config.auto_remove)
type=<class 'bool'>, value=False

In [21]: super_print(container.config.hostname)
type=<class 'str'>, value=1fb602d92924

In [22]: super_print(container.config.domainname)
type=<class 'str'>, value=

In [23]: super_print(container.config.attach_stdin)
type=<class 'bool'>, value=False

In [24]: super_print(container.config.attach_stdout)
type=<class 'bool'>, value=False

In [25]: super_print(container.config.attach_stderr)
type=<class 'bool'>, value=False

In [26]: super_print(container.config.tty)
type=<class 'bool'>, value=False

In [27]: super_print(container.config.open_stdin)
type=<class 'bool'>, value=False

In [28]: super_print(container.config.stdin_once)
type=<class 'bool'>, value=False

In [29]: super_print(container.config.env)
type=<class 'list'>, value=['PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin']

In [30]: super_print(container.config.cmd)
type=<class 'list'>, value=['sleep', 'infinity']

In [31]: super_print(container.config.image)
type=<class 'str'>, value=ubuntu

In [32]: super_print(container.config.labels)
type=<class 'dict'>, value={}

```

## Methods

{{autogenerated}}

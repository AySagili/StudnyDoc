# 2026.6.25

## 工作期间遇见Nvim使用ty LSP的时候函数打上注解后无法通过LSP获取函数类型信息的问题

### 解决方案：处理注解，让注解将函数的类型信息传递一下

```python
from typing import ParamSpec, TypeVar
from collections.abc import Callable
P = ParamSpec('P')
T = TypeVar('T')
def log(func: Callable[P, T]) -> Callable[P, T]:
    @wraps(func)
    def wrap(*args: P.args, **kwargs: P.kwargs) -> T:
        pass
    return wrap


```

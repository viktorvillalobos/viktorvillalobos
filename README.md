
```python
from dataclasses import dataclass
from typing import Tuple


class Meta(type):
    def __new__(cls, name, bases, attrs):
        for attr in attrs:
            if not attr.startswith("_"):
                __annotations__[attr] = Tuple[str, ...]
        attrs["__annotations__"] = __annotations__
        new_cls = super().__new__(cls, name, bases, attrs)
        new_cls = dataclass(new_cls)
        return new_cls


class Stack(metaclass=Meta):
    languages = ("Python", "JS", "Rust")
    databases = ("PostgreSQL", "Redis", "Mongo")
    utils = ("Docker", "Celery", "Citus")
    frameworks = ("Django", "DRF", "Sanic", "FastAPI")

```
</h3>

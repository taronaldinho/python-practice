---
tags:
aliases:
cssclasses:
publish: false
---
# Python開発環境

---

## この資料の目的
Python開発環境とは、＜以降書きかけ＞

![[attachments/Pasted image 20240217112025.png]]
## 例

```python:.main.py
from typing import Union  

from pydantic import ConfigDict, validate_call

validate_call_config = ConfigDict(strict=True)


@validate_call(config=validate_call_config)
def another_sum(a: Union[int, float], b: Union[int, float]) -> float:
    """ふたつの実数値を足した結果を返す。

    Parameters
    ----------
    a : Union[int, float]
        足される数
    b : Union[int, float]
        足す数

    Returns
    -------
    float
        足し算の結果
  
    Examples
    --------
    >>> another_sum(10, 5)
    15
    """
  
    return float(a + b)
```


```python:.\test_main.py
import pytest
from main import another_sum
  
  
@pytest.mark.parametrize("test_a, test_b", [(2, 3), (2, 3.0)])
class TestClass:
    @pytest.mark.parametrize("test_expected", [5, 5.0])
    def test_another_sum_return_value(self, test_a, test_b, test_expected):
        assert another_sum(test_a, test_b) == test_expected
  
    def test_another_sum_return_type(self, test_a, test_b):
        assert isinstance(another_sum(test_a, test_b), float)
```



# Pythonの組み込みの関数名や定数名

組み込みの関数名や定数名を変数として使用すると、元の関数・定数が使えなくなってしまう。また、import したライブラリ、クラス、関数、定数についても同様。これらの名前は使わないことを推奨。

```Python
# 組み込みの関数、定数名の確認方法 
from pprint import pprint
pprint(dir(__builtins__), compact=True)
```

```Python
['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException',
 'BaseExceptionGroup', 'BlockingIOError', 'BrokenPipeError', 'BufferError',
 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError',
 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError',
 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EncodingWarning',
 'EnvironmentError', 'Exception', 'ExceptionGroup', 'False', 'FileExistsError',
 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit',
 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError',
 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt',
 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None',
 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError',
 'OverflowError', 'PendingDeprecationWarning', 'PermissionError',
 'ProcessLookupError', 'PythonFinalizationError', 'RecursionError',
 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning',
 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning',
 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError',
 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError',
 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning',
 'ValueError', 'Warning', 'WindowsError', 'ZeroDivisionError',
 '_IncompleteInputError', '__build_class__', '__debug__', '__doc__',
 '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs',
 'aiter', 'all', 'anext', 'any', 'ascii', 'bin', 'bool', 'breakpoint',
 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex',
 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate',
 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr',
 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int',
 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map',
 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow',
 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set',
 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple',
 'type', 'vars', 'zip']
```

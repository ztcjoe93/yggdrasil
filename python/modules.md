Last updated: 2023-03-05 02:14

## Dynamically importing module using filename

Reference for SO post: https://stackoverflow.com/questions/67631/how-can-i-import-a-module-dynamically-given-the-full-path  
We can utilize the following factory function within `importlib` to create a `ModuleSpec` instance using the path.  

`importlib.util.spec_from_file_location`  
Reference: https://docs.python.org/3/library/importlib.html#importlib.util.spec_from_file_location  

This can then be chained using `importlib.util.module_from_spec`, which creates a new module with the given `ModuleSpec`.  
The module can then be loaded into `sys.modules`  

sys.modules[](https://docs.python.org/3/library/sys.html#sys.modules "Permalink to this definition")
> This is a dictionary that maps module names to modules which have already been loaded. This can be manipulated to force reloading of modules and other tricks. However, replacing the dictionary will not necessarily work as expected and deleting essential items from the dictionary may cause Python to fail. If you want to iterate over this global dictionary always use `sys.modules.copy()` or `tuple(sys.modules)` to avoid exceptions as its size may change during iteration as a side effect of code or activity in other threads.

We then invoke the [loader](https://docs.python.org/3/glossary.html#term-loader) to import the module after it's loaded into the `sys.modules`.  
Thereafter, we can invoke functions/classes from the module as per usual.  

```python
# sample code for dynamic module loading
import importlib.util
import sys
spec = importlib.util.spec_from_file_location("module.name", "/path/to/file.py")
foo = importlib.util.module_from_spec(spec)
sys.modules["module.name"] = foo
spec.loader.exec_module(foo)
foo.MyClass()
```


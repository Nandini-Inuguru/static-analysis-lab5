| **Tool**    | **Issue ID / Code** | **Description**                       | **Severity** | **Status** | **Fix Summary**                                                              |
| ----------- | ------------------- | ------------------------------------- | ------------ | ---------- | ---------------------------------------------------------------------------- |
| **Pylint**  | C0114               | Missing module docstring              | Low          | ✅ Fixed    | Added a module-level docstring at the top of the file.                       |
| **Pylint**  | C0103               | Function name not in `snake_case`     | Low          | ✅ Fixed    | Renamed functions like `addItem` → `add_item`, `removeItem` → `remove_item`. |
| **Pylint**  | C0116               | Missing function or method docstring  | Low          | ✅ Fixed    | Added docstrings for all functions.                                          |
| **Pylint**  | W0702               | Bare `except` statement               | Medium       | ✅ Fixed    | Replaced with `except Exception as e:` and added proper logging.             |
| **Pylint**  | W1514 / R1732       | File opened without `with` context    | Medium       | ✅ Fixed    | Used `with open(..., encoding='utf-8') as f:` instead of plain `open()`.     |
| **Pylint**  | W0611               | Unused import (`logging`)             | Low          | ✅ Fixed    | Removed unnecessary imports.                                                 |
| **Pylint**  | W0123               | Use of `eval()`                       | High         | ✅ Fixed    | Removed `eval()` and replaced with safer logic.                              |
| **Flake8**  | E302 / E305         | Missing blank lines between functions | Low          | ✅ Fixed    | Added two blank lines between top-level functions.                           |
| **Bandit**  | B110                | Bare `except` detected                | Medium       | ✅ Fixed    | Added specific exception handling and logging.                               |
| **Bandit**  | B307                | Insecure `eval()` call                | High         | ✅ Fixed    | Removed `eval()` usage completely.                                           |
| **General** | Code style          | Missing final newline                 | Low          | ✅ Fixed    | Added newline at end of file.                                                |

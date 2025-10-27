# static-analysis-lab5

Overview

This lab focused on improving the quality, security, and readability of an existing Python script called inventory_system.py using static analysis tools such as Pylint, Flake8, and Bandit.

The goal was to identify common coding and security issues, fix them, and verify the improvements using automated code quality reports. During this process, I also documented all issues found, created a cleaned version of the code, and reflected on what I learned about writing cleaner, safer, and more maintainable code.

REFLECTION Q/A
1. Which issues were the easiest to fix, and which were the hardest? Why?

The easiest issues to fix were mostly style-related ones. Adding missing docstrings, removing unused imports, and adding blank lines between functions took very little time because the tools clearly pointed them out, and they didn’t affect how the code actually worked.

The harder issues were the ones that required understanding how the code behaved. For example, fixing the mutable default argument bug took a while to figure out because I had to understand why the same list was being reused between function calls. Replacing the eval() function was also challenging because it required rewriting parts of the logic to make it work safely without breaking anything else. Updating all function names to snake_case was another tedious part since it meant tracking down every place those functions were used.

2. Did the static analysis tools report any false positives?

Yes, there was one case where Pylint warned about the use of a global variable. In this situation, the variable was intentionally global because it was used to keep track of shared state across multiple functions. Even though Pylint marked it as a warning, it wasn’t actually an issue for the way the code was designed. So, while the tool was technically correct, it didn’t fit the context, making it a kind of false positive.

3. How would you integrate static analysis tools into your actual software development workflow?

If I were working on a real software project, I would make static analysis tools a regular part of the workflow. I’d set up pre-commit hooks so that every time code is committed, tools like Pylint, Flake8, and Bandit run automatically to catch issues early.

I’d also include them in a continuous integration (CI) pipeline on GitHub so that every pull request runs these checks before merging. This way, code that doesn’t meet quality or security standards can’t be merged accidentally. On the local side, I’d enable these tools in my IDE so I can see and fix warnings while I’m writing the code instead of waiting until later.

4. What tangible improvements did you observe in the code quality, readability, or potential robustness after applying the fixes?

After fixing the issues, the code felt much cleaner and more professional. The functions now have clear names and proper docstrings, which makes it easier to understand what each part does. The overall structure looks more consistent, and the code follows PEP8 formatting rules, so it’s easier on the eyes.

Replacing eval() and improving exception handling definitely made the program safer and less prone to crashes. Using with open() for file handling also ensured files are properly closed, which helps prevent bugs down the line. Overall, the code not only looks better but also runs more reliably and would be easier for someone else to maintain or build upon.

ISSUE TABLE

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

```markdown
# xdg-desktop-portal Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides a comprehensive guide to contributing to the `xdg-desktop-portal` project, a Python-based codebase for implementing desktop portals. It covers the project's coding conventions, common development workflows (such as adding async portal components, refactoring interfaces, managing documentation, and testing), and provides actionable commands and code examples to streamline your contributions.

## Coding Conventions

- **File Naming:**  
  Use `camelCase` for Python files and follow the pattern `xdp-<component>-dex.c/h` for C source/header files related to portal components.
  ```
  # Example Python file
  sessionManager.py

  # Example C files
  xdp-request-dex.c
  xdp-request-dex.h
  ```

- **Import Style:**  
  Use relative imports in Python modules.
  ```python
  from .utils import get_portal_info
  ```

- **Export Style:**  
  Use named exports (explicitly listing what is exported).
  ```python
  __all__ = ['SessionManager', 'RequestHandler']
  ```

- **Commit Message Patterns:**  
  - Prefixes: `context`, `doc`, `tests`, `permission`, `xdp`, `session`, `dex`, `ci`, `secret`
  - Average length: ~53 characters
  - Example:  
    ```
    session: add async handling to SessionManager
    tests: add shutdown scenario test
    doc: update README with new portal usage
    ```

## Workflows

### Add New Portal Implementation Using Futures
**Trigger:** When adding a new async/fiber-based implementation for a portal component  
**Command:** `/add-async-portal-component`

1. Create new `.c` and `.h` files for the component (e.g., `xdp-request-dex.c`, `xdp-request-dex.h`).
2. Update `desktop-portal/meson.build` to include the new source files.
3. Implement the async logic using futures/fibers in the new files.

**Example:**
```c
// xdp-request-dex.c
#include "xdp-request-dex.h"

// Implement async logic using futures/fibers here
```

```meson
# desktop-portal/meson.build
sources += ['xdp-request-dex.c', 'xdp-request-dex.h']
```

---

### Refactor Portal Method Signatures Across Multiple Portals
**Trigger:** When changing how multiple portals handle method calls or data passing  
**Command:** `/refactor-portal-methods`

1. Update several portal `.c` files to use the new method signature or interface.
2. Update shared or core header/source files to support the new pattern.
3. Update the corresponding header files if needed.

**Example:**
```c
// Before
void portal_method_call(Sender *sender, ...);

// After
void portal_method_call(XdpAppInfo *app_info, ...);
```

---

### Migrate or Cleanup Documentation and Website
**Trigger:** When reorganizing or de-duplicating documentation and website content  
**Command:** `/migrate-docs`

1. Move or copy content between `README.md`, `doc/`, and `doc/website/` files.
2. Delete obsolete website or documentation files.
3. Update or simplify language in documentation and README.

**Example:**
```
mv doc/old_guide.md doc/website/
rm doc/website/legacy_docs.md
# Edit README.md to reflect new structure
```

---

### Add or Improve Tests for New Features or Bugfixes
**Trigger:** When ensuring new features or fixes are tested  
**Command:** `/add-test`

1. Add new test files (e.g., `test_shutdown.py`).
2. Update test utilities or configuration (e.g., `conftest.py`, `xdp_utils.py`).
3. Update `tests/meson.build` to include new tests.

**Example:**
```python
# tests/test_shutdown.py
def test_shutdown_behavior():
    # Test shutdown scenario
    assert shutdown() == "OK"
```

```python
# tests/conftest.py
import pytest

@pytest.fixture
def mock_portal():
    # Setup mock portal for tests
    yield
```

```meson
# tests/meson.build
test('shutdown', shutdown_test_exe)
```

## Testing Patterns

- **Test Framework:** Unknown (no explicit framework detected)
- **File Pattern:** Test files are named with the pattern `*.test.ts` (for TypeScript) and `*.py` (for Python).
- **Test Utilities:** Common utilities are placed in files like `conftest.py` and `xdp_utils.py`.
- **Adding Tests:** Place new tests in the `tests/` directory and update `tests/meson.build` to register them.

## Commands

| Command                        | Purpose                                                      |
|---------------------------------|--------------------------------------------------------------|
| /add-async-portal-component     | Add a new async/fiber-based portal component implementation  |
| /refactor-portal-methods        | Refactor method signatures/interfaces across portal modules  |
| /migrate-docs                   | Migrate, merge, or clean up documentation and website        |
| /add-test                       | Add or improve tests for new features or bugfixes            |
```

---
name: backend-python
description: Strict conventions and formatting rules for Python, FastAPI, and backend development
---

# Backend Development Conventions (Python & FastAPI)

Apply these rules whenever writing, modifying, or refactoring Python backend code.

---

## 1. File Structure & Header Docstring

Every Python file must start with a docstring in the following exact format:

```python
"""
Brief explanation of the module purpose and domain logic without mentioning the file name, class names, or function names.

:author: AUTHOR_NAME
:date: dd/mm/yyyy
"""
```

---

## 2. Standard File Sections & Spacing Rules

Each file is organized into 4 primary sections:
1. `# ----- IMPORTS ----- #`
2. `# ----- CONSTS ----- #`
3. `# ----- CLASSES ----- #`
4. `# ----- FUNCTIONS ----- #`

*(Additional sections may be created only when strictly necessary).*

### Strict Spacing Rules
- **General Banner Spacing**: 1 blank line above and 1 blank line below `# ----- SECTION_NAME ----- #`.
- **EXCEPTION 1 - IMPORTS**: Written directly after the file docstring with **0 blank lines above** and **1 blank line below**.
- **EXCEPTION 2 - CLASSES & FUNCTIONS**: Must have **exactly 2 blank lines above** their respective section banners.

---

## 3. Imports Section Structure

Imports must be organized into 3 distinct tiers, separated by 1 blank line, and ordered alphabetically (A-Z) within each tier:
- **Tier 1**: Python standard library modules (`os`, `sys`, `typing`, etc.)
- **Tier 2**: Third-party libraries (`fastapi`, `pydantic`, `sqlalchemy`, etc.)
- **Tier 3**: Current project internal modules (`app.core`, `app.models`, etc.)

---

## 4. Constants

- All constants must be defined under `# ----- CONSTS ----- #` and written in `UPPER_CASE_WITH_UNDERSCORES`.

---

## 5. Classes & Docstring Rules

- Every class must have a docstring.
- **No Blank Lines**: Do not insert blank lines between the `class` declaration and its docstring, or between the docstring and the first line of code inside the class.
- **Content**: Explain the responsibility and purpose of the class **without** mentioning the class name or any method names.

---

## 6. Functions & Docstring Rules

- All function parameters and return values must have strict type annotations.
- Every function must have a docstring.
- **No Blank Lines**: Do not insert blank lines between `def` and the docstring, or between the docstring and the first line of code inside the function.
- **Format**:
  1. Summary sentence.
  2. One empty line.
  3. `:param PARAM_NAME: Explanation of param` for each parameter.
  4. `:return: WHAT_WE_RETURN` (immediately after params, **without** an empty line; omit `:return:` entirely if the function returns `None` or nothing).
  5. `:raises ERROR_NAME: Explanation of error condition` for each exception raised.

---

## 7. Error Handling & Custom Exceptions

- Always prefer raising custom-made exceptions.
- All custom exceptions must be defined in an `errors.py` (or `errors/` package) module.

---

## 8. Complete Python File Blueprint

```python
"""
Manages user authentication, token generation, and credential validation against the persistent store.

:author: Backend Team
:date: 14/08/2026
"""
# ----- IMPORTS ----- #

import os
from typing import Optional

from fastapi import Depends, HTTPException, status
from pydantic import BaseModel

from app.core.config import settings
from app.errors import InvalidCredentialsError, UserNotFoundError
from app.models.user import User


# ----- CONSTS ----- #

ACCESS_TOKEN_EXPIRE_MINUTES: int = 60
DEFAULT_ALGORITHM: str = "HS256"


# ----- CLASSES ----- #

class TokenPayload(BaseModel):
    """Encapsulates authenticated token claims and expiration metadata."""
    sub: str
    exp: int


# ----- FUNCTIONS ----- #

def authenticate_user(username: str, password_hash: str) -> User:
    """Validates user credentials against active user records.

    :param username: Unique account identifier
    :param password_hash: Cryptographic hash of the candidate password
    :return: Authenticated user entity model
    :raises InvalidCredentialsError: If the password hash does not match stored records
    :raises UserNotFoundError: If no account exists with the provided username
    """
    if username == '':
        raise InvalidCredentialsError("Username cannot be empty")
    user: Optional[User] = None
    if user is None:
        raise UserNotFoundError(f"User {username} not found")
    return user
```

# Todo

- [ ] shutil
- [ ] os

# `pathlib` – Paths and Navigation

## Quick reference

| Method / Attribute | Description |
|---|---|
| `Path.cwd()` | Get current working directory |
| `Path.home()` | Get current user's home directory |
| `Path(__file__)` | Get path to current Python file |
| `Path.resolve()` | Resolve path into an absolute, normalized path |
| `.exists()` | Check if path exists |
| `.is_dir()` | Check if path is a directory |
| `.is_file()` | Check if path is a file |
| `.name` | Get final path component |
| `.parent` | Get immediate parent directory |
| `.parents` | Get all parent directories |
| `.parts` | Get all path components as a tuple |
| `.suffix` | Get file extension |
| `.stem` | Get filename without extension |
| `.iterdir()` | Iterate over immediate directory contents |
| `.glob()` | Find matching entries in immediate directory |
| `.rglob()` | Find matching entries recursively |
| `.match()` | Check whether path matches a pattern |
| `.mkdir()` | Create directory |
| `.rmdir()` | Remove an empty directory |
| `.unlink()` | Delete a file or symlink |
| `.rename()` | Rename or move a file or directory |
| `.touch()` | Create an empty file |
| `.write_text()` | Create or overwrite a text file |
| `.write_bytes()` | Create or overwrite a binary file |

**Remember:** `pathlib` gives you `Path` objects rather than ordinary strings. This means you can combine paths, inspect their components, and navigate the filesystem using convenient methods without manually manipulating strings.

**Remember:** Prefer `pathlib` for everyday filesystem path operations. Use `os` and `shutil` when you need additional operating-system or filesystem functionality.

## Quick code snippets

**-- Basics --**

```python
from pathlib import Path

# Current working dir
# Absolute path - relative to where you execute the script from
cwd = Path.cwd()

# Home directory
home = Path.home()

# Create paths
config = home / ".config" / "nvim"

# Check if something exists
config.exists()
config.is_dir()
config.is_file()

# Get information about a path
config.name  # nvim
config.parent  # /Users/tamasm/.config
config.suffix  # File extension, e.g. .txt
config.stem  # Filename without extension

# List directory contents
for item in config.iterdir():
    if item.is_dir():
        print("Dir: ", item)
    else:
        print("File: ", item)

# Find files recursively
for item in config.rglob("*.lua"):
    print(item)
```

**-- Parent dirs --**

```python
from pathlib import Path

# Path to current file
print(__file__)

# Path obj to get the dir the file is in
file_path = Path(__file__).parent
print(file_path)

# Iterate over all parent dirs
# a special sequence that you can iterate over or index
file_parents = Path(__file__).parents

print("Index 0: ", file_parents[0])  # Same as .parent
print("Index 1: ", file_parents[1])
print("Index 2: ", file_parents[2])
print("Index -1: ", file_parents[-1])  # Root

for parent in file_parents:
    print(parent)
```

**-- Match dir/file name --**

```python
from pathlib import Path

# nvim config
conf = Path.home() / ".config" / "nvim"

# -- 1 --
# `.name` returns only the final component of the path
print(conf.name == "nvim")

# -- 2 --
# `.parts` returns a tuple of all components of the path
# ('/', 'Users', 'tamasm', '.config', 'nvim')
print(conf.parts)
print("tamasm" in conf.parts)

# -- 3 --
# Check if the path matches a pattern
# Useful for wildcard patterns.
print(conf.match("*/.config/*"))
print(conf.match("*/.config/hello"))

# -- 4 --
# Not recommended
print("config" in str(conf))

# -- 5 --
# File
init = conf / "init.lua"

print(init.parts)
print(init.exists())
```

**-- Create dirs --**

```python
from pathlib import Path

config_dir = Path.cwd() / "config"
config_dir_nested = config_dir / "nested"

# if not config_dir.exists():
#     config_dir.mkdir()

config_dir.mkdir(exist_ok=True, parents=True)
config_dir_nested.mkdir(exist_ok=True, parents=True)

```

**-- Create files --**

```python
from pathlib import Path

config_dir = Path(__file__).parent / "config"

# Create empty file
test_file = config_dir / "test.txt"
test_file.touch(exist_ok=True)

# Create and write to file
# Overwrites by default, unlink for demonstration purposes
test_file_2 = config_dir / "test2.txt"
if test_file_2.exists():
    test_file_2.unlink()
test_file_2.write_text("Test file", "utf-8")

# Create and write bytes to file
# Overwrites by default
test_file_3 = config_dir / "test3.txt"
test_file_3.write_bytes(bytes([84, 101, 115, 116, 32, 102, 105, 108, 101]))
```

## `Path.cwd()`

Returns the current working directory (CWD).

The current working directory is the directory from which the Python process is executed, not necessarily the directory where the Python script is stored.

```python
cwd = Path.cwd()

print(cwd)
```

## `Path.home()`

Returns the current user's home directory.

```python
home = Path.home()

print(home)
```

## Creating paths

Use the `/` operator to join path components.

```python
config = home / ".config" / "nvim"

print(config)
```

The `/` operator is overloaded by `Path` to join paths correctly. It does not perform ordinary division.

### Checking if a path exists

```python
config.exists()   # Does the path exist?
config.is_dir()   # Is it a directory?
config.is_file()  # Is it a file?
```

These methods return Boolean values (`True` or `False`).

### Getting information about a path

```python
config.name    # nvim
config.parent  # /Users/tamasm/.config
config.suffix  # File extension, e.g. .txt
config.stem    # Filename without extension
```

| Attribute | Description | Example |
|---|---|---|
| `.name` | Final component of the path | `config.txt` |
| `.parent` | Immediate parent directory | `/home/user` |
| `.parents` | All parent directories | Sequence of parent paths |
| `.suffix` | File extension, including the dot | `.txt` |
| `.stem` | Filename without extension | `config` |
| `.parts` | Path components as a tuple | `('/', 'home', 'user')` |

Note: `.suffix` and `.stem` refer to the final filename, not the directory name. For example, `Path("archive.tar.gz").suffix` returns `.gz`, while `.stem` returns `archive.tar`.

## `Path.iterdir()`

Returns an iterator over the immediate contents of a directory.

```python
for item in config.iterdir():
    if item.is_dir():
        print("Dir: ", item)
    else:
        print("File: ", item)
```

Example directory:

```text
nvim/
├── init.lua
├── lazy-lock.json
├── lua/
│   ├── config/
│   └── plugins/
└── snippets/
```

Example output:

```text
File: /Users/tamasm/.config/nvim/init.lua
File: /Users/tamasm/.config/nvim/lazy-lock.json
Dir: /Users/tamasm/.config/nvim/lua
Dir: /Users/tamasm/.config/nvim/snippets
```

**Important:**
- `.iterdir()` only returns immediate contents.
- It does not enter subdirectories recursively.
- Each `item` is itself a `Path` object, so you can use methods like `.name`, `.suffix`, `.is_dir()`, and `.is_file()` on it.

## `Path.rglob()`

Finds matching files and directories recursively, including inside subdirectories.

```python
for item in config.rglob("*.lua"):
    print(item)
```

This finds all `.lua` files inside the `nvim` directory and its subdirectories.

Common patterns:

| Pattern | Meaning |
|---|---|
| `"*.lua"` | All Lua files |
| `"*.py"` | All Python files |
| `"*.conf"` | All `.conf` files |
| `"config*"` | Names starting with `config` |
| `"*"` | All entries |

Use `.glob()` instead of `.rglob()` when you only want to search the immediate directory.

---

## Working with the current Python file

### `__file__`

`__file__` is a special variable containing the path used to locate the current Python module.

It allows you to work with the directory where the script is located, regardless of the current working directory.

### Getting the current file's path

```python
print(__file__)
```

### `Path.parent`

Convert `__file__` into a `Path` object and use `.parent`.

```python
from pathlib import Path

file_path = Path(__file__).parent

print(file_path)
```

**Important distinction:**

- `Path.cwd()` returns the directory from which the Python process was launched.
- `Path(__file__).parent` returns the directory containing the current script.

### `Path.resolve()`

Get an absolute, normalized path

```python
file_path = Path(__file__).resolve().parent
```

Note: `__file__` is generally available when executing a Python file as a script or importing a module. It is usually not defined in interactive Python sessions or notebooks.

### `Path.parents`

`.parents` returns a special sequence containing all parent directories, starting with the immediate parent.

```python
from pathlib import Path

file_parents = Path(__file__).parents

print("Index 0: ", file_parents[0])  # Same as .parent
print("Index 1: ", file_parents[1])
print("Index 2: ", file_parents[2])
print("Index -1: ", file_parents[-1])

# Iterate over all parent directories
for parent in file_parents:
    print(parent)
```

For example, suppose `__file__` is:

```text
/Users/tamasm/projects/python/scripts/main.py
```

Output:

```text
Index 0: /Users/tamasm/projects/python/scripts
Index 1: /Users/tamasm/projects/python
Index 2: /Users/tamasm/projects
Index -1: /

/Users/tamasm/projects/python/scripts
/Users/tamasm/projects/python
/Users/tamasm/projects
/Users/tamasm
/Users
/
```

**Remember:**

- `.parent` returns one parent directory.
- `.parents` returns all parent directories.
- `.parents[0]` is equivalent to `.parent`.
- `.parents[1]` is two levels up.
- `.parents[-1]` is the filesystem root for an absolute path with parent directories.

`.parents` uses zero-based indexing, just like lists and tuples.

---

## Checking whether a path contains a name

There are several ways to check whether a path contains a particular name. The method you choose depends on what you want to check.

```python
from pathlib import Path

# Neovim configuration
conf = Path.home() / ".config" / "nvim"
```

### `.name` – Check the final path component

`.name` returns only the final component of the path.

```python
print(conf.name == "nvim")
```

Output:

```text
True
```

This checks whether the final directory or filename is exactly `"nvim"`.

### `.parts` – Check all path components

`.parts` returns a tuple containing all components of the path.

```python
print(conf.parts)
```

Output:

```python
('/', 'Users', 'tamasm', '.config', 'nvim')
```

You can use the `in` operator to check whether an exact component exists.

```python
print("tamasm" in conf.parts)
print(".config" in conf.parts)
print("hello" in conf.parts)
```

Output:

```text
True
True
False
```

This is useful when you want to check whether a particular directory or filename exists anywhere in the path.

### `.match()` – Check whether a path matches a pattern

Useful for wildcard pattern matching.

```python
print(conf.match("*/.config/*"))
print(conf.match("*/.config/hello"))
```

Output:

```text
True
False
```

Common wildcards:

| Wildcard | Meaning |
|---|---|
| `*` | Matches any number of characters |
| `?` | Matches exactly one character |
| `[abc]` | Matches one character from the specified set |

**Important:** `.match()` matches the path against a pattern, starting from the right-hand end of the path. It is not a general substring search.

### `str()` – Check for a substring (less recommended)

You can convert the entire path into a string and use `in`.

```python
print("config" in str(conf))
```

Output:

```text
True
```

However, this checks for a substring anywhere in the path, not an exact path component.

For example, it could also match a directory named `"configuration"`.

Prefer `.parts` when you want to check for an exact directory or filename component.

## `Path.mkdir()`

Creates a new directory.

```python
folder.mkdir()
```

**Useful arguments:**

| Argument | Description |
|---|---|
| `parents=True` | Creates missing parent directories |
| `exist_ok=True` | Doesn't raise an error if the directory already exists |

```python
# Create nested directories
path = home / "projects" / "python" / "scripts"
path.mkdir(parents=True, exist_ok=True)
```

Without `parents=True`, the operation fails if parent directories don't exist.

Without `exist_ok=True`, Python raises `FileExistsError` if the directory already exists.

## `Path.rmdir()`

Removes an **empty directory**.

```python
folder.rmdir()
```

- Only works on empty directories.
- Raises `OSError` if the directory contains files or other directories.
- Does not recursively delete directory contents.

## `Path.unlink()`

Deletes a file.

```python
file.unlink()
```

Equivalent to `rm` in Linux.

**Useful argument:**

`missing_ok=True` prevents an error if the file doesn't exist.

```python
file.unlink(missing_ok=True)
```

- Default: `missing_ok=False`.
- Intended for deleting files and symlinks, not directories.

## `Path.glob()`

Finds files and directories matching a specified pattern.

```python
for item in folder.glob("*.txt"):
    print(item)
```

Searches only the immediate directory, not its subdirectories.

**Common patterns:**

| Pattern | Meaning |
|---|---|
| `"*.txt"` | All `.txt` files |
| `"*.py"` | All Python files |
| `"config*"` | Names starting with `config` |
| `"*.conf"` | All `.conf` files |
| `"file?.txt"` | `?` matches exactly one character |
| `"*"` | All immediate entries |

**Find directories:**

```python
for item in folder.glob("*"):
    if item.is_dir():
        print(item)
```

## `Path.rename()`

Renames a file or directory.

**Rename a file:**

```python
file.rename(folder / "new_name.txt")
```

**Rename a directory:**

```python
folder.rename(home / "new-folder")
```

**Move a file:**

```python
file.rename(home / "Documents" / "example.txt")
```

Can rename or move files and directories.

**Important:** Behavior when the destination already exists can differ between operating systems. It can also fail when moving across filesystems. For general-purpose moving and copying, consider `shutil.move()` and `shutil.copy()`.

## `Path.resolve()`

Converts a path into an absolute, normalized path.

```python
path = Path("./scripts/../config/settings.txt")

print(path.resolve())
```

Example output:

```text
/home/tamas/config/settings.txt
```

Resolves:

- Relative paths into absolute paths.
- `.` (current directory).
- `..` (parent directory).
- Symbolic links by default.

**Useful argument: `strict`**

```python
path.resolve(strict=True)
```

| Value | Description |
|---|---|
| `strict=False` | Default. Doesn't require the target to exist |
| `strict=True` | Raises `FileNotFoundError` if the target doesn't exist |

**Example:**

```python
path = Path("../Documents/file.txt")

print(path.is_absolute())  # False

absolute = path.resolve()

print(absolute)
print(absolute.is_absolute())  # True
```

## `Path.touch()`

Creates an empty file at the specified path.

```python
from pathlib import Path

file = Path.home() / "python-test" / "example.txt"

file.touch()
```

Creates:

```text
python-test/
└── example.txt
```

**Useful argument: `exist_ok`**

```python
file.touch(exist_ok=True)
```

| Value | Behaviour |
|---|---|
| `exist_ok=True` | Doesn't raise an error if the file already exists (default) |
| `exist_ok=False` | Raises `FileExistsError` if the file already exists |

**Important:**
- The parent directory must already exist.
- `.touch()` creates an empty file if it doesn't exist.
- If the file already exists, `.touch()` updates its modification time by default.

## `Path.write_text()`

Creates a file and writes text into it.

```python
file = Path.home() / "python-test" / "example.txt"

file.write_text("Hello, world!")
```

Contents of `example.txt`:

```text
Hello, world!
```

**Important:**
- Creates the file if it doesn't exist.
- Overwrites the entire contents if the file already exists.
- The parent directory must already exist.
- Returns the number of characters written.

**Specify encoding:**

```python
file.write_text("Hello, world!", encoding="utf-8")
```

Using `encoding="utf-8"` is recommended when working with text files.

## `Path.write_bytes()`

Similar to `.write_text()`, but writes bytes instead of text.

```python
file = Path.home() / "python-test" / "example.bin"

file.write_bytes(b"Hello, world!")
```

**Important:**
- Creates the file if it doesn't exist.
- Overwrites existing contents.
- The parent directory must already exist.
- Requires a `bytes` object, usually written with the `b` prefix.
- Returns the number of bytes written.

## `pathlib` vs `os.path`

### Comparison

| `pathlib` | `os.path` | Description |
|---|---|---|
| `Path()` | — | Create a `Path` object |
| `Path.cwd()` | `os.getcwd()` | Get current working directory |
| `Path.home()` | `os.path.expanduser("~")` | Get home directory |
| `/` operator | `os.path.join()` | Join path components |
| `.exists()` | `os.path.exists()` | Check if path exists |
| `.is_file()` | `os.path.isfile()` | Check if path is a file |
| `.is_dir()` | `os.path.isdir()` | Check if path is a directory |
| `.name` | `os.path.basename()` | Get final path component |
| `.parent` | `os.path.dirname()` | Get parent directory |
| `.suffix` | `os.path.splitext()` | Get file extension (with `os.path`, returns a tuple) |
| `.stem` | `os.path.splitext()` | Get filename without extension (with `os.path`, returns a tuple) |
| `.resolve()` | `os.path.realpath()` | Resolve absolute path and symbolic links |
| `.relative_to()` | `os.path.relpath()` | Get relative path (different behaviour) |

### Key differences

| `pathlib` | `os.path` |
|---|---|
| Object-oriented | Function-based |
| Works with `Path` objects | Primarily works with strings |
| Uses `/` to join paths | Uses `os.path.join()` |
| Combines path manipulation and filesystem operations | Focuses on path manipulation |
| Generally more readable | Common in older Python code |

**-- Example: Joining paths --**

```python
from pathlib import Path
import os

# pathlib
config = Path.home() / ".config" / "nvim"

# os.path
home = os.path.expanduser("~")
config = os.path.join(home, ".config", "nvim")
```

**Remember:** `pathlib` works with `Path` objects, while `os.path` primarily works with strings.

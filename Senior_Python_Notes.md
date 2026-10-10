# Senior Python Notes for Data Engineering

These notes are focused only on Python topics that are useful for senior data engineering interviews and day-to-day work.

## Table of Contents

1. [Advanced Functions](#1-advanced-functions)
2. [Iterators and Generators](#2-iterators-and-generators)
3. [Context Managers](#3-context-managers)
4. [Working with Files](#4-working-with-files)
5. [CSV, JSON, and Compressed Files](#5-csv-json-and-compressed-files)
6. [Error Handling](#6-error-handling)
7. [Logging](#7-logging)
8. [Type Hints](#8-type-hints)
9. [Dataclasses](#9-dataclasses)
10. [Object Oriented Python](#10-object-oriented-python)
11. [Useful Standard Library Modules](#11-useful-standard-library-modules)
12. [Testing with Pytest](#12-testing-with-pytest)
13. [Packaging and Project Structure](#13-packaging-and-project-structure)
14. [Performance Basics](#14-performance-basics)
15. [Concurrency](#15-concurrency)
16. [Python for Data Work](#16-python-for-data-work)
17. [Clean Code Patterns](#17-clean-code-patterns)

## 1. Advanced Functions

### `*args`

`*args` is used when a function can accept any number of positional arguments.

```python
def add_numbers(*args):
    total = 0
    for number in args:
        total += number
    return total

print(add_numbers(1, 2, 3))  # 6
```

Simple meaning: use `*args` when you do not know how many normal values will be passed.

### `**kwargs`

`**kwargs` is used when a function can accept any number of keyword arguments.

```python
def print_user(**kwargs):
    for key, value in kwargs.items():
        print(key, value)

print_user(name="Ujjawal", role="Data Engineer")
```

Simple meaning: use `**kwargs` when you do not know how many named values will be passed.

### Closures

A closure is a function that remembers values from the place where it was created.

```python
def multiplier(x):
    def multiply(y):
        return x * y
    return multiply

double = multiplier(2)
print(double(5))  # 10
```

Here, `double` remembers that `x` was `2`.

### Decorators

A decorator adds extra behavior to a function without changing the function code directly.

```python
def log_function(func):
    def wrapper(*args, **kwargs):
        print(f"Running {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@log_function
def greet(name):
    return f"Hello {name}"

print(greet("Ujjawal"))
```

In data engineering, decorators are useful for logging, timing, retrying, and validating pipeline steps.

### Interview Notes

- `*args` collects positional arguments into a tuple.
- `**kwargs` collects keyword arguments into a dictionary.
- Decorators are common in frameworks and pipeline utilities.
- Closures are useful when one function needs to remember configuration.

## 2. Iterators and Generators

### Iterable

An iterable is something you can loop over.

Examples:

- List
- Tuple
- String
- Dictionary
- File object

```python
numbers = [1, 2, 3]

for number in numbers:
    print(number)
```

### Iterator

An iterator is an object that gives values one by one.

```python
numbers = [1, 2, 3]
iterator = iter(numbers)

print(next(iterator))  # 1
print(next(iterator))  # 2
print(next(iterator))  # 3
```

### Generator

A generator creates values lazily using `yield`.

```python
def read_numbers():
    yield 1
    yield 2
    yield 3

for number in read_numbers():
    print(number)
```

Simple meaning: a generator does not store all values in memory at once.

### Why Generators Matter in Data Engineering

Generators are useful when working with large data.

Instead of loading a huge file into memory, you can process one line at a time.

```python
def read_large_file(path):
    with open(path, "r") as file:
        for line in file:
            yield line.strip()
```

### Generator Expression

```python
squares = (x * x for x in range(10))

for value in squares:
    print(value)
```

This is like list comprehension, but lazy.

### Interview Notes

- List comprehension stores all values in memory.
- Generator expression produces values one by one.
- `yield` pauses a function and resumes it later.
- Generators help with memory-efficient data processing.

## 3. Context Managers

### What Is a Context Manager?

A context manager handles setup and cleanup automatically.

Most common example:

```python
with open("data.txt", "r") as file:
    content = file.read()
```

The file closes automatically after the `with` block.

### Custom Context Manager Using Class

```python
class FileManager:
    def __init__(self, path, mode):
        self.path = path
        self.mode = mode

    def __enter__(self):
        self.file = open(self.path, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

with FileManager("data.txt", "r") as file:
    print(file.read())
```

### Custom Context Manager Using `contextlib`

```python
from contextlib import contextmanager

@contextmanager
def managed_file(path, mode):
    file = open(path, mode)
    try:
        yield file
    finally:
        file.close()
```

### Interview Notes

- Context managers are used with `with`.
- They help avoid resource leaks.
- Common use cases: files, database connections, locks, temporary directories.

## 4. Working with Files

### Reading Full File

```python
with open("data.txt", "r") as file:
    text = file.read()
```

Good for small files.

### Reading Line by Line

```python
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())
```

Good for large files.

### Writing File

```python
with open("output.txt", "w") as file:
    file.write("Hello Ujjawal")
```

### Appending File

```python
with open("output.txt", "a") as file:
    file.write("\nNew line")
```

### File Modes

- `r`: read
- `w`: write and overwrite
- `a`: append
- `rb`: read binary
- `wb`: write binary

### Large File Rule

For large files, avoid this:

```python
data = file.read()
```

Prefer this:

```python
for line in file:
    process(line)
```

### Interview Notes

- Always prefer `with open(...)`.
- Read large files line by line.
- Use binary mode for images, parquet-like binary files, or compressed streams.

## 5. CSV, JSON, and Compressed Files

### Reading CSV

```python
import csv

with open("users.csv", "r", newline="") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row["name"])
```

`DictReader` returns each row as a dictionary.

### Writing CSV

```python
import csv

rows = [
    {"name": "Ujjawal", "role": "Data Engineer"},
    {"name": "Amit", "role": "Analyst"},
]

with open("users.csv", "w", newline="") as file:
    writer = csv.DictWriter(file, fieldnames=["name", "role"])
    writer.writeheader()
    writer.writerows(rows)
```

### Reading JSON

```python
import json

with open("config.json", "r") as file:
    config = json.load(file)
```

### Writing JSON

```python
import json

config = {"env": "dev", "batch_size": 1000}

with open("config.json", "w") as file:
    json.dump(config, file, indent=2)
```

### JSON Lines

JSON Lines means one JSON object per line. It is common in data pipelines.

```python
import json

with open("events.jsonl", "r") as file:
    for line in file:
        event = json.loads(line)
        print(event)
```

### Reading Gzip File

```python
import gzip

with gzip.open("events.jsonl.gz", "rt") as file:
    for line in file:
        print(line.strip())
```

### Interview Notes

- CSV is row-based text data.
- JSON is nested structured data.
- JSON Lines is better for streaming records.
- Compressed files should often be streamed instead of fully loaded.

## 6. Error Handling

### Basic `try except`

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

### Catching Exception Details

```python
try:
    result = int("abc")
except ValueError as error:
    print(error)
```

### Multiple Exceptions

```python
try:
    value = int("abc")
except ValueError:
    print("Invalid value")
except TypeError:
    print("Invalid type")
```

### Custom Exception

```python
class DataValidationError(Exception):
    pass

def validate_record(record):
    if "id" not in record:
        raise DataValidationError("Missing id")
```

### Exception Chaining

Exception chaining keeps the original error while raising a new one.

```python
try:
    int("abc")
except ValueError as error:
    raise DataValidationError("Invalid record") from error
```

### Retry Pattern

```python
import time

def retry_operation(operation, retries=3):
    for attempt in range(retries):
        try:
            return operation()
        except Exception:
            if attempt == retries - 1:
                raise
            time.sleep(1)
```

### Interview Notes

- Catch specific exceptions when possible.
- Do not silently ignore errors.
- Custom exceptions make pipeline failures clearer.
- Retries are useful for temporary failures, not bad data.

## 7. Logging

### Why Logging Matters

In real projects, `print()` is not enough. Logs help debug production jobs.

Use logging for:

- Job start and end
- Number of records processed
- Warnings
- Errors
- Retry attempts

### Basic Logging

```python
import logging

logging.basicConfig(level=logging.INFO)

logging.info("Job started")
logging.warning("Missing optional field")
logging.error("Job failed")
```

### Logger Object

```python
import logging

logger = logging.getLogger(__name__)

logger.info("Reading input file")
```

### Log Levels

- `DEBUG`: detailed information for debugging
- `INFO`: normal progress messages
- `WARNING`: something unexpected but not fatal
- `ERROR`: something failed
- `CRITICAL`: serious failure

### Logging with Variables

```python
records_count = 1000
logger.info("Processed %s records", records_count)
```

This is better than f-strings in logging because formatting can be delayed.

### Interview Notes

- Use `logging`, not `print()`, for production code.
- Log useful context.
- Avoid logging secrets like passwords, tokens, and keys.

## 8. Type Hints

### Basic Type Hints

```python
name: str = "Ujjawal"
age: int = 25
score: float = 91.5
is_active: bool = True
```

### Function Type Hints

```python
def add(a: int, b: int) -> int:
    return a + b
```

### Collection Type Hints

```python
names: list[str] = ["Ujjawal", "Amit"]
scores: dict[str, int] = {"math": 90}
ids: set[int] = {1, 2, 3}
point: tuple[int, int] = (10, 20)
```

### Optional

Use `Optional` when a value can be `None`.

```python
from typing import Optional

def find_user(user_id: int) -> Optional[str]:
    if user_id == 1:
        return "Ujjawal"
    return None
```

### Union

Use `Union` when a value can have more than one type.

```python
from typing import Union

def parse_id(value: Union[int, str]) -> int:
    return int(value)
```

Modern syntax:

```python
def parse_id(value: int | str) -> int:
    return int(value)
```

### TypedDict

`TypedDict` describes the shape of a dictionary.

```python
from typing import TypedDict

class UserRecord(TypedDict):
    id: int
    name: str
    email: str

def process_user(user: UserRecord) -> None:
    print(user["name"])
```

### Protocol

`Protocol` describes behavior instead of exact class.

```python
from typing import Protocol

class Writer(Protocol):
    def write(self, text: str) -> int:
        ...

def save(writer: Writer) -> None:
    writer.write("hello")
```

### Interview Notes

- Type hints improve readability and editor support.
- They do not enforce types at runtime by default.
- `TypedDict` is useful for dictionary-based records.
- `Protocol` is useful for flexible design.

## 9. Dataclasses

### What Is a Dataclass?

A dataclass is a simple way to create classes that mainly store data.

```python
from dataclasses import dataclass

@dataclass
class User:
    id: int
    name: str
    email: str

user = User(1, "Ujjawal", "ujjawal@example.com")
print(user.name)
```

Python automatically creates methods like `__init__()` and `__repr__()`.

### Default Values

```python
from dataclasses import dataclass

@dataclass
class JobConfig:
    batch_size: int = 1000
    retries: int = 3
```

### Frozen Dataclass

Frozen means values cannot be changed after creation.

```python
@dataclass(frozen=True)
class SourceConfig:
    path: str
    format: str
```

### `field(default_factory=...)`

Use `default_factory` for mutable defaults like lists.

```python
from dataclasses import dataclass, field

@dataclass
class Batch:
    records: list[dict] = field(default_factory=list)
```

### Interview Notes

- Dataclasses reduce boilerplate.
- Avoid mutable defaults like `records=[]`.
- Use `field(default_factory=list)` instead.
- Frozen dataclasses are useful for configuration.

## 10. Object Oriented Python

### Inheritance

Inheritance means one class gets behavior from another class.

```python
class Extractor:
    def extract(self):
        print("Extracting data")

class CsvExtractor(Extractor):
    pass
```

### Composition

Composition means one class uses another class.

```python
class FileReader:
    def read(self):
        return "data"

class Pipeline:
    def __init__(self, reader):
        self.reader = reader

    def run(self):
        data = self.reader.read()
        print(data)
```

Simple rule: prefer composition when you want flexible design.

### Abstract Base Class

An abstract class defines methods that child classes must implement.

```python
from abc import ABC, abstractmethod

class Extractor(ABC):
    @abstractmethod
    def extract(self):
        pass

class CsvExtractor(Extractor):
    def extract(self):
        return ["row1", "row2"]
```

### Magic Methods

Magic methods start and end with double underscores.

```python
class Dataset:
    def __init__(self, records):
        self.records = records

    def __len__(self):
        return len(self.records)

    def __str__(self):
        return f"Dataset with {len(self)} records"
```

### Interview Notes

- Inheritance means "is-a".
- Composition means "has-a".
- Composition is often easier to maintain.
- Abstract classes define required behavior.
- Magic methods make custom classes work naturally with Python.

## 11. Useful Standard Library Modules

### `pathlib`

Modern way to work with file paths.

```python
from pathlib import Path

path = Path("data/input.csv")

print(path.name)
print(path.suffix)
print(path.exists())
```

### `os`

Useful for environment variables and operating system tasks.

```python
import os

env = os.getenv("ENV", "dev")
```

### `sys`

Useful for command-line arguments and Python runtime details.

```python
import sys

print(sys.argv)
```

### `datetime`

Used for dates and times.

```python
from datetime import datetime, timezone

now = datetime.now(timezone.utc)
print(now.isoformat())
```

### `collections`

Useful data structures.

```python
from collections import Counter, defaultdict

counts = Counter(["a", "b", "a"])
print(counts)

groups = defaultdict(list)
groups["team"].append("Ujjawal")
```

### `itertools`

Useful for efficient looping.

```python
from itertools import islice

numbers = range(100)
first_five = list(islice(numbers, 5))
```

### `functools`

Useful for functional programming helpers.

```python
from functools import reduce

total = reduce(lambda a, b: a + b, [1, 2, 3])
```

### Interview Notes

- `pathlib` is preferred for paths.
- `collections.Counter` is useful for counting.
- `defaultdict` avoids manual key checks.
- `itertools` helps process data lazily.

## 12. Testing with Pytest

### Why Testing Matters

Testing makes sure your code works and keeps working after changes.

### Simple Function

```python
def add(a, b):
    return a + b
```

### Test Function

```python
def test_add():
    assert add(2, 3) == 5
```

Run tests:

```bash
pytest
```

### Fixtures

Fixtures provide reusable test setup.

```python
import pytest

@pytest.fixture
def sample_record():
    return {"id": 1, "name": "Ujjawal"}

def test_record_has_id(sample_record):
    assert sample_record["id"] == 1
```

### Parameterized Tests

Run the same test with multiple inputs.

```python
import pytest

@pytest.mark.parametrize(
    "value,expected",
    [
        ("10", 10),
        ("20", 20),
    ],
)
def test_parse_int(value, expected):
    assert int(value) == expected
```

### Mocking

Mocking replaces external calls during tests.

```python
from unittest.mock import Mock

api_client = Mock()
api_client.get_data.return_value = {"status": "ok"}

assert api_client.get_data()["status"] == "ok"
```

### Interview Notes

- Unit tests check small pieces of code.
- Fixtures reduce duplicate setup.
- Mocks avoid calling real APIs, databases, or files.
- Tests are very important for production data pipelines.

## 13. Packaging and Project Structure

### Simple Project Structure

```text
my_project/
  pyproject.toml
  README.md
  src/
    my_project/
      __init__.py
      main.py
      config.py
  tests/
    test_main.py
```

### Modules

A module is a Python file.

```text
utils.py
```

### Packages

A package is a folder containing Python modules.

```text
my_package/
  __init__.py
  reader.py
  writer.py
```

### Imports

```python
from my_project.config import load_config
```

### `pyproject.toml`

Modern Python projects often use `pyproject.toml` for configuration.

Example idea:

```toml
[project]
name = "my-project"
version = "0.1.0"
dependencies = []
```

### Virtual Environment

Create:

```bash
python -m venv .venv
```

Activate on Windows PowerShell:

```bash
.venv\Scripts\Activate.ps1
```

### Interview Notes

- Keep source code and tests separate.
- Use virtual environments per project.
- Avoid messy imports by using a clean package structure.

## 14. Performance Basics

### Time Complexity

Time complexity describes how runtime grows when input grows.

Common examples:

- `O(1)`: constant time
- `O(n)`: loop through all items
- `O(n^2)`: nested loop over same data
- `O(log n)`: repeatedly divide the problem

### List vs Set Lookup

List lookup is usually slower for membership checks.

```python
items = [1, 2, 3, 4]
print(4 in items)
```

Set lookup is usually faster.

```python
items = {1, 2, 3, 4}
print(4 in items)
```

### Memory Usage

This stores all values:

```python
squares = [x * x for x in range(1_000_000)]
```

This creates values lazily:

```python
squares = (x * x for x in range(1_000_000))
```

### Profiling Time

```python
import time

start = time.perf_counter()

# code to measure

end = time.perf_counter()
print(end - start)
```

### Interview Notes

- Use sets for fast membership checks.
- Avoid nested loops when a dictionary or set can solve the problem.
- Use generators for large data.
- Measure before optimizing.

## 15. Concurrency

### Why Concurrency?

Concurrency helps run multiple tasks during the same time period.

It is useful for:

- API calls
- File downloads
- Waiting for network responses
- CPU-heavy processing

### Threading

Threading is useful for I/O-bound work.

```python
from concurrent.futures import ThreadPoolExecutor

def fetch(url):
    return f"data from {url}"

urls = ["url1", "url2", "url3"]

with ThreadPoolExecutor(max_workers=3) as executor:
    results = list(executor.map(fetch, urls))
```

### Multiprocessing

Multiprocessing is useful for CPU-bound work.

```python
from multiprocessing import Pool

def square(x):
    return x * x

with Pool() as pool:
    results = pool.map(square, [1, 2, 3, 4])
```

### Async Basics

Async is useful for many waiting tasks, such as API calls.

```python
import asyncio

async def main():
    await asyncio.sleep(1)
    print("done")

asyncio.run(main())
```

### Interview Notes

- Threading: good for I/O-bound tasks.
- Multiprocessing: good for CPU-bound tasks.
- Async: good for many concurrent I/O tasks.
- Python has a GIL, so threads do not speed up CPU-heavy Python code much.

## 16. Python for Data Work

### Batch Processing Pattern

Process records in chunks instead of all at once.

```python
def chunks(records, size):
    for i in range(0, len(records), size):
        yield records[i:i + size]

for batch in chunks([1, 2, 3, 4, 5], 2):
    print(batch)
```

### Record Validation

```python
def validate(record):
    required_fields = ["id", "name"]

    for field in required_fields:
        if field not in record:
            raise ValueError(f"Missing field: {field}")
```

### Schema-Like Check

```python
def validate_user(record):
    if not isinstance(record.get("id"), int):
        raise ValueError("id must be int")
    if not isinstance(record.get("name"), str):
        raise ValueError("name must be str")
```

### Transform Function

```python
def transform_user(record):
    return {
        "id": record["id"],
        "name": record["name"].strip().title(),
        "email": record["email"].lower(),
    }
```

### Idempotent Thinking in Python

Idempotent means running the same code again should not create wrong duplicate results.

Simple example:

```python
def unique_records(records):
    seen = set()
    output = []

    for record in records:
        record_id = record["id"]
        if record_id not in seen:
            output.append(record)
            seen.add(record_id)

    return output
```

### Interview Notes

- Validate input before processing.
- Keep transformations as pure functions when possible.
- Process large data in chunks.
- Think about duplicate records and reruns.

## 17. Clean Code Patterns

### Use Small Functions

Bad:

```python
def run():
    # read, validate, transform, write, log, retry all together
    pass
```

Better:

```python
def read_data():
    pass

def validate_data(records):
    pass

def transform_data(records):
    pass

def write_data(records):
    pass
```

### Separate Config from Code

```python
import os

INPUT_PATH = os.getenv("INPUT_PATH", "data/input.csv")
BATCH_SIZE = int(os.getenv("BATCH_SIZE", "1000"))
```

### Avoid Hardcoding Secrets

Bad:

```python
api_key = "secret-key"
```

Better:

```python
import os

api_key = os.getenv("API_KEY")
```

### Pure Functions

A pure function gives the same output for the same input and does not change outside state.

```python
def clean_name(name):
    return name.strip().title()
```

Pure functions are easier to test.

### Interview Notes

- Keep functions focused.
- Avoid hardcoded secrets.
- Use environment variables for config.
- Write code that is easy to test and debug.

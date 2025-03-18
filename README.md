# fastxlsx

high performance python library to write xlsx file by rust pyo3

## Usage

```py
from fastxlsx import BookWriter

book = BookWriter(name="test.xlsx")

# first sheet with headers, 2 columns
book.add_sheet("my1", ["col1", "col2"])
book.add_column_str(0, ["hello", "world"])
book.add_column_str(0, ["hello", "world", "grey"])

# second sheet with headers, 2 columnds
book.add_sheet("test", [])
book.add_column_number(1, [i for i in range(10)])
book.add_column_number(1, [i * 10 for i in range(20)])

# save workbook
book.save()
```

## Development

```bash
# activate python environment
source ~/envs/jupy12/bin/activate
# install maturin
pip install --upgrade maturin

maturin init
# choose pyo3

# change Cargo.toml features to 
# features = ["abi3-py38"]

maturin develop

# begin release *whl
maturin build --release

# begin publish to pypi
maturin publish
```
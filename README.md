# Task_1_Cloude (Jupyter Notebook)

This repository contains a Jupyter Notebook solution for a recruitment task:
implementing `add_virtual_column(df, role, new_column)` that adds a calculated
column to a Pandas DataFrame using `+`, `-`, `*`.

## Requirements
- Python 3.9+
- pip

## Setup
```bash
git clone https://github.com/xenlish/Task_1_cloude.git
cd Task_1_cloude
pip install -r requirements.txt
```

## Usage Example

Open **Solution.ipynb** in Jupyter Notebook or JupyterLab and run all cells to load the function.  
Then you can use it as follows:

```python
import pandas as pd

# Example DataFrame
df = pd.DataFrame({
    "quantity": [10, 3],
    "price": [10, 1]
})

# Add calculated column
result = add_virtual_column(df, "quantity * price", "total")
print(result)
```

Expected output:
```
   quantity  price  total
0        10     10    100
1         3      1      3
```

## Testing

Inside **Solution.ipynb** you will also find inline test cases:

```python
# sum
df = pd.DataFrame([[1, 1]] * 2, columns=["label_one", "label_two"])
exp = pd.DataFrame([[1, 1, 2]] * 2, columns=["label_one", "label_two", "label_three"])
assert add_virtual_column(df, "label_one+label_two", "label_three").equals(exp)

# multiply
df = pd.DataFrame([[1, 1]] * 2, columns=["label_one", "label_two"])
exp = pd.DataFrame([[1, 1, 1]] * 2, columns=["label_one", "label_two", "label_three"])
assert add_virtual_column(df, "label_one * label_two", "label_three").equals(exp)

# invalid label
df = pd.DataFrame([[1, 2]] * 3, columns=["label_one", "label_two"])
assert add_virtual_column(df, "label_one + label_two", "label3").empty

print("✅ All inline tests passed")

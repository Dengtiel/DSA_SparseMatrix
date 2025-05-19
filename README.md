## Implementation Details

The `SparseMatrix` class uses a dictionary to store sparse data:
- Key: `(row, col)` tuple
- Value: The non-zero element value

This approach:
- Minimizes memory usage for sparse matrices
- Optimizes operations by only processing non-zero elements
- Provides O(1) lookup/insertion for specific elements
- Enables efficient iteration over non-zero elements

The core operations (add, subtract, multiply) follow standard matrix algorithms but skip zero-value computations for performance.# Sparse Matrix Operations

A Python library for efficient sparse matrix operations that conserves memory by storing only non-zero elements.

## Overview

The `SparseMatrix` class uses a dictionary-based implementation to perform matrix operations efficiently:

- Addition
- Subtraction
- Multiplication

## Features

- Memory-efficient sparse representation (only stores non-zero values)
- File I/O with standard matrix format support
- Automatic file discovery and matrix operation selection
- Robust error handling and validation

## Installation

```bash
git clone https://github.com/Dengtiel/DSA_SparseMatrix.git
cd DSA_SparseMatrix
```

## Usage

### Command Line Interface

```bash
python main.py
```

The program automatically:
1. Finds matrix files in `sample_inputs/`
2. Prompts for operation selection
3. Performs calculation and saves the result

### File Format

```
rows=<number_of_rows>
cols=<number_of_columns>
(<row>, <col>, <value>)
(<row>, <col>, <value>)
...
```

Example (3×3 matrix with three non-zero values):
```
rows=3
cols=3
(0, 0, 5)
(1, 2, 3)
(2, 1, 7)
```
# Perform operations
sum_matrix = matrix1.add(matrix2)
diff_matrix = matrix1.subtract(matrix2)
prod_matrix = matrix1.multiply(matrix2)  # Requires compatible dimensions

# Output result
print(sum_matrix)
```

## Project Structure

```

DSA_SparseMatrix/
├── main.py              # Main program entry point
├── sparse_matrix.py     # Core SparseMatrix implementation
├── utils.py             # Utility functions(empty)
├── sample_inputs/       # Sample matrix files
│   ├── matrix1.txt
│   ├── matrix2.txt
│   └── matrix3.txt
└── __pycache__/         # Python cache directory
```

## API Reference

```python
# Create a matrix
matrix = SparseMatrix(rows, cols)

# Load from file
matrix = SparseMatrix.from_file(filepath)

# Access/modify elements
value = matrix.get_element(row, col)  # Returns 0 if not set
matrix.set_element(row, col, value)   # Removes element if value is 0

# Matrix operations
result = matrix1.add(matrix2)         # Matrices must have same dimensions
result = matrix1.subtract(matrix2)    # Matrices must have same dimensions
result = matrix1.multiply(matrix2)    # matrix1.cols must equal matrix2.rows
```

The implementation validates:
- Matrix dimension compatibility
- Proper file formatting
- Index boundaries
- Element format integrity

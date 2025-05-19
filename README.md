## Implementation Details

The `SparseMatrix` class uses a dictionary-based approach that:
- Stores only non-zero elements as `(row, col): value` pairs
- Optimizes memory usage for large sparse matrices
- Provides efficient operations without processing zero elements
- Uses no built-in template libraries or matrix packages

The implementation follows mathematical rules for matrix operations:
- Addition/subtraction requires identical dimensions
- Multiplication requires the first matrix's column count to equal the second matrix's row count# Sparse Matrix Operations

A Python implementation for efficient sparse matrix operations designed for Data Structures and Algorithms coursework. This implementation optimizes both memory usage and runtime performance for large matrices.

## Assignment Overview

This project satisfies the requirements for Programming Assignment 2: Sparse Matrix in the Data Structures and Algorithms for Engineers course. It implements:

1. Memory-efficient sparse matrix representation
2. Matrix loading from standardized text files
3. Core matrix operations (addition, subtraction, multiplication)
4. Proper validation and error handling

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

## File Format

The program processes sparse matrix files in the following format:
```
rows=<number_of_rows>
cols=<number_of_columns>
(<row>, <col>, <value>)
(<row>, <col>, <value>)
...
```

Example:
```
rows=8433
cols=3180
(0, 381, -694)
(0, 128, -838)
(0, 639, 857)
```

Notes:
- Whitespace is ignored
- All values must be integers
- Only specified positions have non-zero values
- Input validation ensures proper formatting

## Project Structure

```
DSA_SparseMatrix/
├── main.py              # Main program entry point
├── sparse_matrix.py     # Core SparseMatrix implementation
├── utils.py             # Empty placeholder file
├── sample_inputs/       # Sample matrix files
│   ├── matrix1.txt
│   ├── matrix2.txt
│   └── matrix3.txt
└── __pycache__/         # Python cache directory
```

## API Reference

The `SparseMatrix` class provides the following functionality:

```python
# Constructor
matrix = SparseMatrix(rows, cols)  # Create empty matrix with dimensions

# Class method for loading from file
matrix = SparseMatrix.from_file(filepath)

# Element access/modification
value = matrix.get_element(row, col)  # Returns 0 for unset positions
matrix.set_element(row, col, value)   # Removes element if value is 0

# Matrix operations
result = matrix1.add(matrix2)         # Raises ValueError if dimensions mismatch
result = matrix1.subtract(matrix2)    # Raises ValueError if dimensions mismatch
result = matrix1.multiply(matrix2)    # Raises ValueError if incompatible dimensions
```

# Sparse Matrix Operations

A Python library for efficient sparse matrix operations. This project provides a memory-efficient implementation for large matrices that contain mostly zero values.

## Overview

The `SparseMatrix` class implements a dictionary-based sparse matrix representation, storing only non-zero elements to conserve memory. The implementation supports common matrix operations:

- Addition
- Subtraction
- Multiplication

## Features

- Memory-efficient sparse matrix representation
- File I/O support for loading and saving matrices
- Core matrix operations (add, subtract, multiply)
- Automatic file discovery and operation selection
- Comprehensive error handling and validation

## Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/sparse-matrix.git
cd sparse-matrix
```

No additional dependencies are required beyond the Python standard library.

## Usage

### Command Line Interface

Run the main script to perform operations on matrices:

```bash
python main.py
```

The program will:
1. Automatically search for matrix files in the `sample_inputs/` directory
2. Display available operations (Add, Subtract, Multiply)
3. Prompt you to select an operation
4. Perform the operation and save the result

### File Format

Matrix files should follow this format:
```
rows=<number_of_rows>
cols=<number_of_columns>
(<row>, <col>, <value>)
(<row>, <col>, <value>)
...
```

Example:
```
rows=3
cols=3
(0, 0, 5)
(1, 2, 3)
(2, 1, 7)
```

This represents a 3×3 matrix with values 5 at (0,0), 3 at (1,2), and 7 at (2,1). All other positions contain zeros.

### Code Example

```python
from sparse_matrix import SparseMatrix

# Create matrices
matrix1 = SparseMatrix(3, 3)
matrix1.set_element(0, 0, 5)
matrix1.set_element(1, 2, 3)

matrix2 = SparseMatrix(3, 3)
matrix2.set_element(0, 0, 2)
matrix2.set_element(2, 1, 4)

# Add matrices
result = matrix1.add(matrix2)

# Print result
print(result)
```

### Loading from Files

```python
from sparse_matrix import SparseMatrix

# Load matrices from files
matrix1 = SparseMatrix.from_file("sample_inputs/matrix1.txt")
matrix2 = SparseMatrix.from_file("sample_inputs/matrix2.txt")

# Multiply matrices
result = matrix1.multiply(matrix2)

# Save result
with open("result.txt", "w") as f:
    f.write(str(result))
```

## Project Structure

```
sparse-matrix/
├── main.py              # Main program entry point
├── sparse_matrix.py     # Core SparseMatrix implementation
├── utils.py             # Utility functions (empty placeholder)
├── sample_inputs/       # Directory containing sample matrix files
│   ├── matrix1.txt
│   └── matrix2.txt
└── __pycache__/         # Python cache directory
```

## API Documentation

### SparseMatrix Class

#### Constructor

```python
SparseMatrix(rows, cols)
```
- `rows` (int): Number of rows in the matrix
- `cols` (int): Number of columns in the matrix

#### Class Methods

```python
SparseMatrix.from_file(filepath)
```
- Loads a matrix from a file in the specified format
- `filepath` (str): Path to the matrix file

#### Instance Methods

```python
get_element(row, col)
```
- Returns the value at the specified position (returns 0 for unset elements)
- `row` (int): Row index
- `col` (int): Column index

```python
set_element(row, col, value)
```
- Sets the value at the specified position
- Automatically removes the element if value is 0
- `row` (int): Row index
- `col` (int): Column index
- `value` (int): Value to set

```python
add(other)
```
- Adds this matrix with another matrix
- Returns a new SparseMatrix instance
- `other` (SparseMatrix): Matrix to add

```python
subtract(other)
```
- Subtracts another matrix from this matrix
- Returns a new SparseMatrix instance
- `other` (SparseMatrix): Matrix to subtract

```python
multiply(other)
```
- Multiplies this matrix with another matrix
- Returns a new SparseMatrix instance
- `other` (SparseMatrix): Matrix to multiply

## Error Handling

The implementation includes validation for:
- Matrix dimension mismatches
- File format errors
- Out-of-bounds indices
- Invalid element formats

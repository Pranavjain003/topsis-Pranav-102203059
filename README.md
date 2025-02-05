# TOPSIS Implementation Package

This package implements the **Technique for Order Preference by Similarity to Ideal Solution (TOPSIS)**, a multi-criteria decision-making method widely used in ranking and evaluation problems.

---

## What is TOPSIS?

TOPSIS is a decision-making method that ranks alternatives based on their closeness to the ideal solution and distance from the worst solution. It is commonly used in scenarios involving multiple criteria and alternatives.

---

## Installation

To install the package from PyPI, run the following command:

```bash
pip install topsis-Pranav-102203059
```
---
## Usage

After installation, you can use the package via the command line.

### Command Line Syntax:

```bash
topsis <InputDataFile> <Weights> <Impacts> <ResultFileName>
```

### Parameters:
- **`<InputDataFile>`**: Path to the input file (e.g., `data.csv` or `data.xlsx`) containing the dataset.
  - The file must have:
    - At least 3 columns.
    - First column for the names/identifiers (e.g., alternatives like M1, M2, etc.).
    - Remaining columns with numeric values for criteria.

- **`<Weights>`**: Comma-separated weights for the criteria (e.g., `"1,1,1,2"`).

- **`<Impacts>`**: Comma-separated impacts for the criteria. Use `+` for positive impact and `-` for negative impact (e.g., `"+,+,-,+"`).

- **`<ResultFileName>`**: Path for the output file to save the result (e.g., `result.csv`).

---

### Example Usage:

1. **Input File**: `102203059-data.xlsx`
   ```
   Fund Name, P1, P2, P3, P4, P5
   M1, 0.84, 0.71, 6.7, 42.1, 12.59
   M2, 0.91, 0.83, 7.0, 31.7, 10.11
   M3, 0.79, 0.62, 4.8, 46.7, 13.23
   ```

2. **Command**:
   ```bash
   topsis 102203059-data.xlsx "1,1,1,1,2" "+,+,-,+,+" 102203059-result.csv
   ```

3. **Output File**: `102203059-result.csv`
   ```
   Fund Name, P1, P2, P3, P4, P5, Topsis Score, Rank
   M1, 0.84, 0.71, 6.7, 42.1, 12.59, 0.7523, 1
   M2, 0.91, 0.83, 7.0, 31.7, 10.11, 0.6321, 2
   M3, 0.79, 0.62, 4.8, 46.7, 13.23, 0.5809, 3
   ```

---

## How It Works

1. **Normalization**:
   - The criteria values are normalized using vector normalization

2. **Weight Application**:
   - Each normalized value is multiplied by its respective weight

3. **Determine Ideal Best and Worst**:
   - **Ideal Best (A⁺)**:
     - Maximum value for positive impact (`+`).
     - Minimum value for negative impact (`-`).
   - **Ideal Worst (A⁻)**:
     - Minimum value for positive impact (`+`).
     - Maximum value for negative impact (`-`).

4. **Calculate Distances**:
   - Euclidean distance from the ideal best and worst

5. **Calculate TOPSIS Score**:
   - Calculate closeness to the ideal solution

6. **Rank Alternatives**:
   - Rank alternatives based on the TOPSIS score in descending order.

---

## Dependencies

Ensure the following Python libraries are installed:
- `pandas`
- `numpy`

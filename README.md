# RV-Sparse Assignment

My solution for the RV-Sparse coding challenge.

## What it does

`sparse_multiply` does two things:

1. Goes through the matrix `A` row by row and picks out the non-zero
   numbers. It puts the values in `values`, the column of each value in
   `col_indices`, and the index where each row starts in `row_ptrs`.
   This is the CSR format. It also writes the total count into
   `out_nnz`.
2. Once the CSR is built, it does `y = A * x` by looping over each row
   and summing `values[k] * x[col_indices[k]]` for the non-zeros in
   that row.

No `malloc` or `calloc` is used inside the function. All the buffers
are passed in by the caller, which was the main constraint of the
challenge.

## Build and run

```
gcc -o run challenge.c -lm
./run
```

The test harness runs 100 random tests and prints PASS or FAIL for each
one. All 100 pass on my machine.

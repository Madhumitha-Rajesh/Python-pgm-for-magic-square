# Python-pgm-for-magic-square

import numpy as np

order = int(input("Enter order of magic square (order must be odd): "))

# If even number is given, increment it by 1
if order % 2 == 0:
    order += 1
    print("Given order is even so it is incremented by 1.")

magic = np.zeros((order, order), dtype=int)

row = 0
col = order // 2

for num in range(1, order * order + 1):
    magic[row][col] = num

    prev_row = row
    prev_col = col

    # Move up and right
    row -= 1
    col += 1

    # Wrap around
    if row < 0:
        row = order - 1
    if col == order:
        col = 0

    # If cell already filled, move down instead
    if magic[row][col] != 0:
        row = (prev_row + 1) % order
        col = prev_col

print("\nGenerated Magic Square:\n")

for r in range(order):
    print("|", end="")
    for c in range(order):
        print(f"{magic[r][c]:4d} |", end="")
    print()
    print("-" * (6 * order))


Output-

Enter order of magic square (order must be odd): 5

Generated Magic Square:

|  17 |  24 |   1 |   8 |  15 |
------------------------------
|  23 |   5 |   7 |  14 |  16 |
------------------------------
|   4 |   6 |  13 |  20 |  22 |
------------------------------
|  10 |  12 |  19 |  21 |   3 |
------------------------------
|  11 |  18 |  25 |   2 |   9 |
------------------------------




# CS475-MiniMFE

## ToyMFE

#### v1
* This is the original version of the program

#### mod2
* Memory allocation reduced from `N^2` to `2N`
* Memory macro modified so that `T(i,j)` maps to `T[(i)%2][j]`

#### Nmem
* Memory allocation reduced from `2N` to `N`
* Memory macro modified so that `T(i,j)` maps to `T[-(i)+j]`

#### tile
* Tiles the main computation loops


## MiniMFE

#### v1
* This is the original version of the program

#### readable
* This is semantically the same as the original version
* Replaces the computation macros with their corresponding definitions
* Uses a decrementing loop counter for the outer loop which improves readability

#### verbose
* This version will print the reads and writes to the H and T structures to aid in observing the memory access pattern

#### Nmem
* This version allocates only N+1 memory for H by overwriting values that are no longer needed
* Now updated so that the writes are schedule independent

#### Tile
* Tiles the inner loops
* Rectangular tiles, width > height

#### transpose
* Makes a copy of the T array that is transposed in T2.
* The k/c3 innermost loop uses T2 for column dependencies.

#### transpose1x
* Stores transposed copy of T array in the lower triangle of T.
* Similar performance but saves space from initial allocation

#### swapJK
* Swaps the two innermost loops j and k. Renamed from c2, c3. 

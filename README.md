# Red and Green Balls

 #### You have a square grid (NxN). Each cell of the grid has either a red ball or a green ball. Your job is to arrange the balls in such a way that all the red balls are either on or below the main diagonal. The main diagonal starts from cell 1x1 and ends at cell NxN. You have only one move which is to swap adjacent rows. You need to achieve the final arrangement in minimal number of moves. If it is not possible to come to a resolution by swapping then print -1


##### Input:
    First line of input is the number of rows in grid. Rest are the lines in the grid
##### Ouput:
    Minimum number of moves



First, let's consider the input:


```
5
GGRRG
GRRRG
RGGGG
RGGGG
RGRGG
```

The first line contains an integer `n` which is the size of the square grid.

The next `n` lines contain `n` characters each, representing the colors of the cells in the grid.


Now let's step through the code:

The code reads the integer `n` from the first line of input and initializes a 2D character array grid of size `n x n`. It then reads `n` lines of input, converts each line to a character array, and stores it in grid.
```java

Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
sc.nextLine();
char[][] grid = new char[n][n];
for (int i = 0; i < n; i++) {
    grid[i] = sc.nextLine().toCharArray();
}

```
After this, grid contains the following cells:

```

 G  G  R  R  G 
 G  R  R  R  G 
 R  G  G  G  G 
 R  G  G  G  G 
 R  G  R  G  G 
 
```
The code then calls the `red()` method, which determines the position of rightmost red ball in each row of grid and stores the difference between the index of the diagonal cell and the rightmost red ball index   in `redCount[]`.
```java
int redCount[] = new int[n];
red(grid,redCount,n);
```

```java
public static void red(char[][] grid,int[] redCount,int n)
        {
        for (int i = 0; i < n; i++) {
            for (int j = n-1; j>=0; j--) {
                if (grid[i][j] == 'R') {
                    redCount[i]=i-j;
                    break;
                }}}
            System.out.println("Original Array: " + Arrays.toString(redCount));
        }
        
 ```
 for eg. in `grid[i][j]`
```
                                    diagonal-index (i)|  rightmost red ball - index (j)|   difference:redCount[i]=i-j
                                 --------------------------------------------------------------------------------------
 ##G   G    R   *R*   G      -->        ##G  -   0    |       *R*           -  3       |             -3
  G   ##R   R   *R*   G      -->        ##R  -   1    |       *R*           -  3       |             -2
 *R*   G   ##G   G    G      -->        ##G  -   2    |       *R*           -  0       |              2
 *R*   G    G   ##G   G      -->        ##G  -   3    |       *R*           -  0       |              3
  R    G   *R*   G   ##G     -->        ##G  -   4    |       *R*           -  2       |              2
 
```
 
After this, `redCount[]` contains the following values:

```csharp

[-3, -2, 2, 3, 2]
```
The code checks if the sum of the values in `redCount[]` is negative. If it is, it means that there are more red cells on the right side of the grid than on the left, so it prints `-1` and exits. Otherwise, it enters a loop to perform swaps until there are no negative values in `redCount[]`.

```java

int sum=0;
int swap=0;
for(int i=0;i<n;i++){
    sum=sum+redCount[i];
}
if(Math.abs(sum)!=sum)
   System.out.println(-1);
else {
    while(ifAnyNegativeValue(redCount,n)){
        swapper(grid,redCount,n);
        red(grid,redCount,n);
        swap++;
    }
}

```


If the sum of the values in `redCount[]` were positive, the code would enter the loop and call the `swapper()` method, which swaps rows of the grid to move red cells to the left. The `red()` method is then called again to update `redCount[]`. This loop continues until there are no negative values in `redCount[]`.

```java
public static boolean ifAnyNegativeValue(int[] redCount, int n) {
    boolean found = false;
    for (int i = redCount.length - 1; i >= 0; i--) {
        if (redCount[i] < 0) {
            found = true;
        }
    }
    return found;
}
```
This function checks whether any element in the `redCount[]` array is negative or not. It takes an integer array `redCount[] ` and an integer `n` as input and returns a boolean value of `true` if any element in the `redCount[]` array is negative; otherwise, it returns `false`.

```java
public static void swapper(char[][] grid, int[] redCount, int n) {
    boolean found = false;
    char temp[][] = new char[n][n];
    for (int i = redCount.length - 1; i >= 0; i--) {
        if (redCount[i] < 0) {
            for (int j = i; j >= 0; j--) {
                if (redCount[j] < 0) {
                    if (redCount[j + 1] != 0) {
                        temp[i] = grid[j + 1];
                        grid[j + 1] = grid[i];
                        grid[i] = temp[i];
                        found = true;
                        break;
                    }
                    if (redCount[j + 1] == 0) {
                        temp[i] = grid[j + 2];
                        grid[j + 2] = grid[i + 1];
                        grid[i + 1] = temp[i];
                        found = true;
                        break;
                    }
                }
            }
            if (found) {
                break;
            }
        }
    }
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            System.out.print(grid[i][j]);
        }
        System.out.println("");
    }
}

```
This function swaps the rows in the `grid[][]` array if there are negative elements in the `redCount[]` array. It takes a 2D character array `grid[][]`, an integer array `redCount[][]`, and an integer `n` as input. The function uses a temporary 2D character array `temp` to store the values while swapping the rows. It checks for negative elements in the `redCount[]` array using two nested for loops and swaps the rows accordingly. If the swap is successful, the function breaks out of the loop using the found boolean flag. Finally, the function prints the swapped `grid[][]` array.


If the sum of the values in `redCount[]` is not negative, the code prints the number of swaps performed.

```java
System.out.println(swap);

```

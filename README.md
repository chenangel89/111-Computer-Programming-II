# 111-Computer-Programming-II

## Homework 2

### 471	Real Wordle

### 473	String sorting by index

### 472	Joe's Bag

### 474	Number Divider
```c
#include<stdio.h>
#include<stdlib.h>

#define N 201

int main()
{
    int m, n;
    int dp[N][N] = {0};
    scanf("%d%d", &m, &n);
    dp[0][0] = 1;
    for(int i = 0; i <= m; i++) {
        for(int j = 1; j <= n; j++) {
            dp[i][j] = dp[i][j - 1];
            if (i >= j) dp[i][j] += dp[i - j][j];
        }
    }
    printf("%d\n", dp[m][n]);
    return 0;
}
```

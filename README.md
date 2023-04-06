# 111-Computer-Programming-II

## Homework 2

### 471	Real Wordle

### 473	String sorting by index

### 472	Joe's Bag
[題目](https://noj.tw/course/111-Computer-Programming-II/problem/472)
```c
#include <stdio.h>
#include <string.h>

int main() {
    int n, m, i, j;
    scanf("%d", &n);
    int coins[n];
    for (i = 0; i < n; i++) {
        scanf("%d", &coins[i]);
    }
    scanf("%d", &m);
    int dp[m+1];
    memset(dp, 0, sizeof(dp));
    dp[0] = 1;
    for (i = 0; i < n; i++) {
        for (j = m; j >= coins[i]; j--) {
            dp[j] += dp[j-coins[i]];
        }
    }
    printf("%d\n", dp[m]);
    return 0;
}

```
[題解](https://github.com/chenangel89/111-Computer-Programming-II/blob/main/%23472%09Joe's%20Bag.md)

### 474	Number Divider
[題目](https://noj.tw/course/111-Computer-Programming-II/problem/474)
```c
#include<stdio.h>
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
[題解](https://github.com/chenangel89/111-Computer-Programming-II/blob/main/%23474%20-%20Number%20Divider.md)

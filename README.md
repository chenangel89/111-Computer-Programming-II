# 111-Computer-Programming-II

## Homework 2

### 471	Real Wordle

### 473	String sorting by index

[題目](https://noj.tw/course/111-Computer-Programming-II/problem/473)

```c
#include <stdio.h>
#include <string.h>

#define MAX_LEN 40 // 字串的最大長度
#define NUM_STRS 12 // 字串的數量

int main() {
    char zodiac[NUM_STRS][MAX_LEN];
    int index[NUM_STRS];

    // 讀入所有的字串
    for (int i = 0; i < NUM_STRS; i++) {
        scanf("%s", zodiac[i]);
        index[i] = i;
    }

    // 對所有的字串進行排序，同時更新編號序列
    for (int i = NUM_STRS-2; i >= 1; i--) {
        for (int j = 0; j <= i; j++) {
            if (strcmp(zodiac[j], zodiac[j+1]) > 0) {
                // 交換兩個字串

                char temp[MAX_LEN];
                strcpy(temp, zodiac[j]);
                strcpy(zodiac[j], zodiac[j+1]);
                strcpy(zodiac[j+1], temp);

                // 更新編號序列
                int tempIndex = index[j];
                index[j] = index[j+1];
                index[j+1] = tempIndex;
            }
        }
    }

    // 輸出排序後的編號
    for (int i = 0; i < NUM_STRS; i++) {
        printf("%d\n", index[i]);
    }

    return 0;
}

```

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

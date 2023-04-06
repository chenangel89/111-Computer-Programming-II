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
* 初始化 dp 陣列
```c
    int dp[m+1];
    memset(dp, 0, sizeof(dp));
    dp[0] = 1;
```
這裡宣告了一個長度為 m+1 的整數數組 dp，並使用 memset 函數將其所有元素初始化為 0。接著將 dp[0] 初始化為 1，這是為了後面的動態規劃過程中方便計算。  

* 動態規劃
```c
    for (i = 0; i < n; i++) {
        for (j = m; j >= coins[i]; j--) {
            dp[j] += dp[j-coins[i]];
        }
    }

```
這裡使用了兩個 for 迴圈進行動態規劃。外層迴圈用來遍歷硬幣面額，內層迴圈用來更新 dp 陣列。對於每種硬幣面額 coins[i]，內層迴圈從 m 開始倒序遍歷到 coins[i]，將 dp[j-coins[i]] 加到 dp[j] 上，表示使用硬幣 coins[i] 之後，還需要 dp[j-coins[i]] 張硬幣才能湊滿 j 元的找零金額。







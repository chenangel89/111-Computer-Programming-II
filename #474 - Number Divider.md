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
<tr><th>600</th><th>510</th><th>420</th><th>330</th><th>222</th><th>321</th><th>411</th></tr>
<tr><td>60</td><td>51</td><td>42</td><td>33</td><td>111</td><td>210</td><td>300</td></tr>

600 510 420 330 222 321 411  
60  51  42  33  111 210 300  
* 組合數字中有0可視為沒有0，將63換成62 --> dp[i][j - 1]  
* 當組合中沒有0時可將組合中的數字全部減去1，其方法數相同(全減1後須拆分的數為 i-j ) --> dp[i - j][j]  

所以狀態轉移方程則是  
dp[i][j] = dp[i][j - 1] + dp[i - j][j]  

* 初始化  
當拆分0的時候,總共能拆分0次,那麼就有一種拆分方法,則是什麼都不拆  
dp[0][0] = 1  
————————————————  
參考來源：[原文鏈接](https://blog.csdn.net/ghost_him/article/details/123055311)  

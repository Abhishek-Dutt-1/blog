---
layout: post
title:  "Coin Change (Minimum)"
date:   2020-08-31 21:21:00 +0530
categories: dynamic_programming leetcode_medium java
---

_Type: Minimum (Maximum) Path to Reach a Target_
<hr/>


## Problem:

*Source: [LeetCode](https://leetcode.com/problems/coin-change/)*

You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. 

If that amount of money cannot be made up by any combination of the coins, return -1.

**Example 1:**
```
Input: coins = [1, 2, 5], amount = 11
Output: 3 
Explanation: 11 = 5 + 5 + 1
```

**Example 2:**
```
Input: coins = [2], amount = 3
Output: -1
```
Note:
You may assume that you have an infinite number of each kind of coin.

<br/> <br/>

<hr/>

**Contents:** <br/>
- Solution (Using 2D memo array)
  - Step 1: Coin Three
  - Step 2: Coin Three and Five
  - Step 3: Coin Three, Five and Two
- Java code
  - Complexity

## Solution (Using 2D memo array):

Let's work through an example case: <br/>
Coins given are of denominations **[3, 5, 2]** and amount to be made up is **8**.

### Step 1: Coin Three

Instead of using all 3 coins, we start with only the **first** coin (of denomination Three).

Also, instead of making up the given amount, we start by finding the minimum number of coins needed to make amounts **0**, then **1**, then **2**, and so on till **8**.

We tabulate the result in a 2D array where:
- the row labels indicate the coin value
- the columns labels indicate the amounts from 0 to 8
- Number in each cell **(i, j)** is minimum number of coins needed to make amount **j**, using all coins uptill **i**.
- Where it is not possible to make up the exact amount we mark it as **∞**. <br/>

The First row is a special row, with all values as ∞. <br/>
i.e. if we had no coins, we will take minimum ∞ number of coins to make up any amount. <br/>
This extra row simplifies the code. <br/>

The amount 0 needs 0 minimum coins, hence its value is 0. <br/>
This is true even if we were using any number of coins.

```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

For row **Three**, we cannot make up amounts 1 and 2 using only coin Three (since 3 > 1 and 3 > 2), so we copy the cell above. <br/>
Also, we cannot make up the amounts 4, 5, 7 and 8 using Three coins. <br/>
Only the amounts 3 and 6 can be made up by 1 and 2 coins of denomination Three. <br/>

### Step 2: Coin Three and Five:

Now we assume we have one more coin (of denomination Five) and we add a third row to the array.

Again, we fill the second row with minimum number of coins needed to make up the amounts from **0 to 8**, but this time we have two coins.

For amounts 1 to 4 we cannot use the Five coin, so it doesn't matter if we had the Five or not. <br/>
Its same as having just the Three coin. <br/>
So minimum number of coins needed for 1 to 4 will be exactly same as the Three row. <br/>

```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Five  │ 0 │ ∞ │ ∞ │ 1 │ ∞ │   │   │   │   │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

For remaining cells we will have to see:
- is using the Five coin to make up the amount takes minimum number of coins
- or have we got the amount in lesser number of coins already in the previous rows

So for **amount 5**, it will take 1 Five coin, while it cannot me made up by Three coin (∞ in previous row), so we mark it as 1

So for **amount 6**, it will take 1 Five coin, and the remaining amount will 1 (= 6 - 5).
- We see in the same row, column corresponding to amount 1 is ∞
- i.e. if we use Five coin, we cannot make up the amount 6
- So this is the case where it does not matter if we have or do not have the Five, so we copy the value from the previous row.

For **amount 7**: We try using Five, but we see the remaining amount 2 (= 7 - 5) cannot be made up (since row Five and column 2 is ∞), so we copy the value from the row above it.

For **amount 8**: 
- We try using Five, and see remaining amount 3 (= 8 - 5) can be made by using minimum one coin (as indicated by the 1 in the row Five under column 3)
- That means if we use Five, we can make it in 1 Five coin + as many minimum coins needed for making 3.
- i.e. we can make 8 in 1 + 1 = 2 coins
- But were we able to make 8 by using lesser coins earlier? No, as indicated by ∞ in previous row for same amount 8.
- So we put 2 under 8

```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Five  │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ 1 │ 2 │ ∞ │ 2 │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

### Step 3: Coin Three, Five and Two:

Now we assume we have 3 coins of denominations Three, Five and Two.

Again, amount 0 will need 0 coins, and amount 1 cannot be made up by the coin Two, so we copy the value from the row above it.

```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Five  │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ 1 │ 2 │ ∞ │ 2 │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Two   │ 0 │ ∞ │   │   │   │   │   │   │   │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

For **amount 2**: 
- We use up 1 Two coin and remaining 0 amount takes minimum 0 coins
- i.e. we can make 2 in 1 + 0 = 1 coin
- But were we able to make 2 in lesser coins earlier? No, as indicated by ∞ in previous row for same amount 2.
- So we put 1 under column 2

For **amount 3**: We try using 1 Two coin but see that the remaining amount 1 (=3-2) cannot be made up (since row Two and column 1 is ∞), so we copy the value from the row above it.

For **amount 4**: 
- We use up 1 Two coin and remaining 2 (=4-2) amount takes minimum 1 coin
- i.e. we can make 4 in 1 + 1 = 2 coins
- But were we able to make 4 in lesser coins earlier? No, as indicated by ∞ in previous row for same amount 4.
- So we put 2 under column 4

For **amount 5**: 
- We use up 1 Two coin and remaining 3 (=5-2) amount takes minimum 1 coin
- i.e. we can make 5 in 1 + 1 = 2 coins
- But were we able to make 5 in lesser coins earlier? Yes! as indicated by 1 in previous row for same amount 5.
- So we copy 1 from the previous row, instead of putting 2.

```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Five  │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ 1 │ 2 │ ∞ │ 2 │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Two   │ 0 │ ∞ │ 1 │ 1 │ 2 │ 1 │   │   │   │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

For **amount 6**: 
- We use up 1 Two coin and remaining 4 (=6-2) amount takes minimum 2 coins
- i.e. we can make 6 in 1 + 2 = 3 coins
- But were we able to make 6 in lesser coins earlier? Yes! as indicated by 2 in previous row for same amount 6.
- So we copy 2 from the previous row.

For **amount 7**: 
- We use up 1 Two coin and remaining 5 (=7-2) amount takes minimum 1 coin
- i.e. we can make 7 in 1 + 1 = 2 coins
- But were we able to make 7 in lesser coins earlier? No, as indicated by ∞ in previous row for same amount 7.
- So we put 2 under column 7

For **amount 8**: 
- We use up 1 Two coin and remaining 6 (=8-2) amount takes 2 coins
- i.e. we can make 8 in 1 + 2 = 3 coins
- But were we able to make 8 in lesser coins earlier? Yes! as indicated by 2 in previous row for same amount 8.
- So we copy 2 from the previous row.


```
         0   1   2   3   4   5   6   7   8
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Nil   │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Three │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ ∞ │ 2 │ ∞ │ ∞ │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Five  │ 0 │ ∞ │ ∞ │ 1 │ ∞ │ 1 │ 2 │ ∞ │ 2 │
     ──┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
 Two   │ 0 │ ∞ │ 1 │ 1 │ 2 │ 1 │ 2 │ 2 │ 2 │
     ──┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
```

So our answer of makeing up amount 8 using minimum number of coins Three, Five and Two, is the last cell value (Two, 8) = **2**.

## Java code:

We used ∞ instead of -1 (as asked by the question) to indicate cases where it is not possible to make up the amount, because it would have required extra checks and made the code more complex. <br/>
At the end we check if last cell is ∞ and return -1 in that case.

**Trick:** <br/>
In place of ∞ we will use **Interger.MAX_VALUE - 1** to indicate the not possible cases. <br/>
We do a **-1** because we need to add **+1** to get the number of coins needed which can lead to overflow. <br/>
Overflow makes the number from largest to smallest **int** which is also **-ve**. <br/>
However, **(Interger.MAX_VALUE - 1) + 1** is still the largest +ve number and can be compared correctly <br/>

<br/>
We create our **dp** array of size 1 extra row and column than the number of coins and the amount. <br/>
- First columns is initalized to 0 (Java does it automatically for **int** arrays). <br/>
- First row is initalized to **Interger.MAX_VALUE - 1** i.e. ∞. <br/>

<br/>
Then for each coin (given by **coin[i-1]**), we iterate from **1 to amount** and check:
- Minimum no. of coins needed if using the current coin = 1 + no. of coins needed to make up amount (j - Coin's Value)
  - i.e. coins needed **= 1 + dp[i][j - coin[i-1]]**
- We compare this number with previous row for same amount, i.e. **dp[i-1][j]**
- Keep the minimum of these two.

```java
class Solution {
  
  public int coinChange(int[] coins, int amount) {
    
    int[][] dp = new int[coins.length + 1][amount + 1];
    
    Arrays.fill(dp[0], Integer.MAX_VALUE - 1);
        
    for(int i = 1; i <= coins.length; i++) {
      for(int j = 1; j <= amount; j++) {
        if ( coins[i-1] > j ) {
          dp[i][j]=dp[i-1][j];
        } else {
          dp[i][j] = Math.min( 1 + dp[i][j-coins[i-1]], dp[i-1][j] );
        }
      }
    }

    return dp[coins.length][amount]==Integer.MAX_VALUE-1?-1:dp[coins.length][amount];
  }
}
```

#### Complexity:
If \\(A\\) is the amount and \\(n\\) is the number of coins. <br/>

Time complexity \\(= O(n \times A)\\) <br/>
Space complexity \\(= O(n \times A)\\)


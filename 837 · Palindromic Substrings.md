https://www.lintcode.com/problem/837

1. Count from center
O(n * n)
```
class Solution:
    """
    @param str: s string
    @return: return an integer, denote the number of the palindromic substrings
    """
    def count_palindromic_substrings(self, str: str) -> int:
        # write your code here
        res = 0
        l = len(str)
        for i in range(l):
            res += 1
            j = 1
            while i - j >= 0 and i + j < l and str[i - j] == str[i + j]:
                res += 1
                j += 1
            if i + 1 < l and str[i + 1] == str[i]:
                res += 1
                j = 1
                while i - j >= 0 and i + 1 + j < l and str[i - j] == str[i + 1 + j]:
                    res += 1
                    j += 1
        return res
```

2. Manacher 算法 - don't understand this
O(n)
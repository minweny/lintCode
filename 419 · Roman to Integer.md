https://www.lintcode.com/problem/419

O(n)
```
class Solution:
    """
    @param s: Roman representation
    @return: an integer
    """
    def roman_to_int(self, s: str) -> int:
        # write your code here
        d = {"I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000}
        res = 0
        l = len(s)
        for i in range(l):
            if i + 1 < l and d[s[i]] < d[s[i + 1]]:
                res -= d[s[i]]
            else:
                res += d[s[i]]
        return res

```
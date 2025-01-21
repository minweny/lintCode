https://www.lintcode.com/problem/1022

O(m*n)
```
from typing import (
    List,
)

class Solution:
    """
    @param board: the given board
    @return: True if and only if it is possible to reach this board position during the course of a valid tic-tac-toe game
    """
    def valid_tic_tac_toe(self, board: List[str]) -> bool:
        # Write your code
        def win(player):
            for i in range(3):
                if board[i][0] == board[i][1] == board[i][2]:
                    return True
                if board[0][i] == board[1][i] == board[2][i]:
                    return True
            if board[0][0] == board[1][1] == board[2][2]:
                return True
            if board[0][2] == board[1][1] == board[2][0]:
                return True
            return False
        def count(player):
            res = 0
            for i in range(3):
                for j in range(3):
                    if board[i][j] == player:
                        res += 1
            return res
        xCount = count("X")
        yCount = count("O")
        # moves illegal
        if not (xCount == yCount or xCount == yCount + 1):
            return False
        xWin = win("X")
        yWin = win("O")
        if xWin and yWin:
            return False
        if xWin and xCount != yCount + 1:
            return False
        if yWin and xCount != yCount:
            return False
        return True
```
## 找规律成功第一版

~~~python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        row = len(matrix) -1
        col = len(matrix[0]) -1
        x, y = row,0
        while 0<= x <= row and 0<= y <= col:

            if matrix[x][y] == target:return True
            elif matrix[x][y] > target:
                x, y = x-1, y
            else:
                x, y = x, y+1
        return False  
~~~


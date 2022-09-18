#  剑指 Offer 04. 二维数组中的查找

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

##  1. Z字形查找
~~~
class  Solution {

public  boolean  findNumberIn2DArray(int[][] matrix, int  target) {

int  i = matrix.length - 1, j = 0;

while(i >= 0 && j < matrix[0].length)

{

if(matrix[i][j] > target) i--;

else  if(matrix[i][j] < target) j++;

else  return  true;

}

return  false;

}

}
~~~
##  2. 二分查找
~~~
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        for (int[] row : matrix) {
            int index = search(row, target);
            if (index >= 0) {
                return true;
            }
        }
        return false;
    }

    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;
        while (low <= high) {
            int mid = (high - low) / 2 + low;
            int num = nums[mid];
            if (num == target) {
                return mid;
            } else if (num > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return -1;
    }
}
~~~

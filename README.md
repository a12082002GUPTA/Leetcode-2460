# Leetcode-2460

# C++

class Solution {
public:
    vector<int> applyOperations(vector<int>& nums) {
        int n=nums.size();
          for(int i=0;i<n-1;i++)
          {
              if(nums[i]==nums[i+1])
              {
                  nums[i]=2*nums[i];
                  nums[i+1]=0;

              }
          }
          vector<int>ans(nums.size());
        int i=0,j=nums.size()-1;
        for(int k=0;k<nums.size();k++)
        {
            if(nums[k]==0)
            {
                ans[j]=nums[k];
                j--;
            }
            else
            {
                ans[i]=nums[k];
                i++;
            }
        }
        return ans;
    }
};

# Python

from typing import List

class Solution:
    def applyOperations(self, nums: List[int]) -> List[int]:
        n = len(nums)
        
        # First pass: double consecutive equal numbers and set the second to zero
        for i in range(n - 1):
            if nums[i] == nums[i + 1]:
                nums[i] *= 2
                nums[i + 1] = 0
        
        # Second pass: Move zeros to the end while maintaining the order of non-zero elements
        ans = [num for num in nums if num != 0]  # Collect non-zero numbers
        ans.extend([0] * (n - len(ans)))  # Append the required number of zeros
        
        return ans

#Java

import java.util.*;

class Solution {
    public int[] applyOperations(int[] nums) {
        int n = nums.length;

        // First pass: Double equal consecutive numbers and set the second to zero
        for (int i = 0; i < n - 1; i++) {
            if (nums[i] == nums[i + 1]) {
                nums[i] *= 2;
                nums[i + 1] = 0;
            }
        }

        // Second pass: Move all zeros to the end while maintaining the order of non-zero elements
        int[] ans = new int[n];
        int index = 0;

        // Fill non-zero values first
        for (int num : nums) {
            if (num != 0) {
                ans[index++] = num;
            }
        }

        // Remaining values in `ans` are already initialized to zero
        return ans;
    }
}

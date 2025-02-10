
Array
 Two Sum
 Best Time to Buy and Sell Stock
 Contains Duplicate
 Product of Array Except Self
 Maximum Subarray
 Maximum Product Subarray
 Find Minimum in Rotated Sorted Array
 Search in Rotated Sorted Array
 3Sum
 Container With Most Water
Binary
 Sum of Two Integers
 Number of 1 Bits
 Counting Bits
 Missing Number
 Reverse Bits
Interval
 Insert Interval
 Merge Intervals
 Non-overlapping Intervals
 Meeting Rooms (Leetcode Premium)
 Meeting Rooms II (Leetcode Premium)
Linked List
 Reverse a Linked List
 Detect Cycle in a Linked List
 Merge Two Sorted Lists
 Merge K Sorted Lists
 Remove Nth Node From End Of List
 Reorder List
Matrix
 Set Matrix Zeroes
 Spiral Matrix
 Rotate Image
 Word Search
String
 Longest Substring Without Repeating Characters
 Longest Repeating Character Replacement
 Minimum Window Substring
 Valid Anagram
 Group Anagrams
 Valid Parentheses
 Valid Palindrome
 Longest Palindromic Substring
 Palindromic Substrings
 Encode and Decode Strings (Leetcode Premium)
Tree
 Maximum Depth of Binary Tree
 Same Tree
 Invert/Flip Binary Tree
 Binary Tree Maximum Path Sum
 Binary Tree Level Order Traversal
 Serialize and Deserialize Binary Tree
 Subtree of Another Tree
 Construct Binary Tree from Preorder and Inorder Traversal
 Validate Binary Search Tree
 Kth Smallest Element in a BST
 Lowest Common Ancestor of BST
 Implement Trie (Prefix Tree)
 Add and Search Word
 Word Search II
Dynamic Programming
 Climbing Stairs
 Coin Change
 Longest Increasing Subsequence
 Longest Common Subsequence
 Word Break Problem
 Combination Sum
 House Robber
 House Robber II
 Decode Ways
 Unique Paths
 Jump Game
Graph
 Clone Graph
 Course Schedule
 Pacific Atlantic Water Flow
 Number of Islands
 Longest Consecutive Sequence
 Alien Dictionary (Leetcode Premium)
 Graph Valid Tree (Leetcode Premium)
 Number of Connected Components in an Undirected Graph (Leetcode Premium)
Heap
 Merge K Sorted Lists
 Top K Frequent Elements
 Find Median from Data Stream


 Two Sum Solution:

 Intuition
The problem requires finding two numbers in an array that add up to a given target. A brute-force approach is to check every possible pair and see if their sum equals the target. This works but is inefficient for large inputs.

Approach
Iterate over the array with a nested loop.
For each number at index i, check every other number at index j > i.
If nums[i] + nums[j] == target, return the indices {i, j} as the answer.
If no such pair is found, return null.
This approach ensures that all possible pairs are checked.

Complexity Analysis
Time Complexity: (O(n^2))
Since we use a nested loop where each element is compared with every other element once, the worst-case scenario requires checking (O(n^2)) pairs.
Space Complexity: (O(1))
We only use a constant amount of extra space for variables, apart from the input array.
Code

class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for(int  i = 0; i < n; i++)
        {
            for(int j = i + 1; j < n; j++)
            {
                if(nums[j]==target - nums[i])
                {
                    return new int[]{i,j};
                }
            }
        }
        return null;
    }
}
Optimized Approach (Using HashMap - (O(n)) Time Complexity)
Instead of checking every pair, we can use a HashMap to store numbers as we iterate through the array. This allows us to find the required pair in constant time.

import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }

            map.put(nums[i], i);
        }
        return null;
    }
}
Optimized Complexity:
Time Complexity: (O(n)), since we traverse the array once and use a HashMap for lookups (which take (O(1)) time on average).
Space Complexity: (O(n)), as we store elements in the HashMap.

==========

class Solution {
    public int maxProfit(int[] prices) {
        int max = 0;
        int n = prices.length;
        int small = prices[0];
        for(int i = 1; i < n; i++) {
            if(small > prices[i]) {
                small = prices[i];
                continue;
            }
            max = Math.max(max, prices[i] - small);
        }
        return max;
    }
}
Please Like ❤️
Please Like

Intuition
The problem asks to find the maximum profit from buying and selling a stock at different days. The goal is to identify the best day to buy and the best day to sell in order to maximize the profit. The strategy is to keep track of the minimum price and calculate the profit if we sell at the current price.

Approach
Initialize variables:
small to track the minimum price encountered so far.
max to track the maximum profit.
Iterate through the array of prices:
If the current price is smaller than small, update small to the current price.
Otherwise, calculate the profit by subtracting small from the current price and update max if this profit is higher than the current max.
Return the result once the iteration is complete.
Complexity
Time Complexity: O(n) (single pass through the array).
Space Complexity: O(1) (constant extra space).

=========================

Duplicate element::

Approach
First Sort the Array.
Then Compare elements one by one.
We Only have to return a boolean value.
Complexity
Time complexity: O(nlog(n))
Space complexity: O(log(n))
Code
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums); 
        for (int i = 0; i < nums.length - 1; i++) {
                if (nums[i] == nums[i+1]) {
                    return true;
                }
        }
        return false;
    }
}


Complexity using a HashMap
Time complexity: O(n)
Space complexity: O(n)
Code
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(nums[i])) {
                return true;
            }
            map.put(nums[i],1);
        }
        return false;
    }
}
Complexity using a HashSet
Time complexity: O(n)
Space complexity: O(n)
Code
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
                if (set.contains(nums[i])) {
                    return true;
                }
                set.add(nums[i]);
        }
        return false;
    }
}

================
product of array except self:
=============================

Intuition
Similar to finding Prefix Sum array, here the preblem intends us to find the Prefix Product Array and Suffix Product Array for our original array.

pre[i+1] = pre[i] * a[i]
suff[i-1] = suff[i] * a[i]
Complexity
Time complexity: O(n)
Only 2 loops iterating n times each without any nesting.
Space complexity: O(n)
We have taken prefix and suffixProduct as variables instead of arrays to further optimize space, even though the overall complexity remains the same.
Code
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int numsLength = nums.length;
        int prefixProduct = 1;
        int suffixProduct = 1;
        int[] result = new int[numsLength];
        for(int i = 0; i < numsLength; i++) {
            result[i] = prefixProduct;
            prefixProduct *= nums[i];
        }
        for(int i = numsLength-1; i >= 0; i--) {
            result[i] *= suffixProduct;
            suffixProduct *= nums[i];
        }
        return result;
    }
}

================


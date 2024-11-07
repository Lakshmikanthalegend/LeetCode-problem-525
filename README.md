# LeetCode-problem-525
To find the maximum length of a contiguous subarray with equal numbers of 0s and 1s, we transform 0s to -1s and calculate a cumulative sum. We use a hash map to track the first occurrence of each cumulative sum. If the same cumulative sum appears again, it indicates an equal number of 0s and 1s between the two indices. The length of this subarray is then calculated and compared to find the maximum length.

**Code:**

import java.util.HashMap;
public class MaxLengthEqualSubarray {
    public static int findMaxLength(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, -1); // Initialize with sum 0 at index -1
        int maxLength = 0;
        int cumulativeSum = 0;

        for (int i = 0; i < nums.length; i++) {
            // Treat 0 as -1
            cumulativeSum += (nums[i] == 0) ? -1 : 1;

            // Check if this cumulative sum has been seen before
            if (map.containsKey(cumulativeSum)) {
                // Calculate the length of the subarray
                int length = i - map.get(cumulativeSum);
                maxLength = Math.max(maxLength, length);
            } else {
                // Store the index of this cumulative sum
                map.put(cumulativeSum, i);
            }
        }  
        return maxLength;
    }

    public static void main(String[] args) {
        int[] nums = {0, 1, 0, 1, 0, 1};
        int result = findMaxLength(nums);
        System.out.println("Maximum length of contiguous subarray with equal number of 0s and 1s: " + result);
    }
}

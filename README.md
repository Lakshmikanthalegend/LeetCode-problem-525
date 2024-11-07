# LeetCode-problem-525
To find the maximum length of a contiguous subarray with equal numbers of 0s and 1s, we transform 0s to -1s and calculate a cumulative sum. We use a hash map to track the first occurrence of each cumulative sum. If the same cumulative sum appears again, it indicates an equal number of 0s and 1s between the two indices. The length of this subarray is then calculated and compared to find the maximum length.

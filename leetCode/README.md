# 1. Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Example 1:

    Input: nums = [2,7,11,15], target = 9
    Output: [0,1]
    Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

## Example 2:

    Input: nums = [3,2,4], target = 6
    Output: [1,2]

## Example 3:

    Input: nums = [3,3], target = 6
    Output: [0,1]

## Ans

	public int[] twoSum(int[] nums, int target) {
		for (int i = 0; i < nums.length; i++) {
			for (int j = 0; j < nums.length; j++) {
				if (nums[i] + nums[j] == target && i != j) {
					return new int[] { i, j };
				}
			}
		}
		return null;
	}



# 50. Pow(x, n)
Implement pow(x, n), which calculates x raised to the power n (i.e., xn).

## Example 1:

    Input: x = 2.00000, n = 10
    Output: 1024.00000

## Example 2:

    Input: x = 2.10000, n = 3
    Output: 9.26100

## Example 3:

    Input: x = 2.00000, n = -2
    Output: 0.25000
    Explanation: 2的-2次方 = 1/2的2次方 = 1/4 = 0.25



## Ans

    public double myPow(double x, int n) {
        return Math.pow(x,n);
    }


# 70. Climbing Stairs
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
## Example 1:

    Input: n = 2
    Output: 2
    Explanation: There are two ways to climb to the top.
    1. 1 step + 1 step
    2. 2 step

## Example 2:

    Input: n = 3
    Output: 3
    Explanation: There are three ways to climb to the top.
    1. 1 step + 1 step + 1 step
    2. 1 step + 2 step
    3. 2 step + 1 step

## Example 3:

    Input: n = 4
    Output: 5
    Explanation: There are three ways to climb to the top.
    1. 1 step + 1 step + 1 step + 1 step
    2. 1 step + 1 step + 2 step
    3. 1 step + 2 step + 1 step
    4. 2 step + 1 step + 1 step
    5. 2 step + 2 step


## Ans

    public int climbStairs(int n) {
		if (n <= 2) {
			return n;
		}
		// 費波那契數, num[3] = num[1]+num[2]
		// n =  1 , 2 , 3 , 4 , 5 ,  6 ,  7
		// ans= 1 , 2 , 3 , 5 , 8 , 13 , 21
		int tmp1 = 1;
		int tmp2 = 2;
		int tmpAns = 0;
		for (int i = 3; i <= n; i++) {
			tmpAns = tmp1 + tmp2;
			tmp1 = tmp2;
			tmp2 = tmpAns;
		}
		return tmpAns;
    }

# 189. Rotate Array
Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.
## Example 1:

    Input: nums = [1,2,3,4,5,6,7], k = 3
    Output: [5,6,7,1,2,3,4]
    Explanation:
    rotate 1 steps to the right: [7,1,2,3,4,5,6]
    rotate 2 steps to the right: [6,7,1,2,3,4,5]
    rotate 3 steps to the right: [5,6,7,1,2,3,4]

## Example 2:

    Input: nums = [-1,-100,3,99], k = 2
    Output: [3,99,-1,-100]
    Explanation: 
    rotate 1 steps to the right: [99,-1,-100,3]
    rotate 2 steps to the right: [3,99,-1,-100]

## Ans

    public void rotate(int[] nums, int k) {
		int count = nums.length;
		if (k == 0) {
			return;
		}
        // nums =[1, 2, 3, 4, 5, 6, 7]
        // 建立一個兩倍陣列
		int[] bufArray = new int[count * 2];
		// bufArray =[1, 2, 3, 4, 5, 6, 7, 1, 2, 3, 4, 5, 6, 7]
		for (int i = 0; i < bufArray.length; i++) {
			bufArray[i] = nums[i % count];
		}
        // 當k=1與k=8 輸出結果相同
		// index為總長度減去取餘數後的值
		int index = count - (k % count);
		for (int i = 0; i < nums.length; i++) {
			nums[i] = bufArray[index + i];
		}
    }

# 268. Missing Number
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

## Example 1:

    Input: nums = [3,0,1]
    Output: 2
    Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

## Example 2:

    Input: nums = [0,1]
    Output: 2
    Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.

## Example 3:

    Input: nums = [9,6,4,2,3,5,7,0,1]
    Output: 8
    Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.



## Ans

    public int missingNumber(int[] nums) {
		int size = nums.length;

		for (int i = 0; i <= size; i++) {
			boolean isMach = false;
			for (int j = 0; j < size; j++) {
				if (i == nums[j]) {
					isMach = true;
                    break;
				}
			}
			if(!isMach) {
				return i;
			}
		}
		return 0;
    }

# 345. Reverse Vowels of a String
Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

## Example 1:

    Input: s = "hello"
    Output: "holle"

## Example 2:

    Input: s = "leetcode"
    Output: "leotcede"

## Ans

    public String reverseVowels(String s) {
        char[] chars = s.toCharArray();
		Stack<Character> stChar = new Stack<Character>();

		for (int i = 0; i < s.length(); i++) {
        // 取出母音
        if ('a' == chars[i] || 'A' == chars[i] ||
            'e' == chars[i] || 'E' == chars[i] ||
            'i' == chars[i] || 'I' == chars[i] ||
            'o' == chars[i] || 'O' == chars[i] ||
            'u' == chars[i] || 'U' == chars[i]) {
				stChar.push(chars[i]);
				chars[i] = '$';
			}
        }// end_for

        //調換母音順序
        for (int i = 0; i < s.length(); i++) {
			if(chars[i] == '$') {
				chars[i] = stChar.pop();
			}
		}// end_for
        return new String(chars);
    }

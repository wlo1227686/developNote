<h1 id="home">目錄</h1>

[1. Two Sum](#1) </br>
[2. Add Two Numbers](#2) </br>
[50. Pow(x, n)](#50)</br>
[70. Climbing Stairs](#70)</br>
[128. Longest Consecutive Sequence](#128)</br>
[189. Rotate Array](#189)</br>
[268. Missing Number](#268)</br>
[345. Reverse Vowels of a String](#345)</br>
[1502. Can Make Arithmetic Progression From Sequence](#1502)</br>

[回目錄](#home)</br><h1 id="1">1. Two Sum</h1>

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

[回目錄](#home)</br><h1 id="2">2. Add Two Numbers</h1>

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
</br>![addtwonumber1.jpg](img/addtwonumber1.jpg)</br>
## Example 1:

    Input: l1 = [2,4,3], l2 = [5,6,4]
    Output: [7,0,8]
    Explanation: 342 + 465 = 807.

## Example 2:

    Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
    Output: [8,9,9,9,0,0,0,1]

## Example 3:

    Input: l1 = [0], l2 = [0]
    Output: [0]

## Ans

    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
		ListNode ans = new ListNode(0);
		ListNode tmp = ans; // tmp指向ans的記憶體位置
		while (l1 != null || l2 != null) {
			int tmpL1 = 0, tmpL2 = 0, sum = 0;
			boolean carry = false; // 是否進位
			if (l1 != null) { // 取出數值並進位
				tmpL1 = l1.val;
				l1 = l1.next;
			}
			if (l2 != null) { // 取出數值並進位
				tmpL2 = l2.val;
				l2 = l2.next;
			}
			sum = tmp.val + tmpL1 + tmpL2;
			if (sum >= 10) { // 是否需進位
				carry = true;
			}
			tmp.val = sum % 10; // 取sum補數
			if (l1 != null || l2 != null || carry) {
				// 當 l1有值 或 l2有值 或 需進位才增加ListNode
				tmp.next = new ListNode(carry ? 1 : 0); // 有進位則補1反之補0
				tmp = tmp.next;
			}
		} // end_while
		return ans;
    }

[回目錄](#home)</br><h1 id="50">50. Pow(x, n)</h1>

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

[回目錄](#home)</br><h1 id="70">70. Climbing Stairs</h1>

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

[回目錄](#home)</br><h1 id="128">128. Longest Consecutive Sequence</h1>

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

## Example 1:

    Input: nums = [100,4,200,1,3,2]
    Output: 4
    Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

## Example 2:

    Input: nums = [0,3,7,2,5,8,4,6,0,1]
    Output: 9

## Example 3:

    Input: nums = [0,1,2,3,4,5,6,7,0,-1,-2,-3,-4,-7]
    Output: 12

## Ans

    public int longestConsecutive(int[] nums) {
    	if (nums.length == 0) {
    		return 0;
    	}
    	// 1. 使用HashSet移除重複項目
    	HashSet<Integer> hs = new HashSet<Integer>();
    	for (int i = 0; i < nums.length; i++) {
    		hs.add(nums[i]);
    	}
    	int resultCount = 0;
    	// 2. 計算項目連續幾次
    	for (int item : hs) {
    		// 左側
    		if (hs.contains(item - 1)) {
    			// item的左側有值,表示這是中間值
    			// 中間值跳過不計算
    			continue;
    		}
    		// 計算item右側連續幾次
    		int tempItem = item;
    		int countItem = 1;
    		while (hs.contains(tempItem + 1)) {
        	tempItem++;
    			countItem++;
    		}
    		// 保留右側連續最多的次數
    		resultCount = Math.max(countItem, resultCount);
    	}
    	return resultCount;
    }

[回目錄](#home)</br><h1 id="189">189. Rotate Array</h1>

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

[回目錄](#home)</br><h1 id="268">268. Missing Number</h1>

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

[回目錄](#home)</br><h1 id="345">345. Reverse Vowels of a String</h1>

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

[回目錄](#home)</br><h1 id="1502">1502. Can Make Arithmetic Progression From Sequence</h1>

A sequence of numbers is called an arithmetic progression if the difference between any two consecutive elements is the same.

Given an array of numbers arr, return true if the array can be rearranged to form an arithmetic progression. Otherwise, return false.

## Example 1:

    Input: arr = [3,5,1]
    Output: true
    Explanation: We can reorder the elements as [1,3,5] or [5,3,1] with differences 2 and -2 respectively, between each consecutive elements.

## Example 2:

    Input: arr = [1,2,4]
    Output: false
    Explanation: There is no way to reorder the elements to obtain an arithmetic progression.

## Example 3:

    Input: arr = [1,10,10,10,19]
    Output: false

## Ans

    public boolean canMakeArithmeticProgression(int[] arr) {
		// 1. 升冪排序
        Arrays.sort(arr);
		if (arr.length <= 1) {
			return false;
		}
        // 2. 判斷間隔
		int seq = arr[1] - arr[0];
		for (int i = 1; i < arr.length; i++) {
			if (arr[i] - arr[i - 1] != seq) {
				return false;
			}
		}
		return true;
    }

### 88. Merge Sorted Array

**You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.Merge nums1 and nums2 into a single array sorted in non-decreasing order. The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.**

**solved using java**
```Java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i=m-1, j=n-1, k=nums1.length-1;
    while(i>=0 && j>=0){
        if(nums1[i]>nums2[j]){
            nums1[k]=nums1[i];
            i--;
            k--;
        }
        else{
            nums1[k]=nums2[j];
            j--;
            k--;
        }
    }
        while(i>=0){
            nums1[k]=nums1[i];
            i--;
            k--;
        }
        while(j>=0){
            nums1[k]=nums2[j];
            j--;
            k--;
        }
    }
}
```



### 27. Remove Element

**Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.
Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:
Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.**

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int  l=nums.length-1, count=0;
        for(int i=0; i<=l; i++){
            if(nums[i]!=val){
                nums[count++]=nums[i];
            }
        }
    return count;
    }
}
```

### 26.Remove duplicates from sorted array:

**Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.
Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:
Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.**

```
class Solution {
    public int removeDuplicates(int[] nums) {
        int pos=1;
        for (int i=1; i<nums.length; i++) {
            if (nums[i] != nums[i-1]) {
                nums[pos]=nums[i];
                pos++;
            }
        }
        return pos;
    }
}
```

## 169. Majority Element:

**Given an array nums of size n, return the majority element.
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.**

```
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        int n=nums.length;
        return nums[n/2];
    }
}
```

## Rotate Array:

**Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.**

```
void rotate(int* nums, int numsSize, int k) {
    for(int i=0; i<k; i++){
        int last = nums[numsSize-1];
    for(int i=numsSize-1; i>0; i--){
        nums[i]=nums[i-1];
    }
    nums[0]=last;
    }
}
```

## 121. Best time to Buy and Sell Stock - I:
**You are given an array prices where prices[i] is the price of a given stock on the ith day.You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.**

```
class Solution {
    public int maxProfit(int[] prices){
        int minPrice=Integer.MAX_VALUE;
        int maxProfit=0;
        for(int i=0; i<prices.length; i++){
            if(prices[i]<minPrice){
                minPrice=prices[i];
            }
            else{
               int profit=prices[i]-minPrice;
                if(maxProfit<profit){
                    maxProfit=profit;
                }
            }
        }
        return maxProfit;
    }
}
```

### 122. Best Time to Buy and Sell Stock - II:
**You are given an integer array prices where prices[i] is the price of a given stock on the ith day. On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day. Find and return the maximum profit you can achieve.**

```
class Solution {
    public int maxProfit(int[] prices) {
        int profit=0;
        for(int i=1; i<prices.length; i++){
            if(prices[i]>prices[i-1])
                 profit += (prices[i]-prices[i-1]);
        }
        return profit;
    }
}
```
### 13.Roman to Integer
**Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.**

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
**For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.**

**Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:**

**I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.**

**using c++**
```
class Solution {
public:
    int romanToInt(string s) {
        unordered_map<char, int> m;
        
        m['I'] = 1;
        m['V'] = 5;
        m['X'] = 10;
        m['L'] = 50;
        m['C'] = 100;
        m['D'] = 500;
        m['M'] = 1000;
        
        int ans = 0;
        
        for(int i = 0; i < s.length(); i++){
            if(m[s[i]] < m[s[i+1]]){
                ans -= m[s[i]];
            }
            else{
                ans += m[s[i]];
            }
        }
        return ans;
    }
};
```

### 58. Length of Last Word
**Given a string s consisting of words and spaces, return the length of the last word in the string.**
**A word is a maximal substring consisting of non-space characters only.**

**using java**
```
class Solution {
    public int lengthOfLastWord(String s) {
        boolean found = false;
        int counter = 0;
        for(int i = s.length()-1; i >=0; i--) {
            if(s.charAt(i) != ' ') {
                counter++;
                found = true;
            }
            else if(found) break;
        }
        return counter;
    }
}
```

### 28. Find the Index of the First Occurrence in a String
**Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.**

**Ex:01**

**Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.**

**using java**

```
class Solution {
    public int strStr(String haystack, String needle) {
        for(int i=0, j=needle.length(); j<=haystack.length(); i++, j++){
            if(haystack.substring(i,j).equals(needle)){
                return i;
            }
        }
        return -1;
    }
}
```

### 125. Valid Palindrome

**A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
Given a string s, return true if it is a palindrome, or false otherwise.**

**using java**

```
class Solution {
    public boolean isPalindrome(String s) {
        s=s.toLowerCase().replaceAll("[^a-z0-9]", "");
        int i=0;
        int j=s.length()-1;
        while(i<=j){
            if(s.charAt(i)!=s.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
}
```

### 383. RansomNote:

**Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.
Each letter in magazine can only be used once in ransomNote.**

**using java**
```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        char arr1[]=magazine.toCharArray();
        char arr2[]=ransomNote.toCharArray();
        int letters[]=new int[26];
        for(char i:arr1){
            letters[i-'a']++;
        }
        for(char j:arr2){
            letters[j-'a']--;
            if(letters[j-'a']==-1)
                return false;
        }
            return true;
    }
}
```

### 205. Isomorphic Strings

**Given two strings s and t, determine if they are isomorphic.
Two strings s and t are isomorphic if the characters in s can be replaced to get t.
All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.**

**using java**
```
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int[] indexS = new int[200]; 
        int[] indexT = new int[200]; 

        int len = s.length();
        if(len != t.length()) {
            return false;
        }

        for(int i = 0; i < len; i++) {
            if(indexS[s.charAt(i)] != indexT[t.charAt(i)]) {
                return false; // If different, strings are not isomorphic
            }
            indexS[s.charAt(i)] = i + 1; // updating index of current character
            indexT[t.charAt(i)] = i + 1; // updating index of current character
        }

        return true;
    }
}
```

### 290. Word Pattern

**Given a pattern and a string s, find if s follows the same pattern.
Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in s.**

**using java**
```
// Algo Used: Hashing + Linear Traversal
//TC: O N , SC: O 1
import java.util.HashMap;

class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        int n = pattern.length();

        // Early exit if the lengths don't match
        if (n != words.length) return false;

        HashMap<Character, String> charToWord = new HashMap<>();
        HashMap<String, Character> wordToChar = new HashMap<>();

        for (int i = 0; i < n; i++) {
            char c = pattern.charAt(i);
            String word = words[i];

            // Check if there is a mismatch in the current mapping
            if (charToWord.containsKey(c)) {
                if (!charToWord.get(c).equals(word)) return false;
            } else {
                charToWord.put(c, word);
            }

            // Check the reverse mapping
            if (wordToChar.containsKey(word)) {
                if (!wordToChar.get(word).equals(c)) return false;
            } else {
                wordToChar.put(word, c);
            }
        }

        return true;
    }
}
```

### 242. Valid Anagram

**Given two strings s and t, return true if t is an anagram of s, and false otherwise.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.**

**using c++**

```
class Solution {
public:
    bool isAnagram(string s, string t) {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        return s == t;
    }
};
```

### 1. Two Sum:

**Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.**

**using c++**
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
         for(int i=0;i<nums.size();i++)
        {
           for(int j=i+1;j<nums.size();j++)  //i+1 so that same number not repeated
           {
            if(nums[i] + nums[j]==target)  
                return {i,j};  //always return indexes in { }
           }
                
        }
        return {0,1};
    }
};
```

### 202. Happy Number:

**Write an algorithm to determine if a number n is happy.
A happy number is a number defined by the following process:
Starting with any positive integer, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.**

**using c**
```
int sumPow(int n){
    int sum=0;
    while(n){
        sum+=pow(n%10,2);
        n/=10;
    }
    return sum;
}

bool isHappy(int n) {
    int res=n;
    while(1){
        res=sumPow(res);
        if(res == 1)
        return true;
        if(res < 1 || res==89) return false;
    }
}
```
### 20. Valid Parentheses

**Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:
Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.**

**using java**

```
class Solution {
    public static boolean isValid(String s) {
        while(true) {
            if(s.contains("()")) {
                s=s.replace("()", "");
            }
            else if(s.contains("{}")) {
                s=s.replace("{}", "");
            }
            else if(s.contains("[]")) {
                s=s.replace("[]", "");
            }
            else {
                return s.isEmpty();
            }
        }
    }
}
```

### 141. Linked List Cycle

**Given head, the head of a linked list, determine if the linked list has a cycle in it.
There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.
Return true if there is a cycle in the linked list. Otherwise, return false.**

**using java**

```
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head==null || head.next==null){
            return false;
        }
        ListNode slow=head;
        ListNode fast=head.next;

        while(slow!=fast){
            if(fast==null || fast.next==null){
                return false;
            }

            slow=slow.next;
            fast=fast.next.next;
        }

        return true;
    }
}
```

### 21. Merge two sorted lists

**You are given the heads of two sorted linked lists list1 and list2.
Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.
Return the head of the merged linked list.**

**using java**

```

class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 != null && list2 != null){
            if(list1.val < list2.val){
                list1.next=mergeTwoLists(list1.next, list2);
                return list1;
            }
            else{
                list2.next=mergeTwoLists(list1, list2.next);
                return list2;
            }
        }
        if(list1==null)
        return list2;
        return list1;
    }
}
```
### 104. Maximum Depth of Binary Tree

**Given the root of a binary tree, return its maximum depth.
A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.**

**using java**

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
        if(root==null){
            return 0;
        }
        int left=maxDepth(root.left);
        int right=maxDepth(root.right);
        return Math.max(left, right)+1;
    }
}
```

### 2529. Maximum Count of Positive Integer and Negative Integer:

**Given an array nums sorted in non-decreasing order, return the maximum between the number of positive integers and the number of negative integers.
In other words, if the number of positive integers in nums is pos and the number of negative integers is neg, then return the maximum of pos and neg.**

**using java**

```
class Solution {
    public int maximumCount(int[] nums) {
        int dummyNo=1, pos=0, neg=0;
        for(int i=0; i<nums.length; i++){
            if(dummyNo*nums[i] > 0) pos++;
            else if(dummyNo*nums[i]<0) neg++;
        }
        return Math.max(pos, neg);
    }
}
```

### 704. Binary Search:

**Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.
You must write an algorithm with O(log n) runtime complexity.**

**using java**

```
class Solution {
    public int search(int[] nums, int target) {
        int len=nums.length;
        for(int i=0; i<len; i++){
            if(nums[i]==target){
                return i;
            }
        }
        return -1;
    }
}
```

## 88. Merge Sorted Array

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



## 27. Remove Element

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

## 26.Remove duplicates from sorted array:

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


# Problem 1 -  H-Index II
## Time Complexity :
O()

## Space Complexity :
O()

## Did this code successfully run on Leetcode :
Yes.

## Any problem you faced while coding this :
No.
        
### Solution:
        class Solution:
            def hIndex(self, citations: List[int]) -> int:
                l,r=0,len(citations)
                while l<r:
                    mid=(l+r)//2
                    if l+1==r and citations[len(citations)-r]>=r:
                        return r
                    if l+1==r and citations[len(citations)-r]<r:
                        return l
                    if citations[len(citations)-mid]>=mid:
                        l=mid
                    else:
                        r=mid-1
                return l

# Problem 2 - Intersection of Two Arrays II
## Time Complexity :
O()

## Space Complexity :
O()

## Did this code successfully run on Leetcode :
Yes.
## Any problem you faced while coding this :
No.
        
### Solution:
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        
        
        def binary_search(nums, num):
            left = 0
            right = len(nums) - 1

            while left <= right:
                mid = (left + right) // 2       
                if nums[mid] == num:
                    return mid 
                if nums[mid] > num:
                    right = mid - 1
                elif nums[mid] < num:
                    left = mid + 1
            return -1
            
            
        if len(nums1) > len(nums2):
            nums1, nums2 = nums2, nums1
            
        nums1.sort()
        res = []
        for num in nums2:
            index = binary_search(nums1, num)
            if index != -1:
                res.append(nums1[index])
                nums1.pop(index)
                
        return res

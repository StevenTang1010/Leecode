##python算法刷题+最优解记录
- 1.给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那两个整数，
并返回他们的数组下标。你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

    示例:
    
        给定 nums = [2, 7, 11, 15], target = 9
        因为 nums[0] + nums[1] = 2 + 7 = 9
        所以返回 [0, 1]

    解答：
```python
# 只需要进行一次遍历，找到即返回
def twoSum(self, nums: List[int], target: int) -> List[int]:
    # 创建字典，以达到效率最大化的目的
    numsdict = {}
    # 将列表生成键值对并遍历
    for i, num in enumerate(nums):
        # 判断找到的索引值是否为空
        if numsdict.get(target-num) is not None:
            # 若找到则返回对应下表
            return [i, numsdict.get(target-num)]
        # 将值作为键，下表作为值存入字典
        numsdict[num] = i
```

- 2.给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

    示例 1:

        输入: "abcabcbb"
        输出: 3 
        解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
    示例 2:

        输入: "bbbbb"
        输出: 1
        解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
    示例 3:

        输入: "pwwkew"
        输出: 3
        解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
        
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。


    解答：
```python
def lengthOfLongestSubstring(s: str) -> int:
    if s == '':
        return 0
    # 判断字符串长度
    if len(s) <= 1:
        return 1
    # 用于存放不重复的项
    lst = []
    # 存放最大值
    _max = 1
    # 遍历字符串
    for i in s:
        # 判断是否存在于lst中
        if i in lst:
            # 如果存在，则比对替换最大值
            _max = max(_max, len(lst))
            # 同时截取重复项之后的值
            lst = lst[lst.index(i) + 1:]
        # 不管是否存在，都添加到lst
        lst.append(i)
    _max = max(len(lst), _max)
    # 返回最大值
    return _max
```


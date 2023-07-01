# LC-Python29
Greedy Algorithm 4


## 860.Lemonade Change, 406.Queue Reconstruction by Height

June 30, 2023  4h

Congratulations!\
This is the 30th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about ~~sorting both  positive and negative numbers, the concept of net increase, and processing one side at each time and merging the results~~.


## 860.Lemonade Change
This is an easy question.
```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        five = 0
        ten = 0
        twenty = 0
        
        for bill in bills:
            if bill == 5:
                five += 1
            
            if bill == 10:
                if five <= 0:
                    return False
                ten += 1
                five -= 1
            
            if bill == 20:
                if five > 0 and ten > 0:
                    five -= 1
                    ten -= 1
                    #twenty += 1
                elif five >= 3:
                    five -= 3
                    #twenty += 1
                else:
                    return False
        
        return True
```


## 406.Queue Reconstruction by Height
Deal with one side first and then deal with another side!



## 452. 
用最少数量的箭引爆气球, 本题是一道 重叠区间的题目，好好做一做，因为明天三道题目，都是 重叠区间。



# LC-Python29
Greedy Algorithm 4


## 860.Lemonade Change, 406.Queue Reconstruction by Height, 452.Minimum Number of Arrows to Burst Balloons

June 30, 2023  4h

Congratulations!\
This is the 29th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about inserting items according to the ranking and merge intervals of overlapping.


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
Deal with one side first and then deal with another side! Firstly sort h/height from large to small, then adjust orders according to k.
```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]: 
        #firstly sort heights from largest to smallest, if same, sort according to k from least to largest
        people.sort(key = lambda x: (-x[0],  x[1]))
        que = []

        #adjust the order again according to k from least to largest
        #by inserting element p to place p[1]
        for p in people:
            que.insert(p[1], p) 
        
        return que
```


## 452.Minimum Number of Arrows to Burst Balloons
Overlapping intervals. If the ith interval's left boundary is greater than the i-1th interval's right boundary, we need one more arrow. Otherwise, no new arrow is needed, and we need to see if the i+1th interval's left boundary is smaller than the minimum of i-1 and ith right boundary. This is updating the new right boundary for i-1 and ith interval.
```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        if len(points) == 0: return 0
        points.sort(key = lambda x: x[0])
        result = 1
        for i in range(1, len(points)):
            if points[i][0] > points[i-1][1]:   #baloon i and i-1 have no overlapping interval
                result += 1
            else:
                points[i][1] = min(points[i-1][1], points[i][1])
        return result
```



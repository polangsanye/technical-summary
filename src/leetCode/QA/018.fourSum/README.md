
## 四数之和
> 给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。


### 示例 1
> 给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。        
> 满足要求的四元组集合为： [ [-1,  0, 0, 1], [-2, -1, 1, 2], [-2,  0, 0, 2] ]



### 解法
```javascript 1.8
let fourSum = function(nums,target) {
    let res = [];
    nums.sort((a,b)=>a-b);
    for(let i = 0,len = nums.length; i<len - 3; i++){
        if(i > 0 && nums[i - 1] === nums[i]){
            continue;
        }
        let first = nums[i];
        for(let j = i + 1; j<len - 2; j++){
            if(j > i + 1 && nums[j - 1] === nums[j]){
                continue;
            }
            let two = nums[j];
            let left = j + 1;
            let right = len - 1;
            while(left < right){
                let sum = nums[left] + nums[right] + first + two;
                if(sum === target){
                    res.push([first,two,nums[left],nums[right]]);
                    while (left < right && nums[left + 1] === nums[left]){
                        left++;
                    }
                    while (left < right && nums[right - 1] === nums[right]){
                        right--;
                    }
                    left ++;
                    right --;
                }else if(sum > target){
                    right--
                }else{
                    left++
                }
            }
        }
    }
    return res;
};
```

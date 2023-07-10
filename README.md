# DSAAssign3

# Q1

```
function threeSumClosest(nums, target) {
    nums.sort((a, b) => a - b);
    let closestSum = Infinity;
    
    for (let i = 0; i < nums.length - 2; i++) {
        let left = i + 1;
        let right = nums.length - 1;
        
        while (left < right) {
            const sum = nums[i] + nums[left] + nums[right];
            
            if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                closestSum = sum;
            }
            
            if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
    }
    
    return closestSum;
}


```

# Q2

```
function fourSum(nums, target) {
    nums.sort((a, b) => a - b);
    const result = [];
    
    for (let i = 0; i < nums.length - 3; i++) {
        if (i > 0 && nums[i] === nums[i - 1]) {
            continue;
        }
        
        for (let j = i + 1; j < nums.length - 2; j++) {
            if (j > i + 1 && nums[j] === nums[j - 1]) {
                continue;
            }
            
            let left = j + 1;
            let right = nums.length - 1;
            
            while (left < right) {
                const sum = nums[i] + nums[j] + nums[left] + nums[right];
                
                if (sum === target) {
                    result.push([nums[i], nums[j], nums[left], nums[right]]);
                    left++;
                    right--;
                    
                    while (left < right && nums[left] === nums[left - 1]) {
                        left++;
                    }
                    
                    while (left < right && nums[right] === nums[right + 1]) {
                        right--;
                    }
                } else if (sum < target) {
                    left++;
                } else {
                    right--;
                }
            }
        }
    }
    
    return result;
}

```

# Q3

```
function nextPermutation(nums) {
    let i = nums.length - 2;
    
    while (i >= 0 && nums[i] >= nums[i + 1]) {
        i--;
    }
    
    if (i >= 0) {
        let j = nums.length - 1;
        
        while (j >= 0 && nums[j] <= nums[i]) {
            j--;
        }
        
        swap(nums, i, j);
    }
    
    reverse(nums, i + 1);
}

function swap(nums, i, j) {
    [nums[i], nums[j]] = [nums[j], nums[i]];
}

function reverse(nums, start) {
    let i = start;
    let j = nums.length - 1;
    
    while (i < j) {
        swap(nums, i, j);
        i++;
        j--;
    }
}

```

# Q4

```
function searchInsert(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return left;
}

```

# Q5

```
function plusOne(digits) {
    for (let i = digits.length - 1; i >= 0; i--) {
        if (digits[i] === 9) {
            digits[i] = 0;
        } else {
            digits[i]++;
            return digits;
        }
    }
    
    digits.unshift(1);
    return digits;
}

```

# Q6

```
function singleNumber(nums) {
    let result = 0;
    
    for (let num of nums) {
        result ^= num;
    }
    
    return result;
}

// Test case
let nums = [2, 2, 1];
console.log(singleNumber(nums));
```

# Q7

```

function findMissingRanges(nums, lower, upper) {
    const ranges = [];
    let start = lower;
    
    for (let num of nums) {
        if (num > start) {
            ranges.push(getRange(start, num - 1));
        }
        
        start = num + 1;
    }
    
    if (start <= upper) {
        ranges.push(getRange(start, upper));
    }
    
    return ranges;
}

function getRange(start, end) {
    return start === end ? `${start}` : `${start}->${end}`;
}

```



## Slidding Window Maximum
https://leetcode.com/problems/sliding-window-maximum/

input array: [1, 3, 1, 2, 0, 5] and the window size is 3,
output is [3, 3, 2, 5]

```
public int[] SliddingWindowMax(int[] nums, int k) {
    if(nums == null || k <= 0) {
        return null;
    }
    int len = nums.length;
    if(len * k) return null;
    int[] res = new int[len - k + 1];
    Deque<Integer> dq = new ArrayDeque<>();
    for(int i = 0; i < len; i++) {
        //remove the index of element out of the window
        while(!dq.isEmpty() && dp.peekFirst() < i - k + 1) {
            dq.pollFirst();
        }
        //remove the index of element that is less than ith element before ith element
        while(!dq.isEmpty() && nums[dq.peekLast()] < nums[i]) {
            dq.pollLast();
        }
        dq.offer(i); //offer is offerLast
        if(i >= k - 1) {
            res[i - k + 1] = nums[dq.peekFirst()];
        }
    } 
    return res;
}
```

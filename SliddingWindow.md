## LongestSubstring within k distinct characters & Fruit into Baskets
https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/
https://leetcode.com/problems/fruit-into-baskets/

For longestSubstring, the input is a string, while Fruit into Baskets, input is integer.
General Solution:
```
public int solution(String s, int k) {
    if(s == null || s.length() == 0 || k <= 0) {
        return 0;
    }
    int res = 0, left = 0, right = 0;
    int len = s.length();
    HashMap<Character, Integer> cache = new HashMap<>();
    while(right < len) {
        if(cache.size() <= k){
            cache.put(s.charAt(right), right++);
        }
        if(cache.size() == k + 1) {
            int del_idx = Collections.min(cache.values());
            cache.remove(s.charAt(del_idx));
            left = del_idx + 1;
        }
        res = Math.max(res, right - left);
    }
    return res;
}
```

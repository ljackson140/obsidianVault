Arrays and strings are the most common input types on Leetcode and the base for:
- Sliding window
- Two pointers
- Dynamic programming 
- Hashing


Core concepts 
1. Arrays in C#
	- Key facts 
		- Fixed size
		- O(1) access
		- Contiguous memory 
		- Mutating in place is common and often required 
2. Strings in C#
	- strings are immutable (can’t be change after creation)
	- StringBuilder for construction
	- Char[] for modification
	- Indexing for reading
	
```
string s = "abc";
s[0] = 'z'; // ❌ NOT ALLOWED


char[] chars = s.ToCharArray();
chars[0] = 'z';
string result = new string(chars);
```
``
3. Array Problems 
	- Every array/string problem boils down to movement 
	- Always ask: “How are the pointers moving?”

| Pattern           | Movement          |
| ----------------- | ----------------- |
| Simple Scan       | One Pointer       |
| Compare from ends | Two Pointer       |
| Subarray problems | Sliding Window    |
| Prefix logic      | Cumulative memory |

# Pattern 1: One-pass Scan
when to use?
- Find min/max
- Count something
- Track best results so far

```
int max = int.MinValue;

foreach (int num in nums)
{
    max = Math.Max(max, num);
}
Time: O(n)
Space: O(1)
```

# Pattern 2: Two pointers
When to use?
- sorted arrays
- Reverse problems 
- Palindrome checks

```
bool IsPalindrome(string s)
{
    int left = 0, right = s.Length - 1;

    while (left < right)
    {
        if (s[left] != s[right])
            return false;
        left++;
        right--;
    }
    return true;
}
```

# Pattern 3: ✨ Sliding window ✨(very important)
When to use?
- Substrings / subarrays
- “Longest”, “Smallest”, “At most”

```
int left = 0;

for (int right = 0; right < nums.Length; right++)
{
    // expand window
    while (/* window invalid */)
    {
        // shrink window
        left++;
    }
    // update result
}
📌Most Medium array problems are this pattern
```

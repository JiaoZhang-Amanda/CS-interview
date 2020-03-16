## String Coding

### JAVA releted
```
StringBuilder sb = new StringBuilder(s);
sb.reverse().toString();
```
### Leetcode

\#| Title|Difficulty
--|--|--
345  |  Reverse Vowels of a String   |    Easy
535| Encode and Decode TinyURL|    Medium
388  |     Longest Absolute File Path    |   Medium
394  |     Decode String    |   Medium
482   |    License Key Formatting   |    Medium
217 |   Contains Duplicate|   Easy
159   |    Longest Substring with At Most Two Distinct Characters   |    Hard
340   |    Longest Substring with At Most K Distinct Characters   |    Hard
266   |    Palindrome Permutation   |    Easy
336   |    Palindrome Pairs  |     Hard
214    |   Shortest Palindrome     |  Hard

<details>
<summary>345. Reverse Vowels of a String</summary>
Write a function that takes a string as input and reverse only the vowels of a string.

Example 1:

Input: "hello"
Output: "holle"
</details>

<details>
<summary>535. Encode and Decode TinyURL</summary>
TinyURL is a URL shortening service where you enter a URL such as https://leetcode.com/problems/design-tinyurl and it returns a short URL such as http://tinyurl.com/4e9iAk.

Design the encode and decode methods for the TinyURL service. There is no restriction on how your encode/decode algorithm should work. You just need to ensure that a URL can be encoded to a tiny URL and the tiny URL can be decoded to the original URL.
</details>

<details>
<summary>388. Longest Absolute File Path</summary>
Suppose we abstract our file system by a string in the following manner:

The string "dir\n\tsubdir1\n\tsubdir2\n\t\tfile.ext" represents:

dir
    subdir1
    subdir2
        file.ext
The directory dir contains an empty sub-directory subdir1 and a sub-directory subdir2 containing a file file.ext.
</details>

<details>
<summary>394. Decode String</summary>
Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there won't be input like 3a or 2[4].

Examples:

s = "3[a]2[bc]", return "aaabcbc".
s = "3[a2[c]]", return "accaccacc".
s = "2[abc]3[cd]ef", return "abcabccdcdcdef".
</details>

<details>
<summary>482. License Key Formatting</summary>
You are given a license key represented as a string S which consists only alphanumeric character and dashes. The string is separated into N+1 groups by N dashes.

Given a number K, we would want to reformat the strings such that each group contains exactly K characters, except for the first group which could be shorter than K, but still must contain at least one character. Furthermore, there must be a dash inserted between two groups and all lowercase letters should be converted to uppercase.

Given a non-empty string S and a number K, format the string according to the rules described above.

Example 1:
Input: S = "5F3Z-2e-9-w", K = 4

Output: "5F3Z-2E9W"

Explanation: The string S has been split into two parts, each part has 4 characters.
Note that the two extra dashes are not needed and can be removed.
</details>

<details>
<summary>217. Contains Duplicate</summary>
Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

Example 1:

Input: [1,2,3,1]
Output: true
Example 2:

Input: [1,2,3,4]
Output: false
</details>

<details>
<summary>159. Longest Substring with At Most Two Distinct Characters</summary>
Given a string s , find the length of the longest substring t  that contains at most 2 distinct characters.

Example 1:

Input: "eceba"
Output: 3
Explanation: tis "ece" which its length is 3.
Example 2:

Input: "ccaabbb"
Output: 5
Explanation: tis "aabbb" which its length is 5.
</details>

<details>
<summary>340. Longest Substring with At Most K Distinct Characters </summary>
Given a string, find the length of the longest substring T that contains at most k distinct characters.

For example, Given s = “eceba” and k = 2,

T is "ece" which its length is 3.

</details>

<details>
<summary>266. Palindrome Permutation</summary>
Given a string, determine if a permutation of the string could form a palindrome.

Example 1:

Input: "code"
Output: false
Example 2:

Input: "aab"
Output: true
</details>

<details>
<summary>336. Palindrome Pairs</summary>
Given a list of unique words, find all pairs of distinct indices (i, j) in the given list, so that the concatenation of the two words, i.e. words[i] + words[j] is a palindrome.

Example 1:

Input: ["abcd","dcba","lls","s","sssll"]
Output: [[0,1],[1,0],[3,2],[2,4]] 
Explanation: The palindromes are ["dcbaabcd","abcddcba","slls","llssssll"]
</details>

<details>
<summary>214. Shortest Palindrome</summary>
Given a string s, you are allowed to convert it to a palindrome by adding characters in front of it. Find and return the shortest palindrome you can find by performing this transformation.

Example 1:

Input: "aacecaaa"
Output: "aaacecaaa"
Example 2:

Input: "abcd"
Output: "dcbabcd"
</details>

# Longest Substring Without Repeating Characters

This Java program finds the **length of the longest substring without duplicate characters** in a given string.  
It uses the **sliding window technique** with a `HashSet` for efficient checking.

---

## 🚀 Problem Statement
Given a string `s`, find the length of the **longest substring without repeating characters**.

### ✅ Examples
#### Example 1:
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with a length of 3.

---

## 💻 Solution Approach
- Use **two pointers** (`left` and `right`) as a sliding window.
- Store characters in a `HashSet` to check duplicates.
- Expand the window by moving `right`.
- If duplicate found, move `left` pointer until duplicate is removed.
- Keep track of **max window size**.

### ⏳ Time Complexity:
- **O(n)** – Each character is processed at most twice (once added, once removed).

### 📦 Space Complexity:
- **O(min(n, charset_size))**

---

## 📜 Code

```java
import java.util.HashSet;
import java.util.Scanner;

public class Main {
    public static int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();
        int left = 0, maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }
        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        int result = lengthOfLongestSubstring(s);
        System.out.println("Length of longest substring without duplicates: " + result);
    }
}

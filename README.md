Longest Palindrome in an Array in Java
Here, in this page we will discuss the program to find the longest palindrome in an array in java programming language. We are given with an array and need to print the longest palindromic element in the given input array.

java code Longest palindrome in an array
Method Discussed :
Method 1 : Using Naive Approach
Method 2 : Using Sorting
Method 1 :
Create a function ispalindrome(int n), it will return 1 if the passing number is palindrome otherwise return 0.
Inside the main function, create a variable say res = -1, that hold the maximum palindrome number.
Run a loop from [0, n),  and check if(ispalindrome(arr[i]) && res<arr[i]), then set res = arr[i].
Print the value of res.
Method 1 : Code in Java
Run
import java.util.*;

class Main
{
    // Function to check if n is palindrome
    static boolean isPalindrome(int n)
    {
          // Find the appropriate divisor
          // to extract the leading digit
          int divisor = 1;
          while (n / divisor >= 10)
             divisor *= 10;

          while (n != 0) {
             int x = n / divisor;
             int y = n % 10;

             // If first and last digits are
             // not same then return false
             if (x != y)
               return false;

             // Removing the leading and trailing
             // digits from the number
             n = (n % divisor) / 10;

             // Reducing divisor by a factor
             // of 2 as 2 digits are dropped
            divisor = divisor / 100;
         }
         return true;
    }

    // Function to find the largest palindromic number
    static int largestPalindrome(int []A, int n)
    {
         int res = -1;

         for (int i = 0; i < n; i++) { // If a palindrome larger than the currentMax is found 
                 if (A[i] > res && isPalindrome(A[i]))
                     res = A[i];
         }

        // Return the largest palindromic number from the array
        return res;
     }

    // Driver program
    public static void main(String []args)
    {
       int []A = { 121, 2322, 54545, 999990 };
       int n = A.length;

      // print required answer
      System.out.println(largestPalindrome(A, n));
    }

}
Output
54545
Related Pages
Finding the frequency of elements in an array

Sorting elements of an array by frequency

Counting Distinct Elements in an Array

Finding  Repeating elements in an Array

Finding Non Repeating elements in an Array

Method 2 :
In this method we first sort the array and then start traversing the array from end, and return the element that satisfy the condition, that it is palindrome.

Sort the array using inbuilt sort() function.
Start traversing from end of the array,
Print the element if it is palindrome.
If no element found then print -1.
Longest Palindrome in Java
Method 2 : Code in Java
Run
import java.util.*;
class Main
{
// Function to check if n is palindrome
static boolean isPalindrome(int n)
{
// Find the appropriate divisor
// to extract the leading digit
int divisor = 1;
while (n / divisor >= 10)
divisor *= 10;

while (n != 0) {
int x = n / divisor;
int y = n % 10;

// If first and last digits are
// not same then return false
if (x != y)
return false;

// Removing the leading and trailing
// digits from the number
n = (n % divisor) / 10;

divisor = divisor / 100;
}
return true;
}

// Function to find the largest palindromic number
static int largestPalindrome(int []A, int n)
{
Arrays.sort(A);
for (int i = n-1; i >= 0; i--) {
// If a palindrome larger than the currentMax is found
if (isPalindrome(A[i]))
return A[i];
}

// Return the largest palindromic number from the array
return -1;
}

// Driver program
public static void main(String []args)
{
int []A = { 121, 2322, 54545, 999990 };
int n = A.length;

// print required answer
System.out.println(largestPalindrome(A, n));
}

}
Output
545545

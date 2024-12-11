#include <iostream>
#include <stack>
 
using namespace std;
 
// Function to print original and reversed string using stack
void printReversedString(const string& str) {
    stack<char> charStack;
 
    // Push all characters of the string into the stack
    for (char ch : str) {
        charStack.push(ch);
    }
 
    // Print original string
    cout << "Original String: " << str << endl;
 
    // Print reversed string by popping characters from stack
    cout << "Reversed String: ";
    while (!charStack.empty()) {
        cout << charStack.top();
        charStack.pop();
    }
    cout << endl;
}
 
// Function to check whether a given string is a palindrome
bool isPalindrome(const string& str) {
    string filteredStr = "";
 
    // Filter out non-alphabet characters and convert to lowercase manually
    for (char ch : str) {
        if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')) {
            // Convert to lowercase manually by checking the range of characters
            if (ch >= 'A' && ch <= 'Z') {
                ch = ch + ('a' - 'A');  // Convert uppercase to lowercase
            }
            filteredStr += ch;
        }
    }
 
    // Compare the string with its reverse
    int left = 0, right = filteredStr.size() - 1;
    while (left < right) {
        if (filteredStr[left] != filteredStr[right]) {
            return false;
        }
        left++;
        right--;
    }
 
    return true;
}
 
int main() {
    string input;
 
    // Take input string from user
    cout << "Enter a string: ";
    getline(cin, input);  // This is the line causing the error if previous input was an integer
 
    // Clear any remaining characters in the buffer (including newline)
    cin.ignore(); // Ignore the leftover newline from the previous input
 
    // Call function to print original and reversed string
    printReversedString(input);
 
    // Call function to check if the string is a palindrome
    if (isPalindrome(input)) {
        cout << "The string is a palindrome." << endl;
    } else {
        cout << "The string is not a palindrome." << endl;
    }
 
    return 0;
}

# valid_paranthesis
leetcode
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        # Stack to keep track of opening brackets
        stack = []
        
        # Hash map to keep track of mappings
        bracket_map = {')': '(', '}': '{', ']': '['}
        
        # For every bracket in the expression
        for char in s:
            # If the character is a closing bracket
            if char in bracket_map:
                # Pop the topmost element from the stack if it's not empty, otherwise assign a dummy value
                top_element = stack.pop() if stack else '#'
                
                # The mapping for the opening bracket in our hash and the top element of the stack don't match, return False
                if bracket_map[char] != top_element:
                    return False
            else:
                # We have an opening bracket, simply push it onto the stack.
                stack.append(char)
        
        # If the stack is empty, return True because all opening brackets had valid closing brackets.
        return not stack

# Example usage
solution = Solution()
print(solution.isValid("()"))      # Output: True
print(solution.isValid("()[]{}"))  # Output: True
print(solution.isValid("(]"))      # Output: False

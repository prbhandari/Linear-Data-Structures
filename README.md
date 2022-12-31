# Linear-Data-Structures
Edyoda Assingements


Q1. Write a program to find all pairs of an integer array whose sum is equal to a given number?

Ans1.
          def pair_sum(arr, n, given_num):
              count = 0
              for i in range(0,n):
                  for j in range(i+1,n):
                      if arr[i]+arr[j] == given_num:
                          count+=1
              print("Number of pairs whose sum is equal to given number :",count)

          pair_sum([1,5,7,1],4,6)
          
          
          
          Output :- Number of pairs whose sum is equal to given number : 2
          
          
    
    
    
    
Q2. Write a program to reverse an array in place? In place means you cannot create a new array. You have to update the original array.    

Ans.
          def reverse_arr(arr):
              print("Reverse of given array is :",arr[::-1])

          reverse_arr([11,12,13,21,22,23])
          
          
          Output :- Reverse of given array is : [23, 22, 21, 13, 12, 11]
          
          
          
          
          
Q3. Write a program to check if two strings are a rotation of each other?

Ans3.
          str1 = input("Enter first string :")
          str2 = input("Enter second string :")
          n1 = len(str1)
          n2 = len(str2)
          concat = ''
          if n1 != n2:
              print("The two strings are not rotation of each other")
          else:
              concat = str1+str1
              if str2 in concat:
                  print("The two strings are rotation of each other")
              else:
                  print("The two strings are not rotation of each other")
                  
                  
          
          Input1 :-  Enter first string :ABCDE
                     Enter second string :DEACB
          Output1 :- The two strings are not rotation of each other
          
          
          Input2 :-  Enter first string :ABCDE
                     Enter second string :CDEAB
          Output2 :- The two strings are rotation of each other
          
          
          Input3 :-  Enter first string :ABCDE
                     Enter second string :CDE
          Output3 :- The two strings are not rotation of each other
          
          
          
          
          

Q4. Write a program to print the first non-repeated character from a string?

Ans4.
          def FirstNonRepeatedChar(str):
              for i in str:
                  count=0
                  for j in str:
                      if i==j:
                          count+=1
                      if count>1:
                          break
                  if count==1:
                      return i
                      
          FirstNonRepeatedChar("edyoda is a platform to learn everyday ")
          
          Output :-  'i'
          
          
          


Q5. Read about the Tower of Hanoi algorithm. Write a program to implement it.

Ans5. 
          def TowerOfHanoi(n , tower1, tower2, tower3):
              if n == 1:
                  print("Move disk 1 from rod",tower1,"to rod",tower2)
                  return
              TowerOfHanoi(n-1, tower1, tower3, tower2)
              print("Move disk",n,"from rod",tower1,"to rod",tower2)
              TowerOfHanoi(n-1, tower3, tower2, tower1)
          
          TowerOfHanoi(3,'A','B','C')
          
          Output :- Move disk 1 from rod A to rod B
                    Move disk 2 from rod A to rod C
                    Move disk 1 from rod B to rod C
                    Move disk 3 from rod A to rod B
                    Move disk 1 from rod C to rod A
                    Move disk 2 from rod C to rod B
                    Move disk 1 from rod A to rod B
                    





Q6. Read about infix, prefix, and postfix expressions. Write a program to convert postfix to prefix expression.

Ans6. 

          def check_operator(x):
              if x=='+':
                  return True
              if x=='-':
                  return True
              if x=='/':
                  return True
              if x=='*':
                  return True
              if x=='^':
                  return True

              return False


          def postfix_to_prefix(postfix_exp):

              stack = []

              l = len(postfix_exp)

              for i in range(l):
                  if (check_operator(postfix_exp[i])):
                      op1 = stack[-1]
                      stack.pop()
                      op2 = stack[-1]
                      stack.pop()

                      t = postfix_exp[i] + op2 + op1

                      stack.append(t)

                  else:
                      stack.append(postfix_exp[i])

              prefix = ""
              for i in stack:
                  prefix += i
              return prefix
          
         postfix_to_prefix('AB*CD-+')    
              
              
              
              Output :-   '+*AB-CD'
              
              
              




Q7. Write a program to convert prefix expression to infix expression.

Ans7. 
          def PrefixToInfix(prefix_exp):
              stack = []

              i = len(prefix_exp) - 1
              while i >= 0:
                  if not isOperator(prefix_exp[i]):

                      stack.append(prefix_exp[i])
                      i -= 1
                  else:

                      str = "(" + stack.pop() + prefix_exp[i] + stack.pop() + ")"
                      stack.append(str)
                      i -= 1

              return stack.pop()

          def isOperator(x):
              if x == "*" or x == "+" or x == "-" or x == "/" or x == "^" or x == "(" or x == ")":
                  return True
              else:
                  return False

          PrefixToInfix("*-A/BC-/AKL")    
          
          
          
          Output :-  '((A-(B/C))*((A/K)-L))'
          
          
         



Q8. Write a program to check if all the brackets are closed in a given code snippet.

Ans8.
          def Brackets(expr):
              stack = []

              for char in expr:
                  if char in ["(", "{", "["]:
                      stack.append(char)
                  else:
                      if not stack:
                          return False
                      current_char = stack.pop()
                      if current_char == '(':
                          if char != ")":
                              return False
                      if current_char == '{':
                          if char != "}":
                              return False
                      if current_char == '[':
                          if char != "]":
                              return False

              if stack:
                  return False
              return True

          expr = "{()}[]"
          if Brackets(expr):
              print("All Brackets closed")
          else:
              print("All Brackets not closed")
                    
                    
                    
          
          Output :-  All Brackets closed
          
          
          
          


Q9. Write a program to reverse a stack.

Ans9.
          class Stack:

              def __init__(self):
                  self.Elements = []

              def push(self, value):
                  self.Elements.append(value)

              def pop(self):
                  return self.Elements.pop()

              def empty(self):
                  return self.Elements == []

              def show(self):
                  for value in reversed(self.Elements):
                      print(value)


          def BottomInsert(s, value):
              if s.empty():
                  s.push(value)

              else:
                  popped = s.pop()
                  BottomInsert(s, value)
                  s.push(popped) 

          def Reverse(s):
              if s.empty():
                  pass
              else:
                  popped = s.pop()
                  Reverse(s)
                  BottomInsert(s, popped)


          stk = Stack()
          stk.push(10)
          stk.push(20)
          stk.push(30)
          stk.push(4)
          stk.push(5)

          print("Original Stack")
          stk.show()

          print("\nStack after Reversing")
          Reverse(stk)
          stk.show()
          
          
         
         Output :-  Original Stack
                    5
                    4
                    30
                    20
                    10

                    Stack after Reversing
                    10
                    20
                    30
                    4
                    5

                    
                    
                    


Q10. Write a program to find the smallest number using a stack.

Ans10.
          class Node:
              def __init__(self, value):
                  self.value = value
                  self.next = None

              def __str__(self):
                  return "Node({})".format(self.value)

              __repr__ = __str__


          class Stack:
              def __init__(self):
                  self.top = None
                  self.count = 0
                  self.minimum = None

              def __str__(self):
                  temp = self.top
                  out = []
                  while temp:
                      out.append(str(temp.value))
                      temp = temp.next
                  out = '\n'.join(out)
                  return ('Top {} \n\nStack :\n{}'.format(self.top,out))

              __repr__=__str__

              def getMin(self):
                  if self.top is None:
                      return "Stack is empty"
                  else:
                      print("Minimum Element in the stack is: {}" .format(self.minimum))



              def isEmpty(self):
                  if self.top == None:
                      return True
                  else:
                      return False

              def __len__(self):
                  self.count = 0
                  tempNode = self.top
                  while tempNode:
                      tempNode = tempNode.next
                      self.count+=1
                  return self.count

              def peek(self):
                  if self.top is None:
                      print ("Stack is empty")
                  else:
                      if self.top.value < self.minimum:
                          print("Top Most Element is: {}" .format(self.minimum))
                      else:
                          print("Top Most Element is: {}" .format(self.top.value))

              def push(self,value):
                  if self.top is None:
                      self.top = Node(value)
                      self.minimum = value

                  elif value < self.minimum:
                      temp = (2 * value) - self.minimum
                      new_node = Node(temp)
                      new_node.next = self.top
                      self.top = new_node
                      self.minimum = value
                  else:
                      new_node = Node(value)
                      new_node.next = self.top
                      self.top = new_node
                  print("Number Inserted: {}" .format(value))

              def pop(self):
                  if self.top is None:
                      print( "Stack is empty")
                  else:
                      removedNode = self.top.value
                      self.top = self.top.next
                      if removedNode < self.minimum:
                          print ("Top Most Element Removed :{} " .format(self.minimum))
                          self.minimum = ( ( 2 * self.minimum ) - removedNode )
                      else:
                          print ("Top Most Element Removed : {}" .format(removedNode))

          stack = Stack()

          stack.push(3)
          stack.push(5)
          stack.getMin()
          stack.push(2)
          stack.push(1)
          stack.getMin()    
          stack.pop()
          stack.getMin()
          stack.pop()
          stack.peek()
          
          
          
          
          Output :- Number Inserted: 3
                    Number Inserted: 5
                    Minimum Element in the stack is: 3
                    Number Inserted: 2
                    Number Inserted: 1
                    Minimum Element in the stack is: 1
                    Top Most Element Removed :1 
                    Minimum Element in the stack is: 2
                    Top Most Element Removed :2 
                    Top Most Element is: 5
                    

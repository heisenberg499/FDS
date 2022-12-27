"""
       Group A - Assignment 1
       In second year computer engineering class, group A students play cricket,
group B students play badminton and group C students play football. 
Write a python program using functions to compute following: - 
a)	List of students who play both cricket and badminton 
b)	List of students who play either cricket or badminton but not both 
c)	Number of students who play neither cricket nor badminton
d)	Number of students who play cricket and football but not badminton.
(Note- While realizing the group, duplicate entries should be avoided, Do not use SET built-in functions)

"""

def accept_set(A,Str): 
   n = int(input("Enter the total no. of student who play %s : "%Str))
   for i in range(n) :
      x = input("Enter the name of student %d who play %s : "%((i+1),Str))
      A.append(x)
   print("Set accepted successfully");

def display_set(A,Str): 
   n = len(A)
   if(n == 0) :
      print("\nGroup of Students who play %s =  { }"%Str)
   else :
      print("\nGroup of Students who play %s =  {"%Str,end=' ')
      for i in range(n-1) :
         print("%s,"%A[i],end=' ')
      print("%s }"%A[n-1]);
   
def search_set(A,X) :
    n = len(A)
    for i in range(n):
       if(A[i] == X) :
          return (1)
    return (0)


def find_intersection_set(A,B,C):
   for i in range(len(A)): 
      flag = search_set(B,A[i]);
      if(flag == 1) :
          C.append(A[i])

def find_difference_set(A,B,C):
    for i in range(len(A)): 
      flag = search_set(B,A[i]);
      if(flag == 0) :
          C.append(A[i])    


def find_union_set(A,B,C):
   for i in range(len(A)):
      C.append(A[i])
   for i in range(len(B)): 
      flag = search_set(A,B[i]);
      if(flag == 0) :
          C.append(B[i])    
       
def Main() :
   Group_A = []
   Group_B = []
   Group_C = []
   
   while True :
       print ("\t1 : Accept the Information")
       print ("\t2 : List of students who play both cricket and badminton")
       print ("\t3 : List of students who play either cricket or badminton but not both")
       print ("\t4 : Number of students who play neither cricket nor badminton")
       print ("\t5 : Number of students who play cricket and football but not badminton")
       print ("\t6 : Exit")
       ch = int(input("Enter your choice : "))
       Group_R = []       
       if (ch == 6):
           print ("End of Program")
           break
       elif (ch==1):
           accept_set(Group_A,"Cricket")
           accept_set(Group_B,"Badminton")
           accept_set(Group_C,"Football")
           display_set(Group_A,"Cricket")
           display_set(Group_B,"Badminton")
           display_set(Group_C,"Football")           
       elif (ch==2):
           display_set(Group_A,"Cricket")
           display_set(Group_B,"Badminton")
           find_intersection_set(Group_A,Group_B,Group_R)
           display_set(Group_R," both Cricket and Badminton")
       elif (ch==3):
           display_set(Group_A,"Cricket")
           display_set(Group_B,"Badminton")
           R1 = []
           find_union_set(Group_A,Group_B,R1)
           R2 = []
           find_intersection_set(Group_A,Group_B,R2)
           find_difference_set(R1,R2,Group_R)
           display_set(Group_R," either cricket or badminton but not both")
       elif (ch==4):
           display_set(Group_A,"Cricket")
           display_set(Group_B,"Badminton")
           display_set(Group_C,"Football")
           R1 = []
           find_union_set(Group_A,Group_B,R1)
           find_difference_set(Group_C,R1,Group_R)
           display_set(Group_R," neither cricket nor badminton")
           print("Number of students who play neither cricket nor badminton = %s"%len(Group_R))
       elif (ch==5):
           display_set(Group_A,"Cricket")
           display_set(Group_C,"Football")
           display_set(Group_B,"Badminton")
           R1 = []
           find_intersection_set(Group_A,Group_C,R1)           
           find_difference_set(R1,Group_B,Group_R)           
           display_set(Group_R,"cricket and football but not badminton")
           print("Number of students who play cricket and football but not badminton = %s"%len(Group_R))                 
       else :
           print ("Wrong choice entered !! Try again")


Main()
quit()

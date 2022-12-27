"""
       Group B - Assignment 15
Write a python program to store second year percentage of students in array.
Write function for sorting array of floating point numbers in ascending order
using 
a) Insertion sort 
b) Shell Sort and display top five scores


"""

def accept_array(A): 
   n = int(input("Enter the total no. of student : "))
   for i in range(n):
      x = float(input("Enter the  Second year percentage of student %d : "%(i+1)))
      A.append(x)
   print("Array accepted successfully\n\n");

def display_array(A): 
   n = len(A)
   if(n == 0) :
      print("\nNo records in the database")
   else :
      print("Array of SE Marks : ",end=' ')
      for i in range(n) :
         print("%.2f  "%A[i],end=' ')
      print("\n");


def Insertion_sort(A) :
   n = len(A)
   for i in range(1,n) :
      element = A[i]
      j  = i-1
      while( j >= 0) :
         if (A[j] <= element) :
            break
         else :
            A[j+1] = A[j]
            j = j - 1
      A[j+1] = element


def Insertion_sort_gap(A,n,gap,s) :
   for i in range(s+gap,n,gap) :
      element = A[i]
      j = i - gap
      while( j >=0 ) :
         if(A[j] <= element) :
            break;
         else :
            A[j+gap] = A[j]
            j = j - gap
      A[j+gap] = element;
  
def Shell_sort(A) :
   n = len(A)
   gap = int(n / 2)
   while( gap > 0) :
      for s in range(gap) :
         Insertion_sort_gap(A,n,gap,s)
      gap = int(gap / 2)



def Main() :   
   A = []
   while True :
      print ("\t1 : Accept & Display the SE Marks")
      print ("\t2 : Insertion Sort Ascending order")
      print ("\t3 : Shell sort Ascending order and display top five scores")
      print ("\t4 : Exit")
      ch = int(input("Enter your choice : "))
      if (ch == 4):
         print ("End of Program")
         quit()
      elif (ch==1):
         A = []
         accept_array(A)
         display_array(A)
      elif (ch==2):
         print("Marks before sorting")
         display_array(A)
         Insertion_sort(A)
         print("Marks after sorting")
         display_array(A)
      elif (ch==3):
         print("Marks before sorting")
         display_array(A)
         Shell_sort(A)
         print("Marks after sorting")
         display_array(A)
         n =len(A)
         if(n >= 5) :
            print("Top Five Scores : ")
            for i in range(n-1,n-6,-1) :
               print("\t%.2f"%A[i])
         else :
            print("Top Scorers : ")
            for i in range(n-1,-1,-1) :
               print("\t%.2f"%A[i])                  
      else :
           print ("Wrong choice entered !! Try again")


Main()


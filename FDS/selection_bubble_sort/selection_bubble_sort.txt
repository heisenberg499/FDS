"""
       Group B - Assignment 14
Write a pythonprogram to store first year percentage of students in array.
Write function for sorting array of floating point numbers in ascending order
using 
a) Selection Sort 
b) Bubble sort and display top five scores.

"""

def accept_array(A): 
   n = int(input("Enter the total no. of student : "))
   for i in range(n):
      x = float(input("Enter the  first year percentage of student %d : "%(i+1)))
      A.append(x)
   print("Array accepted successfully\n\n");

def display_array(A): 
   n = len(A)
   if(n == 0) :
      print("\nNo records in the database")
   else :
      print("Array of FE Marks : ",end=' ')
      for i in range(n) :
         print("%.2f  "%A[i],end=' ')
      print("\n");


def Selection_sort(A) :
   n = len(A)
   for pos in range(n-1):
      min_ind = pos
      for i in range(pos + 1, n) :
         if(A[i] < A[min_ind]) :
            min_ind = i
      temp = A[pos]
      A[pos] = A[min_ind]
      A[min_ind] = temp

def Bubble_sort(A) :
   n = len(A)
   for Pass in range(1,n) :
      for i in range(n-Pass) :
         if(A[i] < A[i+1]) :
            temp = A[i]
            A[i] = A[i+1]
            A[i+1] = temp
      
def Main() :   
   A = []
   while True :
      print ("\t1 : Accept & Display the FE Marks")
      print ("\t2 : Selection Sort Ascending order")
      print ("\t3 : Bubble sort Descending order and display top five scores")
      print ("\t4 : Exit")
      ch = int(input("Enter your choice : "))
      if (ch == 4):
         print ("End of Program")
         quit()
      elif (ch==1):
         accept_array(A)
         display_array(A)
      elif (ch==2):
         print("Marks before sorting")
         display_array(A)
         Selection_sort(A)
         print("Marks after sorting")
         display_array(A)
      elif (ch==3):
         print("Marks before sorting")
         display_array(A)
         Bubble_sort(A)
         print("Marks after sorting")
         display_array(A)
         if(len(A) >= 5) :
            print("Top Five Scores : ")
            for i in range(5) :
               print("\t%.2f"%A[i])
         else :
            print("Top Scorers : ")
            for i in range(len(A)) :
               print("\t%.2f"%A[i])                  
      else :
           print ("Wrong choice entered !! Try again")


Main()


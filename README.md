# 100_DAYS_DSA

DAY 4/100
#BASIC PROBLEMS ON RECURSIO

TOWER OF HANOI

import java.io.*;
import java.util.*;
public class Recursion2 
{

    public static void towerOfHanoi(int n,String src,String helper, String dest )
    {
        if(n==1)
           {
              System.out.println(" trasfer disk "+ n+ " from "+src+ " to "+ dest );
               return;
           }
        towerOfHanoi(n-1, src, dest, helper);
        System.out.println(" trasfer disk "+ n +"  from "+src+ "  to "+ dest );
        towerOfHanoi(n-1, helper, src, dest);
    }

    public static void main(String[] args) {
        int n=4 ;
        towerOfHanoi(n, "s", "h", "d");


    }
 }


PRINT REVERSE OF STRING

import java.io.*;
import java.util.*;
 public class Recursion3 {
     public static void printRev(String str , int idx)
     {
         if(idx == 0 ){
            System.out.println(str.charAt(idx));
             return;
         }
         System.out.println(str.charAt(idx));
         printRev(str,idx-1);

     }
    public static void main(String[] args) {
    String str="abcd";
    printRev(str,str.lenght()-1);
    }
 } 
 
 
FIRST OCCURANCE PROBLEM

import java.io.*;
import java.util.*;
 public class Recursion3 {
     public static int first= -1;
     public static int last = -1;
     public static void findOccurance(String str , int idx,char element)
     { if(idx == str.length()){
         System.out.println(first);
         System.out.println(last);
         return;
          
     }
         char currChar=str.charAt(idx);
         if(currChar== element)
         {
             if(first == -1)
             {
                 first = idx;
             }
             else 
             {
                 last=idx;
             }
         }findOccurance(str, idx+1, element);
     }
    public static void main(String[] args) {
    String str="absaabcddcdcd";
    findOccurance(str,0,'b');
    }
 } 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

 DAY 05/100

Check if array is sorted using recursion

public class IsSortedUsingRecursion {

 public static boolean isSorted(int [] a, int start){
 if(start==a.length–1)
 return true;
 if(a[start]<=a[start+1])
 return isSorted(a, start+1);
 else
 return false;
 }
 public static void main(String[] args) {
 int [] a = { 1,2,3,4,8,8,22,50};
 System.out.println(isSorted(a,0));
 }
}


Move all occurrence of letter ‘x’ from the string s to the end using Recursion

import java.util.*;
class Check{


static void moveAtEnd(String s, int i, int l)
{
	if (i >= l)
		return;

	// Store current character
	char curr = s.charAt(i);

	// Check if current character is not 'x'
	if (curr != 'x')
		System.out.print(curr);

	// recursive function call
	moveAtEnd(s, i + 1, l);

	// Check if current character is 'x'
	if (curr == 'x')
		System.out.print(curr);

	return;
}

public static void main(String args[])
{
	String s = "twttwtxxxrxxgfdsxx";

	int l = s.length();

	moveAtEnd(s, 0, l);
}
}





# 100_DAYS_DSA

DAY 4/100

TOWER OF HANOI

import java.io.*;
import java.util.*;
 public class Recursion2 {

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


$printreverse

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

first occurance programm
import java.io.*;
import java.util.*;
 public class Recursion3 {
     public static int first=-1;
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

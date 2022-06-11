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
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
DAY 06/100
 DID THREE QUESTION ON 2D ARRAY ON HACKERRANK
 
 #include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);
vector<string> split(const string &);

/*
 * Complete the 'hourglassSum' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts 2D_INTEGER_ARRAY arr as parameter.
 */

int hourglassSum(vector<vector<int>> arr) {
    int result =INT_MIN;
    for(int r=0;r<=3;r++)
    {
        for(int c=0;c<=3;c++)
        {
            int sum =arr[r][c]+arr[r][c+1]+arr[r][c+2]+arr[r+1][c+1]+arr[r+2][c]+arr[r+2][c+1]+arr[r+2][c+2];
            
            result=std::max(result,sum);
        }
    }
    return result;
}

int main()
{
    ofstream fout(getenv("OUTPUT_PATH"));

    vector<vector<int>> arr(6);

    for (int i = 0; i < 6; i++) {
        arr[i].resize(6);

        string arr_row_temp_temp;
        getline(cin, arr_row_temp_temp);

        vector<string> arr_row_temp = split(rtrim(arr_row_temp_temp));

        for (int j = 0; j < 6; j++) {
            int arr_row_item = stoi(arr_row_temp[j]);

            arr[i][j] = arr_row_item;
        }
    }

    int result = hourglassSum(arr);

    fout << result << "\n";

    fout.close();

    return 0;
}

string ltrim(const string &str) {
    string s(str);

    s.erase(
        s.begin(),
        find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );

    return s;
}

string rtrim(const string &str) {
    string s(str);

    s.erase(
        find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
        s.end()
    );

    return s;
}

vector<string> split(const string &str) {
    vector<string> tokens;

    string::size_type start = 0;
    string::size_type end = 0;

    while ((end = str.find(" ", start)) != string::npos) {
        tokens.push_back(str.substr(start, end - start));

        start = end + 1;
    }

    tokens.push_back(str.substr(start));

    return tokens;
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
DAY 08/100 
	STARTED DYNAMIC PROGRAMMING
	
	class DYNAMIC {
 
    /*This function divides a by greatest
    divisible power of b*/
    static int maxDivide(int a, int b)
    {
        while (a % b == 0)
            a = a / b;
        return a;
    }
 
    /* Function to check if a number
    is ugly or not */
    static int isUgly(int no)
    {
        no = maxDivide(no, 2);
        no = maxDivide(no, 3);
        no = maxDivide(no, 5);
 
        return (no == 1) ? 1 : 0;
    }
 
    /* Function to get the nth ugly
    number*/
    static int getNthUglyNo(int n)
    {
        int i = 1;
 
        // ugly number count
        int count = 1;
 
        // check for all integers
        // until count becomes n
        while (n > count) {
            i++;
            if (isUgly(i) == 1)
                count++;
        }
        return i;
    }
 
    /* Driver Code*/
    public static void main(String args[])
    {
        int no = getNthUglyNo(150);
       
        // Function call
        System.out.println("150th ugly "
                           + "no. is " + no);
    }


```
import java.util.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	    String s=sc.nextLine();
	    String[] st=s.split(" ");
	    String k="";
	    for(String i:st){
	        k+=i.charAt(0);
	    }
		System.out.println(k);
	}
}
```
Sample Input
Hello how r u
Your Output
Hhru

```
import java.util.*;
//print true if the string contains more than 2 even digits
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	    String s=sc.nextLine();
	    int k=0;
	    for(int i=0;i<s.length();i++){
	        if(Integer.parseInt(String.valueOf(s.charAt(i)))%2==0){
	            k++;
	        }
	        if(k>=3){break;}
	    }
	    if(k>=3){System.out.println("True");}
	    else{System.out.println("false");}
	}
}
```
Sample Input
777777456677
Your Output
True
```
import java.util.*;
//print string without repeating characters
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	    String s=sc.nextLine();
	    String k="";
	    for(char i:s.toCharArray()){
	        if(k.indexOf(i)==-1){       // or if(!(k.contains(Character.toString(i))))
	            k+=i;
	        }
	    }System.out.println(k);
	}
}
```
Sample Input
7aavb77456677
Your Output
7avb456
```
import java.util.*;
//print factorial of a number
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	    int n=sc.nextInt();
	    long k=1;//don't use int
	    for(int i=1;i<n;i++){
	        k*=i;
	    }System.out.println(k*n);
	    
	}
}
```
Sample Input
13
Your Output
6227020800
```
import java.util.*;
//print sum of prime digits
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	    String s=sc.nextLine();
	    int k=0;
	    for(int i=0;i<s.length();i++){
	        if(isPrime(s.charAt(i))){
	            k+=Integer.parseInt(String.valueOf(s.charAt(i)));
	        }
	    }System.out.println(k);
	    
	    
	}
	public static boolean isPrime(char ch){
	    int c=Integer.parseInt(String.valueOf(ch));
	    if(c<=1){return false;}
	    else if(c<=3){return true;}
	    else{
	        for(int i=2;i<(int) Math.sqrt(c)+1;i++){
	            if(c%i==0){return false;}
	        }
	    }return true;
	}
}
```
Sample Input
3562
Your Output
10
```
import java.util.*;
public class StringToArray {
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        char[] arr = new char[str.length()];
        for(int i=0; i<str.length(); i++)
        {
            arr[i]=str.charAt(i);
        }
        System.out.println(Arrays.toString(arr));
    }
}
```

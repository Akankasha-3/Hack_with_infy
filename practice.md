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

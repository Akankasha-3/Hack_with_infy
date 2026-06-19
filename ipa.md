# TCS IPA Java Coding Practice

This repository contains my Java solutions for the TCS IPA (Integrated Profile Assessment) coding round exam.

## 📌 Problem Description: Character Frequency Counter

Write a program to accept a string value from the user. Print the frequency of each unique character in the order they first appear in the string. Ignore whitespaces.

### Example
* **Input:** `TCS IPA CODE`
* **Output:** `T:1 C:2 S:1 I:1 P:1 A:1 O:1 D:1 E:1`

---

## 🛠️ Java Implementation Logic

Unlike Python, Java requires distinct memory and syntax rules for structures:
* Uses `LinkedHashMap<Character, Integer>` to maintain the correct insertion order.
* Converts strings to a character array using `.toCharArray()` to iterate through them.
* Replaces Python's `m[key] = value` bracket notation with `.put(key, value)`.

```java
// Paste your working Java code here for quick reference
import java.util.Scanner;
import java.util.LinkedHashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        
        LinkedHashMap<Character, Integer> m = new LinkedHashMap<>();
        
        for(char i : s.toCharArray()){
            if(i != ' '){
                m.put(i, m.getOrDefault(i, 0) + 1);
            }
        }
        
        for(Map.Entry<Character, Integer> entry : m.entrySet()){
            System.out.print(entry.getKey() + ":" + entry.getValue() + " ");
        }
        sc.close();
    }
}
```

## 🚀 How to Run the Code Local Environment

1. Compile the program:
   ```bash
   javac 
```
import java.util.* ;
class Solve{
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        String s=sc.nextLine();
        HashMap<Character ,Integer>m=new HashMap<Character,Integer>();
        

        LinkedHashMap<Character, Integer> mi = new LinkedHashMap<>();//for order

        for(char i : s.toCharArray()){
            if(i!=' '){
                if(m.containsKey(i)){
                    m.put(i,m.get(i)+1);
                    mi.put(i,m.get(i)+1);
                    
                }
                else{
                    m.put(i,1);
                    mi.put(i,1);
                }
            }
        }
        for(Map.Entry<Character, Integer> entry : m.entrySet()){
            System.out.print(entry.getKey() + ":" + entry.getValue() + " ");
        }
        System.out.println();
        for(Map.Entry<Character, Integer> entry : mi.entrySet()){
            System.out.print(entry.getKey() + ":" + entry.getValue() + " ");
        }
        
        // int a=sc.nextInt();sc.nextLine();
        // int c=Integer.parseInt(sc.nextLine());
        // System.out.println(c);
        // String b=sc.nextLine();
        // b=b.trim();
        // System.out.println(a);
        // System.out.print(a+" is "+(8+2)+" ");
        // System.out.println(9);
        // System.out.println(b+"ab");
        // System.out.println(b.length());
        // int ar[]={1,2,3};
        // System.out.println(ar.length);
    }
}
```
**sorting the objects based on price**
```
import java.util.*;

class Book{
    private int id;
    private String name;
    private String author;
    private double price;
    Book(int id,String name,String author,double price){
        this.id=id;
        this.name=name;
        this.author=author;
        this.price=price;
    }
    public int getId() { return id; }
    public String getName() { return name; }
    public String getAuthor() { return author; }
    public double getPrice() { return price; }
    
    
}
class Solution{
    public static void main(String [] args){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();sc.nextLine();
        Book a[]=new Book[n];
        for(int i=0;i<n;i++){
            int id=sc.nextInt();sc.nextLine();
            String name=sc.nextLine();
            String author=sc.nextLine();
            Double p=sc.nextDouble();
            a[i]=new Book(id,name,author,p);
            
        }
        Book[] sortedBooks = sortBookByPrice(a);
        if (sortedBooks != null) {
            for (Book b : sortedBooks) {
                System.out.println(b.getId() + " " + b.getName() + " " + b.getAuthor() + " " + b.getPrice());
            }
        }
        sc.close();
   
        
    }
     public static Book[] sortBookByPrice(Book[] books) {
        if (books == null || books.length == 0) {
            return null;
        }

        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book b1, Book b2) {
                return Double.compare(b1.getPrice(), b2.getPrice());
            }
        });

        return books;
    }
}
```
Sample Input:(LINE BY LINE INPUT)
2

1
ak
am
270

2
az
ao
50

Your Output: 2 az ao 50.0
1 ak am 270.0

Input form is same line then:
```
      for (int i = 0; i < n; i++) {
            // Read inputs directly even if they are given space-separated or line-by-line
            int id = sc.nextInt();
            String name = sc.next();
            String author = sc.next();
            double price = sc.nextDouble();
            if(sc.hasNextLine()) sc.nextLine(); // Safe trailing cleanup
            
            books[i] = new Book(id, name, author, price);
        }
        ```
```
	import java.util.*;
	import java.lang.*;
	import java.io.*;
	
	class Codechef
	{
		public static void main (String[] args) throws java.lang.Exception
		{
			Scanner sc=new Scanner(System.in);// your code goes here
			String a=sc.nextLine();
			int x=0,b=0;
			for(int i=0;i<a.length();i++){
			     char ch = a.charAt(i); 
			    
			    if(Character.isUpperCase(ch)){
			        x+=1;
			    }
			    else{
			        b+=1;
			    }
			    
			}System.out.println(x + " " + b);
		}
	}
```
```
	import java.util.*;
	import java.lang.*;
	import java.io.*;
	
	class Codechef
	{
		public static void main (String[] args) throws java.lang.Exception
		{
			Scanner sc=new Scanner(System.in);// your code goes here
			String a=sc.nextLine();
			int x=0,b=0;
			for(int i=0;i<a.length();i++){
			     char ch = a.charAt(i); 
			    
			    if (Character.isLetter(ch)){
			        if(ch=='a'||ch=='e'||ch=='i'||ch=='o'|| ch=='u'||ch=='A'||ch=='E'||ch=='I'||ch=='O'||ch=='U'){
			        x+=1;
			    
			    
			    }
			    else{
			        b+=1;
			    }}
			    
			}System.out.println("Vowels: "+ x + "\n" +"Consonants: " +b);
		}
	}
```
Sample Input
i have67
Your Output
Vowels: 3
Consonants: 2
```
	import java.util.*;
	//@nd largest unique value
	
	class Codechef
	{
		public static void main (String[] args) throws java.lang.Exception
		{
			Scanner sc=new Scanner(System.in);// your code goes here
			int n=sc.nextInt();
			int a[]=new int[n];
			for(int i=0;i<n;i++){
			    a[i]=sc.nextInt();
			}
			int x = Integer.MIN_VALUE; // Tracks highest
			int y = Integer.MIN_VALUE;
			for(int i=0;i<n;i++){
			    if(x<a[i]){
			        y=x;
			        x=a[i];
			        
			    }
			    else if(x>a[i] && a[i]>y){
			        y=a[i];
			    }
			}System.out.println(y);
	// 		Arrays.sort(a);
	// 		System.out.println(a[a.length-2]);
		}
	}
```
Sample Input
4 4 2 6 6
Your Output
4

count the footwera with given type and find the  second highest price of a footwera whose name is eaqual to given brand
```
import java.util.*;

	class Footwear {
	    private int id;
	    private String name;
	    private String type;
	    private double price;
	    
	    Footwear(int id, String name, String type, double price) {
	        this.id = id;
	        this.name = name;
	        this.type = type;
	        this.price = price;
	    }
	    
	    public int getId() { return id; }
	    public String getName() { return name; }
	    public String getType() { return type; }
	    public double getPrice() { return price; }
	}
	
	class sol {
	    public static void main(String ars[]) {
	        Scanner sc = new Scanner(System.in);
        
        // Fix 1: Hardcoded array to size 4 as requested by the specific question
        Footwear[] foot = new Footwear[4];
        for(int i = 0; i < 4; i++) {
            int id = sc.nextInt(); sc.nextLine();
            String name = sc.nextLine().trim();
            String type = sc.nextLine();
            double price = sc.nextDouble(); sc.nextLine();
            foot[i] = new Footwear(id, name, type, price);
        }
        
        String inputType = sc.nextLine();
        String inputBrand = sc.nextLine();
        
        // Output 1
        int count = getCountByType(foot, inputType);
        System.out.println(count); // Print count directly (even if 0)
        
        // Output 2: Checked for full object return
        Footwear resultObj = secondHighestByBrand(foot, inputBrand);
        if(resultObj == null) {
            System.out.println("No Footwear found");
        } else {
            // Print the ID of the matched footwear item as requested
            System.out.println(resultObj.getId());
        }
    }
    
    public static int getCountByType(Footwear[] foot, String type) {
        int c = 0;
        for(Footwear i : foot) {
            if(type.equalsIgnoreCase(i.getType())) {
                c += 1;
            }
        }
        return c;
    }
    
    // Fix 2: Changed return type to Footwear object reference
    public static Footwear secondHighestByBrand(Footwear[] foot, String brand) {
        Footwear firstHighest = null;
        Footwear secondHighest = null;
        
        for(Footwear item : foot) {
            if(brand.equalsIgnoreCase(item.getName())) {
                if(firstHighest == null || item.getPrice() > firstHighest.getPrice()) {
                    secondHighest = firstHighest;
                    firstHighest = item;
                }
                else if((secondHighest == null || item.getPrice() > secondHighest.getPrice()) 
                        && item.getPrice() < firstHighest.getPrice()) {
                    secondHighest = item;
                }
            }
        }
        return secondHighest; // Returns null if less than two items exist for that brand
    }
	}
```
Sample Input
1
te
ka
2509
2
ab
ka
3902
3
ab 
ja
506.3
6
fj
jk
90.0
ka
ab
Your Output
2
3
```

	   import java.util.*
	class Footwear{
	    private int id;
	    private String name;
	    private String type;
	    private double price;
	    Footwear(int id,String name,String type,double price){
	        this.id=id;
	        this.name=name;
	        this.type=type;
	        this.price=price;
	    }
	    public int getId(){
	        return id;
	    }
	    public String getName(){
	        return name;
	    } public String getType(){
	        return type;
	        
	    }
	    public double getPrice(){
	        return price;
	    }
	}
	class sol{
	    public static void main(String ars[]){
	        Scanner sc=new Scanner(System.in);
	        // int n=sc.nextInt();sc.nextLine();
	        Footwear[] foot=new Footwear[4];
	        for(int i=0;i<4;i++){
	            int id=sc.nextInt();sc.nextLine();
	            String name=sc.nextLine().trim();
	            String type=sc.nextLine();
	            double price=sc.nextDouble();sc.nextLine();
	            foot[i]=new Footwear(id,name,type,price);
	        }
	        String a=sc.nextLine();
	        String b=sc.nextLine();
	        int c=getCountByType(foot,a);
	        if(c==0){
	            System.out.println("No matches found");
	        }
	        else{
	          
	            System.out.println(c);
	        }
	        double m=secondHighestByBrand(foot,b);
	        if(m==Integer.MIN_VALUE){
	            System.out.println("no second highest found");
	        }
	        else{
	            System.out.println(m);
	        }
	    }
	    public static int getCountByType(Footwear[] foot,String type){
	        int c=0;
	        for(Footwear i:foot){
	            if(type.equalsIgnoreCase(i.getType())){
	                c+=1;
	            }
	        }return c;
	    }
	    public static double secondHighestByBrand(Footwear[] foot,String brand){
	        double f=0,s=0;
	        for(Footwear i:foot){
	            if(brand.equalsIgnoreCase(i.getName())){
	                if(f<i.getPrice()){
	                    s=f;
	                    f=i.getPrice();
	                    }
	                else if(i.getPrice()<f && i.getPrice()>s){
	                    s=i.getPrice();
	                }
	            }
	        }return s;
	    }
	}

```
Sample Input
1
te
ka
2509
2
ab
ka
3902
3
ab 
ja
506.3
6
fj
jk
90.0
ka
ab
Your Output
2
506.3

**table program**
```
	import java.util.*;
	class sol{
	    public static void main(String args[]){
	        Scanner sc=new Scanner(System.in);
	        int n=sc.nextInt();
	        for(int i=1;i<11;i++){
	            System.out.println(n+" * "+i +" = "+n*i);
	        }
	    }
	}
```
Sample Input
4
Your Output
4 * 1 = 4
4 * 2 = 8
4 * 3 = 12
4 * 4 = 16
4 * 5 = 20
4 * 6 = 24
4 * 7 = 28
4 * 8 = 32
4 * 9 = 36
4 * 10 = 40
**Character count**
```
	import java.util.*;
	class sol{
	    public static void main(String args[]){
	        Scanner sc=new Scanner(System.in);
	        String s=sc.nextLine();
	        char c=sc.nextLine().charAt(0);
	        int a=0;
	        for(int i=0;i<s.length();i++){
	            if(c==s.charAt(i)){
	                a++;
	            }
	        }
	        System.out.println(a);
	    }
	}
```
Sample Input
aakakaa
k
Your Output
2
**print non-repeating characters**
```
	import java.util.*;
	class sol{
	    public static void main(String args[]){
	        Scanner sc=new Scanner(System.in);
	        String s=sc.nextLine();
	        String k="";
	        int n=s.length();
	        for(int i=0;i<n;i++){
	            if(s.indexOf(s.charAt(i))+n-s.lastIndexOf(s.charAt(i))==n){
	                k+=s.charAt(i);
	            }
	        }System.out.println(k);
	        
	    }
	}
```
Sample Input
abaccdftdf
Your Output
bt
**print string without repeating characters**
```
	import java.util.*;
	class Unique_Character {
	    public static void main(String[] args) {
	        Scanner scan=new Scanner(System.in);
	        String str=scan.nextLine();
	        str=str.toLowerCase();
	        int[] freq=new int[256];
	        String ans="";
	        for(int i=0;i<str.length();i++){
	            char ch=str.charAt(i);
	            if(freq[ch]==0){
	                ans+=ch;
	            }
	            freq[ch]++;
	        }
	        // int a='A';
	        // System.out.println(a);
	        // for(int i=0;i<256;i++){
	        //   if(freq[i]>0){ System.out.println(freq[i]+" "+i+" ");}
	        // }
	        System.out.println(ans);
	    }
	}
```
Sample Input
abaccdftdf
Your Output
abcdft
**sum_Num**
```
	import java.util.*;
	class sol{
	    public static void main(String args[]){
	        Scanner sc=new Scanner(System.in);
	        String s=sc.nextLine();
	        int k=0;
	        int a=0;
	        for(int i=0;i<s.length();i++){
	            if(Character.isDigit(s.charAt(i))){
	                a=a*10+Integer.parseInt(String.valueOf(s.charAt(i)));
	            }
	            else{
	                k+=a;
	                a=0;
	            }
	        }k+=a;
	        System.out.println(k);
	        
	    }
	}
```
Sample Input
109abn*19 2 hj1
Your Output
131

**sorting objects**
```
	import java.util.*;
	class Codechef
	{
		public static void main (String[] args) throws java.lang.Exception
		{
			My[] a=new My[]{new My(3,"KA",9.8),new My(1,"Ba",10),new My(2,"Ak",27)};
			//My[] a=new My[]; this also works
	// 		a[0]=new My(3,"KA",9.8);
	// 		a[1]=new My(1,"Ba",10);
	// 		a[2]=new My(2,"Ak",27);
			System.out.println("sort by name");
			Arrays.sort(a,Comparator.comparing(My::getName));
			for(My i:a){
			    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
			}System.out.println("Sort by price");
			Arrays.sort(a,Comparator.comparing(My::getPrice));
			for(My i:a){
			    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
			}System.out.println("sort by id in reverse order");
			Arrays.sort(a,Comparator.comparing(My::getId).reversed());
			for(My i:a){
			    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
			}
		}
	}
	class My{
	    int id;String name;double price;
	    My(int id,String name,double pri){
	        this.id=id;
	        this.name=name;
	        this.price=pri;
	    }
	    public String getName(){return name;}
	    public int getId(){return id;}
	    public double getPrice(){return price;}
	}
```
import java.util.*;
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		My[] a=new My[]{new My(3,"KA",9.8),new My(1,"Ba",10),new My(2,"Ak",27)};
		//My[] a=new My[]; this also works
// 		a[0]=new My(3,"KA",9.8);
// 		a[1]=new My(1,"Ba",10);
// 		a[2]=new My(2,"Ak",27);
		System.out.println("sort by name");
		Arrays.sort(a,Comparator.comparing(My::getName));
		for(My i:a){
		    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
		}System.out.println("Sort by price");
		Arrays.sort(a,Comparator.comparing(My::getPrice));
		for(My i:a){
		    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
		}System.out.println("sort by id in reverse order");
		Arrays.sort(a,Comparator.comparing(My::getId).reversed());
		for(My i:a){
		    System.out.println(i.getId()+" "+i.getName()+" "+i.getPrice());
		}
	}
}
class My{
    int id;String name;double price;
    My(int id,String name,double pri){
        this.id=id;
        this.name=name;
        this.price=pri;
    }
    public String getName(){return name;}
    public int getId(){return id;}
    public double getPrice(){return price;}
}
```
output
sort by name
2 Ak 27.0
1 Ba 10.0
3 KA 9.8
Sort by price
3 KA 9.8
1 Ba 10.0
2 Ak 27.0
sort by id in reverse order
3 KA 9.8
2 Ak 27.0
1 Ba 10.0

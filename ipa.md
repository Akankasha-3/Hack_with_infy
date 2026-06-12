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
Sample Input
    2
    1
    ak
    am
    270
    2
    az
    ao
    50
    Your Output
    2 az ao 50.0
1 ak am 270.0



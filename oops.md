```
import java.util.*;
class Myclass{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        Book b[]=new Book[4];
        for(int i=0;i<4;i++){
            int id=sc.nextInt();sc.nextLine();
            int p=sc.nextInt();sc.nextLine();
            String t=sc.nextLine();
            String a=sc.nextLine();
            double pri=sc.nextDouble();
            sc.nextLine();
            b[i]=new Book(id,p,t,a,pri);
        }
        Book a[]=searchBookByTitle(b,sc.nextLine());
        if(a.length==0){System.out.println("No Book found");}
        else {
            Arrays.sort(a,Comparator.comparing(Book ::getPrice).reversed());
            for(Book i:a){
                System.out.println(i.getId()+" "+i.getPages()+" "+i.getTitle()+" "+i.getAuthor()+" "+i.getPrice());
            }
            
        }
        Book d=findBookWithMaxPrice(b);
        if(d==null){System.out.println("No book");}
        else{
            System.out.println(d.getPrice());
        }
        
    }
    public static Book[] searchBookByTitle(Book[] b,String t){
        int j=0;
        Book[] a= new Book[4];
        for(Book i:b){
            if(t.equalsIgnoreCase(i.getTitle())){
                a[j]=i;
                j+=1;
            }
        }
        a=Arrays.copyOf(a,j);
        return a;
    }
    public static Book findBookWithMaxPrice(Book[] b){
        double a=Integer.MIN_VALUE;
        Book m=null;
        for(Book i:b){
            if(a<i.getPrice()){
                a=i.getPrice();
                m=i;
            }
        }return m;
    }
}
class Book{
    int id;
    int pages;
    String title;
    String author;
    double price;
    Book(int id,int p,String t,String a,double pri){
        this.id=id;this.pages=p;this.title=t;this.author=a;this.price=pri;
    }
    public int getId(){return id;}
    public int getPages(){return pages;}
    public String getTitle(){return title;}
    public String getAuthor(){return author;}
    public double getPrice(){return price;}
}
```
input:
1
845
Bengali
Arijit
525.50
2
456
English
Raju
412.30
3
1022
english
Kaka
525.50
4
125
geography
MN
524
English
Your Output

3 1022 english Kaka 525.5

2 456 English Raju 412.3

525.5

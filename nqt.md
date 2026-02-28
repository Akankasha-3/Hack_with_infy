**ps:given an integer .Toggle all the bits of binary representation of the integer and return the decimal number occurred**
```python
import math
n=int(input())
k=(1<< int(math.log2(n))+1)-1
print(n^k)
```
**ps:given the starting day of the month and days d.return no.of sundays will occur in these days**
```
def main():
    s = input()
    a = int(input())
    m = {
        "mon": 6, "tue": 5, "wed": 4,
        "thu": 3, "fri": 2, "sat": 1,
        "sun": 0
    }
    ans = 0
    if a - m[s[:3]] >= 1:
        ans = 1 + (a - m[s[:3]]) // 7
    print(ans)

if __name__ == "__main__":
    main()
```
**ps:print the count of elements whose values are greater than all its prior elements**
```python
l=list(map(int,input().split()))
m=float('-inf')
k=0
for i in l:
    if i>m:
        m=i
        k+=1
print(k)
```
**ps:you are given a stack of elements which contains black-b and aqua-a colours.you will place p elements in a sack and now you should return the max no.of aqua colou elements present in any of the sack**
```python
l='bbbaaababa'
p=3
i,x=0,0

while i<len(l):
    k=p
    z=0
    j=i
    while(k>0 and j<len(l)):
        if l[j]=='a':
            z+=1
        j+=1
        k-=1
    
    x=max(x,z)
    i=j
print(x)
```
**ps:There are n people sitting in a round table.but two of them always sit together.print the no.of possible ways**
```python
n=int(input())
import math
print(math.factorial(n-1)*2)
```
**Problem Statement**

An intelligence agency has received reports about some threats. The reports consist of numbers in a mysterious method. There is a number “N” and another number “R”. Those numbers are studied thoroughly and it is concluded that all digits of the number ‘N’ are summed up and this action is performed ‘R’ number of times. The resultant is also a single digit that is yet to be deciphered. The task here is to find the single-digit sum of the given number ‘N’ by repeating the action ‘R’ number of times.

If the value of ‘R’ is 0, print the output as ‘0’.

Example 1:

Input :

99 -> Value of N

3  -> Value of R

Output :

9  -> Possible ways to fill the cistern.

Explanation:

Here, the number N=99

Sum of the digits N: 9+9 = 18
Repeat step 2 ‘R’ times i.e. 3 tims  (9+9)+(9+9)+(9+9) = 18+18+18 =54
Add digits of 54 as we need a single digit 5+4
Hence , the output is 9.

Example 2:

Input :

1234   -> Value of N

2      -> Value of R

Output :

2  -> Possible ways to fill the cistern

Explanation:

Here, the number N=1234

Sum of the digits of N: 1+2+3+4 =10
Repeat step 2 ‘R’ times i.e. 2 times  (1+2+3+4)+(1+2+3+4)= 10+10=20
Add digits of 20 as we need a single digit. 2+0=2
Hence, the output is 2.

Constraints:

0<N<=1000

0<=R<=50

The Input format for testing 

The candidate has to write the code to accept 2 input(s)

First input- Accept value for N (positive integer number)

Second input: Accept value for R(Positive integer number)

The output format for testing 
```python
n=int(input())
k=int(input())
s=0

for i in str(n):
    s+=int(i)
n=s*k
s=0
for i in str(n):
    s+=int(i)
    
print(s)
```
Problem Statement

Particulate matters are the biggest contributors to Delhi pollution. The main reason behind the increase in the concentration of PMs include vehicle emission by applying Odd Even concept for all types of vehicles. The vehicles with the odd last digit in the registration number will be allowed on roads on odd dates and those with even last digit will on even dates.

Given an integer array a[], contains the last digit of the registration number of N vehicles traveling on date D(a positive integer). The task is to calculate the total fine collected by the traffic police department from the vehicles violating the rules.

Note : For violating the rule, vehicles would be fined as X Rs.

Example 1:

Input :

4 -> Value of N

{5,2,3,7} -> a[], Elements a[0] to a[N-1], during input each element is separated by a new line

12 -> Value of D, i.e. date 

200 -> Value of x i.e. fine

Output :

600  -> total fine collected 

Explanation:

Date D=12 means , only an even number of vehicles are allowed. 

Find will be collected from 5,3 and 7 with an amount of 200 each.

Hence, the output = 600.

Example 2:

Input :

5   -> Value of N 

{2,5,1,6,8}  -> a[], elements a[0] to a[N-1], during input each element is separated by new line

3 -> Value of D i.e. date 

300 -> Value of X i.e. fine 

Output :

900  -> total fine collected 

Explanation:
Date D=3 means only odd number vehicles with are allowed.
Find will be collected from 2,6 and 8 with an amount of 300 each.
Hence, the output = 900 
Constraints:
0<N<=100
1<=a[i]<=9
1<=D <=30
100<=x<=5000 
The input format for testing 
```python
n=int(input())
l=list(map(int,input().split()))
d=int(input())
f=int(input())
k=0

for i in l:
    if i&1!=d&1:k+=1 
print(k*f)
```

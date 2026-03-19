```python
import sys
class node():
    def __init__(self,val):
        self.val=val
        self.next=None 
if __name__=="__main__":
    print('a')
    c=list(sys.stdin.readline().split())
    d=int(sys.stdin.readline())
    b=node(3)
    n,m=map(int,sys.stdin.readline().split())
    print(n,m)
    print(n+m)
    print(b.val,c,d,end=' ')```
**input:**
4 5
7
7 7
**output;**
a
7 7
14
3 ['4', '5'] 7

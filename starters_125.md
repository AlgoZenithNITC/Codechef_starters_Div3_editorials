<!---
Question 1: 50-50 Rule
Use the if else statements to write the three 3 conditions given:
Print ‘Z’ if x<50 , ‘F’ if x>=50 and y<50 and ‘A’ otherwise.

Question 2 : Fake Certificate
Concept : string
By using a variable keep the track of largest substring of s with 0’s by traversing through it . 
Print the sum of the size of the largest substring of 0’s and no. of one’s in the string s. 
--->

## 50-50 Rule

<details>
<summary>Python</summary>

```python
import sys

def main():
    t = int(sys.stdin.readline().strip())
    for _ in range(t):
        x, y = map(int, sys.stdin.readline().strip().split())
        if x < 50:
            print("Z")
        elif x >= 50 and y < 50:
            print("F")
        else:
            print("A")

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
	cin>>t;
    while(t--)
    {
        int x,y;
        cin>>x>>y;
        if(x<50)
        cout<<"Z\n";
        else if(x>=50 && y<50)
        cout<<"F\n";
        else
        cout<<"A\n";
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            if (x < 50)
                System.out.println("Z");
            else if (x >= 50 && y < 50)
                System.out.println("F");
            else
                System.out.println("A");
        }
    }
}
```

</details>

## Fake Certificate

<details>
<summary>Python</summary>

```python
import sys

def main():
    t = int(input())
    for _ in range(t):
        n = int(input())
        s = input()
        m = 0
        p = 0
        for c in s:
            if c == '0':
                m += 1
            else:
                m = 0
            p = max(m, p)
        m = s.count('1')
        print(m + p)

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
	cin>>t;
	while(t--)
	{
	    int n;
	    string s;
	    cin>>n>>s;
	    int m=0 , p=0;
	    for(char c : s)
	    {
	        if(c=='0')
	        m++;
	        else
	        m=0;
	        p=max(m,p);
	    }
	    m = count(s.begin(),s.end(),'1');
	    cout<<m+p<<"\n";
	}
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            String s = scanner.next();
            int m = 0, p = 0;
            for (char c : s.toCharArray()) {
                if (c == '0')
                    m++;
                else
                    m = 0;
                p = Math.max(m, p);
            }
            m = s.length() - s.replace("1", "").length();
            System.out.println(m + p);
        }
    }
}
```

</details>

## Binary Minimal

<details>
<summary>Python</summary>

```python

```

</details>

<details>
<summary>Cpp</summary>

```cpp

```

</details>

<details>
<summary>Java</summary>

```java

```

</details>

## Bucket Game

<details>
<summary>Python</summary>

```python

```

</details>

<details>
<summary>Cpp</summary>

```cpp

```

</details>

<details>
<summary>Java</summary>

```java

```

</details>

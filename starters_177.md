## 1. Triangle checking

<details>
<summary>Python</summary>

```python
a, b, c = map(int, input().split())

if a + b > c and b + c > a and c + a > b:
    print("YES")
else:
    print("NO")


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a, b, c;
    cin >> a >> b >> c;

    if (a + b > c && b + c > a && c + a > b)
        cout << "YES" << endl;
    else
        cout << "NO" << endl;

    return 0;
}


```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class TriangleCheck {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int a = sc.nextInt();
        int b = sc.nextInt();
        int c = sc.nextInt();

        if (a + b > c && b + c > a && c + a > b)
            System.out.println("YES");
        else
            System.out.println("NO");

        sc.close();
    }
}


```

</details>

## 2. 2 Boxes

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    x, y, k = map(int, input().split())
    change= abs(x - y)  
    if change==k:
        print(0)
    elif (change-k)%2==0:
        print(abs(change-k)//2)
    else:
        print(-1) 

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t,x,y,k;
	cin>>t;
	while(t--){
	    cin>>x>>y>>k;
	    if(abs(k-abs(x-y))%2==0){
	        cout<<abs(k-abs(x-y))/2<<endl;
	    }
	    else{
	        cout<<-1<<endl;
	    }
	}

}


```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;
class Box
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();
		while(t-->0){
		    int x = sc.nextInt();
		    int y = sc.nextInt();
		    int k = sc.nextInt();
		    int diff = Math.abs(x-y);
		    
		    if(diff == k){
		        System.out.println(0);
		        continue;
		    }
		    if(k>x+y || diff%2 != k%2){
		        System.out.println(-1);
		        continue;
		    }
		    int count = 0;
		    if(diff > k){
		        while(diff!=k){
		            diff-=2;
		            count++;    }
		    }
		    else if(diff<k){
		        while(diff!=k){
		            diff+=2;
		            count++;
		        }
		    }
		    System.out.println(count);
		}
	}
}
```

</details>

## 3. Ordered Distances

<details>
<summary>Python</summary>

```python


t = int(input())

for _ in range(t):
    n = int(input())
    ans = True
    a = list(map(int, input().split()))
    b = [-1] * 1001
    y = list(map(int, input().split()))

    for i in range(n):
        b[a[i]] = i + 1

    for i in range(1, n):
        if abs(y[i] - y[0]) < abs(y[i - 1] - y[0]):
            ans = False
        elif abs(y[i] - y[0]) == abs(y[i - 1] - y[0]) and y[i] < y[i - 1]:
            ans = False

    if ans:
        print(b[y[0]])
    else:
        print(-1)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t,n;
	cin>>t;
	while(t--){
	    cin>>n;
	    bool ans = true;
	    vector<int> a(n);
	    vector<int> b(1001,-1);
	    vector<int> y(n);
	    for(int i=0;i<n;i++){
	        cin>>a[i];
	        b[a[i]] = i+1;
	    }
	    for(int i=0;i<n;i++){
	        cin>>y[i];
	        if(i>0){
	            if(abs(y[i]-y[0])<abs(y[i-1]-y[0])){
	                ans = false;
	            }
	            else if(abs(y[i]-y[0])==abs(y[i-1]-y[0]) && y[i]<y[i-1]){
	                ans = false;
	            }
	        }
	    }
	    if(ans){
	        cout<<b[y[0]]<<endl;
	    }
	    else{
	        cout<<-1<<endl;
	    }
	}

}

```

</details>

<details>
<summary>Java</summary>

```java

import java.util.*;

public class TriangleCheck {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            boolean ans = true;
            int[] a = new int[n];
            int[] b = new int[1001];
            Arrays.fill(b, -1);
            int[] y = new int[n];

            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
                b[a[i]] = i + 1;
            }

            for (int i = 0; i < n; i++) {
                y[i] = sc.nextInt();
                if (i > 0) {
                    if (Math.abs(y[i] - y[0]) < Math.abs(y[i - 1] - y[0])) {
                        ans = false;
                    } else if (Math.abs(y[i] - y[0]) == Math.abs(y[i - 1] - y[0]) && y[i] < y[i - 1]) {
                        ans = false;
                    }
                }
            }

            if (ans) {
                System.out.println(b[y[0]]);
            } else {
                System.out.println(-1);
            }
        }
        sc.close();
    }
}


```

</details>

## 4. Counting 01 and 10

<details>
<summary>Python</summary>

```python

def compute_result():
    inputval=int(input())
    halfval=inputval//2
    top=halfval*(3*inputval-2*halfval-1)+6
    final=(halfval+1)*top//6
    print(final)
    
test_cases=int(input())
for _ in range(test_cases):
    compute_result()
    
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;
#define int long long

signed main() {
    int t; cin>>t;
    
    while(t--) {
        int n; cin>>n;
        int ans = 0;
        for(int k=0;k<n;k++) {
            if(k > n-k) break;
            ans += k*(n-k)+1;
        }
        cout<<ans<<endl;
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc= new Scanner(System.in);
	    int T=sc.nextInt();
	    for(int i=0;i<T;i++){
	        int N=sc.nextInt();
	        long res=0;
	        for(int j=0;j<=N/2;j++){
	             res +=(j*1L*(N-j))+1;
	        }
	        System.out.println(res);
	    }
       
	}
}
```

</details>

## 5. Flip or Reverse

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = input()
    b = input()
    
   
    start = -1
    ans = []
    for i in range(n):
        if(a[i]==b[i]):
            if(start!=-1):
                ans.append([1,start+1,i])
            start = -1
        else:
            if(start==-1):
                start = i
         
    if(start!=-1):
        ans.append([1,start+1,n])
    print(len(ans))
    for i in ans:
        print(*i)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

#define ll long long

int main() {
	// your code goes here
    ll t;
    cin>>t;
    while(t--){
        ll n;
        cin>>n;
        string a,b;
        cin>>a>>b;
        vector<pair<ll,ll>> v;
        for (ll i=0; i<n; i++){
            if (a[i]!=b[i]){
                // v.push_back({i+1,i+1});
                ll j;
                for (j=i; j<n; j++){
                    if (a[j]==b[j]){
                        break;
                    }
                }
                v.push_back({i+1,j});
                i=j;
            }
        }
        cout << v.size() << endl;
        for (ll i=0; i<v.size(); i++){
            cout << 1 << " " << v[i].first << " " << v[i].second << endl;
        }
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
        Scanner scn = new Scanner(System.in);
        int t = scn.nextInt();
        
        while(t-->0){
            int n = scn.nextInt();
            scn.nextLine();
            String a = scn.nextLine(), b = scn.nextLine();
            
            boolean on = false;
            int left = -1;
            
            List<int[]> moves = new ArrayList<>();
            for(int i = 0; i<n; i++){
                char ca = a.charAt(i), cb = b.charAt(i);
                if(ca!=cb){
                    if(!on){
                        on = true;
                        left = i;
                    } 
                }
                else {
                    if(on){
                        moves.add(new int[]{1, left+1, i});
                        on = false;
                        left = -1;
                    }
                }
            }
            if(on){
                moves.add(new int[]{1, left+1, n});
            }
            System.out.println(moves.size());
            for(int[] move : moves){
                for(int i : move)
                System.out.print(i+" ");
                System.out.println();
            }
        }
	}
}
```

</details>

# Codechef_starters_134_Div3

<!-- First Question -->
# Money Double
<details>
<summary>Python</summary>

```python
def solve():
    x, y = map(int, input().split())
    am = x
    for i in range(1, y+1):
        if 2 * am > am + 1000:
            am *= 2
        else:
            am += 1000
    print(am)

t = int(input())
for _ in range(t):
    solve()


```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long int
void solve() {
	int x, y;
	cin >> x >> y;
	int am = x;
	for (int i = 1; i <= y; i++) {
		if (2 * am > am + 1000) {
			am = am * 2;
		}
		else
			am = am + 1000;
	}
	cout<<am<<endl;



}



signed main() {
	int t;
	cin >> t;
	while (t--) {
		solve();
	}



#ifndef ONLINE_JUDGE
	//	for getting input from input.txt
	freopen("input.txt", "r", stdin);
	freopen("output.txt", "w", stdout);
#endif




}
```
</details>


<details>
<summary>Java</summary>

```java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;

public class Main {
    public static void solve() {
        Scanner scanner = new Scanner(System.in);
        int x = scanner.nextInt();
        int y = scanner.nextInt();
        long am = x;
        for (int i = 1; i <= y; i++) {
            if (2 * am > am + 1000) {
                am *= 2;
            } else {
                am += 1000;
            }
        }
        System.out.println(am);
        scanner.close();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        for (int i = 0; i < t; i++) {
            solve();
        }
        scanner.close();
    }
}

```
</details>

<!-- Second Question -->
# Rock paper scissors

<details>
<summary>Python</summary>

```python
import sys

def main():
    tt = int(input())

    for _ in range(tt):
        n = int(input())
        s = input().strip()
        answer = 0

        i = 0
        while i < n:
            j = i
            while j < n and s[i] == s[j]:
                j += 1
            answer += (j - i + 1) // 2
            i = j

        print(answer)

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    #ifndef ONLINE_JUDGE
    freopen("input.txt", "r", stdin);
    freopen("output.txt", "w", stdout);
    #endif

    int tt; cin >> tt;

    while(tt--) {
        int n; cin >> n;
        string s; cin >> s;
        int answer = 0;

        for(int i = 0, j = 0; i < n;) {
            while(j < n && s[i] == s[j]) j++;
            answer += (j - i + 1) / 2;
            i = j;
        }

        cout << answer << "\n";
    }
}
```

</details>
<!-- Java -->
<details>
<summary>Java</summary>

```Java
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;

public class Main {
    public static void main(String[] args) {
        try {
            Scanner scanner = new Scanner(new File("input.txt"));
            PrintWriter writer = new PrintWriter("output.txt");
            
            int tt = scanner.nextInt();
            scanner.nextLine(); // Consume newline
            
            while (tt-- > 0) {
                int n = scanner.nextInt();
                String s = scanner.next();
                int answer = 0;

                int i = 0;
                while (i < n) {
                    int j = i;
                    while (j < n && s.charAt(i) == s.charAt(j)) {
                        j++;
                    }
                    answer += (j - i + 1) / 2;
                    i = j;
                }

                writer.println(answer);
            }

            scanner.close();
            writer.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
   


```
</details>

<!-- Third Quesion -->
# Origin

<details>
<summary>Python</summary>

```python
import math

t = int(input())
for _ in range(t):
    n = int(input())
    ans = 0
    x = n // 9
    y = n % 9
    ans = 45 * x + (y * (y + 1) // 2)
    print(ans)


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
	    unsigned long long n;
	    cin>>n;
	    unsigned long long ans =0;
	    unsigned long long x = n/9 , y = n%9 ;
	    ans = 45*x + (y*(y+1)/2 );
	    cout<<ans<<endl;
	}
    return 0;
}


```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            long n = scanner.nextLong();
            long ans = 0;
            long x = n / 9;
            long y = n % 9;
            ans = 45 * x + (y * (y + 1) / 2);
            System.out.println(ans);
        }
    }
}



```
</details>

<!-- Fourth Question -->
# 3 out 1 in

<details>
    <summary>Python</summary>

```python
from typing import List
from collections import deque

def input_vector(vec: List[int], size: int):
    vec.extend(map(int, input().split()))

def update_sums(a: List[int], final: List[int]):
    hi, lo = deque(), deque()
    sum_hi, sum_lo = 0, 0

    i = 0
    while i < len(a):
        if i % 2 == 1:
            if a[i] > hi[0]:
                sum_hi += a[i] - hi[0]
                sum_lo += hi[0]
                lo.append(hi.popleft())
                hi.appendleft(a[i])
            else:
                lo.append(a[i])
                sum_lo += a[i]
        else:
            if not lo:
                hi.appendleft(a[i])
                sum_hi += a[i]
            elif a[i] < lo[-1]:
                sum_hi += lo[-1]
                sum_lo += a[i] - lo[-1]
                hi.appendleft(lo.pop())
                lo.append(a[i])
            else:
                hi.appendleft(a[i])
                sum_hi += a[i]
            final.append(sum_hi - sum_lo)
        i += 1

def process_queries(final: List[int], queries: List[int]):
    for q in queries:
        print(final[q - 1], end=" ")
    print()

def solve():
    n, q = map(int, input().split())
    a = []
    input_vector(a, n)
    queries = []
    input_vector(queries, q)

    final = []
    update_sums(a, final)
    process_queries(final, queries)

if _name_ == "_main_":
    t = int(input())
    for _ in range(t):
        solve()

```
</details>


<details>
  	<summary>C++</summary>
  
```cpp
#include <bits/stdc++.h> 
using namespace std; 
#define int long long 

void inputVector(vector<int>& vec, int size)
{
    for (int i = 0; i < size; i++) 
    cin >> vec[i];
}

void updateSums(const vector<int>& a, vector<int>& final) {
    multiset<int> hi, lo; 
    int sum_hi = 0, sum_lo = 0; 

    int i = 0;
    while (i < a.size()) 
    {
        if (i & 1) 
        {
            if (a[i] > *hi.begin()) 
            {
                sum_hi += a[i] - *hi.begin(); 
                sum_lo += *hi.begin(); 
                lo.insert(*hi.begin()); 
                hi.insert(a[i]); 
                hi.erase(hi.begin()); 
            } 
            
            else 
            {
                lo.insert(a[i]); 
                sum_lo += a[i]; 
            } 
        } 
         else 
        {
            if (lo.empty()) 
            {
                hi.insert(a[i]); 
                sum_hi += a[i]; 
            } 
            
            else if (a[i] < *lo.rbegin()) 
            {
                sum_hi += *lo.rbegin(); 
                sum_lo += a[i] - *lo.rbegin(); 
                hi.insert(*lo.rbegin()); 
                lo.insert(a[i]); 
                lo.erase(lo.find(*lo.rbegin())); 
            } 
            
            else 
            {
                hi.insert(a[i]); 
                sum_hi += a[i]; 
            } 
        } 
        final.push_back(sum_hi - sum_lo); 
        i++;
    }
}

void processQueries(const vector<int>& final, const vector<int>& queries) 
{
    for (int i = 0; i < queries.size(); i++) 
    cout << final[queries[i] - 1] << " "; 
    cout << endl; 
}

void solve() 
{
    int n, q; 
    cin >> n >> q; 

    vector<int> a(n), queries(q); 
    
    inputVector(a, n);
    inputVector(queries, q); 

    vector<int> final;
    updateSums(a, final);
    processQueries(final, queries); 
}

signed main() 
{ 
    ios_base::sync_with_stdio(0); 
    cin.tie(0);cout.tie(0); 
    
    int t = 1; 
    cin >> t; 
    
    while (t--)
    solve();
}


```
</details>


<details>
	<summary>JAVA</summary>
  
```java
import java.util.*;

public class Solution {
    public static void inputVector(List<Long> vec, int size) {
        Scanner scanner = new Scanner(System.in);
        for (int i = 0; i < size; i++) {
            vec.add(scanner.nextLong());
        }
    }

    public static void updateSums(List<Long> a, List<Long> final_) {
        TreeSet<Long> hi = new TreeSet<>();
        TreeSet<Long> lo = new TreeSet<>();
        long sum_hi = 0, sum_lo = 0;

        int i = 0;
        while (i < a.size()) {
            if (i % 2 != 0) {
                if (!hi.isEmpty() && a.get(i) > hi.first()) {
                    sum_hi += a.get(i) - hi.first();
                    sum_lo += hi.first();
                    lo.add(hi.first());
                    hi.add(a.get(i));
                    hi.remove(hi.first());
                } else {
                    lo.add(a.get(i));
                    sum_lo += a.get(i);
                }
            } else {
                if (lo.isEmpty()) {
                    hi.add(a.get(i));
                    sum_hi += a.get(i);
                } else if (a.get(i) < lo.last()) {
                    sum_hi += lo.last();
                    sum_lo += a.get(i) - lo.last();
                    hi.add(lo.last());
                    lo.add(a.get(i));
                    lo.remove(lo.last());
                } else {
                    hi.add(a.get(i));
                    sum_hi += a.get(i);
                }
            }
            final_.add(sum_hi - sum_lo);
            i++;
        }
    }

    public static void processQueries(List<Long> final_, List<Long> queries) {
        for (long query : queries) {
            System.out.print(final_.get((int) query - 1) + " ");
        }
        System.out.println();
    }
     public static void solve() {
        Scanner scanner = new Scanner(System.in);
        long n = scanner.nextLong();
        long q = scanner.nextLong();

        List<Long> a = new ArrayList<>();
        List<Long> queries = new ArrayList<>();

        inputVector(a, (int) n);
        inputVector(queries, (int) q);

        List<Long> final_ = new ArrayList<>();
        updateSums(a, final_);
        processQueries(final_, queries);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            solve();
        }
    }
}





```
</details>


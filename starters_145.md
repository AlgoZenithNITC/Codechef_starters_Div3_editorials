## 1. Gun Master

<details>
<summary>Python</summary>

```python
 t = int(input()) 
for _ in range(t): 
 n, d = map(int, input().split()) 
 a = [0] + list(map(int, input().split())) 
 ans = 0 
 for i in range(1, n + 1): 
 if (a[i] <= d) != (a[i - 1] <= d): 
 ans += 1 
 print(ans) 
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream> 
#include <vector> 
using namespace std; 
int main() { 
 int t; 
 cin >> t; 
 while (t--) { 
 int n, d; 
 cin >> n >> d; 
 vector<int> a(n + 1, 0); 
 for (int i = 1; i <= n; ++i) { 
 cin >> a[i]; 
 } 
 int ans = 0; 
 for (int i = 1; i <= n; ++i) { 
 if ((a[i] <= d) != (a[i - 1] <= d)) { 
 ans += 1; 
 } 
 } 
 cout << ans << endl; 
 } 
 return 0; 
} 
```

</details>

<details>
<summary>Java</summary>

```java
import java.uƟl.Scanner;
public class Main { 
 public staƟc void main(String[] args) {
 Scanner scanner = new Scanner(System.in); 
 int t = scanner.nextInt(); 
 while (t-- > 0) { 
 int n = scanner.nextInt(); 
 int d = scanner.nextInt(); 
 int[] a = new int[n + 1]; 
 for (int i = 1; i <= n; ++i) { 
 a[i] = scanner.nextInt(); 
 } 
 int ans = 0; 
 for (int i = 1; i <= n; ++i) { 
 if ((a[i] <= d) != (a[i - 1] <= d)) { 
 ans += 1; 
 } 
 } 
 System.out.println(ans); 
 } 
 scanner.close(); 
 } 
} 
```

</details>

## 2. Make My Array Equal

<details>
<summary>Python</summary>

```python
for _ in range(int(input())): 
 n = int(input()) 
 a = list(map(int, input().split())) 
 mn, mx = max(a), max(a) 
 for i in range(n): 
 if a[i] > 0: mn = min(mn, a[i]) 
 print('Yes' if mn == mx else 'No') 
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream> 
#include <vector> 
#include <algorithm> 
using namespace std; 
int main() { 
 int t, n; 
 cin >> t; 
 while (t--) { 
 cin >> n; 
 vector<int> a(n); 
 for (int i = 0; i < n; ++i) cin >> a[i]; 
 int mn = *max_element(a.begin(), a.end()), mx = 
*max_element(a.begin(), a.end()); 
 for (int i = 0; i < n; ++i) { 
 if (a[i] > 0) mn = min(mn, a[i]); 
 } 
 cout << (mn == mx ? "Yes" : "No") << endl; 
 } 
 return 0; 
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;
import java.util.Arrays;
public class Main { 
 public staƟc void main(String[] args) {
 Scanner sc = new Scanner(System.in); 
 int t = sc.nextInt(); 
 while (t-- > 0) { 
 int n = sc.nextInt(); 
 int[] a = new int[n]; 
 for (int i = 0; i < n; ++i) a[i] = sc.nextInt(); 
 int mn = Arrays.stream(a).max().getAsInt(); 
 int mx = Arrays.stream(a).max().getAsInt(); 
 for (int i = 0; i < n; ++i) { 
 if (a[i] > 0) mn = Math.min(mn, a[i]); 
 } 
 System.out.println(mn == mx ? "Yes" : "No"); 
 } 
 } 
} 
```

</details>

## 3. Make Bob Win

<details>
<summary>Python</summary>

```python
for _ in range(int(input())): 
 n = int(input()) 
 s = input().strip() 
 if n == 1: 
 print(1 - int(s[0])) 
 conƟnue
 ans = (s[0] == '0') + (s[-1] == '0') 
 print(ans) 
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream> 
#include <string> 
using namespace std; 
int main() { 
 int t; 
 cin >> t; 
 while (t--) { 
 int n; 
 cin >> n; 
 string s; 
 cin >> s; 
 if (n == 1) { 
 cout << 1 - (s[0] - '0') << endl; 
 conƟnue;
 } 
 int ans = (s[0] == '0') + (s[n - 1] == '0'); 
 cout << ans << endl; 
 } 
 return 0; 
} 

```

</details>

<details>
<summary>Java</summary>

```java
import java.uƟl.Scanner;
public class Main { 
 public staƟc void main(String[] args) {
 Scanner sc = new Scanner(System.in); 
 int t = sc.nextInt(); 
 while (t-- > 0) { 
 int n = sc.nextInt(); 
 String s = sc.next(); 
 if (n == 1) { 
 System.out.println(1 - (s.charAt(0) - '0')); 
 conƟnue;
 } 
 int ans = (s.charAt(0) == '0' ? 1 : 0) + (s.charAt(n - 1) 
== '0' ? 1 : 0); 
 System.out.println(ans); 
 } 
 } 
}
```

</details>

## 4. Square String

<details>
<summary>Python</summary>

```python
def power(i, x, m):
    if i == 1:
        return x

    if i % 2 == 0:
        return power(i // 2, (x % m) * (x % m), m) % m
    else:
        return (power(i // 2, (x % m) * (x % m), m) % m * (x % m)) % m

def solve():
    n = int(input())
    ans = 0
    k = 1
    m = 10**9 + 7
    for i in range(n - 1, 0, -1):
        ans = (ans + (i % m) * (power(i, 2, m)) % m * (k % m) * (k % m) % m) % m
        k += 1
    print(ans)

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
typedef long long int ll;
ll m=1e9 + 7;
ll power(ll i, ll x){
  if(i==1) return x;

  ll ans=0;
  if(i%2==0) ans=power(i/2,x%m * x%m);
  else ans=(power(i/2,x%m * x%m)%m * x%m)%m;
  return ans%m;
}
void solve(){
  ll n; cin>>n;
  ll ans=0,k=1;
  for(ll i=n-1;i>0;i--){
    ans=(ans%m + i%m * (power(i,2))%m * (k%m * k%m)%m)%m;
    k++;
  }
  cout<<ans<<endl;
}


int main()
{
  int t; cin >> t;
  while (t--){
    solve();
  }

  return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Main {
    static final long m = 1000000007;

    static long power(long i, long x) {
        if (i == 1) return x;

        long ans = 0;
        if (i % 2 == 0) ans = power(i / 2, (x % m * x % m) % m);
        else ans = (power(i / 2, (x % m * x % m) % m) % m * x % m) % m;
        return ans % m;
    }

    static void solve(Scanner scanner) {
        long n = scanner.nextLong();
        long ans = 0, k = 1;
        for (long i = n - 1; i > 0; i--) {
            ans = (ans % m + i % m * (power(i, 2) % m) % m * (k % m * k % m) % m) % m) % m;
            k++;
        }
        System.out.println(ans);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            solve(scanner);
        }
        scanner.close();
    }
}

```

</details>

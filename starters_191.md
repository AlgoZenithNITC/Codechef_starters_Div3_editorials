## Nearest Square

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    
    for i in range(1, 100):
        if i*i > n: # Exceeded n, so print the previous square
            print((i-1)*(i-1))
            break
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> sqList;

void solve(){
    int n; cin >> n;
    for(auto i : sqList){
        if (i <= n){
            cout << i << "\n";
            return;
        }
    }
}

int main() {
    int t; cin >> t;
    for(int i = 10; i > 0; i--) sqList.push_back(i*i);
    while(t--) solve();
    return 0;
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
		Scanner sc = new Scanner(System.in);

		int t = sc.nextInt(); // number of test cases

		while (t-- > 0) {
			int n = sc.nextInt();

			for (int i = 1; i < 100; i++) {
				if (i * i > n) {
					System.out.println((i - 1) * (i - 1));
					break;
				}
			}
		}

		sc.close();
	}
}
```

</details>

## Add to get GCD

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    x, y = map(int, input().split())
    
    from math import gcd

    if (gcd(x,y) != 1):
        print(0)
    elif(gcd(x+1,y) != 1 || gcd(x,y+1) != 1):
        print(1)
    else:
        print(2)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
    int x,y; cin >> x >> y;
    
    if (gcd(x,y) != 1)
        cout << 0 << '\n';
    else if (gcd(x+1,y) != 1 || gcd(x,y+1) != 1)
        cout << 1 << '\n';
    else
        cout << 2 << '\n';
}

int main() {
    int t; cin >> t;
    while(t--) solve();
    return 0;
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
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();

		while (t-- > 0) {
			int x = sc.nextInt();
			int y = sc.nextInt();

			if (gcd(x, y) != 1) {
				System.out.println(0);
			} else if (gcd(x + 1, y) != 1 || gcd(x, y + 1) != 1) {
				System.out.println(1);
			} else {
				System.out.println(2);
			}
		}

		sc.close();
	}

	// Utility method to compute GCD
	public static int gcd(int a, int b) {
		while (b != 0) {
			int temp = b;
			b = a % b;
			a = temp;
		}
		return a;
	}
}
```

</details>

## Permuted Greater than 2

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    x, y, z = map(int, input().split())
    
    if x > z+1: print('No')
    elif x == z+1 and y > 0: print('No')
    else: print('Yes')
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
    int x, y, z;
    cin >> x >> y >> z;
    
    if (z + 1 == x && y) cout << "No\n";
    else if (x > z + 1) cout << "No\n";
    else cout << "Yes\n";
}

int main() {
    int t; cin >> t;
    while(t--) solve();
    return 0;
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
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();

		while (t-- > 0) {
			int x = sc.nextInt();
			int y = sc.nextInt();
			int z = sc.nextInt();

			if (x > z + 1) {
				System.out.println("No");
			} else if (x == z + 1 && y > 0) {
				System.out.println("No");
			} else {
				System.out.println("Yes");
			}
		}

		sc.close();
	}
}
```

</details>

## Add 1 or 2

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = list(map(int, input().split()))
    b = list(map(int, input().split()))
    
    lo, hi = max(a), 2 * 10**9
    while lo < hi:
        mid = (lo + hi) // 2
        
        # can I make everything <= mid?
        need = have = 0
        for i in range(n):
            if a[i] + b[i] <= mid:
                d = mid - (a[i] + b[i])
                have += d//2
            else:
                need += (a[i] + b[i]) - mid
        
        if have >= need: hi = mid
        else: lo = mid + 1
    print(lo)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
#define vll vector<long long>
#define ll long long
using namespace std;

bool f(ll M, vll& a, vll& b, int n){
    ll recieve = 0, send = 0;
    for(int i=0; i < n; i++){
        if ((a[i] + b[i]) > M) send += (a[i] + b[i] - M);
        else recieve += (M - a[i] - b[i]) / 2;
    }
    return recieve >= send;
}

void solve(){
    int n; cin >> n;
    
    vll a(n); vll b(n);
    for(auto& it : a) cin >> it;
    for(auto& it : b) cin >> it;
    
    // binary search on the max value
    ll low = *max_element(a.begin(), a.end()), high = 2e9;
    while (low < high){
        ll M = (low + high) / 2;
        if (f(M,a,b,n)){
            high = M;
        }else{
            low = M + 1;
        }
    }
    cout << low << "\n";
}

int main() {
    int t; cin >> t;
    while(t--) solve();
    return 0;
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
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();

		while (t-- > 0) {
			int n = sc.nextInt();
			int[] a = new int[n];
			int[] b = new int[n];

			for (int i = 0; i < n; i++) {
				a[i] = sc.nextInt();
			}
			for (int i = 0; i < n; i++) {
				b[i] = sc.nextInt();
			}

			int lo = Arrays.stream(a).max().getAsInt();
			int hi = 2_000_000_000;

			while (lo < hi) {
				int mid = lo + (hi - lo) / 2;
				long need = 0, have = 0;

				for (int i = 0; i < n; i++) {
					if (a[i] + b[i] <= mid) {
						int d = mid - (a[i] + b[i]);
						have += d / 2;
					} else {
						need += (a[i] + b[i]) - mid;
					}
				}

				if (have >= need) {
					hi = mid;
				} else {
					lo = mid + 1;
				}
			}

			System.out.println(lo);
		}

		sc.close();
	}
}
```

</details>

## Grid Path (Easy)

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, q = map(int, input().split())
    a = input()
    b = input()
    
    acost, bcost = [], []
    j = 0
    for i in range(n):
        if a[i] == '1':
            acost.append(i - j)
            j += 1
    j = n-1
    for i in reversed(range(n)):
        if b[i] == '1':
            bcost.append(j - i)
            j -= 1
    
    for i in range(1, len(acost)): acost[i] += acost[i-1]
    for i in range(1, len(bcost)): bcost[i] += bcost[i-1]
    
    ans = 10**14
    for k in range(1, n+1):
        if len(acost) < k: break
        if len(bcost) < n-k+1: continue
        ans = min(ans, acost[k-1] + bcost[n-k])
    if ans == 10**14: ans = -1
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int n, q;
    cin >> n >> q;
    string a, b;
    cin >> a >> b;

    vector<long long> acost, bcost;

    int j = 0;
    for (int i = 0; i < n; ++i) {
        if (a[i] == '1') {
            acost.push_back(i - j);
            j++;
        }
    }

    j = n - 1;
    for (int i = n - 1; i >= 0; --i) {
        if (b[i] == '1') {
            bcost.push_back(j - i);
            j--;
        }
    }

    // Prefix sums
    for (int i = 1; i < acost.size(); ++i) {
        acost[i] += acost[i - 1];
    }
    for (int i = 1; i < bcost.size(); ++i) {
        bcost[i] += bcost[i - 1];
    }

    long long INF = 1e14;
    long long ans = INF;

    for (int k = 1; k <= n; ++k) {
        if ((int)acost.size() < k) break;
        if ((int)bcost.size() < n - k + 1) continue;

        long long costA = acost[k - 1];
        long long costB = bcost[n - k];
        ans = min(ans, costA + costB);
    }

    if (ans == INF) ans = -1;
    cout << ans << '\n';
}

int main() {
    int t;
    cin >> t;
    while (t--) solve();
    return 0;
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
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();

		while (t-- > 0) {
			int n = sc.nextInt();
			int q = sc.nextInt(); // `q` is unused in the logic
			sc.nextLine(); // consume the newline character
			String a = sc.nextLine();
			String b = sc.nextLine();

			ArrayList<Long> acost = new ArrayList<>();
			ArrayList<Long> bcost = new ArrayList<>();

			int j = 0;
			for (int i = 0; i < n; i++) {
				if (a.charAt(i) == '1') {
					acost.add((long)(i - j));
					j++;
				}
			}

			j = n - 1;
			for (int i = n - 1; i >= 0; i--) {
				if (b.charAt(i) == '1') {
					bcost.add((long)(j - i));
					j--;
				}
			}

			// Prefix sums
			for (int i = 1; i < acost.size(); i++) {
				acost.set(i, acost.get(i) + acost.get(i - 1));
			}
			for (int i = 1; i < bcost.size(); i++) {
				bcost.set(i, bcost.get(i) + bcost.get(i - 1));
			}

			long ans = (long)1e14;
			for (int k = 1; k <= n; k++) {
				if (acost.size() < k) break;
				if (bcost.size() < n - k + 1) continue;
				long costA = acost.get(k - 1);
				long costB = bcost.get(n - k);
				ans = Math.min(ans, costA + costB);
			}

			if (ans == (long)1e14) ans = -1;
			System.out.println(ans);
		}

		sc.close();
	}
}
```

</details>

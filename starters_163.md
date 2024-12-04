# Codechef_starters_163_Div3

<!-- First Question -->
#  Binary Sum
<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, k = map(int, input().split())
    print('Yes' if k == n//2 or k == (n+1)//2 else 'No')

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, k;
        cin >> n >> k;
        if (k == n / 2 || k == (n + 1) / 2) {
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
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
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            int k = sc.nextInt();
            if (k == n / 2 || k == (n + 1) / 2) {
                System.out.println("Yes");
            } else {
                System.out.println("No");
            }
        }
    }
}

```
</details>

<!-- Second Question -->
# Minimum Types

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, x = map(int, input().split())
    a = list(map(int, input().split()))
    b = list(map(int, input().split()))

    indices = sorted(range(n), key=lambda i: -a[i] * b[i])
    sm = 0
    for i in range(n):
        sm += a[indices[i]] * b[indices[i]]
        if sm >= x:
            print(i + 1)
            break
    else:
        print(-1)


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
    int t;
    cin >> t;
    while (t--) {
        int n, x;
        cin >> n >> x;
        vector<int> a(n), b(n);
        
        for (int i = 0; i < n; i++) cin >> a[i];
        for (int i = 0; i < n; i++) cin >> b[i];
        
        vector<int> indices(n);
        for (int i = 0; i < n; i++) indices[i] = i;
        
        sort(indices.begin(), indices.end(), [&](int i, int j) {
            return a[i] * b[i] > a[j] * b[j];
        });
        
        long long sm = 0;
        bool found = false;
        for (int i = 0; i < n; i++) {
            sm += a[indices[i]] * b[indices[i]];
            if (sm >= x) {
                cout << i + 1 << endl;
                found = true;
                break;
            }
        }
        if (!found) cout << -1 << endl;
    }
    return 0;
}

```

</details>
<!-- Java -->
<details>
<summary>Java</summary>

```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            int x = sc.nextInt();
            int[] a = new int[n];
            int[] b = new int[n];

            for (int i = 0; i < n; i++) a[i] = sc.nextInt();
            for (int i = 0; i < n; i++) b[i] = sc.nextInt();

            Integer[] indices = new Integer[n];
            for (int i = 0; i < n; i++) indices[i] = i;

            Arrays.sort(indices, (i, j) -> Long.compare((long) b[j] * a[j], (long) b[i] * a[i]));

            long sm = 0;
            boolean found = false;
            for (int i = 0; i < n; i++) {
                sm += (long) a[indices[i]] * b[indices[i]];
                if (sm >= x) {
                    System.out.println(i + 1);
                    found = true;
                    break;
                }
            }
            if (!found) System.out.println(-1);
        }
    }
}


```
</details>

<!-- Third Quesion -->
# Nice Array

<details>
<summary>Python</summary>

```python
from math import *
for _ in range(int(input())):
    n, k = map(int, input().split())
    a = list(map(int, input().split()))
    s2 = 0
    c = 0
    for i in a:
        s2 += max(floor(i/k), ceil(i/k))
        if i % k != 0:
            c += 1
    if s2 >= 0 and s2 <= c:
        print("YES")
    else:
        print("NO")


```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, k;
        cin >> n >> k;
        vector<int> a(n);
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }
        
        int s2 = 0, c = 0;
        for (int i = 0; i < n; i++) {
            s2 += max(floor(a[i] / (double)k), ceil(a[i] / (double)k));
            if (a[i] % k != 0) {
                c++;
            }
        }
        
        if (s2 >= 0 && s2 <= c) {
            cout << "YES" << endl;
        } else {
            cout << "NO" << endl;
        }
    }
    return 0;
}

```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while (t-- > 0) {
            int n = sc.nextInt();
            int k = sc.nextInt();
            int[] a = new int[n];
            
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }
            
            int s2 = 0, c = 0;
            for (int i = 0; i < n; i++) {
                s2 += Math.max((int) Math.floor(a[i] / (double) k), (int) Math.ceil(a[i] / (double) k));
                if (a[i] % k != 0) {
                    c++;
                }
            }
            
            if (s2 >= 0 && s2 <= c) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
        sc.close();
    }
}

```
</details>


<!-- Fourth Quesion -->
# Sort Them

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    s = input().strip()
    p = input().strip()
    
    mapper = {}
    for i in range(26): mapper[p[i]] = p[-i-1]
    
    x, y = 0, 1
    for i in range(1, n):
        nx, ny = n+1, n+1
        
        if s[i] >= s[i-1]: nx = min(nx, x)
        if s[i] >= mapper[s[i-1]]: nx = min(nx, y)
        if mapper[s[i]] >= s[i-1]: ny = min(ny, x + 1)
        if mapper[s[i]] >= mapper[s[i-1]]: ny = min(ny, y + 1)
        
        x, y = nx, ny
    
    if min(x, y) > n: print(-1)
    else: print(min(x, y))


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
	while(t--){
	    int n;
	    cin>>n;
	    string s, t;
	    cin>>s>>t;
	    int ord[26];
	    for(int i = 0; i < 26; i++){
	        ord[t[i] - 'a'] = i;
	    }
	    int dp[n][2];
	    dp[0][0] = 0;
	    dp[0][1] = 1;
	    for(int i = 1; i < n; i++){
	        dp[i][0] = n + 1;
	        dp[i][1] = n + 1;
	        if(s[i] >= s[i - 1]){
	            dp[i][0] = dp[i - 1][0];
	        }
	        if(s[i] >= t[26 - ord[s[i - 1] - 'a'] - 1]){
	            dp[i][0] = min(dp[i][0], dp[i - 1][1]);
	        }
	        if(t[26 - ord[s[i] - 'a'] - 1] >= s[i - 1]){
	            dp[i][1] = dp[i - 1][0] + 1;
	        }
	        if(t[26 - ord[s[i] - 'a'] - 1] >= t[26 - ord[s[i - 1] - 'a'] - 1]){
	            dp[i][1] = min(dp[i][1], dp[i - 1][1] + 1);
	        }
	    }
	    int ans = min(dp[n - 1][0], dp[n - 1][1]);
	    if(ans > n){
	        ans = -1;
	    }
	    cout<<ans<<"\n";
	}
}

```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next().strip();
            String p = sc.next().strip();
            
            // Create a mapping based on 'p'
            char[] mapper = new char[26];
            for (int i = 0; i < 26; i++) {
                mapper[p.charAt(i) - 'a'] = p.charAt(25 - i); 
            }
            
            int x = 0, y = 1; 
            for (int i = 1; i < n; i++) {
                int nx = n + 1, ny = n + 1;
                
                // Check the conditions and update nx, ny accordingly
                if (s.charAt(i) >= s.charAt(i - 1)) nx = Math.min(nx, x);
                if (s.charAt(i) >= mapper[s.charAt(i - 1) - 'a']) nx = Math.min(nx, y);
                if (mapper[s.charAt(i) - 'a'] >= s.charAt(i - 1)) ny = Math.min(ny, x + 1);
                if (mapper[s.charAt(i) - 'a'] >= mapper[s.charAt(i - 1) - 'a']) ny = Math.min(ny, y + 1);
                
                x = nx; y = ny; // Update x, y for the next iteration
            }
            
            if (Math.min(x, y) > n) {
                System.out.println(-1);
            } else {
                System.out.println(Math.min(x, y));
            }
        }
        sc.close();
    }
}


```
</details>


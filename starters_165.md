## 1. Poster Perimeter

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, m, k = map(int, input().split())
    if k >= 2 * (n + m): print(k - 2*(n+m))
    elif k <= 4: print(4 - k)
    else: print(k%2)
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
        int n, m, k;
        cin >> n >> m >> k;

        if (k >= 2 * (n + m)) {
            cout << k - 2 * (n + m) << endl;
        } else if (k <= 4) {
            cout << 4 - k << endl;
        } else {
            cout << k % 2 << endl;
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
            int m = sc.nextInt();
            int k = sc.nextInt();

            if (k >= 2 * (n + m)) {
                System.out.println(k - 2 * (n + m));
            } else if (k <= 4) {
                System.out.println(4 - k);
            } else {
                System.out.println(k % 2);
            }
        }

        sc.close();
    }
}


```

</details>

## 2. Bulk Discount
<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n = int(input())
    a = list(map(int, input().split()))
    a.sort()
    ans = 0
    for i in range(n):
        ans += max(0, a[i] - i)
    print(ans)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
    int t; cin >> t;
    while (t--) {
        int n; 
        cin >> n;
        vector<int> a(n);
        for (int &x : a) cin >> x;
        sort(begin(a), end(a));
        int ans = 0;
        for (int i = 0; i < n; ++i)
            ans += max(0, a[i] - i);
        cout << ans << '\n';
    }
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); 

        while (t-- > 0) {
            int n = sc.nextInt(); 
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt(); 
            }

            Arrays.sort(a); 
            int ans = 0;
            for (int i = 0; i < n; i++) {
                ans += Math.max(0, a[i] - i); 
            }

            System.out.println(ans); 
        }

        sc.close();
    }
}

```

</details>

## 3. Stable Array

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n = int(input())
    a = list(map(int, input().split()))
    
    mx = n - 1  
    ans = 0     
    for i in range(n - 2, -1, -1):
        if a[i] >= a[mx]:  
            ans = max(ans, mx - i - 1)
            mx = i
    ans = max(ans, mx)
    print(ans)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;


int main()
{
    int t; cin >> t;
    while (t--) {
        int n; cin >> n;
        vector<int> a(n);
        for (int &x : a) cin >> x;
        
        int mx = n - 1, ans = 0;
        for (int i = n - 2; i >= 0; --i) {
            if (a[i] >= a[mx]) { 
                ans = max(ans, mx - i - 1);
                mx = i;
            }
        }
        ans = max(ans, mx);
        cout << ans << '\n';
    }
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); 

        while (t-- > 0) {
            int n = sc.nextInt(); 
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt(); 
            }

            int mx = n - 1; 
            int ans = 0;    
            for (int i = n - 2; i >= 0; i--) {
                if (a[i] >= a[mx]) { 
                    ans = Math.max(ans, mx - i - 1);
                    mx = i;
                }
            }
            ans = Math.max(ans, mx);
            System.out.println(ans);
        }

        sc.close();
    }
}

```

</details>

## 4. Reverse and Alternate

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    s = input()

    def check(l, r):
        cur = s[:l] + s[l:r+1][::-1] + s[r+1:]
        for i in range(n-1):
            if cur[i] == cur[i+1]:
                return False
        return True
    
    x = 0
    while x+1 < n:
        if s[x] != s[x+1]: x += 1
        else: break
    y = x+1
    while y+1 < n:
        if s[y] != s[y+1]: y += 1
        else: break
    
    if x == n-1 or check(0, x) or check(x+1, n-1): print('Yes')
    elif y < n-1 and check(x+1, y): print('Yes')
    else: print('No')
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

bool check(const string& s, int l, int r, int n) {
    string cur = s.substr(0, l) + string(s.begin() + l, s.begin() + r + 1) + s.substr(r + 1);
    reverse(cur.begin() + l, cur.begin() + r + 1);
    for (int i = 0; i < n - 1; i++) {
        if (cur[i] == cur[i + 1]) {
            return false;
        }
    }
    return true;
}

int main() {
    int t;
    cin >> t;

    while (t--) {
        int n;
        cin >> n;
        string s;
        cin >> s;

        int x = 0;
        while (x + 1 < n && s[x] != s[x + 1]) {
            x++;
        }

        int y = x + 1;
        while (y + 1 < n && s[y] != s[y + 1]) {
            y++;
        }

        if (x == n - 1 || check(s, 0, x, n) || check(s, x + 1, n - 1, n)) {
            cout << "Yes\n";
        } else if (y < n - 1 && check(s, x + 1, y, n)) {
            cout << "Yes\n";
        } else {
            cout << "No\n";
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

    public static boolean check(String s, int l, int r, int n) {
        String cur = s.substring(0, l) + 
                     new StringBuilder(s.substring(l, r + 1)).reverse().toString() + 
                     s.substring(r + 1);
        for (int i = 0; i < n - 1; i++) {
            if (cur.charAt(i) == cur.charAt(i + 1)) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();

            int x = 0;
            while (x + 1 < n && s.charAt(x) != s.charAt(x + 1)) {
                x++;
            }

            int y = x + 1;
            while (y + 1 < n && s.charAt(y) != s.charAt(y + 1)) {
                y++;
            }

            if (x == n - 1 || check(s, 0, x, n) || check(s, x + 1, n - 1, n)) {
                System.out.println("Yes");
            } else if (y < n - 1 && check(s, x + 1, y, n)) {
                System.out.println("Yes");
            } else {
                System.out.println("No");
            }
        }

        sc.close();
    }
}


```

</details>

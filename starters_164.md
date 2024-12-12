## 1. Itz Simple

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, k, p = map(int, input().split())
    a = list(map(int, input().split()))
    
    k += max(a)
    p += sum(a) - max(a)
    
    if k > p: print('Ved')
    elif k == p: print('Equal')
    else: print('Varun')
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
        int n, k, p;
        cin >> n >> k >> p;
        
        vector<int> a(n);
        int sum = 0, max_val = INT_MIN;
        
        for (int i = 0; i < n; i++) {
            cin >> a[i];
            sum += a[i];
            if (a[i] > max_val) {
                max_val = a[i];
            }
        }
        
        k += max_val;
        p += sum - max_val;
        
        if (k > p) {
            cout << "Ved" << endl;
        } else if (k == p) {
            cout << "Equal" << endl;
        } else {
            cout << "Varun" << endl;
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
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt(); 
        
        while (t-- > 0) {
            int n = scanner.nextInt(); 
            int k = scanner.nextInt();
            int p = scanner.nextInt();
            
            int[] a = new int[n];
            int max = Integer.MIN_VALUE;
            int sum = 0;
            
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
                sum += a[i];
                if (a[i] > max) {
                    max = a[i];
                }
            }
            
            k += max;
            p += sum - max;
            
            if (k > p) {
                System.out.println("Ved");
            } else if (k == p) {
                System.out.println("Equal");
            } else {
                System.out.println("Varun");
            }
        }
        
        scanner.close();
    }
}

```

</details>

## 2. Swap and Flip
<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    s = input()
    t = input()
    
    zs, zt = s.count('0'), t.count('0')
    if zs%2 == zt%2: print('Yes')
    else: print('No')
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int T;
    cin >> T;

    while (T--) {
        int n;
        cin >> n;
        string s, t;
        cin >> s >> t;

        int zs = 0, zt = 0;
        for (char c : s) {
            if (c == '0') zs++;
        }
        for (char c : t) {
            if (c == '0') zt++;
        }

        if (zs % 2 == zt % 2) {
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
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
    public static void main (String[] args) throws java.lang.Exception
    {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();

        while (T-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();
            String t = sc.next();

            int zs = 0, zt = 0;
            for (char c : s.toCharArray()) {
                if (c == '0') zs++;
            }
            for (char c : t.toCharArray()) {
                if (c == '0') zt++;
            }

            if (zs % 2 == zt % 2) {
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

## 3. Construct Permutation

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    if n % 2 == 0:
        print(-1)
        return

    p1 = n
    p2 = 2

    for i in range(1, n + 1):
        if i % 2 == 1:
            print(p1, end=" ")
            p1 -= 2
        else:
            print(p2, end=" ")
            p2 += 2
    print()

t = int(input())
for _ in range(t):
    solve()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

void Solve() 
{
    int n;
    cin >> n;

    if (n % 2 == 0) {
        cout << -1 << "\n";
        return;
    }

    int p1 = n;
    int p2 = 2;

    for (int i = 1; i <= n; i++) {
        if (i % 2 == 1) {
            cout << p1 << " ";
            p1 -= 2;
        } else {
            cout << p2 << " ";
            p2 += 2;
        }
    }
    cout << "\n";
}

int main() 
{
    int t;
    cin >> t;

    for (int i = 0; i < t; i++) {
        Solve();
    }

    return 0;
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.io.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int testCases = scanner.nextInt();
        
        while (testCases-- > 0) {
            int n = scanner.nextInt();
            
            if (n % 2 == 0) {
                System.out.println(-1);
                continue;
            }
            
            for (int i = 1; i <= n; i++) {
                if (i % 2 == 0) {
                    System.out.print(n - i + 1 + " ");
                } else {
                    System.out.print(i + " ");
                }
            }
            System.out.println();
        }
        scanner.close();
    }
}
```

</details>

## 4. Halloween Array

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, l, r = map(int, input().split())
    a = list(map(int, input().split()))
    
    dup = len(set(a)) < n
    if dup:
        print('Yes' if l == 0 else 'No')
        continue
    
    prod = 1
    for i in range(n):
        for j in range(i+1, n):
            prod *= a[i] ^ a[j]
            if prod > r: break
        else:
            continue
        break
    
    print('Yes' if l <= prod <= r else 'No')
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

int main() {
    int t;
    cin >> t; 
    
    while (t--) {
        int n, l, r;
        cin >> n >> l >> r;
        
        vector<int> a(n);
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }
        
        unordered_set<int> seen;
        bool hasDuplicate = false;
        for (int num : a) {
            if (seen.count(num)) {
                hasDuplicate = true;
                break;
            }
            seen.insert(num);
        }
        
        if (hasDuplicate) {
            cout << (l == 0 ? "Yes" : "No") << endl;
            continue;
        }
        
        long long prod = 1;
        bool exceeded = false;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                prod *= (a[i] ^ a[j]);
                if (prod > r) {
                    exceeded = true;
                    break;
                }
            }
            if (exceeded) break;
        }
        
        cout << ((l <= prod && prod <= r) ? "Yes" : "No") << endl;
    }
    
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt(); 
        
        while (t-- > 0) {
            int n = scanner.nextInt(); 
            int l = scanner.nextInt(); 
            int r = scanner.nextInt(); 
            
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
            }
            
            Set<Integer> set = new HashSet<>();
            boolean hasDuplicate = false;
            for (int num : a) {
                if (!set.add(num)) {
                    hasDuplicate = true;
                    break;
                }
            }
            
            if (hasDuplicate) {
                System.out.println(l == 0 ? "Yes" : "No");
                continue;
            }
            
            long prod = 1;
            boolean exceeded = false;
            for (int i = 0; i < n; i++) {
                for (int j = i + 1; j < n; j++) {
                    prod *= (a[i] ^ a[j]);
                    if (prod > r) {
                        exceeded = true;
                        break;
                    }
                }
                if (exceeded) break;
            }
            
            System.out.println((l <= prod && prod <= r) ? "Yes" : "No");
        }
        
        scanner.close();
    }
}

```

</details>

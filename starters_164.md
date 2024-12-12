## Itz Simple

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

## Question - 2

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

## Question - 3

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

## Halloween Array

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

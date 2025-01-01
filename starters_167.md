## 1. Happy New Year!

<details>
<summary>Python</summary>

```python
x = int(input())
print(24 - x)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int x;
    cin >> x;
    cout << 24 - x << endl;
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
        int x = scanner.nextInt();
        System.out.println(24 - x);
        scanner.close();
    }
}

```

</details>

## 2. Delete Not Equal
<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    s = input()
    if min(s) == max(s): print(n)
    else: print(1)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    int t; 
    cin >> t;

    while (t--) {
        int n; 
        cin >> n;
        string s;
        cin >> s;

        if (*min_element(s.begin(), s.end()) == *max_element(s.begin(), s.end())) {
            cout << n << endl;
        } else {
            cout << 1 << endl;
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
        
        for (int i = 0; i < t; i++) {
            int n = scanner.nextInt(); 
            String s = scanner.next(); 
            
            if (s.chars().min().getAsInt() == s.chars().max().getAsInt()) {
                System.out.println(n);
            } else {
                System.out.println(1);
            }
        }
        
        scanner.close();
    }
}


```

</details>

## 3. Lottery Tickets

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = list(map(int, input().split()))
    
    left, right = 1, 10**6
    for y in a[1:]:
        if y < a[0]: left = max(left, a[0] - (a[0] - y)//2)
        else: right = min(right, a[0] + (y - a[0])//2)
    print(right - left + 1)
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
        int n;
        cin >> n;
        vector<int> a(n);
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }

        int left = 1, right = 1e6;
        for (int i = 1; i < n; i++) {
            if (a[i] < a[0]) {
                left = max(left, a[0] - (a[0] - a[i]) / 2);
            } else {
                right = min(right, a[0] + (a[i] - a[0]) / 2);
            }
        }
        cout << (right - left + 1) << endl;
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
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
            }

            int left = 1, right = (int) 1e6;
            for (int i = 1; i < n; i++) {
                if (a[i] < a[0]) {
                    left = Math.max(left, a[0] - (a[0] - a[i]) / 2);
                } else {
                    right = Math.min(right, a[0] + (a[i] - a[0]) / 2);
                }
            }
            System.out.println(right - left + 1);
        }

        scanner.close();
    }
}

```

</details>

## 4. Temperature Balance

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = list(map(int, input().split()))
    pref = ans = 0
    for x in a:
        pref += x
        ans += abs(pref)
    print(ans)

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
        int n;
        cin >> n;
        vector<long long> vec(n);
        for (long long &i : vec) cin >> i;

        int p = 0;
        long long ans = 0;
        for (int i = 0; i < n; i++) {
            while (vec[i] < 0) {
                while (vec[p] <= 0) p++;
                long long val = min(vec[p], -vec[i]);
                vec[p] -= val;
                vec[i] += val;
                ans += val * abs(i - p);
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
import java.util.Scanner;
import java.util.Vector;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        
        while (t-- > 0) {
            int n = scanner.nextInt();
            Vector<Long> vec = new Vector<>();
            for (int i = 0; i < n; i++) {
                vec.add(scanner.nextLong());
            }

            int p = 0;
            long ans = 0;
            for (int i = 0; i < n; i++) {
                while (vec.get(i) < 0) {
                    while (vec.get(p) <= 0) p++;
                    long val = Math.min(vec.get(p), -vec.get(i));
                    vec.set(p, vec.get(p) - val);
                    vec.set(i, vec.get(i) + val);
                    ans += val * Math.abs(i - p);
                }
            }
            System.out.println(ans);
        }

        scanner.close();
    }
}


```

</details>

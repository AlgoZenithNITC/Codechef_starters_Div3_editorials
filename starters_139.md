## 1. Distribute Cookies

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n,m = map(int,input().split())
    temp = m//n
    if temp == 0:
        print(n-m)
        continue
    print(min(m-temp*n,(temp+1)*n-m))
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        int temp = m / n;
        if (temp == 0) {
            cout << n - m << endl;
            continue;
        }
        cout << min(m - temp * n, (temp + 1) * n - m) << endl;
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
            int temp = m / n;
            if (temp == 0) {
                System.out.println(n - m);
                continue;
            }
            System.out.println(Math.min(m - temp * n, (temp + 1) * n - m));
        }
    }
}

```

</details>

## 2. Maximum Distance Permutations

<details>
<summary>Python</summary>

```python
def solve():
  """
  Prints a sequence of numbers in a specific order.
  """
  n = int(input())

  # Print first half in ascending order
  for i in range(n):
    print(i + 1, end=" ")
  print()

  # Print second half in descending order (starting from n/2)
  for i in range(n // 2, n):
    print(i + 1, end=" ")
  print()

  # Print first half again in ascending order
  for i in range(n // 2):
    print(i + 1, end=" ")
  print()

if __name__ == "__main__":
  test_cases = int(input())

  for _ in range(test_cases):
    solve()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

/**
 * @brief helper function to solve
 *        an individual test case
 */
void solve() {
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cout << i + 1 << " ";
    }
    cout << endl;
    
    for (int i = n / 2; i < n; i++) {
        cout << i + 1 << " ";
    }
    
    for (int i = 0; i < n / 2; i++) {
        cout << i + 1 << " ";
    }
    cout << endl;
}

/**
 * @brief Driver Code
 * 
 * @return int 
 */
int main() {
	// your code goes here

    int t;
    cin >> t;

    while (t--)
    {
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

public class SequencePrinter {

    public static void solve() {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();

        // Print first half in ascending order
        for (int i = 0; i < n; i++) {
            System.out.print(i + 1 + " ");
        }
        System.out.println();

        // Print second half in descending order (starting from n/2)
        for (int i = n / 2; i < n; i++) {
            System.out.print(i + 1 + " ");
        }
        System.out.println();

        // Print first half again in ascending order
        for (int i = 0; i < n / 2; i++) {
            System.out.print(i + 1 + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int testCases = scanner.nextInt();

        while (testCases-- > 0) {
            solve();
        }
    }
};
```

</details>

## 3. Sum of N

<details>
<summary>Python</summary>

```python
import math

def sieve(n):
    isprime = [True]*(n+1)
    isprime[0] = isprime[1] = False
    for i in range(2,math.isqrt(n)+1):
        if isprime[i]:
            for j in range(i*i,n+1,i):
                isprime[j] = False
    return isprime
    
isprime = sieve(10**6+1)
total = 0
primeprefix = [0]*(10**6+1)

for i in range(2,10**6+1):
    if isprime[i]:
        total+=i
    primeprefix[i] = total

        
for _ in range(int(input())):
    k = int(input())
    if isprime[k]:
        print(primeprefix[k]*k)
        continue
    ans = 0
    for i in range(2,math.isqrt(k)+1):
        if isprime[i]:
            ans+=i
        if k%i == 0:
            break
    print(ans*k)
    
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

vector<bool> sieve(int n) {
    vector<bool> isprime(n + 1, true);
    isprime[0] = isprime[1] = false;
    for (int i = 2; i * i <= n; ++i) {
        if (isprime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isprime[j] = false;
            }
        }
    }
    return isprime;
}

int main() {
    int limit = 1000000;
    vector<bool> isprime = sieve(limit + 1);
    vector<long long> primeprefix(limit + 1, 0);
    long long total = 0;

    for (int i = 2; i <= limit; ++i) {
        if (isprime[i]) {
            total += i;
        }
        primeprefix[i] = total;
    }

    int t;
    cin >> t;
    while (t--) {
        int k;
        cin >> k;
        if (isprime[k]) {
            cout << primeprefix[k] * k << endl;
            continue;
        }
        long long ans = 0;
        for (int i = 2; i * i <= k; ++i) {
            if (isprime[i]) {
                ans += i;
            }
            if (k % i == 0) {
                break;
            }
        }
        cout << ans * k << endl;
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

    public static boolean[] sieve(int n) {
        boolean[] isprime = new boolean[n + 1];
        for (int i = 0; i <= n; i++) {
            isprime[i] = true;
        }
        isprime[0] = isprime[1] = false;
        for (int i = 2; i * i <= n; i++) {
            if (isprime[i]) {
                for (int j = i * i; j <= n; j += i) {
                    isprime[j] = false;
                }
            }
        }
        return isprime;
    }

    public static void main(String[] args) {
        int limit = 1000000;
        boolean[] isprime = sieve(limit + 1);
        long[] primeprefix = new long[limit + 1];
        long total = 0;

        for (int i = 2; i <= limit; i++) {
            if (isprime[i]) {
                total += i;
            }
            primeprefix[i] = total;
        }

        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int k = sc.nextInt();
            if (isprime[k]) {
                System.out.println(primeprefix[k] * k);
                continue;
            }
            long ans = 0;
            for (int i = 2; i * i <= k; i++) {
                if (isprime[i]) {
                    ans += i;
                }
                if (k % i == 0) {
                    break;
                }
            }
            System.out.println(ans * k);
        }
    }
}

```

</details>

## 4. Destroying Bridges Part 2

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, c = map(int, input().split())
    a = list(map(int, input().split()))
    a[1:] = sorted(a[1:])[::-1]
    ans = n
    for i in range(n-1):
        c1 = sum(a[:i+1])
        c2 = sum(a[i+1:])
        if c1*c2 <= c: ans = min(ans, i+1)
    print(ans)
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

    for (int _ = 0; _ < t; _++) {
    int n, c;
    cin >> n >> c;

    vector<int> a(n);
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    // Sort remaining elements (from index 1) in descending order
    sort(a.begin() + 1, a.end(), greater<int>());

    int ans = n;
    for (int i = 0; i < n - 1; i++) {
        int c1 = accumulate(a.begin(), a.begin() + i + 1, 0); // Sum of first i+1 elements
        int c2 = accumulate(a.begin() + i + 1, a.end(), 0); // Sum of remaining elements
        if (c1 * c2 <= c) {
            ans = min(ans, i + 1);
        }
    }

    cout << ans << endl;

    return 0;
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Collections;

public class SplitArray {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int t = scanner.nextInt();

        for (int _ = 0; _ < t; _++) {
            int n = scanner.nextInt();
            int c = scanner.nextInt();

            ArrayList<Integer> a = new ArrayList<>();
            for (int i = 0; i < n; i++) {
                a.add(scanner.nextInt());
            }

            // Sort remaining elements (from index 1) in descending order
            Collections.sort(a.subList(1, a.size()), Collections.reverseOrder());

            int ans = n;
            for (int i = 0; i < n - 1; i++) {
                int c1 = 0;
                for (int j = 0; j <= i; j++) {
                    c1 += a.get(j);  // Sum of first i+1 elements
                }
                int c2 = 0;
                for (int j = i + 1; j < n; j++) {
                    c2 += a.get(j);  // Sum of remaining elements
                }
                if (c1 * c2 <= c) {
                    ans = Math.min(ans, i + 1);
                }
            }

            System.out.println(ans);
        }
    }
}
```

</details>

## Question - 5

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

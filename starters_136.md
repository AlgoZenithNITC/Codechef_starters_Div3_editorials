## Question - 1

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

## 3. Sum of Modes

<details>
<summary>Python</summary>

```python
from collections import defaultdict
for _ in range(int(input())):
    n = int(input())
    s = input()
    ans = (n*(n+1))//2 # as every substring will have 1 contribution
    total = 0
    d = defaultdict(int)
    d[0] = 1
    for i in s:
        if i == '1':
            total+=1
        else:
            total-=1
        ans+=d[total]
        d[total]+=1
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <unordered_map>
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
        long long ans = (long long)n * (n + 1) / 2;
        int total = 0;
        unordered_map<int, int> map;
        map[0] = 1;
        for (char c : s) {
            if (c == '1') {
                total += 1;
            } else {
                total -= 1;
            }
            ans += map[total];
            map[total]++;
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
import java.util.HashMap;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            scanner.nextLine(); // Consume the newline
            String s = scanner.nextLine();
            long ans = (long) n * (n + 1) / 2;
            int total = 0;
            HashMap<Integer, Integer> map = new HashMap<>();
            map.put(0, 1);
            for (int i = 0; i < s.length(); i++) {
                if (s.charAt(i) == '1') {
                    total += 1;
                } else {
                    total -= 1;
                }
                ans += map.getOrDefault(total, 0);
                map.put(total, map.getOrDefault(total, 0) + 1);
            }
            System.out.println(ans);
        }
        scanner.close();
    }
}

```

</details>

## 4. Sum of Max K Subarray

<details>
<summary>Python</summary>

```python
mod = (10**9)+7
fac = [0]*(10**6)
fac[0] = 1
for i in range(1,10**6):
    fac[i] = (fac[i-1]*i)%mod
for _ in range(int(input())):
    n = int(input())
    for i in range(1,n+1):
        temp = n//i
        rem = n%i
        ans = (fac[temp]*fac[n-temp])%mod
        ans = (ans*(i-rem))%mod
        print(ans,end = ' ')
    print()
       
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#define MOD 1000000007
#define MAX 1000000

using namespace std;

vector<long long> fac(MAX);

void precompute_factorials() {
    fac[0] = 1;
    for (int i = 1; i < MAX; i++) {
        fac[i] = (fac[i - 1] * i) % MOD;
    }
}

int main() {
    precompute_factorials();

    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        for (int i = 1; i <= n; i++) {
            int temp = n / i;
            int rem = n % i;
            long long ans = (fac[temp] * fac[n - temp]) % MOD;
            ans = (ans * (i - rem)) % MOD;
            cout << ans << " ";
        }
        cout << endl;
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
    static final int MOD = (int) (1e9 + 7);
    static final int MAX = (int) (1e6);
    static long[] fac = new long[MAX];

    static {
        fac[0] = 1;
        for (int i = 1; i < MAX; i++) {
            fac[i] = (fac[i - 1] * i) % MOD;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            for (int i = 1; i <= n; i++) {
                int temp = n / i;
                int rem = n % i;
                long ans = (fac[temp] * fac[n - temp]) % MOD;
                ans = (ans * (i - rem)) % MOD;
                System.out.print(ans + " ");
            }
            System.out.println();
        }
        scanner.close();
    }
}

```

</details>

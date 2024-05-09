# Codechef_starters_133_Div3

<!-- First Question -->
# Legs on a Farm
<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    for i in range(t):
        n = int(input())
        print((n + 3) // 4)

if __name__ == "__main__":
    main()

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
	cin >> t;
	for(int i=0; i<t; i++) {
	    int n;
	    cin >> n;
	    cout << (n+3)/4 << "\n";
	}

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
            System.out.println((n + 3) / 4);
        }
        scanner.close();
    }
}

```
</details>

<!-- Second Question -->
# Maximum Alternating Sum

<details>
<summary>Python</summary>

```python
def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    
    index = 0
    t = int(data[index])
    index += 1
    
    results = []
    
    for _ in range(t):
        n = int(data[index])
        index += 1
        vec = [int(data[index + i]) for i in range(n)]
        index += n
        
        vec.sort()
        
        tot = 0
        for i in range(n // 2):
            tot -= vec[i]
        
        for i in range(n // 2, n):
            tot += vec[i]
        
        results.append(tot)
    
    


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
        
        vector<int> vec(n);
        for (int i = 0; i < n; i++) {
            cin >> vec[i];
        }
        
        // Sort the vector
        sort(vec.begin(), vec.end());
        
        // Calculate the difference
        long long tot = 0;
        for (int i = 0; i < n / 2; i++) {
            tot -= vec[i];
        }
        
        for (int i = n / 2; i < n; i++) {
            tot += vec[i];
        }
        
        // Print the result
        cout << tot << "\n";
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
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        long[] results = new long[t];
        
        for (int _ = 0; _ < t; _++) {
            int n = scanner.nextInt();
            int[] vec = new int[n];
            
            for (int i = 0; i < n; i++) {
                vec[i] = scanner.nextInt();
            }
            
            Arrays.sort(vec);
            
            long tot = 0;
            
            for (int i = 0; i < n / 2; i++) {
                tot -= vec[i];
            }
            
            for (int i = n / 2; i < n; i++) {
                tot += vec[i];
            }
            
            results[_] = tot;
        }
        
        for (long result : results) {
            System.out.println(result);
        }
        
        scanner.close();
    }
}


```
</details>

<!-- Third Quesion -->
# Powered Paramters

<details>
<summary>Python</summary>

```python
def check(x, c, v):
    v1 = 1
    for _ in range(c):
        v1 *= x
        if v1 > v:
            return False
    return True

def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    
    index = 0
    t = int(data[index])
    index += 1
    
    results = []
    
    for _ in range(t):
        n = int(data[index])
        index += 1
        
        vec = []
        c = 0
        
        for _ in range(n):
            vec.append(int(data[index]))
            index += 1
        
        for i in range(n):
            if vec[i] == 1:
                c += n
        
        for i in range(min(30, n)):
            for j in range(n):
                if vec[j] != 1:
                    c += check(vec[j], i + 1, vec[i])
        
        results.append(c)
    
    for result in results:
        print(result)

if __name__ == "__main__":
    main()

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>

using namespace std;

typedef long long int lli;

bool check(lli x, int c, lli v) {
    lli v1 = 1;
    for (int i = 0; i < c; i++) {
        v1 *= x;
        if (v1 > v) {
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
        
        vector<lli> vec(n);
        lli c = 0;
        for (int i = 0; i < n; i++) {
            cin >> vec[i];
            if (vec[i] == 1) {
                c += n;
            }
        }
        
        for (int i = 0; i < min(30, n); i++) {
            for (int j = 0; j < n; j++) {
                if (vec[j] != 1) {
                    c += check(vec[j], i + 1, vec[i]);
                }
            }
        }
        
        cout << c << "\n";
    }

    return 0;
}


```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {
    public static boolean check(long x, int c, long v) {
        long v1 = 1;
        for (int i = 0; i < c; i++) {
            v1 *= x;
            if (v1 > v) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        
        while (t-- > 0) {
            int n = scanner.nextInt();
            
            long[] vec = new long[n];
            long c = 0;
            
            for (int i = 0; i < n; i++) {
                vec[i] = scanner.nextLong();
                if (vec[i] == 1) {
                    c += n;
                }
            }
            
            for (int i = 0; i < Math.min(30, n); i++) {
                for (int j = 0; j < n; j++) {
                    if (vec[j] != 1) {
                        c += check(vec[j], i + 1, vec[i]);
                    }
                }
            }
            
            System.out.println(c);
        }
        
        scanner.close();
    }
}

```
</details>

<!-- Fourth Question -->
# ABC Conjucture 3

<details>
    <summary>Python</summary>

```python
def fastio():
    import sys
    input = sys.stdin.read
    data = input().split()
    index = 0
    t = int(data[index])
    index += 1
    
    results = []
    
    for _ in range(t):
        n = int(data[index])
        index += 1
        str_ = data[index]
        index += 1
        
        pra = [0] * (n + 2)
        sfc = [0] * (n + 2)
        
        # Calculate prefix sum of 'a'
        for i in range(1, n + 1):
            pra[i] = pra[i - 1] + (1 if str_[i - 1] == 'a' else 0)
        
        # Calculate suffix sum of 'c'
        for i in range(n, 0, -1):
            sfc[i] = sfc[i + 1] + (1 if str_[i - 1] == 'c' else 0)
        
        mi = float('inf')
        bpos = []
        
        # Collect positions of 'b'
        for i in range(1, n + 1):
            if str_[i - 1] == 'b':
                bpos.append(i)
        
        if len(bpos) == 0:
            results.append("0")
            continue
        
        mi = min(pra[bpos[-1]], sfc[bpos[0]])
        
        # Calculate minimum value
        for i in range(len(bpos) - 1):
            mi = min(mi, pra[bpos[i]] + sfc[bpos[i + 1]])
        
        results.append(str(mi))
    
    # Print results
    for result in results:
        print(result)

if __name__ == "__main__":
    fastio()

```
</details>


<details>
  	<summary>C++</summary>
  
```cpp
#include <bits/stdc++.h>

using namespace std;

#define scd(t) scanf("%d", &t)
#define forr(i, j, k) for (int i = j; i < k; i++)
#define frange(i, j) forr(i, 0, j)
#define all(cont) cont.begin(), cont.end()
typedef vector<int> vi;

void usaco()
{
    freopen("/media/hariaakash646/785EF1075EF0BF46/CompetitiveProgramming/input.in", "r", stdin);
//    freopen("problem.out", "w", stdout);
}

void fastio()
{
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);
}

int main() {
    // usaco();
    fastio();
    int t;
    cin >> t;
    frange(_, t) {
        int n;
        string str;
        cin >> n >> str;

        vector<int> pra(n+2), sfc(n+2);

        forr(i, 1, n+1) {
            pra[i] = pra[i-1] + (str[i-1] == 'a');
        }
        for(int i=n; i>=1; i--) {
            sfc[i] = sfc[i+1] + (str[i-1] == 'c');
        }

        int mi = 1e9;
        vector<int> bpos;
        forr(i, 1, n+1) {
            if(str[i-1] == 'b') bpos.push_back(i);
        }
        if(bpos.size() == 0) {
            printf("0\n");
            continue;
        }
        mi = min(pra[bpos.back()], sfc[bpos.front()]);
        forr(i, 0, (int)bpos.size() - 1) {
            mi = min(mi, pra[bpos[i]] + sfc[bpos[i+1]]);
        }
        printf("%d\n", mi);
    }
}
```
</details>


<details>
	<summary>JAVA</summary>
  
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        
        int t = Integer.parseInt(tokenizer.nextToken());
        List<Integer> results = new ArrayList<>();
        
        for (int _ = 0; _ < t; _++) {
            tokenizer = new StringTokenizer(reader.readLine());
            int n = Integer.parseInt(tokenizer.nextToken());
            String str = tokenizer.nextToken();
            
            int[] pra = new int[n + 2];
            int[] sfc = new int[n + 2];
            
            // Calculate prefix sum of 'a'
            for (int i = 1; i <= n; i++) {
                pra[i] = pra[i - 1] + (str.charAt(i - 1) == 'a' ? 1 : 0);
            }
            
            // Calculate suffix sum of 'c'
            for (int i = n; i >= 1; i--) {
                sfc[i] = sfc[i + 1] + (str.charAt(i - 1) == 'c' ? 1 : 0);
            }
            
            int mi = Integer.MAX_VALUE;
            List<Integer> bpos = new ArrayList<>();
            
            // Collect positions of 'b'
            for (int i = 1; i <= n; i++) {
                if (str.charAt(i - 1) == 'b') {
                    bpos.add(i);
                }
            }
            
            if (bpos.isEmpty()) {
                results.add(0);
                continue;
            }
            
            // Calculate minimum value
            mi = Math.min(pra[bpos.get(bpos.size() - 1)], sfc[bpos.get(0)]);
            for (int i = 0; i < bpos.size() - 1; i++) {
                mi = Math.min(mi, pra[bpos.get(i)] + sfc[bpos.get(i + 1)]);
            }
            
            results.add(mi);
        }
        
        // Print results
        for (int result : results) {
            System.out.println(result);
        }
    }
}

```
</details>

<!-- Fifth Question -->
# Too Far For Comfort

<details>
<summary>Python</summary>
  
```python
MOD = 998244353
MAX_FACT = int(5e5) + 1

# Precompute factorials
fact = [1] * MAX_FACT

for i in range(1, MAX_FACT):
    fact[i] = (fact[i - 1] * i) % MOD

def inv(a):
    """Calculate the modular inverse of a under MOD using Fermat's Little Theorem."""
    return pow(a, MOD - 2, MOD)

def combi(n, r):
    """Calculate combination C(n, r) under MOD."""
    return (fact[n] * inv(fact[r]) % MOD) * inv(fact[n - r]) % MOD

def binexp(x, c):
    """Calculate binary exponentiation x^c under MOD."""
    if c == 0:
        return 1
    v = binexp(x, c // 2)
    v = (v * v) % MOD
    if c % 2:
        return (v * x) % MOD
    else:
        return v

def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    index = 0
    
    t = int(data[index])
    index += 1
    
    results = []
    
    for _ in range(t):
        n = int(data[index])
        index += 1
        m = int(data[index])
        index += 1
        
        tot = 0
        # Calculate total sum
        for i in range(1, min(n, m) + 1):
            out = binexp(fact[i], n // i)
            c = n % i
            out = (out * (fact[i] * inv(fact[i - c]) % MOD)) % MOD
            out = (out * combi(m, i)) % MOD
            tot = (tot + out) % MOD
        
        results.append(tot)
    
    for result in results:
        print(result)

if __name__ == "__main__":
    main()

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>

using namespace std;

#define scd(t) scanf("%d", &t)
#define forr(i, j, k) for (int i = j; i < k; i++)
#define frange(i, j) forr(i, 0, j)

typedef long long int lli;
typedef vector<int> vi;
typedef vector<lli> vll;


void usaco()
{
    freopen("/media/hariaakash646/785EF1075EF0BF46/CompetitiveProgramming/input.in", "r", stdin);
//    freopen("problem.out", "w", stdout);
}

const lli mod = 998244353;
vll fact(5e5+1, 1);

lli inv(lli a) {
  return a <= 1 ? a : mod - (mod/a) * inv(mod % a) % mod;
}

lli combi(int n, int r) {
    return (fact[n] * inv(fact[r]) % mod) * inv(fact[n-r]) % mod;
}

lli binexp(lli x, int c) {
    if(c == 0) return 1;
    lli v = binexp(x, c/2);
    v = (v*v) % mod;
    if(c % 2) return v * x % mod;
    else return v;
}

int main() {
    // usaco();
    forr(i, 1, 5e5+1) {
        fact[i] = (fact[i-1]*i) % mod;
    }
    int t;
    scd(t);

    frange(_, t) {
        int n, m;
        scd(n);
        scd(m);
        lli tot = 0;
        forr(i, 1, min(n, m)+1) {
            lli out = binexp(fact[i], n/i);
            int c = n%i;
            out = out * (fact[i] * inv(fact[i-c]) % mod) % mod;
            out = out * combi(m, i) % mod;
            tot = (tot + out) % mod;
        }
        printf("%lld\n", tot);
    }
}
```
</details>

<details>
<summary>Java</summary>

```java
import java.io.*;
import java.util.*;

public class Main {
    static final long MOD = 998244353;
    static final int MAX_FACT = (int) 5e5 + 1;
    static long[] fact = new long[MAX_FACT];
    
    static {
        // Precompute factorials
        fact[0] = 1;
        for (int i = 1; i < MAX_FACT; i++) {
            fact[i] = (fact[i - 1] * i) % MOD;
        }
    }
    
    public static long inv(long a) {
        return binexp(a, MOD - 2);
    }
    
    public static long combi(int n, int r) {
        return (fact[n] * inv(fact[r]) % MOD) * inv(fact[n - r]) % MOD;
    }
    
    public static long binexp(long x, long c) {
        if (c == 0) {
            return 1;
        }
        long v = binexp(x, c / 2);
        v = (v * v) % MOD;
        if (c % 2 == 1) {
            return (v * x) % MOD;
        } else {
            return v;
        }
    }
    
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(reader.readLine());
        
        int t = Integer.parseInt(tokenizer.nextToken());
        List<Long> results = new ArrayList<>();
        
        for (int _ = 0; _ < t; _++) {
            tokenizer = new StringTokenizer(reader.readLine());
            int n = Integer.parseInt(tokenizer.nextToken());
            int m = Integer.parseInt(tokenizer.nextToken());
            
            long tot = 0;
            
            for (int i = 1; i <= Math.min(n, m); i++) {
                long out = binexp(fact[i], n / i);
                int c = n % i;
                out = (out * (fact[i] * inv(fact[i - c]) % MOD)) % MOD;
                out = (out * combi(m, i)) % MOD;
                tot = (tot + out) % MOD;
            }
            
            results.add(tot);
        }
        
        for (long result : results) {
            System.out.println(result);
        }
    }
}

```
</details>
##  No Odd Sum

<details>
<summary>Python</summary>

```python
t = int(input())
while t != 0:
    n = int(input())
    arr = list(map(int, input().split()))
    
    one = arr.count(1)
    two = n - one  
    
    if one == 0 or two == 0:
        print(0)
    elif one % 2 == 0:
        if one // 2 < two:
            print(one // 2)
        else:
            print(two)
    else:
        print(two)
    
    t -= 1


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    // your code goes here
    int t;
    cin >> t;
    while (t != 0) {
        int n;
        cin >> n;
        int arr[n];
        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }
        int one = 0, two = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] == 1) {
                one++;
            }
            else {
                two++;
            }
        }
        if(one==0||two==0){
            cout<<0<<"\n";
        }
       else if(one%2==0){
           if(one/2<two){
            cout<<one/2<<"\n";
           }
           else{
               cout<<two<<"\n";
           }
        }
        else{
            cout<<two<<"\n";
        }
        t--;
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while (t != 0) {
            int n = sc.nextInt();
            int[] arr = new int[n];
            int one = 0, two = 0;

            for (int i = 0; i < n; i++) {
                arr[i] = sc.nextInt();
                if (arr[i] == 1) {
                    one++;
                } else {
                    two++;
                }
            }

            if (one == 0 || two == 0) {
                System.out.println(0);
            } else if (one % 2 == 0) {
                if (one / 2 < two) {
                    System.out.println(one / 2);
                } else {
                    System.out.println(two);
                }
            } else {
                System.out.println(two);
            }

            t--;
        }
        
        sc.close();
    }
}


```

</details>

##  Security Lines

<details>
<summary>Python</summary>

```python
T=int(input())
for _ in range(T):
    N=int(input())
    A=[0]+list(map(int,input().split()))
    ans=A[1]
    for j in range(2,N+1):
        t=max(A[j]+1,j-1)
        ans=min(ans,t)
    print(ans)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int T;
    cin >> T;
    while (T--) {
        int N;
        cin >> N;
        vector<int> A(N + 1);
        for (int i = 1; i <= N; ++i) cin >> A[i];
        int ans = A[1];
        for (int j = 2; j <= N; ++j) {
            int t = max(A[j] + 1, j - 1);
            ans = min(ans, t);
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
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            int[] A = new int[N + 1];
            for (int i = 1; i <= N; i++) A[i] = sc.nextInt();
            int ans = A[1];
            for (int j = 2; j <= N; j++) {
                int t = Math.max(A[j] + 1, j - 1);
                ans = Math.min(ans, t);
            }
            System.out.println(ans);
        }
    }
}


```

</details>

##  No 3 Please!

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    a = list(map(int, input().split()))

    if n == 1:
        print("Yes")
        return

    k = -1
    for i in range(1, n):
        if a[i] == a[i - 1]:
            k = i
            break

    if k == -1 and n >= 2:
        print("No")
        return

    prefix = [0] * n
    prefix[0] = a[k]

    i = 1
    for j in range(k - 1, -1, -1):
        prefix[i] = prefix[i - 1] + a[j]
        i += 1

    for i in range(k + 1, n):
        prefix[i] = prefix[i - 1] + a[i]

    for val in prefix:
        if val % 3 == 0:
            print("No")
            return

    print("Yes")


for _ in range(int(input())):
    solve()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
    int n; cin >> n;
    vector<int> a(n);
    for(auto& it : a) cin >> it;
    if (n == 1) {cout << "Yes\n"; return;}
    int k = -1;
    for(int i = 1; i < n; i++){
        if (a[i] == a[i-1]) {
            k = i;
            break;
        }
    }
    if (k == -1 && n >= 2) {cout << "No\n"; return;}
    vector<int> prefix(n,0);
    prefix[0] = a[k];
    for(int i = 1, j = k - 1; j >= 0; j--, i++){
        prefix[i] = prefix[i - 1] + a[j];
    }
    for(int i = k + 1; i < n; i++){
        prefix[i] = prefix[i - 1] + a[i];
    }
    for(auto i : prefix){
        if (i % 3 == 0){
            cout << "No\n";
            return;
        }
    }
    cout << "Yes\n";
}

int main() {
    int t; cin >> t;
    while(t--){
        solve();
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) solve(sc);
        sc.close();
    }

    static void solve(Scanner sc) {
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();

        if (n == 1) {
            System.out.println("Yes");
            return;
        }

        int k = -1;
        for (int i = 1; i < n; i++) {
            if (a[i] == a[i - 1]) {
                k = i;
                break;
            }
        }

        if (k == -1 && n >= 2) {
            System.out.println("No");
            return;
        }

        int[] prefix = new int[n];
        prefix[0] = a[k];
        for (int i = 1, j = k - 1; j >= 0; j--, i++) {
            prefix[i] = prefix[i - 1] + a[j];
        }
        for (int i = k + 1; i < n; i++) {
            prefix[i] = prefix[i - 1] + a[i];
        }

        for (int i = 0; i < n; i++) {
            if (prefix[i] % 3 == 0) {
                System.out.println("No");
                return;
            }
        }

        System.out.println("Yes");
    }
}
```

</details>


## Equate XY

<details>
<summary>Python</summary>

```python
import math
import sys

def get_divisors(n):
    divs = []
    i = 1
    while i * i <= n:
        if n % i == 0:
            divs.append(i)
            if i != n // i:
                divs.append(n // i)
        i += 1
    return divs

def main():
    data = sys.stdin.read().split()
    t = int(data[0])
    index = 1
    out_lines = []
    for _ in range(t):
        X = int(data[index]); Y = int(data[index+1]); Z = int(data[index+2]); C = int(data[index+3])
        index += 4
        if X == Y:
            out_lines.append("0")
            continue
        
        ans = 2 * C
        
        if X % Y == 0:
            g = math.gcd(X, Y)
            base = X // g
            divisors = get_divisors(base)
            for d in divisors:
                T_val = g * d
                cost_candidate = abs(Z - T_val) + C
                if cost_candidate < ans:
                    ans = cost_candidate
        
        if Y % X == 0:
            g = math.gcd(X, Y)
            base = Y // g
            divisors = get_divisors(base)
            for d in divisors:
                T_val = g * d
                cost_candidate = abs(Z - T_val) + C
                if cost_candidate < ans:
                    ans = cost_candidate
        
        out_lines.append(str(ans))
    
    print("\n".join(out_lines))

if __name__ == "__main__":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<long long> get_divisors(long long n)
{
    vector<long long> divs;
    if(n==0)
    {
        return divs;
    }
    for(long long i=1; i<=n/i; ++i)
    {
        if(n%i==0)
        {
            divs.push_back(i);
            if(i!=n/i)
            {
                divs.push_back(n/i);
            }
        }
    }
    return divs;
}

long long gcd(long long a, long long b)
{
    while(b)
    {
        a%=b;
        swap(a, b);
    }
    return a;
}

long long lcm(long long a, long long b)
{
    return a*b/gcd(a,b);
}

int main() {
	// your code goes here
    int t;
    cin >> t;
    while(t)
    {
        long long X, Y, Z, C;
        cin >> X >> Y >> Z >> C;
        if(X==Y)
        {
            cout << 0 << endl;
            t--;
            continue;
        }
        if(X>Y)
        {
            swap(X,Y);
        }
        int cost = 2*C;
        vector<long long> divs = get_divisors(Y);
        for(auto i: divs)
        {
            if(lcm(X, i)==gcd(Y, i))
            {
                if(C+abs(Z-i)<cost)
                {
                    cost = abs(Z-i)+C;
                }
            }
        }
        cout << cost << endl;
        t--;
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
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine());
        StringBuilder out = new StringBuilder();
        while (t-- > 0) {
            String[] tokens = br.readLine().split(" ");
            long X = Long.parseLong(tokens[0]);
            long Y = Long.parseLong(tokens[1]);
            long Z = Long.parseLong(tokens[2]);
            long C = Long.parseLong(tokens[3]);

            if (X == Y) {
                out.append("0\n");
                continue;
            }

            long ans = 2 * C;

            if (X % Y == 0) {
                long g = gcd(X, Y);
                long base = X / g;
                List<Long> divisors = getDivisors(base);
                for (long d : divisors) {
                    long T_val = g * d;
                    long candidate = Math.abs(Z - T_val) + C;
                    if (candidate < ans) {
                        ans = candidate;
                    }
                }
            }

            if (Y % X == 0) {
                long g = gcd(X, Y);
                long base = Y / g;
                List<Long> divisors = getDivisors(base);
                for (long d : divisors) {
                    long T_val = g * d;
                    long candidate = Math.abs(Z - T_val) + C;
                    if (candidate < ans) {
                        ans = candidate;
                    }
                }
            }

            out.append(ans).append('\n');
        }
        System.out.print(out);
    }

    static long gcd(long a, long b) {
        while (b != 0) {
            long temp = a % b;
            a = b;
            b = temp;
        }
        return a;
    }

    static List<Long> getDivisors(long n) {
        List<Long> divisors = new ArrayList<>();
        if (n == 0) {
            return divisors;
        }
        long sqrt = (long) Math.sqrt(n);
        for (long i = 1; i <= sqrt; i++) {
            if (n % i == 0) {
                divisors.add(i);
                if (i != n / i) {
                    divisors.add(n / i);
                }
            }
        }
        return divisors;
    }
}
```

</details>


## MinPath Minimize

<details>
<summary>Python</summary>

```python
# cook your dish here
def solve():
    n = int(input())
    A = list(map(int, input().split()))
    E = [[] for _ in range(n)]
    for _ in range(n - 1):
        u, v = map(int, input().split())
        u -= 1
        v -= 1
        E[u].append(v)
        E[v].append(u)

    L = [0] * (n + 2)
    for a in A:
        if a:
            L[a] = 1

    I = [0] * n
    J = [0] * n
    K = [0] * n
    for i in range(n):
        I[i] = len(E[i])
        for j in E[i]:
            if A[j]:
                J[i] = max(J[i], A[j])
            else:
                K[i] += 1

    P = [0] * (n + 1)
    for i in range(1, n + 1):
        P[i] = P[i - 1] + (1 if not L[i] else 0)

    R = [n + 1] * (n + 2)
    for i in range(n, 0, -1):
        R[i] = R[i + 1] if L[i] else i

    def t2(u, v):
        return P[u - 1] >= v

    def f(y):
        l, h = 1, n
        while l < h:
            m = (l + h) // 2
            if P[m] >= y:
                h = m
            else:
                l = m + 1
        return l

    def g2(x):
        if A[x]:
            z = A[x]
            if I[x] < z and J[x] < z and t2(z, K[x]):
                return z
            return n + 1

        y = K[x]
        if P[n] < y:
            return n + 1

        z = max(I[x] + 1, J[x] + 1, 2)
        c0 = max(z, f(y) + 1)
        c1 = R[c0]
        while c1 <= n and not t2(c1, y):
            c1 = R[c1 + 1]

        return c1 if c1 <= n else n + 1

    w = n + 1
    for i in range(n):
        w = min(w, g2(i))

    print(w)


T = int(input())
for _ in range(T):
    solve()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    auto a = []() {
        int x;
        cin >> x;
        return x;
    };

    auto b = [&](int n) {
        vector<int> v(n);
        for (int &i : v)
            i = a();
        return v;
    };

    auto c = [&](int n) {
        vector<vector<int>> g(n);
        for (int i = 1; i < n; i++) {
            int u = a() - 1;
            int v = a() - 1;
            g[u].push_back(v);
            g[v].push_back(u);
        }
        return g;
    };

    for (int t = a(); t--; ) {
        int n = a();
        auto A = b(n);
        auto E = c(n);

        vector<char> L(n + 2);
        for (int i = 0; i < n; i++)
            if (A[i])
                L[A[i]] = 1;

        vector<int> I(n), J(n), K(n);
        for (int i = 0; i < n; i++) {
            I[i] = E[i].size();
            for (int j : E[i])
                if (A[j])
                    J[i] = max(J[i], A[j]);
                else
                    K[i]++;
        }

        vector<int> P(n + 1);
        for (int i = 1; i <= n; i++)
            P[i] = P[i - 1] + !L[i];

        vector<int> R(n + 2, n + 1);
        for (int i = n; i >= 1; i--)
            R[i] = L[i] ? R[i + 1] : i;

        auto t2 = [&](int u, int v) {
            return P[u - 1] >= v;
        };

        auto f = [&](int y) {
            int l = 1, h = n;
            while (l < h) {
                int m = (l + h) >> 1;
                if (P[m] >= y)
                    h = m;
                else
                    l = m + 1;
            }
            return l;
        };

        auto g2 = [&](int x) {
            if (A[x]) {
                int z = A[x];
                if (I[x] < z && J[x] < z && t2(z, K[x]))
                    return z;
                else
                    return n + 1;
            }
            int y = K[x];
            if (P[n] < y)
                return n + 1;
            int z = max({I[x] + 1, J[x] + 1, 2});
            int c0 = max(z, f(y) + 1);
            int c1 = R[c0];
            while (c1 <= n && !t2(c1, y))
                c1 = R[c1 + 1];
            return c1 <= n ? c1 : n + 1;
        };

        int w = n + 1;
        for (int i = 0; i < n; i++)
            w = min(w, g2(i));

        cout << w << "\n";
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

class Codechef {
    static Scanner sc = new Scanner(System.in);

    static int readInt() {
        return sc.nextInt();
    }

    static int[] readArray(int n) {
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = readInt();
        return arr;
    }

    static List<List<Integer>> readTree(int n) {
        List<List<Integer>> g = new ArrayList<>();
        for (int i = 0; i < n; i++) g.add(new ArrayList<>());
        for (int i = 1; i < n; i++) {
            int u = readInt() - 1;
            int v = readInt() - 1;
            g.get(u).add(v);
            g.get(v).add(u);
        }
        return g;
    }

    public static void main(String[] args) throws java.lang.Exception {
        int T = readInt();
        while (T-- > 0) {
            int n = readInt();
            int[] A = readArray(n);
            List<List<Integer>> E = readTree(n);

            boolean[] L = new boolean[n + 2];
            for (int val : A)
                if (val != 0)
                    L[val] = true;

            int[] I = new int[n], J = new int[n], K = new int[n];
            for (int i = 0; i < n; i++) {
                I[i] = E.get(i).size();
                for (int j : E.get(i)) {
                    if (A[j] != 0) J[i] = Math.max(J[i], A[j]);
                    else K[i]++;
                }
            }

            int[] P = new int[n + 1];
            for (int i = 1; i <= n; i++)
                P[i] = P[i - 1] + (!L[i] ? 1 : 0);

            int[] R = new int[n + 2];
            Arrays.fill(R, n + 1);
            for (int i = n; i >= 1; i--)
                R[i] = L[i] ? R[i + 1] : i;

            int w = n + 1;

            for (int i = 0; i < n; i++) {
                int res = g2(i, A, I, J, K, P, R, n);
                w = Math.min(w, res);
            }

            System.out.println(w);
        }
    }

    static boolean t2(int u, int v, int[] P) {
        return P[u - 1] >= v;
    }

    static int f(int y, int[] P, int n) {
        int l = 1, h = n;
        while (l < h) {
            int m = (l + h) / 2;
            if (P[m] >= y)
                h = m;
            else
                l = m + 1;
        }
        return l;
    }

    static int g2(int x, int[] A, int[] I, int[] J, int[] K, int[] P, int[] R, int n) {
        if (A[x] != 0) {
            int z = A[x];
            if (I[x] < z && J[x] < z && t2(z, K[x], P))
                return z;
            return n + 1;
        }

        int y = K[x];
        if (P[n] < y)
            return n + 1;

        int z = Math.max(Math.max(I[x] + 1, J[x] + 1), 2);
        int c0 = Math.max(z, f(y, P, n) + 1);
        int c1 = R[c0];
        while (c1 <= n && !t2(c1, y, P))
            c1 = R[c1 + 1];

        return c1 <= n ? c1 : n + 1;
    }
}
```

</details>







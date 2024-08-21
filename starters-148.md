## Let Me Eat Cake!

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    a, b = map(int, input().split())
    ans = 0
    while a != b:
        if a > b: a, b = b, a
        # now b is larger
        if b%2 == 0:
            ans += b//2
            b -= b//2
        else:
            ans += (b+1)//2
            b -= (b+1)//2
    print(ans)
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
        int a, b;
        cin >> a >> b;
        int ans = 0;
        while (a != b) {
            if (a > b) swap(a, b);  // Ensure b is larger
            if (b % 2 == 0) {
                ans += b / 2;
                b -= b / 2;
            } else {
                ans += (b + 1) / 2;
                b -= (b + 1) / 2;
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

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int a = sc.nextInt();
            int b = sc.nextInt();
            int ans = 0;
            while (a != b) {
                if (a > b) {
                    int temp = a;
                    a = b;
                    b = temp;  // Ensure b is larger
                }
                if (b % 2 == 0) {
                    ans += b / 2;
                    b -= b / 2;
                } else {
                    ans += (b + 1) / 2;
                    b -= (b + 1) / 2;
                }
            }
            System.out.println(ans);
        }
        sc.close();
    }
}

```

</details>

## FightBots

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, x, y = map(int, input().split())
    s = input()
    ax, ay = 0, 0
    ans = 'No'
    for i in range(n):
        if s[i] == 'R': ax += 1
        if s[i] == 'L': ax -= 1
        if s[i] == 'U': ay += 1
        if s[i] == 'D': ay -= 1

        dx, dy = abs(x-ax), abs(y-ay)
        if dx+dy <= i+1 and (dx+dy)%2 == (i+1)%2: ans = 'Yes'
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, x, y;
        cin >> n >> x >> y;
        string s;
        cin >> s;

        int ax = 0, ay = 0;
        string ans = "No";

        for (int i = 0; i < n; i++) {
            if (s[i] == 'R') ax++;
            if (s[i] == 'L') ax--;
            if (s[i] == 'U') ay++;
            if (s[i] == 'D') ay--;

            int dx = abs(x - ax);
            int dy = abs(y - ay);
            if (dx + dy <= i + 1 && (dx + dy) % 2 == (i + 1) % 2) {
                ans = "Yes";
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

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int n = sc.nextInt();
            int x = sc.nextInt();
            int y = sc.nextInt();
            String s = sc.next();

            int ax = 0, ay = 0;
            String ans = "No";

            for (int i = 0; i < n; i++) {
                if (s.charAt(i) == 'R') ax++;
                if (s.charAt(i) == 'L') ax--;
                if (s.charAt(i) == 'U') ay++;
                if (s.charAt(i) == 'D') ay--;

                int dx = Math.abs(x - ax);
                int dy = Math.abs(y - ay);
                if (dx + dy <= i + 1 && (dx + dy) % 2 == (i + 1) % 2) {
                    ans = "Yes";
                }
            }
            System.out.println(ans);
        }
        sc.close();
    }
}


```

</details>

## The Undisappearance

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
        a = list(map(int, data[index:index + n]))
        index += n
        
        ans = 0
        for x in [1, 2, 3]:
            bad = x - 1
            if bad == 0:
                bad = 3

            L, R = n, 0
            for i in range(n):
                if a[i] == x:
                    L = min(i, L)
                    R = i

            L2, R2, good = L, R, 1
            for i in range(L, R + 1):
                if a[i] == bad:
                    good = 0
                    break

            while L2 >= 0 and a[L2] != bad:
                L2 -= 1
            while R2 < n and a[R2] != bad:
                R2 += 1

            ans += good * (R2 - R) * (L - L2)

        total_subarrays = n * (n + 1) // 2
        results.append(str(total_subarrays - ans))

    print("\n".join(results))

if __name__ == "__main__":
    main()


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include "bits/stdc++.h"
using namespace std;
using ll = long long int;
mt19937_64 RNG(chrono::high_resolution_clock::now().time_since_epoch().count());

int main()
{
    ios::sync_with_stdio(false); cin.tie(0);

    int t; cin >> t;
    while (t--) {
        int n; cin >> n;
        vector<int> a(n);
        for (int &x : a) cin >> x;
        ll ans = 0;
        for (int x : {1, 2, 3}) {
            int bad = x-1;
            if (bad == 0) bad = 3;

            int L = n, R = 0;
            for (int i = 0; i < n; ++i) {
                if (a[i] == x) {
                    L = min(i, L);
                    R = i;
                }
            }

            int L2 = L, R2 = R, good = 1;
            for (int i = L; i <= R; ++i) {
                good &= a[i] != bad;
            }
            
            while (L2 >= 0) {
                if (a[L2] == bad) break;
                --L2;
            }
            while (R2 < n) {
                if (a[R2] == bad) break;
                ++R2;
            }

            ans += 1ll * good * (R2 - R) * (L - L2);
        }
        cout << 1ll*n*(n+1)/2 - ans << '\n';
    }
}

```

</details>

<details>
<summary>Java</summary>

```java
//package practice;

import java.util.*;
import java.lang.*;
import java.io.*;

/* Name of the class has to be "Main" only if the class is public. */
class Codechef
{
	static long[] factorial;
	static int SPF[];
		
	static void factorial(int n) {
		factorial = new long[n];
		factorial[0] = 1;
	    for (int i = 1; i < factorial.length; i++) {
	        factorial[i] = (factorial[i - 1] * i) % mod;
	    }
	}
	static long ncr(int n, int r) {
	    if (n < r) {
	       return 0;
	    }
	    long numerator = factorial[n];
	    long denominator = factorial[r] * factorial[n - r] % mod;
	    return (numerator * modInverse(denominator)) % mod;
	}
	
	static void seive(int n) {
		SPF = new int[n+1];
		for (int i = 2; i <= n; i++) {
            SPF[i] = i;
        }

        for (int i = 2; i * i <= n; i++) {
            if (SPF[i] == i) {
                for (int j = i * i; j <= n; j += i) {
                    if (SPF[j] == j) {
                        SPF[j] = i;
                    }
                }
            }
        }
	}
	static List<Integer> getFactors(int n) {
        List<Integer> factors = new ArrayList<>();

        while (n > 1) {
            factors.add(SPF[n]);
            n /= SPF[n];
        }

        return factors;
    }
	static long gcd(long a, long b) {
		return b==0?a:gcd(b,a%b);
	}
	
	
	
	static long power(long x, long y, long p) {
        long res = 1;
        x = x % p;
        while (y > 0) {
            if ((y & 1) > 0)
                res = (res * x) % p;
            y = y >> 1; // y = y/2
            x = (x * x) % p;
        }
        return res;
    }
	
	static int gcd(int a, int b) {
		return b==0?a:gcd(b,a%b);
	}
	static long mod=1000000007;


    private static long modInverse(long n) { 
        return power(n, mod - 2, mod);
    }
	
	
	static long a(long ... a) {
		long res = 0L;
		for(long i:a) {
			res = (res%mod + i%mod)%mod;
		}
		return res;
	}
	static long m(long ... a) {
		long res = 1L;
		for(long i:a) {
			res = (res%mod * i%mod)%mod;
		}
		return res;
	}
	
	static boolean ok(int[]a, long g, long k) {
		long temp = g*k;
		for(int i:a) {
			long x = Math.min(temp, Math.min(temp,Math.min(i,g) ));
			temp -= x;
			if(temp==0) return true;
		}
		return false;
	}
	
	static long get(int a[], int num) {
	    int n = a.length;
	    
	    int left = n, right = 0;
	    
	    for(int i=0; i<n; i++) {
	        if(a[i] == num) right = i;
	       if(a[n-i-1] == num) left = n - i - 1;
	    }
	    
	    
	    int bad = num - 1;
	    if(num == 1) bad = 3;
	    for(int i=left; i<=right; i++) {
	       if(a[i] == bad) return 0;
	    }
	    
	    int c1 = 0, c2 = 0;
	    while(left >=0 && a[left] != bad) {
	        c1++;
	        left--;
	    }
	    
	    while(right < n && a[right] != bad) {
	        c2++;
	        right++;
	    }
	    
	   // System.out.println(num+":"+c1+" "+c2);
	    
	    return (long)c1 * c2;
	}
	
	static Scanner s = new Scanner(System.in);
	static void solve() throws IOException {
		int n = s.nextInt();
		int a[] = new int[n];
		for(int i=0; i<n; i++) a[i] = s.nextInt();
		
		long ans = 0;
		ans += get(a, 1);
		ans += get(a, 2);
		ans += get(a, 3);
		
		long total = n;
		total = total * (total + 1) / 2;
		
		ans = total - ans;
		System.out.println(ans);
	}
	public static void main(String[] args) 
		throws IOException 
	{ 
		int t = s.nextInt();
		//System.out.println(t);
	    while(t-->0) solve();
	}
}

```

</details>

## Double Trouble

<details>
<summary>Python</summary>

```python
import sys
import time
import heapq
from functools import lru_cache

MOD = int(1e9 + 7)

def binmod(a, b, mod=MOD):
    x = 1
    while b > 0:
        if b & 1:
            x = (x * a) % mod
        a = (a * a) % mod
        b >>= 1
    return x

def powermod(a, b, mod):
    if b == 0:
        return 1
    k = powermod(a, b // 2, mod)
    k = (k * k) % mod
    if b & 1:
        k = (k * a) % mod
    return k

def inverse(b, mod):
    return powermod(b, mod - 2, mod)

def ncr(n, r, fac, inv, mod=MOD):
    if r > n:
        return 0
    if r == n:
        return 1
    if r < 0:
        return 0
    ans = (fac[n] * inv[n - r] % mod) * inv[r] % mod
    return ans

def solve():
    n, k = map(int, input().split())
    vec = list(map(int, input().split()))
    vec.sort()

    val = vec[-1]
    pq = vec[:]
    heapq.heapify(pq)

    kk = min(k, 30 * n)
    k -= kk

    for _ in range(kk):
        t = heapq.heappop(pq)
        heapq.heappush(pq, t * 2)

    vec = sorted([heapq.heappop(pq) for _ in range(n)])

    if k > 0:
        y = k // n
        z = k % n
        for i in range(z):
            vec[i] = (vec[i] * 2) % MOD

        ans = sum((vec[i] * binmod(2, y)) % MOD for i in range(n)) % MOD
        print(ans)
    else:
        ans = sum(vec) % MOD
        print(ans)

def main():
    start_time = time.time()
    
    # Uncomment and initialize fac and inv if nCr calculations are needed
    # fac = [1] * (N)
    # inv = [1] * (N)
    # for i in range(2, N):
    #     fac[i] = fac[i - 1] * i % MOD
    # inv[N - 1] = inverse(fac[N - 1], MOD)
    # for i in range(N - 2, -1, -1):
    #     inv[i] = inv[i + 1] * (i + 1) % MOD

    tt = int(input())
    for _ in range(tt):
        solve()
    
    elapsed_time = time.time() - start_time
    sys.stderr.write(f"Time measured: {elapsed_time} seconds.\n")

if __name__ == "__main__":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include "bits/stdc++.h"
using namespace std;
using ll = long long int;
mt19937_64 RNG(chrono::high_resolution_clock::now().time_since_epoch().count());

int main()
{
    ios::sync_with_stdio(false); cin.tie(0);

    int t; cin >> t;
    while (t--) {
        int n, k; cin >> n >> k;
        vector<int> a(n);
        for (int &x : a) cin >> x;

        priority_queue<int, vector<int>, greater<int>> pq;
        for (int i = 0; i < n; ++i) pq.push(a[i]);

        const int lim = (1 << 30);
        while (k > 0) {
            if (pq.top() >= lim) break;
            int x = pq.top(); pq.pop();
            pq.push(2*x);
            --k;
        }

        while (pq.size() > 0) {
            a[pq.size()-1] = pq.top();
            pq.pop();
        }
        reverse(begin(a), end(a));

        ll ans = 0;
        const int mod = 1e9 + 7;
        auto pow2m = [&] (int x) {
            ll res = 1, a = 2;
            while (x) {
                if (x & 1) res = (res * a) % mod;
                a = (a * a) % mod;
                x /= 2;
            }
            return res;
        };
        for (int i = 0; i < n; ++i) {
            if (i < k%n) ans += a[i] * pow2m(k/n + 1);
            else ans += a[i] * pow2m(k/n);
            ans %= mod;
        }
        cout << ans << '\n';
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.io.*;
import java.util.*;

class Main{
    static final long mod = 1000000007;
    static long power(long x, long y, long p) {
        long res = 1;
        x = x % p;
        if (x == 0) return 0;
        while (y > 0) {
            if ((y & 1) != 0)
                res = (res % p * x % p) % p;
            y = y >> 1;
            x = (x % p * x % p) % p;
        }
        return res;
    }

    public static void main(String... args) throws Exception {
        OutputStream outputStream = System.out;
        PrintWriter out = new PrintWriter(outputStream);
        FastReader in = new FastReader();
        int testcase = in.nextInt();
        while (testcase-- > 0) {
            // Start 
            int n = in.nextInt();
            long k = in.nextLong();
            long[] arr = new long[n];
            for (int i = 0; i < n; i++) arr[i] = in.nextLong();
            PriorityQueue<Long> pq = new PriorityQueue<>();
            for(long l : arr) pq.add(l);
            while(k > 0 && pq.peek() < (1l << 30)) {--k; pq.add(pq.poll() * 2);}
            for(int i = 0 ; !pq.isEmpty() ; i++) arr[i] = pq.poll();
            long val = power(2, k / n, mod), val2 = power(2, (k / n) + 1, mod), ans = 0;
            for(int i = 0 ; i < n ; i++) {
                if(i < k % n) arr[i] = (arr[i] % mod * val2 % mod) % mod;
                else arr[i] = (arr[i] % mod * val % mod) % mod;
                ans = (ans % mod + arr[i] % mod) % mod;
            }
            out.println(ans % mod);
        }
        out.close();
    }
    static class FastReader
    {
        BufferedReader br;
        StringTokenizer st;
        public FastReader() {br = new BufferedReader(new InputStreamReader(System.in));} 
        String next() 
        { 
            while (st == null || !st.hasMoreElements()) 
            { 
                try{st = new StringTokenizer(br.readLine());} 
                catch (IOException  e){e.printStackTrace();} 
            } 
            return st.nextToken(); 
        } 
        int nextInt() {return Integer.parseInt(next());} 
        long nextLong(){return Long.parseLong(next());} 
        double nextDouble(){return Double.parseDouble(next());} 
        String nextLine() 
        { 
            String str = ""; 
            try{str = br.readLine();} 
            catch (IOException e){e.printStackTrace();} 
            return str; 
        } 
    }
    static class Pair implements Comparable<Pair>{
	    Pair(){
	    }
	    public int compareTo(Pair that){
	        return 0;
	    }
	}
	static int[] par;
	static int[] rank;
	static int find(int a){
	    if(par[a] == a) return a;
	    else return par[a] = find(par[a]);
	}
	static void merge(int a, int b){
	    int para = find(a);
	    int parb = find(b);
	    if(para == parb) return;
	    if(rank[para] < rank[parb]) par[para] = parb;
	    else if(rank[parb] < par[a]) par[parb] = para;
	    else{
            par[parb] = para;
            ++rank[para];
	    }
	}
	static long gcd(long a, long b){return (b==0)?a:gcd(b,a%b);}
    static int gcd(int a, int b){return (b==0)?a:gcd(b,a%b);}
    static boolean biPartite(ArrayList<ArrayList<Integer>> adj,int V){
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=1;i<=V;i++) if(hm.get(i)==null) if(!(modDFS(i,adj,hm,0))) return false;
        return true;
    }
    static boolean modDFS(int V,ArrayList<ArrayList<Integer>> adj,HashMap<Integer,Integer> hm,int c){
        if(hm.get(V)!=null) if(hm.get(V)!=c) return false; else return true;
        hm.put(V,c);
            for(Integer k:adj.get(V)){
                if(c==1)if(!modDFS(k,adj,hm,0)) return false;
                else if(!modDFS(k,adj,hm,1)) return false;
            }
        return true;
    }
    static ArrayList<ArrayList<Integer>> getGraph(int n, int m, FastReader in){
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for(int i = 0 ; i < n ; i++) adj.add(new ArrayList<>());
        for(int i = 0 ; i < m ; i++){
            int u = in.nextInt() - 1; int v = in.nextInt() - 1;
            adj.get(u).add(v); adj.get(v).add(u);
        }
        return adj;
    }
}
```

</details>



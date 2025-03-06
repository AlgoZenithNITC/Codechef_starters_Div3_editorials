## 1. Run for Fun

<details>
<summary>Python</summary>

```python
x,y=list(map(int,input().split()))

if y%x==0:
   print(y//x-1)
else:
    print(y//x)


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int X, Y;
    cin >> X >> Y; 
    
    int rests = (Y - 1) / X;
    
    cout << rests << endl;  
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
		Scanner sc=new Scanner(System.in);
		int x=sc.nextInt();
		int y=sc.nextInt();
		
		if(x>=y)
		{
		    System.out.println("0");
		}
		else if (x==1)
		{
		    System.out.println(y-1);
		}
		else
		{
		    System.out.println(y/x);
		}

	}
}

```

</details>

## 2. Clothing Store

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    x,y,z,a,b,c=map(int,input().split())
    h=0
    for i in range(z):
        if c>0:
            c-=1
            h+=1
        elif b>0:
            b-=1
            h+=1
        elif a>0:
            a-=1
            h+=1
    for i in range(y):
        if b>0:
            b-=1
            h+=1
        elif a>0:
            a-=1
            h+=1
    for i in range(x):
        if a>0:
            a-=1
            h+=1
    print(h)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
	int tt;
	cin>>tt;
	while(tt--){
	    int x,y,z,a,b,c;
	    cin>>x>>y>>z>>a>>b>>c;
	    int need = 0;
	    if(a>x){
	        need+=(a-x);
	    }
	    if(b>y){
	        need+=(b-y);
	        
	    }
	    if(z>c && need>0){
	        
	        need-=(z-c);
	        
	    }
	    if(y>b && need>0){
	        need-=(y-b);
	    }
	    if(need<0){
	        need = 0;
	    }
	    if(c-z>0){
	        need+=(c-z);
	    }
	    cout<<(a+b+c)-need<<endl;
	}

}

```

</details>

<details>
<summary>Java</summary>

```java
import java.io.*;
import java.util.*;

class Clothing_Store {
    public static int fun(int x, int y, int z, int a, int b, int c) {
        int ans = 0;
        ans = ans + Math.min(z, c);
        if(z > c) y += (z - c);
        ans = ans + Math.min(y, b);
        if(y > b) x += (y - b);
        ans = ans + Math.min(x, a);
        return ans;
    }

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int t = Integer.parseInt(st.nextToken());
        while (t-- > 0) {
            st = new StringTokenizer(br.readLine());
            int x = Integer.parseInt(st.nextToken());
            int y = Integer.parseInt(st.nextToken());
            int z = Integer.parseInt(st.nextToken());
            int a = Integer.parseInt(st.nextToken());
            int b = Integer.parseInt(st.nextToken());
            int c = Integer.parseInt(st.nextToken());
            bw.write(fun(x, y, z, a, b, c) + "\n");
        }
        br.close();
        bw.flush();
        bw.close();
    }
}
```

</details>

## 3. Costly Summit

<details>
<summary>Python</summary>

```python

from collections import Counter
t=int(input())
for _ in range(t):
    n,c=map(int,input().split())
    s=input()
    mydict=Counter(s)
    uniq=sorted(mydict.keys(),key=lambda x:mydict[x])
    temp=1
    totalcost=0
    for i in uniq:
        translatorcharge=0
        prev=temp
        for j in range(mydict[i]):
            translatorcharge+=temp
            temp+=1
        if translatorcharge>=c:
            totalcost+=c
            temp=prev
        else:
            totalcost+=translatorcharge
            
    print(totalcost)
    

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
    int testCases;
    cin >> testCases;

    while (testCases--) {
        int length, costPerCharacter;
        cin >> length >> costPerCharacter;
        string inputString;
        cin >> inputString;

        vector<int> characterCount(5, 0);
        for (char character : inputString) {
            characterCount[character - 'A']++;
        }

        int minimumCost = 1e9;

        for (int bitmask = 0; bitmask < (1 << 5); bitmask++) {
            int totalCost = 0;
            int learnedCharacters = 0;

            for (int i = 0; i < 5; i++) {
                if (bitmask & (1 << i)) {
                    totalCost += costPerCharacter;
                    learnedCharacters += characterCount[i];
                }
            }

            int remainingCharacters = length - learnedCharacters;
            int translationCost = remainingCharacters * (remainingCharacters + 1) / 2;
            totalCost += translationCost;

            minimumCost = min(minimumCost, totalCost);
        }

        cout << minimumCost << endl;
    }

    return 0;
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.io.*;
import java.util.*;

class CodeChef {

    static class FastIO {
        BufferedReader br;
        StringTokenizer st;

        public FastIO() {
            br = new BufferedReader(new InputStreamReader(System.in));
        }

        String next() {
            while (st == null || !st.hasMoreElements()) {
                try {
                    st = new StringTokenizer(br.readLine());
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            return st.nextToken();
        }

        int nextInt() {
            return Integer.parseInt(next());
        }

        long nextLong() {
            return Long.parseLong(next());
        }

        double nextDouble() {
            return Double.parseDouble(next());
        }

        String nextLine() {
            String str = "";
            try {
                str = br.readLine();
            } catch (IOException e) {
                e.printStackTrace();
            }
            return str;
        }

        void print(String s) {
            System.out.print(s);
        }

        void println(String s) {
            System.out.println(s);
        }
    }

    static void debug(Object... o) {
        System.err.println(Arrays.deepToString(o));
    }

    static long gcd(long a, long b) {
        if (b == 0) return a;
        return gcd(b, a % b);
    }

    static long lcm(long a, long b) {
        return (a / gcd(a, b)) * b;
    }

    static boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }

    static boolean[] sieve(int n) {
        boolean[] isPrime = new boolean[n + 1];
        Arrays.fill(isPrime, true);
        isPrime[0] = isPrime[1] = false;
        for (int i = 2; i * i <= n; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= n; j += i) {
                    isPrime[j] = false;
                }
            }
        }
        return isPrime;
    }

    static long modExp(long base, long exp, long mod) {
        long result = 1;
        base = base % mod;
        while (exp > 0) {
            if ((exp & 1) == 1) {
                result = (result * base) % mod;
            }
            base = (base * base) % mod;
            exp >>= 1;
        }
        return result;
    }

    static long factorialMod(int n, int mod) {
        long result = 1;
        for (int i = 2; i <= n; i++) {
            result = (result * i) % mod;
        }
        return result;
    }

    static class Pair implements Comparable<Pair> {
        int first, second;

        public Pair(int first, int second) {
            this.first = first;
            this.second = second;
        }

        @Override
        public int compareTo(Pair o) {
            return Integer.compare(this.first, o.first); 
        }
    }

    static int[] prefixSum(int[] arr) {
        int n = arr.length;
        int[] prefix = new int[n];
        prefix[0] = arr[0];
        for (int i = 1; i < n; i++) {
            prefix[i] = prefix[i - 1] + arr[i];
        }
        return prefix;
    }

    static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] == target) return mid;
            if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return -1; 
    }

    public static void main(String[] args) {
       Scanner sc=new Scanner(System.in);
       int t=sc.nextInt();
       while(t-->0){
           int n=sc.nextInt();
           int cost=sc.nextInt();
           sc.nextLine();
           String s=sc.nextLine();
           int[] freq=new int[5];
           for(int i=0;i<n;i++){
               freq[s.charAt(i)-'A']++;
           }
           Arrays.sort(freq);
           reverse(freq);
           
           int[] prefixCost=new int[6];
           for(int i=1;i<6;i++){
                prefixCost[i]=prefixCost[i-1]+freq[i-1];
		    }
		  int totalCost=Integer.MAX_VALUE;
		  for(int i=0;i<6;i++){
                int learningCost=prefixCost[i];
                int remainingCost=n-learningCost;
                int translatorCost=remainingCost*(remainingCost+1)/2;
                int currentCost=i*cost+translatorCost;
                totalCost=Math.min(totalCost,currentCost);
               
		    }
		    System.out.println(totalCost);
		    
           
       }
    }
    private static void reverse(int freq[]){
        int i=0;
        int j=freq.length-1;
        while(i<j){
            int temp=freq[i];
            freq[i]=freq[j];
            freq[j]=temp;
            i++;
            j--;
        }
    }

    
}
```

</details>

## 4. Same And

<details>
<summary>Python</summary>

```python
def find_seq(N, M):
    if N > M: return -1
    seq = [N] + [N | (1 << k) for k in range(64) if (N & (1 << k)) == 0 and (N | (1 << k)) <= M]
    return seq if len(seq) > 1 else -1

def main():
    import sys
    data = sys.stdin.read().split()
    T = int(data[0])
    idx = 1
    res = []
    for _ in range(T):
        N, M = int(data[idx]), int(data[idx + 1])
        idx += 2
        seq = find_seq(N, M)
        if seq == -1: res.append("-1")
        else: res.append(f"{len(seq)}\n{' '.join(map(str, seq))}")
    print("\n".join(res))

if __name__ == "__main__":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
#define int long long
using namespace std;

signed main() {
	int t;
	cin >> t;
	while(t--)
	{
	    int n, m;
	    cin >> n >> m;
	    set<int>ans;
	    if(n > m){
	        cout << -1 << "\n";
	        continue;
	    }
	    ans.insert(n);
	    for(int i = 0; i < 63; ++i)
	    {
	        int mask = (1ll << i);
	        if(((mask|n) <= m))
	        ans.insert(mask|n);
	    }
	    if(ans.size() == 1)
	    {
	        cout << -1 << "\n";
	        continue;
	    }
	    cout << ans.size() << "\n";
	    for(auto &i : ans)
	        cout << i << " ";
	    cout << "\n";
	    
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

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		Scanner scn=new Scanner(System.in);
		int t=scn.nextInt();
		while(t-->0){
		    long n=scn.nextLong();
		    long m=scn.nextLong();
		    if(n>m){
		        System.out.println(-1);
		        continue;
		    }
		    ArrayList<Long> arr=new ArrayList<>();
		    arr.add(n);
		    for(int i=0;i<64;i++){
		        if(((1L<<i)&n)==0){
		            long ele=n|(1L<<i);
		            if(ele<=m){
		                arr.add(ele);
		            }
		            else{
		                break;
		            }
		        }
		        
		    }
		    if(arr.size()>1){
		    System.out.println(arr.size());
		    for(int i=0;i<arr.size();i++){
		        System.out.print(arr.get(i)+" ");
		    }
		    System.out.println();
		    }
		    else{
		        System.out.println(-1);
		    }
		    
		
		}
	}
}
```

</details>

## 5. Friendly Binary Strings

<details>
<summary>Python</summary>

```python
def main():
    import sys
    data = sys.stdin.read().strip().split()
    t = int(data[0])
    i = 1
    for _ in range(t):
        N = int(data[i]); i += 1
        A = data[i]; i += 1
        B = data[i]; i += 1
        qq1 = qq2 = qq3 = 0
        for k in range(N):
            x = A[k]
            y = B[k]
            if x == '0' and y == '0':
                qq1 += 1
            elif x == '1' and y == '1':
                qq2 += 1
            else:
                qq3 += 1
        if N % 2 == 0:
            if qq1 % 2 == 0 and qq2 % 2 == 0 and qq3 % 2 == 0:
                print("YES")
            else:
                print("NO")
        else:
            odd_hai = (qq1 % 2) + (qq2 % 2) + (qq3 % 2)
            if odd_hai <= 1:
                print("YES")
            else:
                print("NO")

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
	    while(t--)
	    {
	        int n;
	        cin >> n;
	        string a, b;
	        cin >> a >> b;
	        map<pair<int,int>,int>occ;
	        for(int i = 0; i < n; ++i)
	        occ[make_pair(min(a[i], b[i]), max(a[i], b[i]))]++;
	        int odd = 0;
	        for(auto &[x, y] : occ)
	            odd += (y%2 == 1);
	        if(odd < 2)
	            cout << "YES\n";
	        else
	            cout << "NO\n";
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

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
Scanner sc =new Scanner(System.in);
int t=sc.nextInt();
while(t-->0){
    int n=sc.nextInt();
    String a=sc.next();
    String b=sc.next();
    int c=0,d=0,e=0;
    for(int i=0;i<n;i++){
        
          if(a.charAt(i)==b.charAt(i)){
              if(a.charAt(i)=='0'){
              c++;
              }
              else{
                 d++;
              }
          }
          else{
              e++;
          }
    }
    if(n%2==0){
        if(c%2==0 && d%2==0&&e%2==0){
            System.out.println("YES");
        }
        else{
             System.out.println("NO");
        }
    }
    else{
        if((c%2+d%2+e%2)==1){
             System.out.println("YES");
        }
        else{
             System.out.println("NO");
        }
    }
}
	}
}
```

</details>

## 6. Mex-P Tree (Easy)

<details>
<summary>Python</summary>

```python
import sys
sys.setrecursionlimit(10 ** 6)
from collections import defaultdict
import math
for i in range(int(input())):
    n = int(input())
    l = list(map(int,input().split()))
    l = [0] + l
    d = defaultdict(list)
    for i in range(n - 1):
        u,v = map(int,input().split())
        d[u] += [v]
        d[v] += [u]
    # print(d)
    m = [0] * (n + 1)
    primes = [2,3,5,7,11,13,17,19,23,29,31]
    for i in range(1,n + 1):
        for prime in primes:
            if l[i] % prime:
                m[i] = prime
                break   
    def f(cur,par,val):
        global res
        res += min(val,m[cur])
        for neighbor in d[cur]:
            if neighbor != par:
                f(neighbor,cur,min(val,m[cur]))
    for i in range(1,n + 1):
        res = 0 
        f(i,i,10 ** 10)
        print(res,end = " ")
    print()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long int
int mod = 1e9 + 7;
bool comp(pair<int,int> a,pair<int,int> b){
    return a.first>b.first;
}
vector<int> prime;

int dfs(int ind,vector<int>& a, vector<int> adj[],int n,int prev,vector<int>& vis){
    //cout<<ind<<endl;
    vis[ind]=1;
    int pr;
    for(int i=0;i<prime.size();i++){
        if(a[ind]%prime[i]){
            pr = prime[i];
            break;
        }
    }
    pr = min(pr,prev);
    int ret = pr;
    for(auto ch : adj[ind]){
        if(!vis[ch]){
          ret += dfs(ch,a,adj,n,pr,vis);
        }
    }
    return ret;
}
bool isprime(int num){
    for(int i=2;i<=sqrt(num);i++){
        if(num%i == 0){
            return false;
        }
    }
    return true;
}
signed main() {
    std::ios::sync_with_stdio(false);
    std::cin.tie(nullptr); std::cout.tie(nullptr);
     int t;
     cin>>t;
     for(int i=2;i<1e4;i++){
        if(isprime(i)){
            prime.push_back(i);
        }
        if(prime.size()>28){
            break;
        }
     }
      while(t--){
        int n;
        cin>>n;
        vector<int> a(n+1);
        for(int i=1;i<=n;i++){
            cin>>a[i];
        }
        vector<int> adj[n+1];
        for(int i=1;i<n;i++){
            int u,v;
            cin>>u>>v;
            adj[u].push_back(v);
            adj[v].push_back(u);
        }

        for(int i=1;i<=n;i++){
            vector<int> vis(n+1,0);
            cout<<dfs(i,a,adj,n,1e9,vis)<<" ";
        }
        cout<<endl;
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
    static int MOD = 998244353;
    static ArrayList<Integer> primes;

    public static void main(String[] args) throws Exception {
        FastReader ab = new FastReader();
        PrintWriter out = new PrintWriter(System.out);

        primes = getFirstTenPrimes();
        int T = ab.nextInt();
        for (int test = 1; test <= T; test++) {
            int N = ab.nextInt();
            int[] a = new int[N];
            for(int i=0; i<N; i++) a[i] = ab.nextInt();
            ArrayList<Integer>[] g = new ArrayList[N];
            for(int i=0; i<N; i++) g[i] = new ArrayList<>();
            for(int i=0; i<N-1; i++) {
                int u = ab.nextInt()-1;
                int v = ab.nextInt()-1;
                g[u].add(v);
                g[v].add(u);
            }

            long cnt = 0;
            StringBuilder ans = new StringBuilder();
            for(int i=0; i<N; i++) {
                ans.append(f(i, -1, Integer.MAX_VALUE, g, a)).append(' ');
            }

            out.println(ans);
        }

        out.flush();
        out.close();
    }

    static long f(int i, int par, int p, ArrayList<Integer>[] g, int[] a) {
        int nextPrime = Math.min(getPrime(a[i]),p);
        long ans = nextPrime;
        for(int next: g[i]) {
            if(next != par) ans += f(next, i, nextPrime, g, a);
        }
        return ans;

    }

    static int getPrime(int num) {
        for(int p: primes) {
            if(num % p != 0) return p;
        }
        return Integer.MIN_VALUE;
    }

    public static ArrayList<Integer> getFirstTenPrimes() {
        ArrayList<Integer> primes = new ArrayList<>();
        int count = 0, num = 2;

        while (count < 10) {
            if (isPrime(num)) {
                primes.add(num);
                count++;
            }
            num++;
        }
        return primes;
    }

    public static boolean isPrime(int n) {
        if (n < 2) return false;
        for (int i = 2; i * i <= n; i++) {
            if (n % i == 0) return false;
        }
        return true;
    }

    static class FastReader {
        BufferedReader br;
        StringTokenizer st;

        public FastReader() {
            br = new BufferedReader(new InputStreamReader(System.in));
        }

        String next() {
            while (st == null || !st.hasMoreTokens()) {
                try {
                    st = new StringTokenizer(br.readLine());
                } catch (IOException e) {
                }
            }
            return st.nextToken();
        }

        int nextInt() {
            return Integer.parseInt(next());
        }

        long nextLong() {
            return Long.parseLong(next());
        }
    }
}
```

</details>

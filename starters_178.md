## 1. Placing 01 and 10

<details>
<summary>Python</summary>

```python
def min_transitions(t, test_cases):
    results = []
    for x, y in test_cases:
        diff = abs(x - y)
        ans = min(x, y) * 2 + (diff * 2)
        
        if diff > 0:
            ans -= 1
        results.append(ans)
    
    return results

# Input Handling
t = int(input())
test_cases = [tuple(map(int, input().split())) for _ in range(t)]

# Output Results
for res in min_transitions(t, test_cases):
    print(res)

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
    while (t--) {
        int x, y;
        cin >> x >> y;
        int diff = abs(x - y);
        int ans = min(x, y) * 2 + (diff * 2);
        
        if (diff > 0)
            ans -= 1;
        cout << ans << endl;
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class MinTransitions {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int x = sc.nextInt();
            int y = sc.nextInt();
            int diff = Math.abs(x - y);
            int ans = Math.min(x, y) * 2 + (diff * 2);

            if (diff > 0)
                ans -= 1;

            System.out.println(ans);
        }
        sc.close();
    }
}

```

</details>

## 2. Permutation Construct
<details>
<summary>Python</summary>

```python
t=int(input())
while t>0:
    l=list(map(int,input().split()))
    n=l[0]
    k=l[1]
    ls=[]
    if n-k<k:
        print(-1)
    
    else:
        for i in range(1,n+1):
            if i+k<=n:
                ls.append(i+k)
            else:
                if i%k==0:
                    ls.append(k)
                else:
                    ls.append(i%k)
        for i in ls:
            print(i,end=" ")
        print()
    t-=1
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h> 
using namespace std;

typedef long long ll;
typedef long double dl;


void solve() {
    ll n, k; cin >> n >> k;

    if (n < 2 * k) {
        cout << -1 << endl;
        return;
    }

    vector<ll> ans(n);
    map<int, int> mp;
    for (int i = 1; i <= k; i++) {
        mp[i % k] = i;
    }
    ll val = k + 1;
    for (ll i = 0; i < n; i++) {
        if (val <= n) ans[i] = val++;
        else {
            ans[i] = mp[(i + 1) % k];
        } 
    }

    for (ll &i : ans) cout << i << ' ';
    cout << endl;
}

int main() {
    ll t = 1;
    cin >> t;
    while (t--) solve();

    

    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    
    public static void solve(Scanner sc) {
        long n = sc.nextLong();
        long k = sc.nextLong();
        
        if (n < 2 * k) {
            System.out.println(-1);
            return;
        }
        
        long[] ans = new long[(int) n];
        Map<Integer, Integer> mp = new HashMap<>();
        
        for (int i = 1; i <= k; i++) {
            mp.put(i % (int) k, i);
        }
        
        long val = k + 1;
        for (int i = 0; i < n; i++) {
            if (val <= n) ans[i] = val++;
            else {
                ans[i] = mp.get((i + 1) % (int) k);
            }
        }
        
        for (long num : ans) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            solve(sc);
        }
        sc.close();
    }
}

```

</details>

## 3. Big Difference

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    
    for _ in range(t):
        n, k = map(int, input().split())
        
        if n <= k:
            print(-1, -1)
        elif n % 2 == 0:
            if n - 1 - k >= 2:
                print(n - 1, 2)
            else:
                print(-1, -1)
        else:
            if n - k >= 2:
                print(n, 2)
            else:
                print(-1, -1)

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
	cin>>t;
	while(t--)
	{
	  long long   int n,k;
	    cin>>n>>k;
	    if(n<=k)
	    cout<<-1<<" "<<-1<<endl;
	    else if(n%2==0)
	    {
	        if(n-1-k>=2)
	        cout<<n-1<<" "<<2<<endl;
	        else
	        cout<<-1<<" "<<-1<<endl;
	    }
	    else
	    {
	        if(n-k>=2)
	        cout<<n<<" "<<2<<endl;
	        else
	        cout<<-1<<" "<<-1<<endl;
	    }
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
            long n = sc.nextLong();
            long k = sc.nextLong();
            
            if (n <= k) {
                System.out.println("-1 -1");
            } else if (n % 2 == 0) {
                if (n - 1 - k >= 2) {
                    System.out.println((n - 1) + " 2");
                } else {
                    System.out.println("-1 -1");
                }
            } else {
                if (n - k >= 2) {
                    System.out.println(n + " 2");
                } else {
                    System.out.println("-1 -1");
                }
            }
        }
        
        sc.close();
    }
}
```

</details>

## 4. Smoothly Increasing

<details>
<summary>Python</summary>

```python
def is_smooth(B):
    cur = B[:]
    while len(cur) >= 2:
        if any(cur[j] >= cur[j + 1] for j in range(len(cur) - 1)):
            return False
        cur = [cur[j + 1] - cur[j] for j in range(len(cur) - 1)]
    return True

def solve(N, A):
    prefix, suffix = [False] * N, [False] * N
    prefix[0] = True
    for i in range(1, N):
        prefix[i] = prefix[i - 1] and (A[i - 1] < A[i])

    suffix[N - 1] = True
    for i in range(N - 2, -1, -1):
        suffix[i] = suffix[i + 1] and (A[i] < A[i + 1])

    ans = ['0'] * N

    for i in range(N):
        strictly_inc = True
        if i > 0 and not prefix[i - 1]:
            strictly_inc = False
        if i < N - 1 and not suffix[i + 1]:
            strictly_inc = False
        if i > 0 and i < N - 1 and not (A[i - 1] < A[i + 1]):
            strictly_inc = False

        if not strictly_inc:
            continue

        B = [A[j] for j in range(N) if j != i]
        if is_smooth(B):
            ans[i] = '1'

    return ''.join(ans)

# Input Handling
T = int(input())
for _ in range(T):
    N = int(input())
    A = list(map(int, input().split()))
    print(solve(N, A))

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isSmooth(const vector<long long>& B) {
    vector<long long> cur = B;
    while(cur.size() >= 2) {
  
        for (size_t j = 0; j + 1 < cur.size(); j++) {
            if(cur[j] >= cur[j+1])
                return false;
        }

        vector<long long> nxt;
        nxt.resize(cur.size()-1);
        for (size_t j = 0; j + 1 < cur.size(); j++){
            nxt[j] = cur[j+1] - cur[j];
        }
        cur = move(nxt);
    }
    return true;
}
 
int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
 
    int T;
    cin >> T;
    while(T--){
        int N;
        cin >> N;
        vector<long long> A(N);
        for (int i = 0; i < N; i++){
            cin >> A[i];
        }

        vector<bool> prefix(N, false), suffix(N, false);
        prefix[0] = true;
        for (int i = 1; i < N; i++){
            prefix[i] = prefix[i-1] && (A[i-1] < A[i]);
        }
        suffix[N-1] = true;
        for (int i = N-2; i >= 0; i--){
            suffix[i] = suffix[i+1] && (A[i] < A[i+1]);
        }
 

        string ans;
        ans.resize(N, '0');
 

        for (int i = 0; i < N; i++){
            bool strictlyInc = true;

            if(i > 0 && !prefix[i-1]) {
                strictlyInc = false;
            }

            if(i < N-1 && !suffix[i+1]) {
                strictlyInc = false;
            }

            if(i > 0 && i < N-1 && !(A[i-1] < A[i+1])){
                strictlyInc = false;
            }
 
            if(!strictlyInc){
                ans[i] = '0';
                continue;
            }
 
             vector<long long> B;
            B.reserve(N-1);
            for (int j = 0; j < N; j++){
                if(j == i) continue;
                B.push_back(A[j]);
            }
 

            if(isSmooth(B))
                ans[i] = '1';
            else
                ans[i] = '0';
        }
 
        cout << ans << endl;
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class SmoothlyIncreasing {
    static boolean isSmooth(long[] B) {
        long[] cur = B.clone();
        while (cur.length >= 2) {
            for (int j = 0; j + 1 < cur.length; j++) {
                if (cur[j] >= cur[j + 1])
                    return false;
            }
            long[] nxt = new long[cur.length - 1];
            for (int j = 0; j + 1 < cur.length; j++) {
                nxt[j] = cur[j + 1] - cur[j];
            }
            cur = nxt;
        }
        return true;
    }

    static String solve(int N, long[] A) {
        boolean[] prefix = new boolean[N], suffix = new boolean[N];
        prefix[0] = true;
        for (int i = 1; i < N; i++) {
            prefix[i] = prefix[i - 1] && (A[i - 1] < A[i]);
        }

        suffix[N - 1] = true;
        for (int i = N - 2; i >= 0; i--) {
            suffix[i] = suffix[i + 1] && (A[i] < A[i + 1]);
        }

        StringBuilder ans = new StringBuilder("0".repeat(N));

        for (int i = 0; i < N; i++) {
            boolean strictlyInc = true;
            if (i > 0 && !prefix[i - 1]) strictlyInc = false;
            if (i < N - 1 && !suffix[i + 1]) strictlyInc = false;
            if (i > 0 && i < N - 1 && !(A[i - 1] < A[i + 1])) strictlyInc = false;

            if (!strictlyInc) continue;

            long[] B = new long[N - 1];
            int index = 0;
            for (int j = 0; j < N; j++) {
                if (j != i) B[index++] = A[j];
            }

            if (isSmooth(B)) ans.setCharAt(i, '1');
        }

        return ans.toString();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            long[] A = new long[N];
            for (int i = 0; i < N; i++) {
                A[i] = sc.nextLong();
            }
            System.out.println(solve(N, A));
        }
        sc.close();
    }
}


```

</details>

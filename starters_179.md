## 1. Lost in the Fest!!

<details>
<summary>Python</summary>

```python
# cook your dish here
t = int(input())  # Reading number of test cases
for _ in range(t):
    n = int(input())  # Reading the size of the array
    a = list(map(int, input().split()))  # Reading the array elements
    
    i = 0
    while i < n:
        if a[i] >= a[n - 1]:
            break
        i += 1
    
    if i == n:
        print(0)  # If the condition isn't met for any element, print 0
    else:
        print(n - 1 - i)  # Print the number of elements remaining


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long
int32_t main() {
    // your code goes here
    int t;
    cin >> t;
    while (t--) 
    {
        int n;cin>>n;
        int a[n];
        for(int i=0;i<n;i++)cin>>a[i];
        int i;
        for( i=0;i<n;i++){
            if(a[i]>=a[n-1])break;
        }
        if(i==n)cout<<0<<endl;
        else cout<< n-1-i<<endl;
    }
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); // Reading number of test cases
        while (t-- > 0) {
            int n = sc.nextInt(); // Reading the size of the array
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt(); // Reading elements of the array
            }
            
            int i;
            for (i = 0; i < n; i++) {
                if (a[i] >= a[n - 1]) break;
            }
            
            if (i == n) {
                System.out.println(0); // If the condition isn't met for any element, print 0
            } else {
                System.out.println(n - 1 - i); // Print the number of elements remaining
            }
        }
	}
}


```

</details>

## 2. Unlock The Safe
<details>
<summary>Python</summary>

```python
# cook your dish here
t = int(input())  # Read number of test cases
for _ in range(t):
    n, k = map(int, input().split())  # Read n and k
    a = list(map(int, input().split()))  # Read array a
    b = list(map(int, input().split()))  # Read array b
    
    sum_val = 0
    diff = float('inf')
    
    # Calculate the sum and diff
    for i in range(n):
        v = abs(a[i] - b[i])
        v = min(v, 9 - v)
        diff = min(diff, abs(v - (9 - v)))
        sum_val += v
    
    # Output based on conditions
    if sum_val > k:
        print("NO")
    elif sum_val % 2 == k % 2:
        print("YES")
    elif sum_val + diff <= k:
        print("YES")
    else:
        print("NO")

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
        int n, k;
        cin >> n >> k;
        vector <int> a(n);
        vector <int> b(n);
        for (int i = 0; i < n; i++) cin >> a[i];
        for (int i = 0; i < n; i++) cin >> b[i];
        int sum = 0;
        int diff = INT_MAX;
        for (int i = 0; i < n; i++){
            int v = abs(a[i] - b[i]);
            v = min(v, 9 - v);
            diff = min(diff, abs(v - (9 - v)));
            sum += v;
        }
        if (sum > k) cout << "NO\n";
        else if (sum % 2 == k % 2) {
            cout << "Yes\n";
        }
        else if (sum + diff <= k) cout << "Yes\n";
        else cout << "No\n";
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
	 Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); // Read number of test cases
        while (t-- > 0) {
            int n = sc.nextInt(); // Read size of arrays
            int k = sc.nextInt(); // Read value of k
            int[] a = new int[n];
            int[] b = new int[n];
            
            // Reading arrays a and b
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }
            for (int i = 0; i < n; i++) {
                b[i] = sc.nextInt();
            }
            
            int sum = 0;
            int diff = Integer.MAX_VALUE;
            
            // Calculate the sum and diff
            for (int i = 0; i < n; i++) {
                int v = Math.abs(a[i] - b[i]);
                v = Math.min(v, 9 - v);
                diff = Math.min(diff, Math.abs(v - (9 - v)));
                sum += v;
            }
            
            // Output based on conditions
            if (sum > k) {
                System.out.println("NO");
            } else if (sum % 2 == k % 2) {
                System.out.println("YES");
            } else if (sum + diff <= k) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
        sc.close();

	}
}



```

</details>

## 3. Can you reach

<details>
<summary>Python</summary>

```python
def count_friendships(test_cases):
    results = []

    for n, heights in test_cases:
        Larr = [0] * n
        Rarr = [0] * n

        for i in range(1, n):
            if i == 1 or (heights[i] - heights[i - 1]) != (heights[i - 1] - heights[i - 2]):
                Larr[i] = i - 1
            else:
                Larr[i] = Larr[i - 1]
        Rarr[-1] = n - 1
        for i in range(n - 2, -1, -1):
            if i == n - 2 or (heights[i + 1] - heights[i]) != (heights[i + 2] - heights[i + 1]):
                Rarr[i] = i + 1
            else:
                Rarr[i] = Rarr[i + 1]
        intervals = sorted(zip(Larr, Rarr))
        def lower_bound(key):
            lo, hi = 0, n
            while lo < hi:
                mid = (lo + hi) // 2
                if intervals[mid][0] > key:
                    hi = mid
                else:
                    lo = mid + 1
            return lo
        non_intersect = 0
        for i in range(n):
            idx = lower_bound(intervals[i][1])
            non_intersect += (n - idx)
        total_pairs = n * (n - 1) // 2
        friendships = total_pairs - non_intersect
        results.append(str(friendships))
    return results
T = int(input())
test_cases = []

for _ in range(T):
    N = int(input())
    H = list(map(int, input().split()))
    test_cases.append((N, H))
for res in count_friendships(test_cases):
    print(res)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
using ll = long long;

int main() {
    int t; cin >> t;
    while(t--) {
        ll n,enem=0;
        cin>>n;
        vector<ll> h(n);
        vector<ll> ind(n);
        for(ll i=0;i<n;i++) cin>>h[i];

        for(ll i=1;i<n-1;i++) {
            if(h[i-1]>h[i]&&h[i+1]>h[i] || h[i-1]<h[i]&&h[i+1]<h[i]) ind.push_back(i);
        }

        for(ll i=0;i<ind.size()-2;i++) {
          enem+=  (ind[i+1]-ind[i])*(n-1-ind[i+2]);
        }

        cout<<n*(n-1)/2-enem<<endl; 
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
		// your code goes here
		Scanner s = new Scanner(System.in);
		int t = s.nextInt();
		while(t--!=0){
		    int n = s.nextInt();
		    int H[] = new int[n+1];
		    for(int i = 1;i<=n;i++) H[i]  = s.nextInt();
		    
		    if(n==0){ System.out.println(0); continue;
		    }
		    
		    int L[] = new int[n+1];
		    int R[] = new int[n+1];
		    
		    L[1] = 1;
		    L[2] = 2;
		    
		    for(int i = 3;i<= n;i++){
		        if(H[i]==H[i-2])
		            L[i] = i-1;
		        else    
		            L[i] = L[i-1];
		    }
		    
		    R[n] = n;
		    R[n-1] = n ;
		    
		    for(int i = n-2;i>=1;i--){
		        if(H[i+2] == H[i])
		            R[i] = i+1;
		        else 
		            R[i] = R[i+1];
		    }
		    
		    int f[]  = new int [n+1];
		    
		    int freq[] = new int[n+2];
		    for(int i = 1;i<=n;i++){
		        freq[L[i]]++;
		    }
		    
		    for(int x = 1;x<=n;x++){
		        f[x] = f[x-1] + freq[x];
		    }
		    
		    
		    long ans = 0;
		    
		    for(int i = 1;i<n-1;i++){
		        int cnt1 = Math.max(0,R[i]-i);
		        int cnt2 = f[R[i]] - R[i];
		        ans+= cnt1+cnt2;
		    }
		    System.out.println(ans+1);
		    
		}

	}
}
 

```

</details>

## 4. Station Allocation

<details>
<summary>Python</summary>

```python
# cook your dish here
import sys
import bisect

def main():
    inp = sys.stdin.read().split()
    i = 0
    T = int(inp[i]); i += 1
    out = []

    for _ in range(T):
        n = int(inp[i]); i += 1
        c = list(map(int, inp[i:i + n])); i += n
        c.sort()
        p = [0] * (n + 1)

        for j in range(1, n + 1):
            p[j] = p[j - 1] + c[j - 1]

        q = int(inp[i]); i += 1
        res = []

        for _ in range(q):
            x, y = map(int, inp[i:i + 2]); i += 2
            pos = bisect.bisect_left(c, x)
            t = float('inf')

            if pos < n:
                t = min(t, max(0, y - (p[n] - c[pos])))
            if pos > 0:
                t = min(t, max(0, y - (p[n] - c[pos - 1])) + (x - c[pos - 1]))
            
            res.append(str(t))
        out.append(" ".join(res))

    sys.stdout.write("\n".join(out) + "\n")

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include<bits/stdc++.h>
using namespace std;
using ll = long long;
int main()
{
    ll t;
    cin>>t;
    while(t--)
    {
        ll n;
        cin>>n;
        vector<ll> a(n);
        ll s = 0;
        for(ll i = 0;i<n;i++)
        {
            cin>>a[i];
            s+=a[i];
        }
        sort(a.begin(),a.end());
        
        ll m;
        cin>>m;
        while(m--)
        {
            ll x,y;
            cin>>x>>y;
            auto it = lower_bound(a.begin(),a.end(),x);
            if(it == a.end())//not in there ---> x>ci
            {
                ll rx = x - a[n-1];
                ll ry = max(0ll,y - (s - a[n-1]));
                ll ans = rx+ry;
                cout<<ans<<endl;
            }
            else
            {
                ll ind = it - a.begin();
                ll cmx = a[ind];
                ll ind1 = -1;
                for(ll i = ind;i>=0;i--)
                {
                    if(a[i]<x)
                    {
                        ind1 = i;
                        break;
                    }
                }
                ll cmx1 = (ind1 == -1?0:a[ind1]);
                
                //op1 choose cmx
                ll ry1 = max(0ll,y - (s - cmx));
                ll ans1 = ry1;
                
                
                //op2 choose cmx1
                ll ans2 = 1e9;
                if(ind1 != -1)
                {
                ll rx2 = x - cmx1;
                ll ry2 = max(0ll,y - (s - cmx1));
                 ans2 = rx2+ry2;
            }
                cout<<min(ans1,ans2)<<endl;
            }
        }
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
    private static int bs(long[] arr, long val) {
        int lo = 0, hi = arr.length - 1;
        int ans = arr.length;
        while(lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if(arr[mid] == val) {
                return mid;
            } else if(arr[mid] > val) {
                ans = mid;
                hi = mid - 1;
            } else {
                lo = mid + 1;
            }
        }
        return ans;
    }
    
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc = new Scanner(System.in);
		int t = sc.nextInt();
		while(t-- > 0) {
		    int n = sc.nextInt();
		    long sum = 0;
		    long[] arr = new long[n];
		    for(int i = 0; i < n; i++) {
		        arr[i] = sc.nextLong();
		        sum += arr[i];
		    }
		    Arrays.sort(arr);
		    
		    int q = sc.nextInt();
		    for(int i = 0; i < q; i++) {
		        long x = sc.nextLong();
		        long y = sc.nextLong();
		        
		        int idx = bs(arr, x);
		        long ans = 0;
		        if(idx == n) {
		            ans = x - arr[n - 1];
		            if(sum - arr[n - 1] < y) {
		                ans += (y - (sum - arr[n - 1]));
		            }
		        } else if(arr[idx] == x) {
		            if(sum - x < y) {
		                ans = y - (sum - x);
		            }
		        } else {
		            if(idx == 0) {
		                if(sum - arr[0] < y) {
		                    ans = y - (sum - arr[0]);
		                }
		            } else {
		              //  long ans1 = Long.MAX_VALUE, ans2 = Long.MAX_VALUE;
		                long ans1 = 0, ans2 = 0;
		                if(sum - arr[idx] < y) {
		                    ans1 = y - (sum - arr[idx]);
		                }
		                ans2 = x - arr[idx - 1];
		                if(sum - arr[idx - 1] < y) {
		                    ans2 += (y - (sum - arr[idx - 1]));
		                }
		                ans = Math.min(ans1, ans2);
		            }
		        }
		        System.out.println(ans);
		    }
		}
	}
}

```

</details>

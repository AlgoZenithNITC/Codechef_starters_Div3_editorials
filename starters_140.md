## 1. Yoga Day

<details>
<summary>Python</summary>

```Python
import math

t = int(input())
for _ in range(t):
    n, x, y = map(int, input().split())
    s1 = n * x
    s2 = (n % 2) * x + (n // 2) * y
    print(max(s1, s2))

```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
	cin>>t;
	while(t--)
	{
	    int x , y , n;
	    cin>>n>>x>>y;
	    int s1 = n*x;
	    int s2 = (n%2)*x + (n/2)*y;
	    cout<<max(s1,s2)<<endl;
	}
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```Java
import Java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            int s1 = n * x;
            int s2 = (n % 2) * x + (n / 2) * y;
            System.out.println(Math.max(s1, s2));
        }
    }
}

```

</details>

## 2. Make Permutation

<details>
<summary>Python</summary>
	
```Python
def main():
    t = int(input())
    while t > 0:
        n = int(input())
        a = list(map(int, input().split()))
        c = list(range(1, n + 1)) 
        
        a.sort()  
        c.sort() 
        
        possible = True
        for i in range(n):
            if c[i] < a[i]:
                possible = False
                break
        
        if possible:
            print("YES")
        else:
            print("NO")
        
        t -= 1

if __name__ == "__main__":
    main()

```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        vector<int> a(n, 0);
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }
        vector<int> c(n, 0);
        for (int i = 0; i < n; i++) {
            c[i] = i + 1;
        }
        sort(a.begin(), a.end());
        sort(c.begin(), c.end());
        
        bool possible = true;
        for (int i = 0; i < n; i++) {
            if (c[i] - a[i] < 0) {
                cout << "NO" << endl;
                possible = false;
                break;
            }
        }
        
        if (possible) {
            cout << "YES" << endl;
        }
    }
    return 0;
}
```
</details>

<details>
<summary>Java</summary>
	
```Java
    import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            List<Integer> a = new ArrayList<>(n);
            for (int i = 0; i < n; i++) {
                a.add(scanner.nextInt());
            }
            List<Integer> c = new ArrayList<>(n);
            for (int i = 0; i < n; i++) {
                c.add(i + 1);
            }
            Collections.sort(a);
            Collections.sort(c);
            boolean possible = true;
            for (int i = 0; i < n; i++) {
                if (c.get(i) - a.get(i) < 0) {
                    System.out.println("NO");
                    possible = false;
                    break;
                }
            }
            if (possible) {
                System.out.println("YES");
            }
        }
    }
}
```

</details>

## 3. Trick Or Treat

<details>
<summary>Python</summary>
	
```Python
import collections

t = int(input())
while t > 0:
    n, m = map(int, input().split())
    can = list(map(int, input().split()))
    cho = list(map(int, input().split()))
    
    for i in range(n):
        can[i] = can[i] % m
        cho[i] = cho[i] % m
    
    m1 = collections.defaultdict(int)
    for c in cho:
        m1[c] += 1
    
    cnt = 0
    for c in can:
        if c == 0:
            cnt += m1[0]
        else:
            cnt += m1[m - c]
    
    print(cnt)
    t -= 1
```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        long long can[n], cho[n];
        for (int i = 0; i < n; i++) {
            cin >> can[i];
        }
        for (int i = 0; i < n; i++) {
            cin >> cho[i];
        }
        for (int i = 0; i < n; i++) {
            can[i] %= m;
            cho[i] %= m;
        }
        unordered_map<long long, long long> m1;
        for (int i = 0; i < n; i++) {
            long long k = cho[i];
            m1[k]++;
        }
        long long cnt = 0;
        for (int i = 0; i < n; i++) {
            if (can[i] == 0) {
                cnt += m1[0];
            } else {
                cnt += m1[m - can[i]];
            }
        }
        cout << cnt << endl;
    }
    return 0;
}
```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int m = scanner.nextInt();
            long[] can = new long[n];
            long[] cho = new long[n];
            for (int i = 0; i < n; i++) {
                can[i] = scanner.nextLong();
            }
            for (int i = 0; i < n; i++) {
                cho[i] = scanner.nextLong();
            }
            for (int i = 0; i < n; i++) {
                can[i] %= m;
                cho[i] %= m;
            }
            Map<Long, Long> m1 = new HashMap<>();
            for (int i = 0; i < n; i++) {
                long k = cho[i];
                m1.put(k, m1.getOrDefault(k, 0L) + 1);
            }
            long cnt = 0;
            for (int i = 0; i < n; i++) {
                if (can[i] == 0) {
                    cnt += m1.getOrDefault(0L, 0L);
                } else {
                    cnt += m1.getOrDefault(m - can[i], 0L);
                }
            }
            System.out.println(cnt);
        }
    }
}
```
</details>

## 4. Split Permutation

<details>
<summary>Python</summary>
	
```Python
import sys

t = int(input())
while t > 0:
    n = int(input())
    if n % 2 == 0:
        for i in range(n // 2):
            print(i + 1, n - i, end=" ")
    else:
        x = n - 1
        for i in range(x // 2):
            print(i + 1, x - i, end=" ")
        print(n)
    print()
    t -= 1

```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        if (n % 2 == 0) {
            for (int i = 0; i < n / 2; i++) {
                cout << i + 1 << " " << n - i << " ";
            }
        } else {
            int x = n - 1;
            for (int i = 0; i < x / 2; i++) {
                cout << i + 1 << " " << x - i << " ";
            }
            cout << n;
        }
        cout << endl;
    }
    return 0;
}

```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            if (n % 2 == 0) {
                for (int i = 0; i < n / 2; i++) {
                    System.out.print((i + 1) + " " + (n - i) + " ");
                }
            } else {
                int x = n - 1;
                for (int i = 0; i < x / 2; i++) {
                    System.out.print((i + 1) + " " + (x - i) + " ");
                }
                System.out.print(n);
            }
            System.out.println();
        }
    }
}

```
</details>

## 5. Tree Removal
<details>
<summary>Python</summary>
	
```Python
import sys
from collections import deque

def main():
    t = int(input())
    while t > 0:
        t -= 1
        n = int(input())
        a = list(map(int, input().split()))
        mn = float('inf')
        mni = -1
        for i in range(n):
            if a[i] < mn:
                mn = a[i]
                mni = i
        adj = [[] for _ in range(n)]
        for i in range(n - 1):
            u, v = map(int, input().split())
            adj[u - 1].append(v - 1)
            adj[v - 1].append(u - 1)
        vis = [0] * n
        q = deque()
        q.append(mni)
        vis[mni] = 1
        ans = []
        while q:
            node = q.popleft()
            for it in adj[node]:
                if vis[it] == 0:
                    q.append(it)
                    ans.append(it)
                    vis[it] = 1
        print(len(ans))
        print(*[x + 1 for x in reversed(ans)])

if __name__ == "__main__":
    main()

```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin >> t;
    while(t--) {
        int n;
        cin >> n;
        vector<long long int> a(n);
        long long int mn = 1e12;
        int mni = -1;
        for(int i = 0; i < n; i++) {
            cin >> a[i];
            if(a[i] < mn) {
                mn = a[i];
                mni = i;
            }
        }
        vector<vector<int>> adj(n);
        for(int i = 0; i < n - 1; i++) {
            int u, v;
            cin >> u >> v;
            u--;
            v--;
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        vector<int> vis(n, 0);
        queue<int> q;
        q.push(mni);
        vis[mni] = 1;
        vector<int> ans;
        while(q.size() > 0) {
            int node = q.front();
            q.pop();
       
            for(auto it: adj[node]) {
               if(vis[it] == 0) {
                   q.push(it);
                   ans.push_back(it);
                   vis[it] = 1;
               }
            }
            
        }
        cout << ans.size() << endl;
        reverse(ans.begin(), ans.end());
        for(int i = 0; i < ans.size(); i++) {
            cout << ans[i] + 1 << ' ';
        }
        cout << endl;
    }
}
```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            long[] a = new long[n];
            long mn = Long.MAX_VALUE;
            int mni = -1;
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextLong();
                if (a[i] < mn) {
                    mn = a[i];
                    mni = i;
                }
            }
            List<Integer>[] adj = new ArrayList[n];
            for (int i = 0; i < n; i++) {
                adj[i] = new ArrayList<>();
            }
            for (int i = 0; i < n - 1; i++) {
                int u = scanner.nextInt() - 1;
                int v = scanner.nextInt() - 1;
                adj[u].add(v);
                adj[v].add(u);
            }
            boolean[] vis = new boolean[n];
            Queue<Integer> q = new LinkedList<>();
            q.offer(mni);
            vis[mni] = true;
            List<Integer> ans = new ArrayList<>();
            while (!q.isEmpty()) {
                int node = q.poll();
                for (int it : adj[node]) {
                    if (!vis[it]) {
                        q.offer(it);
                        ans.add(it);
                        vis[it] = true;
                    }
                }
            }
            System.out.println(ans.size());
            Collections.reverse(ans);
            for (int i : ans) {
                System.out.print((i + 1) + " ");
            }
            System.out.println();
        }
    }
}
```
</details>

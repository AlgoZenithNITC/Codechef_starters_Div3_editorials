## 1. Nearly Equal

<details>
<summary>Python</summary>

```python
 from sys import maxsize

def help(p, q, x, y):
    if p < q:
        return help(q, p, y, x)
    
    ans = maxsize
    for i in range(p - q + 1):
        a = x[i:i+q]
        b = 0
        for j in range(q):
            if a[j] != y[j]:
                b += 1
        ans = min(ans, b)
    return ans

n = int(input())
for _ in range(n):
    p, q = map(int, input().split())
    x, y = input().split()
    print(help(p, q, x, y))
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int help(int p , int q , string x , string y)
{
    if(p<q)
    {
        return help(q,p,y,x);
    }
    
    int ans = INT_MAX;
    for(int i = 0 ; i <= (p-q) ; i++)
    {
        string a = x.substr(i,i+q);
        int b = 0;
        for(int j = 0 ; j<q ; j++)
        {
            if(a[j]!=y[j])
            b++;
        }
        ans = min(ans , b);
    }
    return ans;
}

int main() {
    int n;
    cin>>n;
    while(n--)
    {
        string x,y;
        int p , q;
        cin>>p>>q;
        cin>>x>>y;
        cout<<help(p,q,x,y)<<endl;
    }

}
```

</details>

<details>
<summary>Java</summary>

```java
mport java.util.*;

public class Solution {
    public static int help(int p, int q, String x, String y) {
        if (p < q) {
            return help(q, p, y, x);
        }

        int ans = Integer.MAX_VALUE;
        for (int i = 0; i <= (p - q); i++) {
            String a = x.substring(i, i + q);
            int b = 0;
            for (int j = 0; j < q; j++) {
                if (a.charAt(j) != y.charAt(j)) {
                    b++;
                }
            }
            ans = Math.min(ans, b);
        }
        return ans;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.nextLine(); // consume newline character
        for (int i = 0; i < n; i++) {
            int p = scanner.nextInt();
            int q = scanner.nextInt();
            String x = scanner.next();
            String y = scanner.next();
            System.out.println(help(p, q, x, y));
        }
    }
}
```

</details>

## 2. Redundant Array

<details>
<summary>Python</summary>

```python
import sys
from collections import defaultdict

def main():
    t = int(input())

    while t > 0:
        n = int(input())
        arr = list(map(int, input().split()))

        freq_map = defaultdict(int)
        for num in arr:
            freq_map[num] += 1

        min_cost = sys.maxsize
        for max_freq, max_key in freq_map.items():
            min_cost = min(min_cost, (len(arr) - max_freq) * max_key)

        if min_cost > len(arr):
            print(len(arr))
        else:
            print(min_cost)

        t -= 1

if _name_ == "_main_":
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

    while (t-- > 0) {
        int n;
        cin >> n;
        vector<int> arr(n);

        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }

        map<int, int> freqMap;
        for (int num : arr) {
            freqMap[num]++;
        }

        long long minCost = LLONG_MAX;
        for (auto& entry : freqMap) {
            long long maxFreq = entry.second;
            long long maxKey = entry.first;
            minCost = min(minCost, (long long)(arr.size() - maxFreq) * maxKey);
        }

        if (minCost > arr.size()) {
            cout << arr.size() << endl;
        } else {
            cout << minCost << endl;
        }
    }
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            int[] arr = new int[n];

            for (int i = 0; i < n; i++) {
                arr[i] = scanner.nextInt();
            }

            Map<Integer, Integer> freqMap = new HashMap<>();
            for (int num : arr) {
                freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
            }

            long minCost = Long.MAX_VALUE;
            for (Map.Entry<Integer, Integer> entry : freqMap.entrySet()) {
                long maxFreq = entry.getValue();
                long maxKey = entry.getKey();
                minCost = Math.min(minCost, (long)(arr.length - maxFreq) * maxKey);
            }

            if (minCost > arr.length) {
                System.out.println(arr.length);
            } else {
                System.out.println(minCost);
            }
        }
    }
}
```

</details>

## 3. Amphibian Escape

<details>
<summary>Python</summary>

```python
import math

T = int(input())
while T > 0:
    N, K, H = map(int, input().split())
    A, B, temp = 1, 1, 0
    while A <= N:
        if A < H:
            if A * K - B * (K - 1) >= H:
                while A * K - B * (K - 1) >= H:
                    B += 1
                temp += B - 1
            else:
                A += 1
        else:
            temp += N
            A += 1
    print(temp)
    T -= 1
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int T;
    cin >> T;
    while (T--) {
        int N, K, H;
        cin >> N >> K >> H;
        long long A = 1, B = 1, temp = 0;
        while (A <= N) {
            if (A < H) {
                if (A * K - B * (K - 1) >= H) {
                    while (A * K - B * (K - 1) >= H) {
                        B++;
                    }
                    temp += B - 1;
                } else {
                    A++;
                }
            } else {
                temp += N;
                A++;
            }
        }

        cout << temp << endl;
    }
    return 0;
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int T = scanner.nextInt();
        while (T-- > 0) {
            int N = scanner.nextInt();
            int K = scanner.nextInt();
            int H = scanner.nextInt();
            long A = 1, B = 1, temp = 0;
            while (A <= N) {
                if (A < H) {
                    if (A * K - B * (K - 1) >= H) {
                        while (A * K - B * (K - 1) >= H) {
                            B++;
                        }
                        temp += B - 1;
                    } else {
                        A++;
                    }
                } else {
                    temp += N;
                    A++;
                }
            }
            System.out.println(temp);
        }
    }
}
```

</details>

## 4. Perfect Prefixes

<details>
<summary>Python</summary>

```python
def main():
    import sys
    input = sys.stdin.read
    data = input().split()

    t = int(data[0])
    index = 1

    results = []

    for _ in range(t):
        n = int(data[index])
        index += 1
        p = list(map(int, data[index:index + n]))
        index += n

        s = set()
        after = [0] * (n - 1)
        cnt = 1

        for i in range(n - 1):
            s.add(p[i])
            if max(s) == i + 1:
                cnt += 1
                after[i] = -1
                continue
            
            s.discard(p[i])
            s.add(p[i + 1])
            if max(s) == i + 1:
                after[i] = 1
            s.discard(p[i + 1])
            s.add(p[i])

        sum_even = 0
        maxi = 0

        for i in range(0, n - 1, 2):
            sum_even += after[i]
            sum_even = max(0, sum_even)
            maxi = max(sum_even, maxi)

        sum_odd = 0

        for i in range(1, n - 1, 2):
            sum_odd += after[i]
            sum_odd = max(0, sum_odd)
            maxi = max(maxi, sum_odd)

        results.append(cnt + maxi)

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

int main() {
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vector<int>p(n,0);
        for(int i = 0;i<n;i++){
            cin>>p[i];
        }
        set<int>s;
        vector<int>after(n-1,0);
        int cnt = 1;
        for(int i = 0;i<n-1;i++){
            s.insert(p[i]);
            if(*s.rbegin() == i+1){
                cnt+=1;
                after[i] = -1;
                continue;
            }
            s.erase(p[i]);
            s.insert(p[i+1]);
            if(*s.rbegin() == i+1){
                after[i] = 1;
            }
            s.erase(p[i+1]);
            s.insert(p[i]);
        }
        int sum = 0;
        int maxi = 0;
        for(int i = 0;i<n-1;i+=2){
            sum+=after[i];
            sum = max(0,sum);
            maxi = max(sum,maxi);
        }
        sum = 0;
        for(int i =1;i<n-1;i+=2){
            sum+=after[i];
            sum = max(0,sum);
            maxi=max(maxi,sum);
        }
        cout<<cnt+maxi<<endl;
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
            int n = sc.nextInt();
            int[] p = new int[n];

            for (int i = 0; i < n; i++) {
                p[i] = sc.nextInt();
            }

            TreeSet<Integer> s = new TreeSet<>();
            int[] after = new int[n - 1];
            int cnt = 1;

            for (int i = 0; i < n - 1; i++) {
                s.add(p[i]);

                if (s.last() == i + 1) {
                    cnt += 1;
                    after[i] = -1;
                    continue;
                }

                s.remove(p[i]);
                s.add(p[i + 1]);

                if (s.last() == i + 1) {
                    after[i] = 1;
                }

                s.remove(p[i + 1]);
                s.add(p[i]);
            }

            int sum = 0;
            int maxi = 0;

            for (int i = 0; i < n - 1; i += 2) {
                sum += after[i];
                sum = Math.max(0, sum);
                maxi = Math.max(sum, maxi);
            }

            sum = 0;

            for (int i = 1; i < n - 1; i += 2) {
                sum += after[i];
                sum = Math.max(0, sum);
                maxi = Math.max(maxi, sum);
            }

            System.out.println(cnt + maxi);
        }

        sc.close();
    }
}

```

</details>

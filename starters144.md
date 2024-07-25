## Savings Account

<details>
<summary>Python</summary>

```python
   def main():
    t = int(input())
    
    for _ in range(t):
        x, y, z = map(int, input().split())
        
        total_production = x * y
        
        if total_production <= z:
            print(0)
        else:
            remaining_production = total_production - z
            full_units = remaining_production // y
            
            if remaining_production % y == 0:
                print(full_units)
            else:
                print(full_units + 1)

    if __name__ == "__main__":
       main()


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

    while (t-- > 0) {
        int x, y, z;
        cin >> x >> y >> z;

        int totalProduction = x * y;

        if (totalProduction <= z) {
            cout << 0 << endl;
        } else {
            int remainingProduction = totalProduction - z;
            int fullUnits = remainingProduction / y;

            if (remainingProduction % y == 0) {
                cout << fullUnits << endl;
            } else {
                cout << fullUnits + 1 << endl;
            }
        }
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
            int x = sc.nextInt();
            int y = sc.nextInt();
            int z = sc.nextInt();
            
            int totalProduction = x * y;
            
            if (totalProduction <= z) {
                System.out.println(0);
            } else {
                int remainingProduction = totalProduction - z;
                int fullUnits = remainingProduction / y;
                
                if (remainingProduction % y == 0) {
                    System.out.println(fullUnits);
                } else {
                    System.out.println(fullUnits + 1);
                }
            }
        }
        
        sc.close();
    }
}


```

</details>

## Budget Allotment

<details>
<summary>Python</summary>

```python

import sys
input = sys.stdin.read

def solve():
    data = input().split()
    index = 0
    
    T = int(data[index])
    index += 1
    results = []
    
    for _ in range(T):
        N = int(data[index])
        X = int(data[index + 1])
        index += 2
        
        A = list(map(int, data[index:index + N]))
        index += N
        
        A.sort()
        
        # Redistribution logic
        for i in range(N - 2, -1, -1):
            if A[i + 1] >= X:
                A[i] += A[i + 1] - X
                A[i + 1] = X
        
        # Count elements greater than or equal to X
        count = sum(1 for value in A if value >= X)
        
        results.append(count)
    
    for result in results:
        print(result)

if _name_ == "_main_":
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

    int t;
    cin >> t;
    while (t--) {
        long long int n, x, sum = 0, ct = 0;
        cin >> n >> x;
        long long int a[n];
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }

        sort(a, a + n);
        for (int i = n - 2; i >= 0; i--) {
            if (a[i + 1] >= x) {
                a[i] += a[i + 1] - x;
                a[i + 1] = x;
            }
        }
        for (int i = 0; i < n; i++) {
            if (a[i] >= x) ct++;
        }

        cout << ct << endl;
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
    public static void main(String[] args) throws java.lang.Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        int t = Integer.parseInt(st.nextToken());
        while (t-- > 0) {
            st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
            int x = Integer.parseInt(st.nextToken());
            
            long[] a = new long[n];
            st = new StringTokenizer(br.readLine());
            for (int i = 0; i < n; i++) {
                a[i] = Long.parseLong(st.nextToken());
            }
            
            // Sort the array
            Arrays.sort(a);
            
            // Redistribution logic
            for (int i = n - 2; i >= 0; i--) {
                if (a[i + 1] >= x) {
                    a[i] += a[i + 1] - x;
                    a[i + 1] = x;
                }
            }
            
            // Count elements greater than or equal to X
            int ct = 0;
            for (int i = 0; i < n; i++) {
                if (a[i] >= x) {
                    ct++;
                }
            }
            
            System.out.println(ct);
        }
    }
}

```

</details>

## Largest K

<details>
<summary>Python</summary>

```python
def largest_k(arr):
    from collections import Counter
    
    # Count frequencies of each element
    freq = Counter(arr)
    
    # Extract the frequencies and sort them in descending order
    freq_values = sorted(freq.values(), reverse=True)
    
    total_elements = 0
    max_k = 0
    
    # Iterate over the number of distinct elements
    for i, count in enumerate(freq_values):
        total_elements += count
        distinct_elements = i + 1
        max_k = max(max_k, (total_elements // distinct_elements) * distinct_elements)
    
    return max_k

def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    
    t = int(data[0])
    index = 1
    
    results = []
    for _ in range(t):
        n = int(data[index])
        arr = list(map(int, data[index + 1: index + 1 + n]))
        index += 1 + n
        
        result = largest_k(arr)
        results.append(result)
    
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
    while(t--)
    {
        int n;
        cin>>n;
        vector<int> arr(n);
        map<int,int> mp;
        for (int i = 0; i < n; ++i) {
            cin >> arr[i];
            mp[arr[i]]++;
        }
        vector<int> vec;
        for(auto it:mp)
        	  vec.push_back(it.second);
        sort(vec.begin(),vec.end(),greater<int>());
        int ans=0, sum=0;
        for(int i=0; i<vec.size(); i++){
            sum+=vec[i];
            int maxi=(sum/(i+1))*(i+1);
            ans=max(ans,maxi);
        }
        cout<<ans<<endl;
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
        
        while (t-- > 0) {
            int n = sc.nextInt();
            Map<Integer, Integer> freqMap = new HashMap<>();
            for (int i = 0; i < n; ++i) {
                int num = sc.nextInt();
                freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
            }
            
            List<Integer> freqList = new ArrayList<>(freqMap.values());
            Collections.sort(freqList, Collections.reverseOrder());
            
            int ans = 0, sum = 0;
            for (int i = 0; i < freqList.size(); ++i) {
                sum += freqList.get(i);
                int maxK = (sum / (i + 1)) * (i + 1);
                ans = Math.max(ans, maxK);
            }
            
            System.out.println(ans);
        }
        
        sc.close();
    }
}


```

</details>

## Minimise Inversions

<details>
<summary>Python</summary>

```python
import sys
input = sys.stdin.read

def solve():
    data = input().split()
    index = 0
    T = int(data[index])
    index += 1
    results = []
    
    for _ in range(T):
        N = int(data[index])
        K = int(data[index + 1])
        S = data[index + 2]
        index += 3
        
        result = float('inf')
        
        for changesOnLeft in range(K + 1):
            modifiedS = list(S)
            changesToZero = changesOnLeft
            changesToOne = K - changesOnLeft
            lastChangeIndex = -1

            # First pass: Change '1' to '0' from left to right
            for i in range(N):
                if modifiedS[i] == '1' and changesToZero > 0:
                    modifiedS[i] = '0'
                    lastChangeIndex = i
                    changesToZero -= 1
                    if changesToZero == 0:
                        break

            # Second pass: Change '0' to '1' from right to left
            for i in range(N - 1, lastChangeIndex, -1):
                if modifiedS[i] == '0' and changesToOne > 0:
                    modifiedS[i] = '1'
                    changesToOne -= 1
                    if changesToOne == 0:
                        break

            currentCost = 0
            incrementalCount = 0

            # Calculate the cost
            for char in modifiedS:
                if char == '0':
                    currentCost += incrementalCount
                else:
                    incrementalCount += 1

            result = min(currentCost, result)

        results.append(result)
    
    for res in results:
        print(res)

if _name_ == "_main_":
    solve()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

const long long MOD = 1000000007;
const double PI = 3.141592653589;

void solve() {
    int N, K;
    cin >> N >> K;
    string S;
    cin >> S;

    long long result = 1e9;

    for (int changesOnLeft = 0; changesOnLeft <= K; changesOnLeft++) {
        string modifiedS = S;
        int changesToZero = changesOnLeft;
        int changesToOne = K - changesOnLeft;
        int lastChangeIndex = -1;

        // First pass: Change '1' to '0' from left to right
        for (int i = 0; i < N; i++) {
            if (modifiedS[i] == '1' && changesToZero > 0) {
                modifiedS[i] = '0';
                lastChangeIndex = i;
                changesToZero--;
                if (changesToZero == 0)
                    break;
            }
        }

        // Second pass: Change '0' to '1' from right to left
        for (int i = N - 1; i > lastChangeIndex; i--) {
            if (modifiedS[i] == '0' && changesToOne > 0) {
                modifiedS[i] = '1';
                changesToOne--;
                if (changesToOne == 0)
                    break;
            }
        }

        long long currentCost = 0;
        long long incrementalCount = 0;

        // Calculate the cost
        for (int i = 0; i < N; i++) {
            if (modifiedS[i] == '0')
                currentCost += incrementalCount;
            else
                incrementalCount++;
        }

        result = min(currentCost, result);
    }

    cout << result << endl;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);
    
    int T;
    cin >> T;
    for (int i = 0; i < T; i++)
        solve();
    
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
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(System.out);
        
        int T = Integer.parseInt(br.readLine());
        
        while (T-- > 0) {
            String[] input = br.readLine().split(" ");
            int N = Integer.parseInt(input[0]);
            int K = Integer.parseInt(input[1]);
            String S = br.readLine();

            long result = Long.MAX_VALUE;

            for (int changesOnLeft = 0; changesOnLeft <= K; changesOnLeft++) {
                char[] modifiedS = S.toCharArray();
                int changesToZero = changesOnLeft;
                int changesToOne = K - changesOnLeft;
                int lastChangeIndex = -1;

                // First pass: Change '1' to '0' from left to right
                for (int i = 0; i < N; i++) {
                    if (modifiedS[i] == '1' && changesToZero > 0) {
                        modifiedS[i] = '0';
                        lastChangeIndex = i;
                        changesToZero--;
                        if (changesToZero == 0)
                            break;
                    }
                }

                // Second pass: Change '0' to '1' from right to left
                for (int i = N - 1; i > lastChangeIndex; i--) {
                    if (modifiedS[i] == '0' && changesToOne > 0) {
                        modifiedS[i] = '1';
                        changesToOne--;
                        if (changesToOne == 0)
                            break;
                    }
                }

                long currentCost = 0;
                long incrementalCount = 0;

                // Calculate the cost
                for (int i = 0; i < N; i++) {
                    if (modifiedS[i] == '0')
                        currentCost += incrementalCount;
                    else
                        incrementalCount++;
                }

                result = Math.min(currentCost, result);
            }

            pw.println(result);
        }
        
        pw.flush();
        br.close();
        pw.close();
    }
}


```

</details>

## Find P

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    for _ in range(t):
        n, l, r = map(int, input().split())
        j = 1
        sum_ = 0
        while sum_ < l:
            sum_ += j
            if sum_ < l:
                j += 1
        sum_ -= (l - 1)
        arr = []
        for i in range(1, j + 1):
            if i != sum_:
                arr.append(i)
        for i in range(n, j - 1, -1):
            arr.append(i)
        arr[-1] = sum_
        print(" ".join(map(str, arr)))

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
  #include <iostream>

#include <bits/stdc++.h>

using namespace std;

int main() {
    // your code goes here
    int t;
    cin >> t;
    while (t--) {
        long long int n, l,r;
        cin >> n >> l >> r;
        long long int j=1;
        long long int sum = 0;
        while (sum <l) {
            sum += j;
            if(sum<l) j++;
        }
        sum -=l-1;
        int arr[n];
        int k = 0;
        for (int i = 1; i <= j; i++) {
            if (i!=sum) arr[k++] = i;
        }
        for (int i=n; i>=j; i--) arr[k++] = i;
        arr[n - 1]=sum;
        for (int i=0; i<n; i++) {
            cout<<arr[i]<<" ";
        }
        cout<<endl;
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
            long n = sc.nextLong();
            long l = sc.nextLong();
            long r = sc.nextLong();
            long j = 1;
            long sum = 0;
            while (sum < l) {
                sum += j;
                if (sum < l) j++;
            }
            sum -= (l - 1);
            int[] arr = new int[(int)n];
            int k = 0;
            for (int i = 1; i <= j; i++) {
                if (i != sum) arr[k++] = i;
            }
            for (int i = (int)n; i >= j; i--) arr[k++] = i;
            arr[(int)n - 1] = (int)sum;
            for (int i = 0; i < n; i++) {
                System.out.print(arr[i] + " ");
            }
            System.out.println();
        }
        sc.close();
    }
}



```

</details>

## Sort Lexicographically

<details>
<summary>Python</summary>

```python
   
# cook your dish here
import sys
from collections import defaultdict
from bisect import insort, bisect_left

input = sys.stdin.read
data = input().split()

index = 0
test_cases = int(data[index])
index += 1

result = []

for _ in range(test_cases):
    n = int(data[index])
    index += 1
    
    a = [0] + list(map(int, data[index:index + n]))
    index += n
    
    maxi = [0] * (n + 1)
    load = defaultdict(list)
    load2 = [0] * (n + 1)
    poss = [0] * (n + 1)
    v = []
    
    mini = float('inf')
    flag = False
    last = 0
    
    for i in range(1, n + 1):
        maxi[i] = max(maxi[i - 1], a[i])
        
        if mini > a[i]:
            mini = a[i]
            v.append(i)
            poss[i] = 1
            last = i
            flag = True
        else:
            if flag:
                flag = False
                load[last].append(i)
            else:
                load2[i - 1] = i
    
    s = []
    
    for i in range(n, 0, -1):
        while s:
            pp = s[0]
            if pp[0] < a[i]:
                poss[pp[1]] = 1
                s.pop(0)
                if load2[pp[1]] != 0:
                    insort(s, (a[load2[pp[1]]], load2[pp[1]]))
            else:
                break
        
        for it in load[i]:
            insort(s, (a[it], it))
    
    v.append(n + 1)
    p = len(v) - 2
    ans = [0] * (n + 1)
    done = 0
    
    for i in range(p, -1, -1):
        cnt = v[i + 1] - v[i]
        fact = 1
        
        for j in range(v[i], v[i + 1]):
            if poss[j] == 1 and j + 1 < v[i + 1] and poss[j + 1] == 1:
                ans[done + cnt] = j
                cnt -= 1
            else:
                ans[done + fact] = j
                fact += 1
        
        done += v[i + 1] - v[i]
    
    result.append(" ".join(map(str, ans[1:])))

sys.stdout.write("\n".join(result) + "\n")

```

</details>

<details>
<summary>Cpp</summary>

```cpp
      #include <bits/stdc++.h>
using namespace std;

#define ll long long

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    ll test_cases;
    cin >> test_cases;

    while (test_cases--) {
        ll n;
        cin >> n;

        vector<ll> a(n + 1);
        vector<ll> maxi(n + 1, 0);
        vector<vector<ll>> load(n + 1);
        vector<ll> load2(n + 1, 0);
        vector<ll> poss(n + 1, 0);
        vector<ll> v;
        ll last, mini = 1e9;
        ll flag = 0;

        // Read input array a
        for (int i = 1; i <= n; ++i) {
            cin >> a[i];
        }

        // Calculate max array
        for (int i = 1; i <= n; ++i) {
            maxi[i] = max(maxi[i - 1], a[i]);

            if (mini > a[i]) {
                mini = a[i];
                v.push_back(i);
                poss[i] = 1;
                last = i;
                flag = 1;
            } else {
                if (flag) {
                    flag = 0;
                    load[last].push_back(i);
                } else {
                    load2[i - 1] = i;
                }
            }
        }

        // Set to keep track of the smallest elements
        set<pair<ll, ll>> s;
        pair<ll, ll> pp;

        // Process from right to left
        for (int i = n; i >= 1; --i) {
            while (!s.empty()) {
                pp = *s.begin();
                if (pp.first < a[i]) {
                    poss[pp.second] = 1;
                    s.erase(s.begin());
                    if (load2[pp.second] != 0) {
                        s.insert({a[load2[pp.second]], load2[pp.second]});
                    }
                } else {
                    break;
                }
            }
            for (auto it : load[i]) {
                s.insert({a[it], it});
            }
        }

        v.push_back(n + 1);
        ll p = v.size() - 2;
        vector<ll> ans(n + 1);
        ll done = 0;

        // Calculate the answer array
        for (int i = p; i >= 0; --i) {
            ll cnt = v[i + 1] - v[i];
            ll fact = 1;

            for (int j = v[i]; j < v[i + 1]; ++j) {
                if (poss[j] == 1 && j + 1 < v[i + 1] && poss[j + 1] == 1) {
                    ans[done + cnt] = j;
                    cnt--;
                } else {
                    ans[done + fact] = j;
                    fact++;
                }
            }
            done += v[i + 1] - v[i];
        }

        // Print the result
        for (int i = 1; i <= n; ++i) {
            cout << ans[i] << " ";
        }
        cout << "\n";
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
            long n = sc.nextLong();
            long l = sc.nextLong();
            long r = sc.nextLong();
            long j = 1;
            long sum = 0;
            while (sum < l) {
                sum += j;
                if (sum < l) j++;
            }
            sum -= (l - 1);
            int[] arr = new int[(int)n];
            int k = 0;
            for (int i = 1; i <= j; i++) {
                if (i != sum) arr[k++] = i;
            }
            for (int i = (int)n; i >= j; i--) arr[k++] = i;
            arr[(int)n - 1] = (int)sum;
            for (int i = 0; i < n; i++) {
                System.out.print(arr[i] + " ");
            }
            System.out.println();
        }
        sc.close();
    }
}

```

</details>
## Big Achiever

<details>
<summary>Python</summary>

```python
import sys

def main():
    input = sys.stdin.read
    data = input().split()

    index = 0
    t = int(data[index])
    index += 1

    for _ in range(t):
        n = int(data[index])
        index += 1
        arr = list(map(int, data[index:index + n]))
        index += n

        max1 = 0
        result = []

        for num in arr:
            if max1 < num:
                result.append(1)
            else:
                result.append(0)
            max1 = max(max1, num)

        print(" ".join(map(str, result)))

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
	for(int i = 0; i<t; i++)
	{
	    int n;
	    cin>>n;
	    int arr[n];
	    for(int j = 0; j<n; j++)
	    {
	        cin>>arr[j];
	    }
	    int max1 = 0;
	    for(int j = 0; j<n; j++)
	    {
	        if(max1<arr[j])
	        cout<<1<<" ";
	        else
	        cout<<0<<" ";
	        max1 = max(max1,arr[j]);
	    }
	    cout<<endl;
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
            int[] arr = new int[n];

            for (int j = 0; j < n; j++) {
                arr[j] = scanner.nextInt();
            }

            int max1 = 0;
            for (int j = 0; j < n; j++) {
                if (max1 < arr[j]) {
                    System.out.print(1 + " ");
                } else {
                    System.out.print(0 + " ");
                }
                max1 = Math.max(max1, arr[j]);
            }
            System.out.println();
        }

        scanner.close();
    }
}
```

</details>

## Make Odd

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    a = input().strip()
    b = input().strip()
    cnt = 0
    mixed = 0

    for i in range(n):
        if a[i] == '1' and b[i] == '1':
            cnt += 1
        elif a[i] == '1' or b[i] == '1':
            mixed += 1

    if cnt % 2 == 1:
        print("YES")
    elif mixed > 0:
        print("YES")
    else:
        print("NO")

def main():
    t = int(input())
    for _ in range(t):
        solve()

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
    int n;
    cin >> n;
    string a,b;
    cin >> a >> b;
    int cnt = 0, mixed = 0;
    for(int i = 0; i < n; i++){
        if(a[i] == '1' && b[i] == '1'){
            cnt++;
        }
        else if(a[i] == '1' || b[i] == '1'){
            mixed++;
        }
    }
    if(cnt % 2 == 1){
        cout << "YES\n";
    }
    else if(mixed > 0){
        cout << "YES\n";
    }
    else{
        cout << "NO\n";
    }
}

int main() {
    int t;
    cin >> t;
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
        int T = sc.nextInt();
        
        for (int t = 0; t < T; t++) {
            int N = sc.nextInt();
            String A = sc.next();
            String B = sc.next();
            
                int score=0;
                int tot =0;
            
            for (int i = 0; i < N; i++) {
                if (A.charAt(i) == '1' || B.charAt(i) == '1') {
                    score++;
                }
                if(A.charAt(i)=='1' && B.charAt(i)=='0' || A.charAt(i)=='0' && B.charAt(i)=='1')
                tot++;
            }
            
            if (score % 2 == 1 || tot >0) {
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

## Binary Removals

<details>
<summary>Python</summary>

```python
import sys


def solve():
    n, x, k = map(int, input().split())
    s = input()

    inversions = 0
    ones = 0
    for i in range(n):
        if s[i] == '0':
            inversions += ones
        else:
            ones += 1

    operations = 1

    if inversions > x or inversions % k != 0:
        operations = 2

    return operations


def main():
    tests_cnt = int(input())
    for i in range(tests_cnt):
        print(solve())


if _name_ == '_main_':
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>

#define lil long long int
const int MOD = 1e9 + 7;
using namespace std;

int main() {
    
	int test;cin>>test;
	while(test--)
	{
	    lil n,x,k;cin>>n>>x>>k;
	    string s;
	    cin>>s;
	    
	    lil o=0,inv=0;
	    for(int i=0;i<n;i++)
	    {
	        if(s[i]=='1') o++;
	        else inv+=o;
	    }
	    
	    if(inv<=x && inv%k==0) cout<<"1\n";
	    else cout<<"2\n";
	    
	}

}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.io.*;

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        int t = Integer.parseInt(br.readLine());

        while (t-- > 0) {
            st = new StringTokenizer(br.readLine());
            long length = Long.parseLong(st.nextToken());
            long threshold = Long.parseLong(st.nextToken());
            long divisor = Long.parseLong(st.nextToken());

            String binaryString = br.readLine();

            long onesCount = 0, totalSum = 0;

            for (long i = 0; i < length; i++) {
                if (binaryString.charAt((int)i) == '1') {
                    onesCount++;
                } else {
                    totalSum += onesCount;
                }
            }

            if (totalSum <= threshold && totalSum % divisor == 0) {
                System.out.println(1);
            } else {
                System.out.println(2);
            }
        }
    }
}
```

</details>

## No Two Alike

<details>
<summary>Python</summary>

```python
from collections import defaultdict

def main():
    import sys
    input = sys.stdin.read
    data = input().split()

    index = 0
    T = int(data[index])
    index += 1

    results = []

    for _ in range(T):
        N = int(data[index])
        index += 1
        A = list(map(int, data[index:index + N]))
        index += N

        pos = {}
        for i in range(N):
            if A[i] not in pos:
                pos[A[i]] = [i, i]
            else:
                pos[A[i]][1] = i

        v = [value for value in pos.values() if value[0] != value[1]]

        if not v:
            results.append(0)
            continue

        v.sort()
        ans = 0
        l = v[0][0]
        r = v[0][1]
        s = set()

        for start, end in v:
            if start <= r:
                r = max(r, end)
            else:
                s = set(A[l:r + 1])
                ans += len(s)
                l = start
                r = end

        s = set(A[l:r + 1])
        ans += len(s)

        results.append(ans)

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
    int T; // Number of test cases
    cin >> T;

    while (T--) {
        int N; 
        cin >> N;
        vector<int> A(N); 
        for (int i = 0; i < N; ++i) {
            cin >> A[i];
        }

        map<int, pair<int, int>> pos; 
        vector<pair<int, int>> v;   
        for (int i = 0; i < N; ++i) {
            if (pos.find(A[i]) == pos.end()) {
                pos[A[i]] = {i, i};
            } else {
                pos[A[i]].second = i;
            }
        }
        for (auto& entry : pos) {
            if (entry.second.first != entry.second.second) {
                v.push_back(entry.second);
            }
        }

        if (v.empty()) {
            cout << 0 << endl;
            continue;
        }
        sort(v.begin(), v.end()); 
        int ans = 0;
        int l = v[0].first; 
        int r = v[0].second; 
        set<int> s;
        for (int i = 0; i < v.size(); ++i) {
            int start = v[i].first;
            int end = v[i].second;

            if (start <= r) {
                r = max(r, end);
            } else {
                for (int j = l; j <= r; ++j) {
                    s.insert(A[j]);
                }
                ans += s.size();
                s.clear();
                l = start;
                r = end;
            }
        }
        for (int j = l; j <= r; ++j) {
            s.insert(A[j]);
        }
        ans += s.size();

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
        Scanner scanner = new Scanner(System.in);
        int T = scanner.nextInt(); // Number of test cases

        while (T-- > 0) {
            int N = scanner.nextInt();
            int[] A = new int[N];
            for (int i = 0; i < N; ++i) {
                A[i] = scanner.nextInt();
            }

            Map<Integer, int[]> pos = new HashMap<>();
            List<int[]> v = new ArrayList<>();
            for (int i = 0; i < N; ++i) {
                if (!pos.containsKey(A[i])) {
                    pos.put(A[i], new int[]{i, i});
                } else {
                    pos.get(A[i])[1] = i;
                }
            }
            for (Map.Entry<Integer, int[]> entry : pos.entrySet()) {
                if (entry.getValue()[0] != entry.getValue()[1]) {
                    v.add(entry.getValue());
                }
            }

            if (v.isEmpty()) {
                System.out.println(0);
                continue;
            }
            v.sort(Comparator.comparingInt(a -> a[0]));
            int ans = 0;
            int l = v.get(0)[0];
            int r = v.get(0)[1];
            Set<Integer> s = new HashSet<>();
            for (int i = 0; i < v.size(); ++i) {
                int start = v.get(i)[0];
                int end = v.get(i)[1];

                if (start <= r) {
                    r = Math.max(r, end);
                } else {
                    for (int j = l; j <= r; ++j) {
                        s.add(A[j]);
                    }
                    ans += s.size();
                    s.clear();
                    l = start;
                    r = end;
                }
            }
            for (int j = l; j <= r; ++j) {
                s.add(A[j]);
            }
            ans += s.size();

            System.out.println(ans);
        }

        scanner.close();
    }
}

```

</details>

## 1. Ratio by 2

<details>
<summary>Python</summary>

```python
t = int(input())
for i in range(t):
    x,y = map(int, input().split())
    if(x >= 2*y or y >= 2*x):
        print(0)
    else:
        if x < y:
            x, y = y, x 
        ans = (2*y-x+2-1)//2
        print(ans)
    
    t -= 1
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
    int x,y;
    cin >> x >> y;
    if(x >= 2*y or y >= 2*x){
        cout << 0 << '\n';
        return;
    }
    int ans = 0;
    if(x < y){
        swap(x,y);
    }
    ans = (2*y - x + 2 - 1)/2;
    cout << ans << '\n';
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
import java.util.Scanner;

public class Main {
    
    public static void solve(Scanner sc) {
        int x = sc.nextInt();
        int y = sc.nextInt();
        
        if (x >= 2 * y || y >= 2 * x) {
            System.out.println(0);
            return;
        }
        if (x < y) {
            int temp = x;
            x = y;
            y = temp;
        }
        
        int ans = (2 * y - x + 1) / 2;
        System.out.println(ans);
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

## 2. Find Multiset State

<details>
<summary>Python</summary>

```python
import sys
input = sys.stdin.read

def main():
    data = input().split()
    idx = 0
    t = int(data[idx])
    idx += 1
    result = []
    
    for _ in range(t):
        b = int(data[idx])
        q = int(data[idx + 1])
        idx += 2
        
        A = list(map(int, data[idx:idx + b]))
        idx += b
        
        S = sum(A[:q])
        A[-1] += S
        
        result.append(' '.join(map(str, A[q:])))
    
    sys.stdout.write('\n'.join(result) + '\n')

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <numeric>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int b, q;
        cin >> b >> q;
        int A[b];
        for (int i = 0; i < b; ++i) {
            cin >> A[i];
        }
        int S = accumulate(A, A + q, 0);
        A[b - 1] += S;
        for (int i = q; i < b; ++i) {
            if (i > q) 
                cout << " "; 
            cout << A[i];
        }
        cout << endl;
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while (t-- > 0) {
            int b = sc.nextInt();
            int q = sc.nextInt();
            int[] A = new int[b];
            
            for (int i = 0; i < b; ++i) {
                A[i] = sc.nextInt();
            }
            
            int S = 0;
            for (int i = 0; i < q; ++i) {
                S += A[i];
            }
            
            A[b - 1] += S;
            
            for (int i = q; i < b; ++i) {
                if (i > q)
                    System.out.print(" ");
                System.out.print(A[i]);
            }
            
            System.out.println();
        }
        
        sc.close();
    }
}
```

</details>

## 3. Equal Pairs(Easy)

<details>
<summary>Python</summary>

```python
import sys
input = sys.stdin.read

def main():
    data = input().split()
    index = 0
    t = int(data[index])
    index += 1
    
    results = []
    
    while t > 0:
        t -= 1
        n = int(data[index])
        index += 1
        v = list(map(int, data[index:index + n]))
        index += n
        
        store = [0] * 101
        
        for i in range(n):
            store[v[i]] += 1
        
        zero_count = store[0]
        max_freq = 0
        max_value = -1
        
        for i in range(1, 101):
            if store[i] > max_freq:
                max_freq = store[i]
                max_value = i
        
        max_freq += zero_count
        max_freq -= 1
        result = max_freq * (max_freq + 1) // 2
        
        for i in range(1, 101):
            if i != max_value:
                result += (store[i] * (store[i] - 1)) // 2
        
        results.append(str(result))
    
    sys.stdout.write("\n".join(results) + "\n")

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long

int32_t main() {
    int t; 
    cin >> t;
    while (t--) {
        int n; 
        cin >> n; 
        vector<int> v(n);
        vector<int> store(101, 0);
        
        for (int i = 0; i < n; i++) {
            cin >> v[i];
            store[v[i]]++;
        }
        
        int zeroCount = store[0];
        int maxFreq = 0, maxValue = -1;
        
        for (int i = 1; i <= 100; i++) {
            if (store[i] > maxFreq) {
                maxFreq = store[i];
                maxValue = i;
            }
        }
        
        maxFreq += zeroCount;
        maxFreq--;
        int result = maxFreq * (maxFreq + 1) / 2;
        
        for (int i = 1; i <= 100; i++) {
            if (i != maxValue) {
                result += (store[i] * (store[i] - 1)) / 2;
            }
        }
        
        cout << result << endl;
    }
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while (t-- > 0) {
            int n = sc.nextInt();
            int[] v = new int[n];
            int[] store = new int[101];
            
            for (int i = 0; i < n; i++) {
                v[i] = sc.nextInt();
                store[v[i]]++;
            }
            
            int zeroCount = store[0];
            int maxFreq = 0, maxValue = -1;
            
            for (int i = 1; i <= 100; i++) {
                if (store[i] > maxFreq) {
                    maxFreq = store[i];
                    maxValue = i;
                }
            }
            
            maxFreq += zeroCount;
            maxFreq--;
            long result = (long) maxFreq * (maxFreq + 1) / 2;
            
            for (int i = 1; i <= 100; i++) {
                if (i != maxValue) {
                    result += (long) store[i] * (store[i] - 1) / 2;
                }
            }
            
            System.out.println(result);
        }
        
        sc.close();
    }
}
```

</details>

## 4. Equal Pairs (Hard)

<details>
<summary>Python</summary>

```python
t = int(input())

for _ in range(t):
    n = int(input())
    freq = [0] * (n+1)
    freq[0] = n
    maxi = 0
    maxel = -1
    ans = (n * (n-1))//2
    
    for _ in range(n):
        x, y = map(int, input().split())
        freq[y] += 1
        freq[0] -= 1
        
        if freq[y] > maxi:
            if y == maxel:
                maxi = freq[y]
            else:
                maxi = freq[y]
                maxel = y
        
        else:
            ans -= freq[0] + maxi
            ans += freq[y] - 1
        
        print(ans, end = ' ')
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>

using namespace std;


void solve() {
    long long n;
    cin >> n;
    vector <int> cnt(200001);
    cnt[0] = n;
    long long max = 0, maxel = -1;
    long long sum = n*(n-1)/2;
    while (n--) {
        long long x, y;
        cin >> x >> y;
        cnt[y] += 1;
        
        cnt[0] -= 1;

        if (cnt[y]>max){
            if (y==maxel){
                max = cnt[y];
            }
            else {
                max = cnt[y];
                maxel = y;
            }
        }
        else {
            sum += cnt[y]-1;
            sum -= cnt[0]+max;
        }
        
        cout << sum << ' ';
    }
    cout << endl;   
}

int main () {
    ios_base :: sync_with_stdio(false);
    cin.tie(0);
    int t;
    cin >> t;
    while (t--) {
        solve();
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

    public static void solve(Scanner scanner) {
        long n = scanner.nextLong();
        int[] cnt = new int[200001];
        cnt[0] = (int) n;
        long max = 0;
        long maxel = -1;
        long sum = n * (n - 1) / 2;

        while (n-- > 0) {
            long x = scanner.nextLong();
            long y = scanner.nextLong();
            cnt[(int) y] += 1;
            cnt[0] -= 1;

            if (cnt[(int) y] > max) {
                if (y == maxel) {
                    max = cnt[(int) y];
                } else {
                    max = cnt[(int) y];
                    maxel = y;
                }
            } else {
                sum += cnt[(int) y] - 1;
                sum -= cnt[0] + max;
            }

            System.out.print(sum + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            solve(scanner);
        }
        scanner.close();
    }
}

```

</details>

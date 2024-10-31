# Codechef_starters_158_Div3

<!-- First Question -->
#  Even vs Odd Divisors
<details>
<summary>Python</summary>

```python
T = int(input())

for _ in range(T):
    N = int(input())
    f = 0  
    g = 0  

    for i in range(1, N + 1):
        if N % i == 0:
            if i % 2 == 0:
                f += 1
            else:
                g += 1

    if f > g:
        print("1")
    elif f == g:
        print("0")
    else:
        print("-1")

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <stdio.h>

int main() {
    int T;
    scanf("%d", &T);
    
    while (T--) {
        int N;
        scanf("%d", &N);
        
        int f = 0, g = 0;
        
        for (int i = 1; i <= N; i++) {
            if (N % i == 0) {
                if (i % 2 == 0) {
                    f++;
                } else {
                    g++;
                }
            }
        }
        
        if (f > g) {
            printf("1\n");
        } else if (f == g) {
            printf("0\n");
        } else {
            printf("-1\n");
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
        Scanner scanner = new Scanner(System.in);
        int T = scanner.nextInt();

        while (T-- > 0) {
            int N = scanner.nextInt();
            int f = 0, g = 0;

            for (int i = 1; i <= N; i++) {
                if (N % i == 0) {
                    if (i % 2 == 0) {
                        f++;
                    } else {
                        g++;
                    }
                }
            }

            if (f > g) {
                System.out.println("1");
            } else if (f == g) {
                System.out.println("0");
            } else {
                System.out.println("-1");
            }
        }
        
        scanner.close();
    }
}
```
</details>

<!-- Second Question -->
# Largest Subsequence

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    a = input().strip()
    ans = 0
    
    for i in range(n):
        if a[i] == a[0]:
            ans = max(ans, i + 1)
        if a[i] == a[-1]:
            ans = max(ans, n - i)
    
    print(ans)

t = int(input())
for _ in range(t):
    solve() 

```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include <bits/stdc++.h>
using namespace std;


void solve() {
    int n;
    string a;
    cin >> n >> a;
    int ans = 0;
    for (int i = 0; i < n; i++) {
        if (a[i] == a[0])
            ans = max(ans, i + 1);
        if (a[i] == a[n - 1])
            ans = max(ans, n - i);
    }
    cout << ans << endl;
}


int main() {
    int t;
    cin >> t;
    while (t--) {
    solve();
    }
    return 0;
}
```

</details>
<!-- Java -->
<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {
    public static void solve() {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String a = sc.next();
        int ans = 0;
        
        for (int i = 0; i < n; i++) {
            if (a.charAt(i) == a.charAt(0))
                ans = Math.max(ans, i + 1);
            if (a.charAt(i) == a.charAt(n - 1))
                ans = Math.max(ans, n - i);
        }
        
        System.out.println(ans);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            solve();
        }
        sc.close();
    }
}

```
</details>

<!-- Third Quesion -->
# XOR Smaller

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    nums = list(map(int, input().split()))

    and_result = nums[0]
    for num in nums:
        and_result &= num

    result = 0
    for bit in range(31):
        if and_result & (1 << bit):
            result += (1 << bit)
    
    print(result)

test_cases = int(input())
for _ in range(test_cases):
    solve()

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
#define CODE ios::sync_with_stdio(false); cin.tie(0);
using namespace std;

void solve() {
    int n;
    cin >> n;

    vector<int> nums(n);
    for (int &num : nums) cin >> num;

    int andResult = nums[0];
    for (int num : nums) {
        andResult &= num;
    }

    long long result = 0;
    for (int bit = 0; bit < 31; ++bit) {
        if (andResult & (1 << bit)) {
            result += (1LL << bit);
        }
    }

    cout << result << "\n";
}

int main() {

    CODE
    
    int testCases;
    cin >> testCases;
    
    while (testCases--) {
        solve();
    }

    return 0;
}
```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {
    public static void solve(Scanner sc) {
        int n = sc.nextInt();
        int[] nums = new int[n];
        
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int andResult = nums[0];
        for (int num : nums) {
            andResult &= num;
        }

        long result = 0;
        for (int bit = 0; bit < 31; bit++) {
            if ((andResult & (1 << bit)) != 0) {
                result += (1L << bit);
            }
        }

        System.out.println(result);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int testCases = sc.nextInt();
        
        while (testCases-- > 0) {
            solve(sc);
        }
        
        sc.close();
    }
}
```
</details>

<!-- Fourth Question -->
# Buying Game

<details>
    <summary>Python</summary>

```python
t = int(input())

for _ in range(t):
    n = int(input())
    
    a = list(map(int,input().split()))
    b = list(map(int, input().split()))

    res = 0
    arr = []
    
    for i in range(n):
        if b[i] < a[i]:
            res += b[i]
        else:
            arr += [i]
    
    if len(arr) > 1:
        for i in arr:
            res += a[i]
    elif len(arr) == 1:
        index = arr[0]
        res += b[index]
        ans = res
        
        for i in range(n):
            if i != index:
                ans2 = ans + a[i] - b[i] + a[index] - b[index]
                res = min(res, ans2)
    
    print(res)

```
</details>


<details>
  	<summary>C++</summary>
  
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;

    while (t--) {
        int n;
        cin >> n;
        
        vector<int> a(n), b(n);
        for (int i = 0; i < n; i++) cin >> a[i];
        for (int i = 0; i < n; i++) cin >> b[i];

        long long res = 0;
        vector<int> arr;
        
        for (int i = 0; i < n; i++) {
            if (b[i] < a[i]) {
                res += b[i];
            } else {
                arr.push_back(i);
            }
        }
        
        if (arr.size() > 1) {
            for (int i : arr) {
                res += a[i];
            }
        } else if (arr.size() == 1) {
            int index = arr[0];
            res += b[index];
            long long ans = res;

            for (int i = 0; i < n; i++) {
                if (i != index) {
                    long long ans2 = ans + a[i] - b[i] + a[index] - b[index];
                    res = min(res, ans2);
                }
            }
        }
        
        cout << res << endl;
    }

    return 0;
}

```
</details>


<details>
	<summary>JAVA</summary>
  
```java
import java.util.*;
import java.io.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            int[] a = new int[n];
            int[] b = new int[n];

            for (int i = 0; i < n; i++) a[i] = scanner.nextInt();
            for (int i = 0; i < n; i++) b[i] = scanner.nextInt();

            long res = 0;
            List<Integer> arr = new ArrayList<>();
            
            for (int i = 0; i < n; i++) {
                if (b[i] < a[i]) {
                    res += b[i];
                } else {
                    arr.add(i);
                }
            }
            
            if (arr.size() > 1) {
                for (int i : arr) {
                    res += a[i];
                }
            } else if (arr.size() == 1) {
                int index = arr.get(0);
                res += b[index];
                long ans = res;

                for (int i = 0; i < n; i++) {
                    if (i != index) {
                        long ans2 = ans + a[i] - b[i] + a[index] - b[index];
                        res = Math.min(res, ans2);
                    }
                }
            }
            
            System.out.println(res);
        }
        
        scanner.close();
    }
}

```
</details>


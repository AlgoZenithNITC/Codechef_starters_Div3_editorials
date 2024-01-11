# Codechef_starters_116_Div3

# Hattrick
<details>
<summary>Python</summary>

```python
#if there three W's consecutively then the bowler will have hattrick
t = int(input())
while t>0:
    s = input()
    ns = "".join(s.split())
    count = 0
    flag = 0
    for i in ns:
        if i == 'W':
            count+=1
        else:
            count = 0
        if count>=3:#checking if wickets are consecutive
            flag = 1
            print("YES")
            break
    if flag == 0:
        print("NO")
    t-=1
```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
    int t;
    cin >> t;
    while(t--) {
        char a[6];
            
        for (int i = 0; i < 6; i++)
            cin >> a[i];
        int count = 1;
        for (int j = 0; j < 5; j++) {
            if (a[j] == a[j + 1] && a[j] == 'W')
                count++;
            else
                count = 1;
                
            if (count == 3) {
                cout << "YES\n";
                break;
            }
        }
        if (count != 3)
            cout << "NO\n";
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
        int t = scanner.nextInt();

        while (t-- > 0) {
            char[] a = new char[6];
            for (int i = 0; i < 6; i++) {
                a[i] = scanner.next().charAt(0); // Read a single character
            }

            int count = 1;
            for (int j = 0; j < 5; j++) {
                if (a[j] == a[j + 1] && a[j] == 'W') {
                    count++;
                } else {
                    count = 1;
                }

                if (count == 3) {
                    System.out.println("YES");
                    break;
                }
            }

            if (count != 3) {
                System.out.println("NO");
            }
        }
    }
}

```
</details>

<!-- Second Question -->
# Access Control

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n,x = map(int,input().split())
    s = input()
    count = 0
    flag = 0
    for i in s:
        if i == '0' and count == 0:#if you have and you cant renew 
            print("NO")#print no as you cant reach next door
            flag = 1
            break
        elif i == '0' and count>0:
            count-=1
        else:
            count = x#as you should renew when s[i] == 1
    if flag == 0:
        print("YES")
```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
    int t;
    cin >> t;
    while (t--) {
        // 	n - renewals, x - no. of swipes
        int n, x;
        cin >> n >> x;
        
        string s;
        cin >> s;
        
        int swipes = 0;
        
        for (auto i : s) {
            if (i == '0')
                swipes--;
            else
                swipes = x;
            
            if (swipes < 0) {
                cout << "no\n";
                break;
            }
        }
        if (swipes >= 0)
            cout << "Yes\n";
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
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();  // Number of renewals
            int x = scanner.nextInt();  // Number of swipes
            String s = scanner.next();  // String of 0s and 1s

            int swipes = 0;

            for (char i : s.toCharArray()) {  // Iterate through characters
                if (i == '0') {
                    swipes--;
                } else {
                    swipes = x;
                }

                if (swipes < 0) {
                    System.out.println("no");
                    break;
                }
            }

            if (swipes >= 0) {
                System.out.println("Yes");
            }
        }
    }
}
```
</details>

# ORST

<details>
<summary>Python</summary>

```python
#we should sort last b[i] numbers in array a
t = int(input())
for _ in range(t):
    n,m = map(int,input().split())
    s = input()
    elements = s.split()
    a = [int(i) for i in elements]
    s = input()
    elements = s.split()
    b = [int(i) for i in elements]
    x = max(b)
    #instead of sorting for every last b[i] numbers just
    #sort for maximum number in b so every length below that maximum number
    #will also be sorted 
    ans = []
    for i in range(n-x):
        ans.append(a[i])#numbers that will not be sorted
    ans2 = []
    for i in range(n-x,n):
        ans2.append(a[i])
    ans2.sort()#sorting the remaining numbers
    fa = ans+ans2
    for i in fa:
        print(i,end = ' ')
    print()
```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
    int t;
    cin >> t;
    
    while (t--) {
        int n, m;
        cin >> n >> m;
        
        int a[n], b;
        
        int b_max = 0;
        
        for (int i = 0; i < n; i++)
            cin >> a[i];

        for (int i = 0; i < m; i++) {
            cin >> b;
            b_max = max(b_max, b);
        }
        
        sort(a+(n-b_max), a+n);
        
        for (int i = 0; i < n; i++)
            cout << a[i] << " ";
        cout << endl;
    }
    return 0;
}
```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();  // Number of elements in array a
            int m = scanner.nextInt();  // Number of elements in array b
            int[] a = new int[n];      // Array a
            int b_max = 0;            // Maximum value in array b

            // Read array a
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
            }

            // Find maximum value in array b
            for (int i = 0; i < m; i++) {
                int b = scanner.nextInt();
                b_max = Math.max(b_max, b);
            }

            // Sort the last b_max elements of array a
            Arrays.sort(a, n - b_max, n);

            // Print the sorted array a
            for (int i = 0; i < n; i++) {
                System.out.print(a[i] + " ");
            }
            System.out.println();
        }
    }
}
```
</details>

# Chef Product

<details>
    <summary>Python</summary>

```python
#***for some reasons sqrt function is not working of python users***
#so use isqrt funtion instead sqrt function which rounds to nearest integer
import math
t = int(input())
for _ in range(t):
    n = int(input())#set can be only formed by odd numbers as product of odd numbers is always odd
    if n%2 == 1:#if its odd the number of odd numbers should be odd 
        ans = int(math.isqrt(n))#nearst odd number whose sum is odd
        if ans%2 == 0:
            ans-=1
        print(((ans-1)//2)+1)
    if n%2 == 0:#if even number of odd numbers should be even
        ans = int(math.isqrt(n))
        print(ans//2)
```
</details>


<details>
  	<summary>C++</summary>
  
```cpp
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    int t;
    cin >> t;

    for (int _ = 0; _ < t; _++) {
        int n;
        cin >> n;

        if (n % 2 == 1) {
            int ans = int(sqrt(n));  // Use sqrt for nearest integer rounding in C++
            if (ans % 2 == 0) {
                ans--;
            }
            cout << ((ans - 1) / 2 + 1) << endl;
        } else {
            int ans = int(sqrt(n));
            cout << ans / 2 << endl;
        }
    }

    return 0;
}
```
</details>


<details>
	<summary>JAVA</summary>
  
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        for (int i = 0; i < t; i++) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            int K = Math.min(n, k - 1);
            if (K == 0) {
                System.out.println(K);
                continue;
            }
            int a = (n - K) % k;
            int b = (K / 2) + (K % 2);
            System.out.println(b + a / 2);
        }
    }
}
```
</details>

# Exact Savings

<details>
<summary>Python</summary>
  
```python
import sys

# Use sys.maxsize for infinity
INF = sys.maxsize

def min_subset_sum(i, j, x, a, dp):
    if i == 0:
        return 0 if j == 0 else INF

    if dp[i][j] != -1:
        return dp[i][j]

    dp[i][j] = min(min_subset_sum(i - 1, j, x, a, dp),
                   min_subset_sum(i - 1, (j - a[i - 1]) % x + x) % x, x, a, dp) + a[i - 1])
    return dp[i][j]

def solve():
    n, x, z = map(int, input().split())
    a = list(map(int, input().split()))

    if z % x == 0:
        print(z // x)
        return

    dp = [[-1] * x for _ in range(n + 1)]
    req = z % x
    result = min_subset_sum(n, x - req, x, a, dp)

    if result == INF:
        print(-1)
    else:
        print((z + result) // x)

t = 1  # Assuming a single test case
while t > 0:
    solve()
    t -= 1

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include "bits/stdc++.h"
// the code is entire idea how the dp for better understanding it is presented in top down approach
// But if it is changed by any value it is giving a TLE
// Better use top down approch by refering this
using namespace std;

#define int long long int
#define double long double
#define endl '\n'

const int MOD = 1000000007;
const int inf = 1ll << 60;

vector<vector<int>> dp;

int minSubsetSum(int i, int j, int x, vector<int>& a) {
    if (i == 0) {
        return (j == 0) ? 0 : inf;
        // if the amount we want is cancelling out return zero or return inf
    }

    if (dp[i][j] != -1) {
        return dp[i][j];
    }

    dp[i][j] = min(minSubsetSum(i - 1, j, x, a),
        minSubsetSum(i - 1, ((j - a[i - 1]) % x + x) % x, x, a) + a[i - 1]);
    //return the minimum sum such that we will get our remainder

    return dp[i][j];
}

void solve() {
    int n, x, z;
    cin >> n >> x >> z;
    //z is exact savings he want
    //x is money he is getting hourly
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    if (z % x == 0) {
        cout << z / x << endl;
        return;
    }

    // initialize dp table with -1
    dp.assign(n + 1, vector<int>(x, -1));

    int req = z % x;
    //if he is not getting his exact savings he is getting some extra money(remainder)
    // we should exhaust the extra money by purchasing some toys so that 
    // his savings+purchase value is divible by x and is minimum
    // if savings is not divible by x then z%x is the extra part we had
    int result = minSubsetSum(n, x - req, x, a);
    //return some subset sum such that when divided by x it will have remainder rem
    if (result == inf) {
        cout << -1 << endl;
    }
    else {
        cout << (z + result) / x << endl;
    }
}

int main()
{
    int t = 1;
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
import java.util.*;

public class Main {
    static final int INF = Integer.MAX_VALUE;
    static int[][] dp;

    static int minSubsetSum(int i, int j, int x, int[] a) {
        if (i == 0) {
            return j == 0 ? 0 : INF;
        }

        if (dp[i][j] != -1) {
            return dp[i][j];
        }

        dp[i][j] = Math.min(minSubsetSum(i - 1, j, x, a),
                minSubsetSum(i - 1, ((j - a[i - 1]) % x + x) % x, x, a) + a[i - 1]);
        return dp[i][j];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = 1;  // Assuming a single test case
        while (t > 0) {
            int n = scanner.nextInt();
            int x = scanner.nextInt();
            int z = scanner.nextInt();
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
            }

            if (z % x == 0) {
                System.out.println(z / x);
                continue;
            }

            dp = new int[n + 1][x];
            for (int[] row : dp) {
                Arrays.fill(row, -1);
            }

            int req = z % x;
            int result = minSubsetSum(n, x - req, x, a);

            if (result == INF) {
                System.out.println(-1);
            } else {
                System.out.println((z + result) / x);
            }
            t--;
        }
    }
}
```
</details>

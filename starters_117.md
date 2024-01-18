# Codechef_starters_117_Div3

<!-- First Question -->
# Weapon Choice
<details>
<summary>Python</summary>

```python
import math
t = int(input())
for _ in range(t):
    h,x,y1,y2,k = map(int,input().split())
    c1 = math.ceil(h/x)
    if y1<=x:
        print(c1)
        continue
    if y1*k>=h:
        print(math.ceil(h/y1))
    else:
        count = k
        h-=(y1*k)
        count+=(math.ceil(h/y2))
        print(min(count,c1))
```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <cmath>

using namespace std;

/**
 * @brief Calculates the minimum hits needed to defeat a boss with given weapons and health.
 * 
 * @param h The boss's health.
 * @param x The gun's damage per hit.
 * @param y1 The laser's initial damage per hit.
 * @param y2 The laser's lowered damage per hit.
 * @param k The threshold of laser hits before output drops.
 * @return The minimum number of hits needed to defeat the boss.
 */
int calculateMinHits() {

    int h, x, y1, y2, k;
    
    cin >> h >> x >> y1 >> y2 >> k;
    
    int gunHits = ceil((double)h / x); // Minimum hits needed with the gun

    // If laser's initial damage is less than or equal to gun damage, use gun
    if (y1 <= x) {
        return gunHits;
    }

    // If laser can defeat the boss within its threshold, use laser
    if (y1 * k >= h) {
        return ceil((double)h / y1); 
    }

    // Calculate hits needed after laser's output drops
    int laserHits = k + ceil((double)(h - (y1 * k)) / y2);

    // Return the minimum of gun hits and laser hits
    return min(gunHits, laserHits);
}

int main() {
    int t;
    cin >> t;

    while (t--) {

        cout << calculateMinHits(h, x, y1, y2, k) << endl;
    }

    return 0;
}
```
</details>


<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class ChefAndBoss {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int h = scanner.nextInt();
            int x = scanner.nextInt();
            int y1 = scanner.nextInt();
            int y2 = scanner.nextInt();
            int k = scanner.nextInt();

            int gunHits = (int) Math.ceil((double) h / x);

            if (y1 <= x) {
                System.out.println(gunHits);
                continue;
            }

            if (y1 * k >= h) {
                System.out.println((int) Math.ceil((double) h / y1));
            } else {
                int laserHits = k + (int) Math.ceil((double) (h - (y1 * k)) / y2);
                System.out.println(Math.min(gunHits, laserHits));
            }
        }
    }
}
```
</details>

<!-- Second Question -->
# Spell Shortening

<details>
<summary>Python</summary>

```python
import sys

def lexicographic_string():
    t = int(sys.stdin.readline())

    for _ in range(t):
        n = int(sys.stdin.readline())
        v = sys.stdin.readline().strip()

        max_index = -1
        for i in range(1, n):
            if v[i - 1] > v[i]:
                max_index = i - 1
                break

        if max_index == -1:
            max_index = n - 1

        v = v[:max_index] + v[max_index + 1:]
        print(v)

if __name__ == "__main__":
    lexicographic_string()

```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	/**
	 * t - testcases
     * n - size of the string
     * v - input string
	 */
    int t;
    cin >> t;
    
    while (t--) {
        int n;
        cin >> n;
        
        string v;
        cin >> v;
        
        /**
         * The Logic :
         * ---------
         * - The lexicographically least string after removing a character, is what we are after
         * - consider the examples in the testcases
         *      ab, if the string is already lexographically sorted
         *      What we can do is remove the largest character so we
         *      can have the lexicographically short string
         *      
         *      ex : abeg --> abe;
         *           defgh --> defh;
         *      
         *      Any other character removal results in rather larger string
         * 
         * - if we happen to find characters that are not in lexographically sorted order, what
         *   we can do is find the first out of order character and remove it, so that the operation
         *   results in a lexigraphically small string 
         *      ex : magic --> agic, 1st out of order `m > a`
         *           author --> athor 1st out of order `u > t` 
         */

        // the max element out of found `out of order` pair
        int max_index = -1;
        
        for (int i = 1; i < n; i++) {
            if (v[i - 1] > v[i]) {
                max_index = i - 1;
                break;
            }
        }
        
        if (max_index == -1)
            max_index = n - 1;
        
        v.erase(v.begin() + max_index);
        
        cout << v << endl;
        
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

public class LexicographicString {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            String v = scanner.next();

            int maxIndex = -1;
            for (int i = 1; i < n; i++) {
                if (v.charAt(i - 1) > v.charAt(i)) {
                    maxIndex = i - 1;
                    break;
                }
            }

            if (maxIndex == -1) {
                maxIndex = n - 1;
            }

            StringBuilder sb = new StringBuilder(v);
            sb.deleteCharAt(maxIndex);
            v = sb.toString();

            System.out.println(v);
        }
    }
}

```
</details>

<!-- Third Quesion -->
# Not Prime Permutation

<details>
<summary>Python</summary>

```python
import sys

def non_prime_permutation():
    t = int(sys.stdin.readline())

    for _ in range(t):
        n = int(sys.stdin.readline())
        v = list(map(int, sys.stdin.readline().split()))

        if n <= 2:
            print(-1)
            continue

        for i in v:
            print(3 if i == 1 else 1 if i == 3 else i, end=" ")
        print()

if __name__ == "__main__":
    non_prime_permutation()

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
        
        int n;
        cin >> n;
        
        vector<int> v(n);
        
        for (auto & i : v) {
            cin >> i;
        }

        /**
         * @brief 
         * 
         * The Logic :
         * *********
         * 
         * The permutation possible here to make the given permutation's
         * combo sum a non-prime is --> Adding itself to every element. Now
         * the sum has a factor 2 making it a non prime
         * 
         * However this has a down side
         * 
         * in the case of element 1, if we add it to itself we get 2, which
         * is prime
         *      so every time we get 1 we print 3 making it's sum 4
         *      and at 3 we print 1, making the sum again as 4
         * 
         * if the size of permutation is less than or equal to 2 we don't
         * have the luxury of doing the swap any more. so print -1 
         * 
         */
        
        if (n <= 2) {
            cout << "-1" << endl;
            continue;
        }
        
        vector<int> t = v;
        
        for (auto i : v) {
            if (i == 1)
                cout << 3 << " ";
            else if (i == 3)
                cout << 1 << " ";
            else 
                cout << i << " ";
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
import java.util.ArrayList;
import java.util.Scanner;

public class NonPrimePermutation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            ArrayList<Integer> v = new ArrayList<>();

            for (int i = 0; i < n; i++) {
                v.add(scanner.nextInt());
            }

            if (n <= 2) {
                System.out.println("-1");
                continue;
            }

            for (int i : v) {
                System.out.print((i == 1) ? 3 : (i == 3) ? 1 : i + " ");
            }
            System.out.println();
        }
    }
}
```
</details>

<!-- Fourth Question -->
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

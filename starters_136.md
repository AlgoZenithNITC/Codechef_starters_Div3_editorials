## 1. Even Sum Subarray

<details>
<summary>Python</summary>

```python
def solve():
    """
    Solves a single test case for finding the maximum length subarray with even sum.

    Reads input for array size, array elements, and calculates the length of the
    maximum subarray with even sum.
    """
    n = int(input())
    a = [int(x) for x in input().split()]
    sum = sum(a)

    l, r = 0, n - 1
    left_sum, right_sum = sum, sum

    # Find closest odd element from right
    while left_sum % 2 != 0 and r >= 0:
        left_sum -= a[r]
        r -= 1

    # Find closest odd element from left
    while right_sum % 2 != 0 and l < n:
        right_sum -= a[l]
        l += 1

    # Print the length of the maximum subarray with even sum
    print(max(r + 1, n - l))

def main():
    """
    Driver function to read the number of test cases and call solve for each.
    """
    t = int(input())
    for _ in range(t):
        solve()

if __name__ == "__main__":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

/**
 * @brief helper function to solve
 *        an individual test case
 */
void solve() {
    int n;
    
    cin >> n;
    
    int a[n], sum = 0;
    
    for (int i = 0; i < n; i++) {
        cin >> a[i];
        sum += a[i];
    }
    
    int l, r, leftSum = sum, rightSum = sum;
    
    for (r = n - 1; leftSum % 2; r--) {
        leftSum -= a[r];
    }
    
    for (l = 0; rightSum % 2; l++) {
        rightSum -= a[l];
    }
    
    cout << max(r + 1, n - l) << endl;
}

/**
 * @brief Driver Code
 * 
 * @return int 
 */
int main() {
	// your code goes here

    int t;
    cin >> t;

    while (t--)
    {
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

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while (t-- > 0) {
            solve(sc);
        }

        sc.close();
    }

    public static void solve(Scanner sc) {
        int n = sc.nextInt();
        int[] a = new int[n];
        int sum = 0;

        for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
            sum += a[i];
        }

        int l = 0, r = n - 1;
        int leftSum = sum, rightSum = sum;

        // Find closest odd element from right
        while (leftSum % 2 != 0 && r >= 0) {
            leftSum -= a[r];
            r--;
        }

        // Find closest odd element from left
        while (rightSum % 2 != 0 && l < n) {
            rightSum -= a[l];
            l++;
        }

        // Output the length of the maximum subarray with even sum
        System.out.println(Math.max(r + 1, n - l));
    }
};
```

</details>

## 2. My First Geometry Problem

<details>
<summary>Python</summary>

```python
def main():
    """
    Reads the number of test cases, processes each case, and prints the answer.
    """
    t = int(input())

    for _ in range(t):
        s = input()  # Read entire line for string input
        count_ones = 0
        for char in s:
            if char == '1':
                count_ones += 1

        if count_ones == 1:
            print(11)
        elif count_ones == 2:
            if (s[0] == '1' and s[1] == '1') or (s[2] == '1' and s[3] == '1'):
                print(21)
            else:
                print(121)
        elif count_ones == 3:
            print(231)
        else:
            print(441)

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
	cin >> t;
	while(t--){
	    string s;
	    cin >> s;
	    
	    int onecount = 0;
	    
	    for(int i = 0;i<4;i++){
	        if(s[i]=='1')onecount++;
	    }
	    
	    if(onecount == 1){
	        cout << 11 << endl;
	    }
	    else if(onecount == 2){
	        if((s[0] == '1' && s[1] == '1') || (s[2] == '1' && s[3] == '1')){
	            cout << 21 << endl;
	        }
	        else{
	            cout << 121 << endl;
	        }
	    }
	    else if(onecount == 3){
	        cout << 231 << endl;
	    }
	    else{
	        cout << 441 << endl;
	    }
	}

}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while (t-- > 0) {
            String s = sc.nextLine(); // Read entire line for string input

            int countOnes = 0;
            for (int i = 0; i < 4; i++) {
                if (s.charAt(i) == '1') {
                    countOnes++;
                }
            }

            if (countOnes == 1) {
                System.out.println(11);
            } else if (countOnes == 2) {
                if ((s.charAt(0) == '1' && s.charAt(1) == '1') || (s.charAt(2) == '1' && s.charAt(3) == '1')) {
                    System.out.println(21);
                } else {
                    System.out.println(121);
                }
            } else if (countOnes == 3) {
                System.out.println(231);
            } else {
                System.out.println(441);
            }
        }

        sc.close();
    }
}
```

</details>

## 3. Sum of Modes

<details>
<summary>Python</summary>

```python
from collections import defaultdict
for _ in range(int(input())):
    n = int(input())
    s = input()
    ans = (n*(n+1))//2 # as every substring will have 1 contribution
    total = 0
    d = defaultdict(int)
    d[0] = 1
    for i in s:
        if i == '1':
            total+=1
        else:
            total-=1
        ans+=d[total]
        d[total]+=1
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <unordered_map>
#include <string>

using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        string s;
        cin >> s;
        long long ans = (long long)n * (n + 1) / 2;
        int total = 0;
        unordered_map<int, int> map;
        map[0] = 1;
        for (char c : s) {
            if (c == '1') {
                total += 1;
            } else {
                total -= 1;
            }
            ans += map[total];
            map[total]++;
        }
        cout << ans << endl;
    }
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.HashMap;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            scanner.nextLine(); // Consume the newline
            String s = scanner.nextLine();
            long ans = (long) n * (n + 1) / 2;
            int total = 0;
            HashMap<Integer, Integer> map = new HashMap<>();
            map.put(0, 1);
            for (int i = 0; i < s.length(); i++) {
                if (s.charAt(i) == '1') {
                    total += 1;
                } else {
                    total -= 1;
                }
                ans += map.getOrDefault(total, 0);
                map.put(total, map.getOrDefault(total, 0) + 1);
            }
            System.out.println(ans);
        }
        scanner.close();
    }
}

```

</details>

## 4. Sum of Max K Subarray

<details>
<summary>Python</summary>

```python
mod = (10**9)+7
fac = [0]*(10**6)
fac[0] = 1
for i in range(1,10**6):
    fac[i] = (fac[i-1]*i)%mod
for _ in range(int(input())):
    n = int(input())
    for i in range(1,n+1):
        temp = n//i
        rem = n%i
        ans = (fac[temp]*fac[n-temp])%mod
        ans = (ans*(i-rem))%mod
        print(ans,end = ' ')
    print()
       
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#define MOD 1000000007
#define MAX 1000000

using namespace std;

vector<long long> fac(MAX);

void precompute_factorials() {
    fac[0] = 1;
    for (int i = 1; i < MAX; i++) {
        fac[i] = (fac[i - 1] * i) % MOD;
    }
}

int main() {
    precompute_factorials();

    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        for (int i = 1; i <= n; i++) {
            int temp = n / i;
            int rem = n % i;
            long long ans = (fac[temp] * fac[n - temp]) % MOD;
            ans = (ans * (i - rem)) % MOD;
            cout << ans << " ";
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
import java.util.Scanner;

public class Main {
    static final int MOD = (int) (1e9 + 7);
    static final int MAX = (int) (1e6);
    static long[] fac = new long[MAX];

    static {
        fac[0] = 1;
        for (int i = 1; i < MAX; i++) {
            fac[i] = (fac[i - 1] * i) % MOD;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            for (int i = 1; i <= n; i++) {
                int temp = n / i;
                int rem = n % i;
                long ans = (fac[temp] * fac[n - temp]) % MOD;
                ans = (ans * (i - rem)) % MOD;
                System.out.print(ans + " ");
            }
            System.out.println();
        }
        scanner.close();
    }
}

```

</details>

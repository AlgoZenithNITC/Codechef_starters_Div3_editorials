## 1. Spell Splice

<details>
<summary>Python</summary>

```Python
for _ in range(int(input())):
    n = int(input())
    l = []
    for i in range(n):
        a,b = map(int,input().split())
        l.append((a,b))
    ans = 0
    for i in range(n):
        for j in range(i+1,n):
            ans = max(ans,l[i][1]*l[j][0]+l[j][1]*l[i][0])
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```Cpp
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
        vector<pair<int, int>> l(n);
        for (int i = 0; i < n; ++i) {
            int a, b;
            cin >> a >> b;
            l[i] = make_pair(a, b);
        }
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                ans = max(ans, l[i].second * l[j].first + l[j].second * l[i].first);
            }
        }
        cout << ans << endl;
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
            int[][] l = new int[n][2];
            for (int i = 0; i < n; i++) {
                l[i][0] = scanner.nextInt();
                l[i][1] = scanner.nextInt();
            }
            int ans = 0;
            for (int i = 0; i < n; i++) {
                for (int j = i + 1; j < n; j++) {
                    ans = Math.max(ans, l[i][1] * l[j][0] + l[j][1] * l[i][0]);
                }
            }
            System.out.println(ans);
        }
        scanner.close();
    }
}

```

</details>

## 2. Large Differences

<details>
<summary>Python</summary>

```Python
for _ in range(int(input())):
    n,k = map(int,input().split())
    a = list(map(int,input().split()))
    ans = 0
    def f(ind,num):
        res = 0
        for i in range(1,n):
            temp1 = a[i] if i != ind else num
            temp2 = a[i-1] if i-1 != ind else num
            res+=abs(temp1-temp2)
        return res
        
    for i in range(n):
        ans = max(ans,f(i,1))
        ans = max(ans,f(i,k))
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

using namespace std;

int f(const vector<int>& a, int n, int ind, int num) {
    int res = 0;
    for (int i = 1; i < n; ++i) {
        int temp1 = (i != ind) ? a[i] : num;
        int temp2 = (i - 1 != ind) ? a[i - 1] : num;
        res += abs(temp1 - temp2);
    }
    return res;
}

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, k;
        cin >> n >> k;
        vector<int> a(n);
        for (int i = 0; i < n; ++i) {
            cin >> a[i];
        }
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            ans = max(ans, f(a, n, i, 1));
            ans = max(ans, f(a, n, i, k));
        }
        cout << ans << endl;
    }
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```Java
import Java.util.Scanner;

public class Solution {
    public static int f(int[] a, int n, int ind, int num) {
        int res = 0;
        for (int i = 1; i < n; i++) {
            int temp1 = (i != ind) ? a[i] : num;
            int temp2 = (i - 1 != ind) ? a[i - 1] : num;
            res += Math.abs(temp1 - temp2);
        }
        return res;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = scanner.nextInt();
            }
            int ans = 0;
            for (int i = 0; i < n; i++) {
                ans = Math.max(ans, f(a, n, i, 1));
                ans = Math.max(ans, f(a, n, i, k));
            }
            System.out.println(ans);
        }
        scanner.close();
    }
}

```

</details>

## 3. Double Trouble

<details>
<summary>Python</summary>

```Python
def solve(n):
    x = list(map(int,input().split()))
    p = list(map(int,input().split()))
    if n == 2:
        return True
    left = [1]*n #activations i nedd if go in the left direction
    right = [1]*n #activations i need if go in the right direction
    for i in range(1,n):
        if x[i-1]+p[i-1] >= x[i]:
            right[i] = right[i-1]
        else:
            right[i] = right[i-1]+1
    for i in range(n-1,0,-1):
        if x[i]-p[i]<= x[i-1]:
            left[i-1] = left[i]
        else:
            left[i-1] = left[i]+1
    if right[-1]<=2 or left[0]<=2:#case1 and case2 if all balls goes right or left
        return True
    for i in range(1,n):
        if left[i-1]+right[i] <=2 or right[i-1]+left[i]<=2:
            return True
        if left[0] == left[i-1] and right[i] == right[-1]:
            return True
    return False
        
    
                    
for _ in range(int(input())):
    if solve(int(input())):
        print('YES')
    else:
        print('NO')
```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <iostream>
#include <vector>

using namespace std;

bool solve(int n) {
    vector<int> x(n), p(n);
    for (int i = 0; i < n; ++i) {
        cin >> x[i];
    }
    for (int i = 0; i < n; ++i) {
        cin >> p[i];
    }
    if (n == 2) {
        return true;
    }
    vector<int> left(n, 1);  // activations needed if go in the left direction
    vector<int> right(n, 1); // activations needed if go in the right direction
    for (int i = 1; i < n; ++i) {
        if (x[i - 1] + p[i - 1] >= x[i]) {
            right[i] = right[i - 1];
        } else {
            right[i] = right[i - 1] + 1;
        }
    }
    for (int i = n - 1; i > 0; --i) {
        if (x[i] - p[i] <= x[i - 1]) {
            left[i - 1] = left[i];
        } else {
            left[i - 1] = left[i] + 1;
        }
    }
    if (right[n - 1] <= 2 || left[0] <= 2) {
        return true;
    }
    for (int i = 1; i < n; ++i) {
        if (left[i - 1] + right[i] <= 2 || right[i - 1] + left[i] <= 2) {
            return true;
        }
        if (left[0] == left[i - 1] && right[i] == right[n - 1]) {
            return true;
        }
    }
    return false;
}

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        if (solve(n)) {
            cout << "YES" << endl;
        } else {
            cout << "NO" << endl;
        }
    }
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```Java
import Java.util.Scanner;

public class Solution {
    public static boolean solve(int n) {
        Scanner scanner = new Scanner(System.in);
        int[] x = new int[n];
        int[] p = new int[n];
        for (int i = 0; i < n; i++) {
            x[i] = scanner.nextInt();
        }
        for (int i = 0; i < n; i++) {
            p[i] = scanner.nextInt();
        }
        if (n == 2) {
            return true;
        }
        int[] left = new int[n];  // activations needed if go in the left direction
        int[] right = new int[n]; // activations needed if go in the right direction
        for (int i = 0; i < n; i++) {
            left[i] = 1;
            right[i] = 1;
        }
        for (int i = 1; i < n; i++) {
            if (x[i - 1] + p[i - 1] >= x[i]) {
                right[i] = right[i - 1];
            } else {
                right[i] = right[i - 1] + 1;
            }
        }
        for (int i = n - 1; i > 0; i--) {
            if (x[i] - p[i] <= x[i - 1]) {
                left[i - 1] = left[i];
            } else {
                left[i - 1] = left[i] + 1;
            }
        }
        if (right[n - 1] <= 2 || left[0] <= 2) {
            return true;
        }
        for (int i = 1; i < n; i++) {
            if (left[i - 1] + right[i] <= 2 || right[i - 1] + left[i] <= 2) {
                return true;
            }
            if (left[0] == left[i - 1] && right[i] == right[n - 1]) {
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            if (solve(n)) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
    }
}

```

</details>

## 4. Speedrun

<details>
<summary>Python</summary>

```Python
def solve(n, k):
    a = list(map(int, input().split()))
    h = list(map(int, input().split()))

    # Check where the cumulative sum of h exceeds a
    ind = -1
    prev = 0
    for i in range(n):
        prev += h[i]
        if prev > a[i]:
            ind = i
            break

    # If no such index exists, return True
    if ind == -1:
        return True

    # Find the range to reset health
    ind2 = n - 1
    for i in range(ind, n):
        if a[i] - a[ind] > 2 * k:
            ind2 = i - 1
            break

    # Reset health in 2*k range
    for i in range(ind2,-1,-1):
        if a[ind2]-a[i] > 2*k:
            break
        h[i] = 0

    # Check again after reset
    prev = 0
    for i in range(n):
        prev += h[i]
        if prev > a[i]:
            return False

    return True

# Read input and solve for each test case
for _ in range(int(input())):
    n, k = map(int, input().split())
    if solve(n, k):
        print('YES')
    else:
        print('NO')


```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <iostream>
#include <vector>

using namespace std;

bool solve(int n, int k) {
    vector<int> a(n), h(n);

    // Input a and h
    for (int i = 0; i < n; ++i) {
        cin >> a[i];
    }
    for (int i = 0; i < n; ++i) {
        cin >> h[i];
    }

    // Check where the cumulative sum of h exceeds a
    int ind = -1, prev = 0;
    for (int i = 0; i < n; ++i) {
        prev += h[i];
        if (prev > a[i]) {
            ind = i;
            break;
        }
    }

    // If no such index exists, return true
    if (ind == -1) {
        return true;
    }

    // Find the range to reset health
    int ind2 = n - 1;
    for (int i = ind; i < n; ++i) {
        if (a[i] - a[ind] > 2 * k) {
            ind2 = i - 1;
            break;
        }
    }

    // Reset health in 2*k range
    for (int i = ind2; i >= 0; --i) {
        if (a[ind2] - a[i] > 2 * k) {
            break;
        }
        h[i] = 0;
    }

    // Check again after reset
    prev = 0;
    for (int i = 0; i < n; ++i) {
        prev += h[i];
        if (prev > a[i]) {
            return false;
        }
    }

    return true;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);

    int t;
    cin >> t;
    while (t--) {
        int n, k;
        cin >> n >> k;
        if (solve(n, k)) {
            cout << "YES\n";
        } else {
            cout << "NO\n";
        }
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
    public static boolean solve(int n, int k, int[] a, int[] h) {
        // Check where the cumulative sum of h exceeds a
        int ind = -1, prev = 0;
        for (int i = 0; i < n; ++i) {
            prev += h[i];
            if (prev > a[i]) {
                ind = i;
                break;
            }
        }

        // If no such index exists, return true
        if (ind == -1) {
            return true;
        }

        // Find the range to reset health
        int ind2 = n - 1;
        for (int i = ind; i < n; ++i) {
            if (a[i] - a[ind] > 2 * k) {
                ind2 = i - 1;
                break;
            }
        }

        // Reset health in 2*k range
        for (int i = ind2; i >= 0; --i) {
            if (a[ind2] - a[i] > 2 * k) {
                break;
            }
            h[i] = 0;
        }

        // Check again after reset
        prev = 0;
        for (int i = 0; i < n; ++i) {
            prev += h[i];
            if (prev > a[i]) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            int[] a = new int[n];
            int[] h = new int[n];
            for (int i = 0; i < n; ++i) {
                a[i] = scanner.nextInt();
            }
            for (int i = 0; i < n; ++i) {
                h[i] = scanner.nextInt();
            }
            if (solve(n, k, a, h)) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
        scanner.close();
    }
}

```

</details>

## 1. Knockout Tournament

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    s = list(map(int, input().split()))
    indices = list(range(16))
    indices.sort(key = lambda x: s[x])
    ans = [0]*16

    nxt, cur = 1, 0
    for i in range(1, 17):
        ans[indices[i-1]] = cur
        if i == nxt:
            cur += 1
            nxt = 2*nxt + 1
    print(*ans)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int numTests;
    cin >> numTests;

    while (numTests--) {
        vector<int> s(16);
        vector<int> indices(16);
        iota(indices.begin(), indices.end(), 0);

        for (int i = 0; i < 16; ++i) {
            cin >> s[i];
        }

        sort(indices.begin(), indices.end(), [&](int x, int y) {
            return s[x] < s[y];
        });

        vector<int> ans(16, 0);
        int nxt = 1, cur = 0;

        for (int i = 1; i <= 16; ++i) {
            ans[indices[i-1]] = cur;
            if (i == nxt) {
                cur++;
                nxt = 2 * nxt + 1;
            }
        }

        for (int i = 0; i < 16; ++i) {
            cout << ans[i] << " ";
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

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int numTests = sc.nextInt();

        while (numTests-- > 0) {
            int[] s = new int[16];
            Integer[] indices = new Integer[16];
            for (int i = 0; i < 16; i++) {
                s[i] = sc.nextInt();
                indices[i] = i;
            }

            Arrays.sort(indices, new Comparator<Integer>() {
                public int compare(Integer x, Integer y) {
                    return Integer.compare(s[x], s[y]);
                }
            });

            int[] ans = new int[16];
            int nxt = 1, cur = 0;

            for (int i = 1; i <= 16; i++) {
                ans[indices[i-1]] = cur;
                if (i == nxt) {
                    cur++;
                    nxt = 2 * nxt + 1;
                }
            }

            for (int i = 0; i < 16; i++) {
                System.out.print(ans[i] + " ");
            }
            System.out.println();
        }

        sc.close();
    }
}

```

</details>

## 2. Bouncing Ball

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = list(map(int, input().split()))
    pref = a[:]
    for i in range(1, n):
        pref[i] += pref[i-1]
    
    ans = 0
    for i in range(1, n-1):
        if a[i] != 0: continue
        if pref[i-1] - (pref[n-1] - pref[i]) == 0: ans += 2
        elif abs(pref[i-1] - (pref[n-1] - pref[i])) == 1: ans += 1
    if sum(a) == 0: ans += 4 # account for 1 and N
    print(ans)

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

    while (t--) {
        int n;
        cin >> n;
        vector<int> a(n);
        vector<int> pref(n);

        for (int i = 0; i < n; ++i) {
            cin >> a[i];
            pref[i] = a[i];
        }

        // Calculate prefix sums
        for (int i = 1; i < n; ++i) {
            pref[i] += pref[i-1];
        }

        int ans = 0;
        for (int i = 1; i < n-1; ++i) {
            if (a[i] != 0) continue;
            int left_sum = pref[i-1];
            int right_sum = pref[n-1] - pref[i];
            if (left_sum - right_sum == 0) {
                ans += 2;
            } else if (abs(left_sum - right_sum) == 1) {
                ans += 1;
            }
        }

        if (pref[n-1] == 0) { // sum(a) == 0
            ans += 4; // account for 1 and N
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
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            int[] a = new int[n];
            int[] pref = new int[n];

            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
                pref[i] = a[i];
            }

            // Calculate prefix sums
            for (int i = 1; i < n; i++) {
                pref[i] += pref[i-1];
            }

            int ans = 0;
            for (int i = 1; i < n-1; i++) {
                if (a[i] != 0) continue;
                int leftSum = pref[i-1];
                int rightSum = pref[n-1] - pref[i];
                if (leftSum - rightSum == 0) {
                    ans += 2;
                } else if (Math.abs(leftSum - rightSum) == 1) {
                    ans += 1;
                }
            }

            if (pref[n-1] == 0) { // sum(a) == 0
                ans += 4; // account for 1 and N
            }

            System.out.println(ans);
        }

        sc.close();
    }
}

```

</details>

## 3. Back Front

<details>
<summary>Python</summary>

```python
def solve(s, pattern):
    n, m = len(s), len(pattern)
    ct = [0]*(m+1)
    ct[0] = 10**9
    for i in range(n):
        for j in range(m):
            if s[i] == pattern[j]:
                if ct[j] > 0:
                    ct[j] -= 1
                    ct[j+1] += 1
    i = 0
    while i < ct[m]:
        for j in reversed(range(m)):
            if ct[j] > 0:
                ct[j] -= 1
                ct[j+1] += 1
                break
        i += 1
    return (m-1)*ct[m]

for _ in range(int(input())):
    n = int(input())
    s = input()
    print(n - solve(s, 'front') - solve(s[::-1], 'kcab'))
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int solve(const string &s, const string &pattern) {
    int n = s.length(), m = pattern.length();
    vector<int> ct(m+1, 0);
    ct[0] = 1e9;

    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            if (s[i] == pattern[j]) {
                if (ct[j] > 0) {
                    ct[j]--;
                    ct[j+1]++;
                }
            }
        }
    }

    int i = 0;
    while (i < ct[m]) {
        for (int j = m - 1; j >= 0; --j) {
            if (ct[j] > 0) {
                ct[j]--;
                ct[j+1]++;
                break;
            }
        }
        i++;
    }

    return (m - 1) * ct[m];
}

int main() {
    int t;
    cin >> t;

    while (t--) {
        int n;
        string s;
        cin >> n >> s;
        int result = n - solve(s, "front") - solve(string(s.rbegin(), s.rend()), "kcab");
        cout << result << endl;
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

    public static int solve(String s, String pattern) {
        int n = s.length(), m = pattern.length();
        int[] ct = new int[m + 1];
        Arrays.fill(ct, 0);
        ct[0] = (int) 1e9;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (s.charAt(i) == pattern.charAt(j)) {
                    if (ct[j] > 0) {
                        ct[j]--;
                        ct[j + 1]++;
                    }
                }
            }
        }

        int i = 0;
        while (i < ct[m]) {
            for (int j = m - 1; j >= 0; j--) {
                if (ct[j] > 0) {
                    ct[j]--;
                    ct[j + 1]++;
                    break;
                }
            }
            i++;
        }

        return (m - 1) * ct[m];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            String s = sc.next();
            int result = n - solve(s, "front") - solve(new StringBuilder(s).reverse().toString(), "kcab");
            System.out.println(result);
        }

        sc.close();
    }
}

```
</details>
## 4. Permutation Construction

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    
    for _ in range(t):
        n = int(input())
        i = 1
        j = (n + 3) // 2
        
        while i < ((n + 3) // 2) or j <= n:
            if i < ((n + 3) // 2):
                print(i, end=" ")
                i += 1
            if j <= n:
                print(j, end=" ")
                j += 1
        print()

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
	// your code goes here
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        int i=1;
        int j = (n+3)/2;
        while(i<((n+3)/2) || j<=n){
            if(i<(n+3)/2) cout<<i++<<" ";
            if(j<=n) cout<<j++<<" ";
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
        
        while (t-- > 0) {
            int n = scanner.nextInt();
            int i = 1;
            int j = (n + 3) / 2;
            
            while (i < ((n + 3) / 2) || j <= n) {
                if (i < ((n + 3) / 2)) {
                    System.out.print(i++ + " ");
                }
                if (j <= n) {
                    System.out.print(j++ + " ");
                }
            }
            System.out.println();
        }
        
        scanner.close();
    }
}

```

</details>

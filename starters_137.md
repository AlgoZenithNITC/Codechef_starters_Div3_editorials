## Question - 1

<details>
<summary>Python</summary>

```python

```

</details>

<details>
<summary>Cpp</summary>

```cpp

```

</details>

<details>
<summary>Java</summary>

```java

```

</details>

## Question - 2

<details>
<summary>Python</summary>

```python

```

</details>

<details>
<summary>Cpp</summary>

```cpp

```

</details>

<details>
<summary>Java</summary>

```java

```

</details>

## 3. Double Trouble

<details>
<summary>Python</summary>

```python
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

```cpp
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

```java
import java.util.Scanner;

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

## Question - 4

<details>
<summary>Python</summary>

```python

```

</details>

<details>
<summary>Cpp</summary>

```cpp

```

</details>

<details>
<summary>Java</summary>

```java

```

</details>

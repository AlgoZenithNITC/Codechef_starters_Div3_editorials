## .Long Queue

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())  # Number of people in the queue
    a = list(map(int, input().split()))  # Wealth of each person in the queue
    pos = n - 1  # Sushil's initial position (last person in the queue)
    
    # Simulate bullying process
    while pos > 0:
        if a[n - 1] >= 2 * a[pos - 1]:  # Check if Sushil can bully the person in front
            pos -= 1  # Move Sushil forward by bullying the person in front
        else:
            break  # Stop if bullying is not possible
    
    print(pos + 1)  # Output the final position (1-based index)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int t;
    cin >> t;  // Number of test cases

    while (t--) {
        int n;
        cin >> n;  // Number of people in the queue
        vector<int> a(n);

        for (int i = 0; i < n; i++) {
            cin >> a[i];  // Wealth of each person in the queue
        }

        int pos = n - 1;  // Sushil's initial position (last person)
        
        // Simulate Sushil's bullying process
        while (pos > 0) {
            if (a[n - 1] >= 2 * a[pos - 1]) {
                pos--;  // Bully the person in front and move forward
            } else {
                break;  // Stop if bullying is not possible
            }
        }

        cout << pos + 1 << endl;  // Output final position (1-based indexing)
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
        
        int t = sc.nextInt();  // Number of test cases
        
        while (t-- > 0) {
            int n = sc.nextInt();  // Number of people in the queue
            int[] a = new int[n];  // Array to store wealth of each person
            
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();  // Input wealth of each person
            }

            int pos = n - 1;  // Sushil's initial position (last person)
            
            // Simulate bullying process
            while (pos > 0) {
                if (a[n - 1] >= 2 * a[pos - 1]) {
                    pos--;  // Bully the person in front and move forward
                } else {
                    break;  // Stop if bullying isn't possible
                }
            }

            System.out.println(pos + 1);  // Output final position (1-based indexing)
        }

        sc.close();

	}
}
```

</details>

## Even Numbers Hate

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    a = list(map(int, input().split()))
    odd, even = 0, 0
    
    for i in range(n):
        if a[i] % 2 == 0:
            even += 1
        else:
            odd += 1
    
    if odd == 0:
        print(0)
    else:
        print(even + (odd + 1) // 2)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int t;
    cin >> t;
    while(t--) {
        int n;
        cin >> n;
        vector<int> a(n);
        int odd = 0, even = 0;
        
        for(int i = 0; i < n; i++) {
            cin >> a[i];
            if(a[i] % 2 == 0) even++;
            else odd++;
        }
        
        if(odd == 0) cout << 0 << endl;
        else cout << even + (odd + 1) / 2 << endl;
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
        
        while(t-- > 0) {
            int n = sc.nextInt();
            int[] a = new int[n];
            int odd = 0, even = 0;
            
            for(int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
                if(a[i] % 2 == 0) even++;
                else odd++;
            }
            
            if(odd == 0) System.out.println(0);
            else System.out.println(even + (odd + 1) / 2);
        }
        sc.close();
    }
}

```

</details>

## Partition Score

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, k = map(int, input().split())
    a = sorted(list(map(int, input().split())))
    
    ans = a[0] + a[-1] + a[-2] + a[-k-1]
    if k == 1:
        ans = 2 * a[-1] + a[0] + a[-2]
    print(ans)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;
    while(t--) {
        int n, k;
        cin >> n >> k;
        vector<int> a(n);
        for(int i = 0; i < n; i++) {
            cin >> a[i];
        }
        
        sort(a.begin(), a.end());
        int ans = a[0] + a[n-1] + a[n-2] + a[n-k-1];
        if(k == 1) {
            ans = 2 * a[n-1] + a[0] + a[n-2];
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
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while(t-- > 0) {
            int n = sc.nextInt();
            int k = sc.nextInt();
            int[] a = new int[n];
            
            for(int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }
            
            Arrays.sort(a);
            int ans = a[0] + a[n-1] + a[n-2] + a[n-k-1];
            if(k == 1) {
                ans = 2 * a[n-1] + a[0] + a[n-2];
            }
            
            System.out.println(ans);
        }
        
        sc.close();
    }
}

```

</details>

## Count Triplets

<details>
<summary>Python</summary>

```python
import sys
input = sys.stdin.readline

for _ in range(int(input())):
    n = int(input())  # Size of array
    a = list(map(int, input().split()))  # Array elements
    ans = 0  # To store the count of valid triplets
    
    # Iterate over each i
    for i in range(n):
        # Check for k in the range [i - 105, i + 105] while keeping it within bounds
        for k in range(max(0, i - 105), min(n, i + 105)):
            indd = abs(k - i)  # Difference in indices
            eled = abs(a[i] - a[k])  # Difference in elements
            
            # Case 1: If the difference in indices equals the difference in elements
            if indd == eled:
                ans += abs(k - i) + 1  # Add the distance + 1 to the result
            # Case 2: If the difference in indices is less than the difference in elements
            elif indd < eled:
                # Try two possible values for j
                for j in (i + k + eled, i + k - eled):
                    if j % 2 == 0 and 0 <= j < 2 * n:
                        ans += 1  # Valid j found, increment the result
    
    print(ans)  # Output the result for the current test case
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

using namespace std;

void Solve() 
{
    int n;
    cin >> n;
    
    vector<int> a(n + 1);  // Array a of size n + 1 (1-based indexing)
    
    for (int i = 1; i <= n; i++) {
        cin >> a[i];  // Reading array elements
    }
    
    long long ans = 0;  // To store the count of valid triplets
    
    // Iterate over all possible pairs (i, j)
    for (int i = 1; i <= n; i++) {
        for (int j = max(i - 100, 1); j <= min(i + 100, n); j++) {
            int v = abs(a[i] - a[j]);  // Difference between a[i] and a[j]
            int m1 = min(i, j);  // Smaller index between i and j
            int m2 = max(i, j);  // Larger index between i and j
            int d = m2 - m1;  // Difference between the indices
            
            // Conditions to check based on the problem constraints
            if (d % 2 != v % 2 || v < d) continue;
            
            if (v == d) {
                ans += (m2 - m1 + 1);  // If valid, add the number of positions
                continue;
            }
            
            // Additional checks for edge cases
            if (v <= abs(1 - i) + abs(1 - j)) ans++;
            if (v <= abs(n - i) + abs(n - j)) ans++;
        }
    }
    
    cout << ans << "\n";  // Output the result for the current test case
}

int main() 
{
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    
    int t;
    cin >> t;  // Number of test cases
    
    for (int i = 1; i <= t; i++) 
    {
        Solve();  // Solve each test case
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
        int t = sc.nextInt();  // Number of test cases

        while (t-- > 0) {
            int n = sc.nextInt();  // Number of elements in the array

            int[] a = new int[n + 1];  // Array with 1-based indexing
            for (int i = 1; i <= n; i++) {
                a[i] = sc.nextInt();  // Reading array elements
            }

            long ans = 0;  // To store the count of valid triplets

            // Iterate over all possible pairs (i, j)
            for (int i = 1; i <= n; i++) {
                for (int j = Math.max(i - 100, 1); j <= Math.min(i + 100, n); j++) {
                    int v = Math.abs(a[i] - a[j]);  // Difference between a[i] and a[j]
                    int m1 = Math.min(i, j);  // Smaller index between i and j
                    int m2 = Math.max(i, j);  // Larger index between i and j
                    int d = m2 - m1;  // Difference between the indices

                    // Conditions to check based on the problem constraints
                    if (d % 2 != v % 2 || v < d) continue;

                    if (v == d) {
                        ans += (m2 - m1 + 1);  // If valid, add the number of positions
                        continue;
                    }

                    // Additional checks for edge cases
                    if (v <= Math.abs(1 - i) + Math.abs(1 - j)) ans++;
                    if (v <= Math.abs(n - i) + Math.abs(n - j)) ans++;
                }
            }

            System.out.println(ans);  // Output the result for the current test case
        }
        
        sc.close();
    }
}
```

</details>
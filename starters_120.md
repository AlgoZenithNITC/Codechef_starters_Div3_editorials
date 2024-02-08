# Codechef_starters_120_Div3

<!-- First Question -->

# Valentine Gifts

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
	cin>>t;
	while(t--)
	{
	    int x;
	    cin>>x;
	    if(x>=127)
	    cout<<"YES\n";
	    else
	    cout<<"NO\n";
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
            int x = scanner.nextInt();
            if (x >= 127) {
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

<details>
<summary>Python</summary>

```python
import sys
t = int(input())

for _ in range(t):
    x = int(input())
    if x >= 127:
        print("YES")
    else:
        print("NO")
```
</details>

# Largest K

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin>>t;
    while(t--)
    {
        int x,y;
        cin>>x>>y;
        int k = y/(x-1);
        cout<<k<<"\n";
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
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            int k = y / (x - 1);
            System.out.println(k);
        }
        scanner.close();
    }
}
```
</details>


<details>
<summary>Python</summary>

```python
import sys
t = int(input())
for _ in range(t):
    x, y = map(int, input().split())
    k = y // (x - 1)
    print(k)
```
</details>




# Sub or Swp

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin>>t;
    while(t--)
    {
        int x,y;
        cin>>x>>y;
        cout<<gcd(x,y)<<"\n";
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
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            System.out.println(gcd(x, y));
        }
        scanner.close();
    }

    private static int gcd(int x, int y) {
        while (y != 0) {
            int temp = y;
            y = x % y;
            x = temp;
        }
        return x;
    }
}
```
</details>

<details>
<summary>Python</summary>

```python
from math import gcd

t = int(input())
for _ in range(t):
    x, y = map(int, input().split())
    print(gcd(x, y))
```
</details>


# Count Subarrays

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t=0;
	cin>>t;
	while(t--){
	    int n; cin>>n;
	   vector<int> vect(n);
	   for(int i=0;i<n;i++){
	       cin>>vect[i];
	   }
	   vector<int>ans(n+1,1);
	   int sum =vect[0];
	   int s=0;
	   for(int i=1;i<n;i++){
	       sum+=vect[i];
	       while(sum>n){
	           sum-=vect[s++];
	       }
	      int temp=s;
	     int cum=sum;
	   while(i-temp){
	       ans[cum]++;
	       cum-=vect[temp++];
	   } 
	   }
	   for(int i=1;i<=n;i++){
	       cout<<ans[i]<<" ";
	   }
	   cout<<endl;
	}
    return 0;
}
```
</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Collections;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            ArrayList<Integer> vect = new ArrayList<>(Collections.nCopies(n, 0));
            for (int i = 0; i < n; i++) {
                vect.set(i, scanner.nextInt());
            }
            ArrayList<Integer> ans = new ArrayList<>(Collections.nCopies(n + 1, 1));
            int sum = vect.get(0);
            int s = 0;
            for (int i = 1; i < n; i++) {
                sum += vect.get(i);
                while (sum > n) {
                    sum -= vect.get(s++);
                }
                int temp = s;
                int cum = sum;
                while (i - temp > 0) {
                    ans.set(cum, ans.get(cum) + 1);
                    cum -= vect.get(temp++);
                }
            }
            for (int i = 1; i <= n; i++) {
                System.out.print(ans.get(i) + " ");
            }
            System.out.println();
        }
        scanner.close();
    }
}
```
</details>

<details>
<summary>Python</summary>

```python
# Importing the required library for taking input
from collections import deque

# Function to perform the operation
def process_test_cases(t):
    for _ in range(t):
        n = int(input())
        vect = [int(x) for x in input().split()]
        ans = [1] * (n + 1)
        sum = vect[0]
        s = 0
        for i in range(1, n):
            sum += vect[i]
            while sum > n:
                sum -= vect[s]
                s += 1
            temp = s
            cum = sum
            while i - temp:
                ans[cum] += 1
                cum -= vect[temp]
                temp += 1
        for i in range(1, n + 1):
            print(ans[i], end=" ")
        print()

# Taking the number of test cases as input
t = int(input())
process_test_cases(t)
```
</details>

# Find Permutation
<details>
<summary>Cpp</summary>

```cpp

#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm>

std::vector<int> find_permutation(int N, const std::vector<int>& A) {
    
    std::unordered_set<int> added;
    
    std::vector<int> P;
    
    for (auto it = A.rbegin(); it != A.rend(); ++it) {
        
        if (added.find(*it) == added.end()) {
            P.push_back(*it);
            added.insert(*it);
        }
    }
    
    return P;
}

int main() {
    int T;
    std::cin >> T;
    for (int i = 0; i < T; ++i) {
        int N;
        std::cin >> N;
        std::vector<int> A(N);
        for (int j = 0; j < N; ++j) {
            std::cin >> A[j];
        }
        std::vector<int> permutation = find_permutation(N, A);
        for (int num : permutation) {
            std::cout << num << " ";
        }
        std::cout << std::endl;
    }
    return 0;
}
```
</details>


<details>
<summary>Java</summary>

```java
import java.util.Scanner;
import java.util.LinkedHashSet;
import java.util.ArrayList;
import java.util.Collections;

public class Main {
    public static ArrayList<Integer> findPermutation(int N, ArrayList<Integer> A) {
        LinkedHashSet<Integer> added = new LinkedHashSet<>();
        ArrayList<Integer> P = new ArrayList<>();
        
        Collections.reverse(A);
        for (int num : A) {
            if (!added.contains(num)) {
                P.add(num);
                added.add(num);
            }
        }
        Collections.reverse(P);
        return P;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int T = Integer.parseInt(scanner.nextLine().trim());
        for (int i = 0; i < T; i++) {
            int N = Integer.parseInt(scanner.nextLine().trim());
            String[] input = scanner.nextLine().trim().split(" ");
            ArrayList<Integer> A = new ArrayList<>();
            for (String num : input) {
                A.add(Integer.parseInt(num));
            }
            ArrayList<Integer> permutation = findPermutation(N, A);
            for (int j = 0; j < permutation.size(); j++) {
                System.out.print(permutation.get(j));
                if (j < permutation.size() - 1) {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
        scanner.close();
    }
}
```
</details>

<details>
<summary>Python</summary>

```python
def find_permutation(N, A):
    # Initialize an empty set to keep track of elements added to the permutation
    added = set()
    
    # Initialize the permutation list
    P = []
    
    # Iterate over the elements of A in reverse order
    for num in reversed(A):
        # If the element hasn't been added previously, add it to the permutation
        if num not in added:
            P.append(num)
            added.add(num)
    
    # Return the permutation P
    return P

# Input
T = int(input().strip())  # Number of test cases

for _ in range(T):
    N = int(input().strip())  # Length of A
    A = list(map(int, input().strip().split()))  # Array A
    permutation = find_permutation(N, A)
    print(' '.join(map(str, permutation)))
```
</details>

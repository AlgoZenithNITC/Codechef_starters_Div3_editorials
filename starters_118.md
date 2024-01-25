# Codechef_starters_118_Div3

# Literacy Rate
<details>
<summary>Python</summary>

```python
t = int(input()) # number of test cases
while t > 0:
    t -= 1
    p, l = map(int, input().split()) # two integers
    l = l * 100 # convert to percentage
    l = l // p # integer division by p
    if l >= 75:
        print("YES")
    else:
        print("NO")

```
</details>

<details>
<summary>Cpp</summary>

```cpp

#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;
    cin>>t;
    while(t--)
    {
        int l,p;
        cin>>p>>l;
        l=l*100;
        l=l/p;
        if(l>=75)
        cout<<"YES\n";
        else
        cout<<"NO\n";
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); // number of test cases
        while (t-- > 0) {
            int p = sc.nextInt(); // first integer
            int l = sc.nextInt(); // second integer
            l = l * 100; // convert to percentage
            l = l / p; // divide by p
            if (l >= 75) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
        sc.close();
    }
}

```
</details>

<!-- Second Question -->
# Join States

<details>
<summary>Python</summary>

```python
t = int(input()) # number of test cases
while t > 0:
    t -= 1
    n, m = map(int, input().split()) # two integers
    a = list(map(int, input().split())) # array of n integers
    ans = 0 # count of sums
    sum = 0 # current sum
    for i in range(n):
        sum += a[i] # add element to sum
        if sum >= m: # check if sum is greater than or equal to m
            sum = 0 # reset sum
            ans += 1 # increment count
    print(ans) # print count for this test case

```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;
    cin>>t;
    while(t--)
    {
        int n,m;
        cin>>n>>m;
        int a[n];
        int ans=0;
        int sum=0;
        for(int i=0;i<n;i++)
        {
            cin>>a[i];
            sum+=a[i];
            if(sum >= m)
            {
                sum=0;
                ans++;
            }
        }
        cout<<ans<<endl;
    }
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); // number of test cases
        while (t-- > 0) {
            int n = sc.nextInt(); // first integer
            int m = sc.nextInt(); // second integer
            int[] a = new int[n]; // array of n integers
            int ans = 0; // count of sums
            int sum = 0; // current sum
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt(); // read element
                sum += a[i]; // add element to sum
                if (sum >= m) { // check if sum is greater than or equal to m
                    sum = 0; // reset sum
                    ans++; // increment count
                }
            }
            System.out.println(ans); // print count for this test case
        }
        sc.close();
    }
}

```
</details>

#  Subset GCD

<details>
<summary>Python</summary>

```python
t= int(input())
while t > 0:
    t -= 1
    n, k = map(int, input().split())
    i = 1
    while i <= n:
        if n // i >= k:
            i += 1
        else:
            break
    while k > 0:
        print((i - 1) * k, end=" ")
        k -= 1
    print()

```
</details>

<details>
<summary>Cpp</summary>

```cpp

#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;
    cin>>t;
    while(t--)
    {
        int n,k;
        cin>>n>>k;
        int i;
        for(i=1;i<=n;i++)
        {
            if(n/i >= k)
            continue;
            else
            break;
        }
        while(k>0)
        {
            cout<<(i-1)*(k)<<' ';
            k--;
        }
        cout<<endl;
    }
}
```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int n = sc.nextInt();
            int k = sc.nextInt();
            int i;
            for (i = 1; i <= n; i++) {
                if (n / i >= k)
                    continue;
                else
                    break;
            }
            while (k > 0) {
                System.out.print((i - 1) * (k) + " ");
                k--;
            }
            System.out.println();
        }
        sc.close();
    }
}

```
</details>

# Xorry 1

<details>
    <summary>Python</summary>

```python
import math

t = int(input())

while t > 0:
    x = int(input())

    nearest_power_of_2 = 2 ** int(math.log2(x))

    a = x - nearest_power_of_2
    b = nearest_power_of_2

    print(a, b)

    t -= 1
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

    while (t > 0) {
        int x;
        cin >> x;

        int nearest_power_of_2 = pow(2, static_cast<int>(log2(x)));

        int a = x - nearest_power_of_2;
        int b = nearest_power_of_2;

        cout << a << " " << b << endl;

        t--;
    }

    return 0;
}

```
</details>


<details>
	<summary>JAVA</summary>
  
```java

import java.util.Scanner;
import java.lang.Math;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t > 0) {
            int x = sc.nextInt();

            int nearest_power_of_2 = (int) Math.pow(2, (int) Math.log(x) / Math.log(2));

            int a = x - nearest_power_of_2;
            int b = nearest_power_of_2;

            System.out.println(a + " " + b);

            t--;
        }

        sc.close();
    }
}
```
</details>

# Xorry 2

<details>
<summary>Python</summary>
  
```python

t = int(input())

while t > 0:
    n = int(input())
    a = 1
    b = 0
    count = 0
    while a * 2 <= n:
        a = a * 2
        count += 1
    ans = 1
    check = False
    for i in range(count - 1, -1, -1):
        if n & (1 << i):
            b = b | (1 << i)
            check = True
        else:
            if check: ans = ans * 2
    print(ans)
    t -= 1

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include "bits/stdc++.h"
using namespace std;

#define int long long int
#define double long double
#define endl '\n'

const int MOD = 1000000007;

void solve(){
    int n;
    cin>>n;
    int a = 1;
    int b = 0;
    int count = 0;
    while (a*2<=n){
        a = a*2;
        count++;
    }
    int ans = 1;
    bool check = false;
    for (int i = count - 1; i >= 0; i--) {
        if ((n&1<<i)){
            b = b | (1<<i);
            check = true;
        } else {
            if (check) ans = ans * 2;
        }
    }
    cout<<ans<<endl;
}

signed main()
{
    int t;
    cin>>t;
    while(t--){
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

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t > 0) {
            int n = sc.nextInt();
            int a = 1;
            int b = 0;
            int count = 0;
            while (a * 2 <= n) {
                a = a * 2;
                count++;
            }
            int ans = 1;
            boolean check = false;
            for (int i = count - 1; i >= 0; i--) {
                if ((n & (1 << i)) != 0) {
                    b = b | (1 << i);
                    check = true;
                } else {
                    if (check) ans = ans * 2;
                }
            }
            System.out.println(ans);
            t--;
        }

        sc.close();
    }
}

```
</details>
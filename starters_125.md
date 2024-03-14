## 50-50 Rule

<details>
<summary>Python</summary>

```python
import sys

def main():
    t = int(sys.stdin.readline().strip())
    for _ in range(t):
        x, y = map(int, sys.stdin.readline().strip().split())
        if x < 50:
            print("Z")
        elif x >= 50 and y < 50:
            print("F")
        else:
            print("A")

if _name_ == "_main_":
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
	cin>>t;
    while(t--)
    {
        int x,y;
        cin>>x>>y;
        if(x<50)
        cout<<"Z\n";
        else if(x>=50 && y<50)
        cout<<"F\n";
        else
        cout<<"A\n";
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
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            if (x < 50)
                System.out.println("Z");
            else if (x >= 50 && y < 50)
                System.out.println("F");
            else
                System.out.println("A");
        }
    }
}
```

</details>

## Fake Certificate

<details>
<summary>Python</summary>

```python
import sys

def main():
    t = int(input())
    for _ in range(t):
        n = int(input())
        s = input()
        m = 0
        p = 0
        for c in s:
            if c == '0':
                m += 1
            else:
                m = 0
            p = max(m, p)
        m = s.count('1')
        print(m + p)

if _name_ == "_main_":
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
	cin>>t;
	while(t--)
	{
	    int n;
	    string s;
	    cin>>n>>s;
	    int m=0 , p=0;
	    for(char c : s)
	    {
	        if(c=='0')
	        m++;
	        else
	        m=0;
	        p=max(m,p);
	    }
	    m = count(s.begin(),s.end(),'1');
	    cout<<m+p<<"\n";
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
            String s = scanner.next();
            int m = 0, p = 0;
            for (char c : s.toCharArray()) {
                if (c == '0')
                    m++;
                else
                    m = 0;
                p = Math.max(m, p);
            }
            m = s.length() - s.replace("1", "").length();
            System.out.println(m + p);
        }
    }
}
```

</details>

## Binary Minimal

<details>
<summary>Python</summary>

```python
def solve(s, k):

  # Count the number of 1s in the string
  count_ones = s.count('1')

  # If the number of 1s is greater than k, replace the rightmost 1s with 0s until k is reached
  if count_ones > k:
    for i in range(len(s) - 1, -1, -1):
      if s[i] == '1' and k > 0:
        s = s[:i] + '0' + s[i+1:]
        k -= 1
    return s

  # If the number of 1s is less than or equal to k, replace all 1s with 0s and append (n-k) zeroes
  else:
    new_s = '0' * len(s)
    return new_s[:k] + '0' * (len(s) - k)

# Get input for number of test cases, string, and k
t = int(input())
while t > 0:
  s = input()
  k = int(input())
  result = solve(s, k)
  print(result)
  t -= 1

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;  cin >> t;
    while (t--) {
        int n,k;    cin >> n >> k;
        string s; cin >> s;
      
      vector<int> idx;
      int ct=0;
      
      for (int i=0;i<n;i++) {
        if (s[i] == '1') ct++;
      }
      
      if (ct >k) {
        for (int i=0;i<n;i++) {
          if (s[i]=='1' && k>0) {
            s[i]='0';
            k--;
          }
        }
        cout << s << endl;
      } else {
        for (int i=0;i<(n-k);i++) cout << 0;
        cout << endl;
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
    public static String solve(String s, int k) {
        // Count the number of 1s
        int countOnes = 0;
        for (char c : s.toCharArray()) {
            if (c == '1') {
                countOnes++;
            }
        }

        // If number of 1s is greater than k, replace rightmost 1s with 0s
        if (countOnes > k) {
            StringBuilder sb = new StringBuilder(s);
            for (int i = sb.length() - 1; i >= 0 && k > 0; i--) {
                if (sb.charAt(i) == '1') {
                    sb.setCharAt(i, '0');
                    k--;
                }
            }
            return sb.toString();
        }

        // If number of 1s is less than or equal to k, replace all 1s with 0s and append (n-k) zeroes
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < k; i++) {
            sb.append('0');
        }
        sb.append('0'.repeat(s.length() - k));
        return sb.toString();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            String s = sc.next();
            int

```

</details>

## Bucket Game

<details>
<summary>Python</summary>

```python
def solve():
  n = int(input())
  k = 0
  bob = 0
  alice = 0
  v = [int(input()) for _ in range(n)]
  for num in v:
    if num == 1:
      k += 1
  v.sort(reverse=True)
  ct = 0
  for i in range(n - k):
    if v[i] >= 2:
      ct += v[i] - 2

  if k % 2 == 1:  # Check if k is odd
    alice += (k + 1) // 2
    bob += k // 2
    if ct % 2 == 1:
      bob += n - k
    else:
      alice += n - k
  else:
    alice += k // 2
    bob += k // 2
    if ct % 2 == 1:
      alice += n - k
    else:
      bob += n - k

  if bob > alice:
    print("Bob")
  elif bob == alice:
    print("Draw")
  else:
    print("Alice")

t = int(input())
while t > 0:
  solve()
  t -= 1

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb push_back
#define all(v) v.begin(), v.end()

void solve()
{
    ll n;
    cin >> n;

    ll k = 0;

    ll bob = 0,
       alice = 0;
    vector<ll> v(n);
    for (ll i = 0; i < n; i++)
    {
        cin >> v[i];
        if (v[i] == 1)
        {
            k++;
        }
    }

    sort(all(v), greater<int>());

    ll ct = 0;
    for (int i = 0; i < n - k; i++)
    {
        if (v[i] >= 2)
        {
            ct += v[i] - 2;
        }
    }

    if (k & 1)
    {
        alice += (k + 1) / 2;
        bob += k / 2;

        if (ct & 1)
        {

            bob += n - k;
        }
        else
        {

            alice += (n - k);
        }
    }
    else
    {
        alice += (k) / 2;
        bob += k / 2;

        if (ct & 1)
        {
            alice += (n - k);
        }
        else
        {
            bob += (n - k);
        }
    }

    if (bob > alice)
    {
        cout << "Bob" << endl;
    }
    else if (bob == alice)
    {
        cout << "Draw" << endl;
    }
    else
    {
        cout << "Alice" << endl;
    }
}

int main()
{
    // fast io
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);

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
  public static void solve() {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();
    int k = 0;
    int bob = 0;
    int alice = 0;
    Integer[] v = new Integer[n];
    for (int i = 0; i < n; i++) {
      v[i] = sc.nextInt();
      if (v[i] == 1) {
        k++;
      }
    }
    Arrays.sort(v, Collections.reverseOrder());
    int ct = 0;
    for (int i = 0; i < n - k; i++) {
      if (v[i] >= 2) {
        ct += v[i] - 2;
      }
    }

    if (k % 2 == 1) {
      alice += (k + 1) / 2;
      bob += k / 2;
      if (ct % 2 == 1) {
        bob += n - k;
      } else {
        alice += n - k;
      }
    } else {
      alice += k / 2;
      bob += k / 2;
      if (ct % 2 == 1) {
        alice += n - k;
      } else {
        bob += n - k;
      }
    }

    if (bob > alice) {
      System.out.println("Bob");
    } else if (bob == alice) {
      System.out.println("Draw");
    } else {
      System.out.println("Alice");
    }
  }

  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int t = sc.nextInt();
    while (t-- > 0) {
      solve();
    }
  }
}
```

</details>

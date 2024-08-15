## Independence Day 101

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    a, b, c = map(int, input().split())
    print('Yes' if 2*max(a, b, c) <= a+b+c+1 else 'No')
```

</details>

<details>
<summary>Cpp</summary>
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int a, b, c;
        cin >> a >> b >> c;
        int max_val = max({a, b, c});
        if (2 * max_val <= a + b + c + 1) {
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
    }
    return 0;
}

```cpp

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
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            int c = scanner.nextInt();
            int max_val = Math.max(a, Math.max(b, c));
            if (2 * max_val <= a + b + c + 1) {
                System.out.println("Yes");
            } else {
                System.out.println("No");
            }
        }
        scanner.close();
    }
}

```

</details>

## Truth Teller And Liars 101

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, m = map(int, input().split())
    if n <= m: print(-1)
    else: print(2*m + 1)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        if (n <= m) {
            cout << -1 << endl;
        } else {
            cout << 2 * m + 1 << endl;
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

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int m = scanner.nextInt();
            if (n <= m) {
                System.out.println(-1);
            } else {
                System.out.println(2 * m + 1);
            }
        }
        scanner.close();
    }
}

```

</details>

## Gold Coins 101

<details>
<summary>Python</summary>

```python
# cook your dish here
a,b,x,y = map(int, input().split())
if x > y:
    print(a)
else:
    print(b)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a,b,x,y;
    cin >> a >> b >> x >> y;
    if(x > y){
        cout << a << '\n';
    }
    else{
        cout << b << '\n';
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
        
        int a = sc.nextInt();
        int b = sc.nextInt();
        int x = sc.nextInt();
        int y = sc.nextInt();
        
        if (x > y) {
            System.out.println(a);
        } else {
            System.out.println(b);
        }

        sc.close();
    }
}

```

</details>

## Non-Primes 101

<details>
<summary>Python</summary>

```python
def sieve_of_eratosthenes(limit):
    sieve = [True] * (limit + 1)
    sieve[0] = sieve[1] = False
    for i in range(2, int(limit ** 0.5) + 1):
        if sieve[i]:
            for j in range(i * i, limit + 1, i):
                sieve[j] = False
    return sieve

def main():
    M_SUM = 200
    isp = sieve_of_eratosthenes(M_SUM)
    
    t = int(input())
    for _ in range(t):
        n = int(input())
        a = list(map(int, input().split()))
        freq = [0] * 101
        
        for num in a:
            freq[num] += 1
        
        found = False
        for i in range(1, 101):
            if found:
                break
            for j in range(i, 101):
                if freq[i] > 0 and freq[j] > 0:
                    if i != j or freq[i] > 1:
                        if not isp[i + j]:
                            x, y = -1, -1
                            for k in range(n):
                                if a[k] == i and x == -1:
                                    x = k
                                elif a[k] == j and (y == -1 or y == x):
                                    y = k
                                if x != -1 and y != -1 and x != y:
                                    print(x + 1, y + 1)
                                    found = True
                                    break
                            if found:
                                break
        if not found:
            print(-1)

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

const int M_SUM = 200;


vector<bool>isprimes(int m_num) {
    vector<bool> isp(m_num+1,true);
    isp[0]=isp[1] =false;
    for (int i=2; i*i<=m_num;i++) {
        if (isp[i])
        {
            for (int j=i*i;j<=m_num; j+=i)
            {
                isp[j]=false;
            }
        }
    }
    return isp;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    vector<bool> isp=isprimes(M_SUM);

    int test;
    cin>>test;

    while (test--) {
        int n;
        cin>>n;
        vector<int> freq(101, 0);
        vector<int> a(n);

        for (int i = 0; i < n; ++i) {
            cin>>a[i];
            freq[a[i]]++;
        }

        bool f=false;

        
        for(int i=1;i<=100&&!f;i++) 
        {
            for (int j=i;j<=100&&!f;j++) {
                if (freq[i]>0 && freq[j]>0) {
                    
                    
                    if (i!=j||freq[i]>1) {
                        int sum =i+j;
                        if (!isp[sum]) {
                            int x=-1, y=-1;
                            for (int k=0; k<n;k++) {
                               
                               
                                if (a[k]==i&&x==-1) {
                                    x=k; 
                                } else if (a[k]==j&&(y==-1||y==x)) {
                                    y=k; 
                                }
                                if (x !=-1 && y!=-1 && x!=y) {
                                    cout << x+1<<" "<<y+1<<"\n";
                                    f=true;
                                    break;
                                }
                            }
                        }
                    }
                }
            }
        }

        if (!f) {
            cout<<"-1\n";
        }
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

    static final int M_SUM = 200;

    static boolean[] sieveOfEratosthenes(int limit) {
        boolean[] isp = new boolean[limit + 1];
        Arrays.fill(isp, true);
        isp[0] = isp[1] = false;
        for (int i = 2; i * i <= limit; i++) {
            if (isp[i]) {
                for (int j = i * i; j <= limit; j += i) {
                    isp[j] = false;
                }
            }
        }
        return isp;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        boolean[] isp = sieveOfEratosthenes(M_SUM);

        int test = sc.nextInt();

        while (test-- > 0) {
            int n = sc.nextInt();
            int[] freq = new int[101];
            int[] a = new int[n];

            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
                freq[a[i]]++;
            }

            boolean found = false;

            for (int i = 1; i <= 100 && !found; i++) {
                for (int j = i; j <= 100 && !found; j++) {
                    if (freq[i] > 0 && freq[j] > 0) {
                        if (i != j || freq[i] > 1) {
                            int sum = i + j;
                            if (!isp[sum]) {
                                int x = -1, y = -1;
                                for (int k = 0; k < n; k++) {
                                    if (a[k] == i && x == -1) {
                                        x = k;
                                    } else if (a[k] == j && (y == -1 || y == x)) {
                                        y = k;
                                    }
                                    if (x != -1 && y != -1 && x != y) {
                                        System.out.println((x + 1) + " " + (y + 1));
                                        found = true;
                                        break;
                                    }
                                }
                            }
                        }
                    }
                }
            }

            if (!found) {
                System.out.println("-1");
            }
        }

        sc.close();
    }
}

```

</details>



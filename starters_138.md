## 1. Heat Wave

<details>
<summary>Python</summary>

```python
x,y = map(int,input().split())
if y>x:
    print('YES')
else:
    print('NO')
    
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() {
    int x, y;
    cin >> x >> y;
    if (y > x) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
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
        int x = scanner.nextInt();
        int y = scanner.nextInt();
        if (y > x) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
        scanner.close();
    }
}

```

</details>

## 2. Long Drive

<details>
<summary>Python</summary>

```python
import math
for _ in range(int(input())):
    x,y = map(int,input().split())
    temp = 10*(y-x)
    print(math.ceil(temp/(100-y)))
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int x, y;
        cin >> x >> y;
        double temp = 10 * (y - x);
        cout << ceil(temp / (100 - y)) << endl;
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
            double temp = 10 * (y - x);
            System.out.println((int) Math.ceil(temp / (100 - y)));
        }
        scanner.close();
    }
}

```

</details>

## 3. Distinct Substring

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n,k = map(int,input().split())
    temp = (k*(k+1))//2
    if temp+k-1>n:
        print('NO')
    else:
        print('YES')
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
        int n, k;
        cin >> n >> k;
        int temp = (k * (k + 1)) / 2;
        if (temp + k - 1 > n) {
            cout << "NO" << endl;
        } else {
            cout << "YES" << endl;
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
            int k = scanner.nextInt();
            int temp = (k * (k + 1)) / 2;
            if (temp + k - 1 > n) {
                System.out.println("NO");
            } else {
                System.out.println("YES");
            }
        }
        scanner.close();
    }
}

```

</details>

## 4. Prefix Suffix Inequality

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n = int(input())
    l = []
    if n==1:
        print('1')
        continue
        
    for i in range(n-2):
        l.append(3)
    l.append(2)
    l.append(1)
    print(*l)
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
    while (t--) {
        int n;
        cin >> n;
        if (n == 1) {
            cout << "1" << endl;
            continue;
        }

        vector<int> l(n-2, 3);
        l.push_back(2);
        l.push_back(1);

        for (int i = 0; i < l.size(); ++i) {
            if (i > 0) cout << " ";
            cout << l[i];
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
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            if (n == 1) {
                System.out.println("1");
                continue;
            }

            ArrayList<Integer> l = new ArrayList<>();
            for (int i = 0; i < n - 2; i++) {
                l.add(3);
            }
            l.add(2);
            l.add(1);

            for (int i = 0; i < l.size(); i++) {
                if (i > 0) System.out.print(" ");
                System.out.print(l.get(i));
            }
            System.out.println();
        }
        scanner.close();
    }
}

```

</details>

## 5. TRIPLE PRIMES

<details>
<summary>Python</summary>

```python
import math

def sieve(n):
    isprime = [True] * (n + 1)
    isprime[0] = isprime[1] = False
    for i in range(2, math.isqrt(n) + 1):
        if isprime[i]:
            for j in range(i * i, n + 1, i):
                isprime[j] = False
    return isprime

def is_sum_of_two_prime_squares(n):
    if n < 8:
        return False
    
    max_prime = math.isqrt(n) + 1
    primes = sieve(max_prime)
    
    for i in range(3, len(primes)):
        if primes[i]:
            square_i = i * i
            if square_i > n:
                break
            remaining = n - square_i
            sqrt_remaining = math.isqrt(remaining)
            if sqrt_remaining * sqrt_remaining == remaining and primes[sqrt_remaining] and sqrt_remaining != i and sqrt_remaining != 2:
                return True
    
    return False

for _ in range(int(input())):
    n = int(input())
    if is_sum_of_two_prime_squares(n - 4):
        print('Yes')
    else:
        print('No')

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <cmath>

std::vector<bool> sieve(int n) {
    std::vector<bool> isprime(n + 1, true);
    isprime[0] = isprime[1] = false;
    for (int i = 2; i <= std::sqrt(n); ++i) {
        if (isprime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isprime[j] = false;
            }
        }
    }
    return isprime;
}

bool is_sum_of_two_prime_squares(int n) {
    if (n < 8) {
        return false;
    }

    int max_prime = std::sqrt(n) + 1;
    std::vector<bool> primes = sieve(max_prime);

    for (int i = 3; i < primes.size(); ++i) {
        if (primes[i]) {
            int square_i = i * i;
            if (square_i > n) {
                break;
            }
            int remaining = n - square_i;
            int sqrt_remaining = std::sqrt(remaining);
            if (sqrt_remaining * sqrt_remaining == remaining && primes[sqrt_remaining] && sqrt_remaining != i && sqrt_remaining != 2) {
                return true;
            }
        }
    }

    return false;
}

int main() {
    int t;
    std::cin >> t;
    while (t--) {
        int n;
        std::cin >> n;
        if (is_sum_of_two_prime_squares(n - 4)) {
            std::cout << "Yes" << std::endl;
        } else {
            std::cout << "No" << std::endl;
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
import java.util.Arrays;

public class Main {
    
    public static boolean[] sieve(int n) {
        boolean[] isprime = new boolean[n + 1];
        Arrays.fill(isprime, true);
        isprime[0] = isprime[1] = false;
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (isprime[i]) {
                for (int j = i * i; j <= n; j += i) {
                    isprime[j] = false;
                }
            }
        }
        return isprime;
    }
    
    public static boolean is_sum_of_two_prime_squares(int n) {
        if (n < 8) {
            return false;
        }
        
        int max_prime = (int) Math.sqrt(n) + 1;
        boolean[] primes = sieve(max_prime);
        
        for (int i = 3; i < primes.length; i++) {
            if (primes[i]) {
                int square_i = i * i;
                if (square_i > n) {
                    break;
                }
                int remaining = n - square_i;
                int sqrt_remaining = (int) Math.sqrt(remaining);
                if (sqrt_remaining * sqrt_remaining == remaining && primes[sqrt_remaining] && sqrt_remaining != i && sqrt_remaining != 2) {
                    return true;
                }
            }
        }
        
        return false;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            if (is_sum_of_two_prime_squares(n - 4)) {
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

## 6. A power B mod C

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

## 1. Distribute Cookies

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n,m = map(int,input().split())
    temp = m//n
    if temp == 0:
        print(n-m)
        continue
    print(min(m-temp*n,(temp+1)*n-m))
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        int temp = m / n;
        if (temp == 0) {
            cout << n - m << endl;
            continue;
        }
        cout << min(m - temp * n, (temp + 1) * n - m) << endl;
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
        while (t-- > 0) {
            int n = sc.nextInt();
            int m = sc.nextInt();
            int temp = m / n;
            if (temp == 0) {
                System.out.println(n - m);
                continue;
            }
            System.out.println(Math.min(m - temp * n, (temp + 1) * n - m));
        }
    }
}

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

## Question - 3

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

## Question - 5

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

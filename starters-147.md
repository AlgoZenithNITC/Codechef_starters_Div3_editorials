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

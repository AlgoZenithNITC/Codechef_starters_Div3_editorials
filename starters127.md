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

## 3. Anti-Triangle

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n,l = map(int,input().split())
    if l>10**4:
        for i in range(n):
            print(i+1,end = ' ')
    else:
        for i in range(n):
            print(i*l+1,end = ' ')
    print()
        
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
        int n, l;
        cin >> n >> l;
        if (l > 10000) {
            for (int i = 0; i < n; ++i) {
                cout << i + 1 << " ";
            }
        } else {
            for (int i = 0; i < n; ++i) {
                cout << i * l + 1 << " ";
            }
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

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            int l = scanner.nextInt();
            if (l > 10000) {
                for (int i = 0; i < n; ++i) {
                    System.out.print((i + 1) + " ");
                }
            } else {
                for (int i = 0; i < n; ++i) {
                    System.out.print((i * l + 1) + " ");
                }
            }
            System.out.println();
        }
        scanner.close();
    }
}

```

</details>

## 4. ABC Conjecture

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

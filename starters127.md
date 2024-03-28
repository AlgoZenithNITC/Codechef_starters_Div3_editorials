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
from collections import deque
for _ in range(int(input())):
    n = int(input())
    a = input()
    b = input()
    if a == b:
        print("Yes")
        continue
    curr = -1
    flag = 0
    q = deque()
    for i in range(n):
        if a[i] == b[i]:
            if a[i] == 'b':
                curr = i
        elif a[i] == 'a' and b[i] == 'c':
            q.append(i)
        elif a[i] == 'c' and b[i] == 'a':
            if q and q[0]<curr:
                q.popleft()
            else:
                flag = 1
                break
        else:
            flag = 1
            break
    if q:
        flag =1
    if flag == 1:
        print("No")
    else:
        print("Yes")
        
        
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        string a, b;
        cin >> a >> b;
        if (a == b) {
            cout << "Yes" << endl;
            continue;
        }
        int curr = -1;
        int flag = 0;
        deque<int> q;
        for (int i = 0; i < n; ++i) {
            if (a[i] == b[i]) {
                if (a[i] == 'b') {
                    curr = i;
                }
            } else if (a[i] == 'a' && b[i] == 'c') {
                q.push_back(i);
            } else if (a[i] == 'c' && b[i] == 'a') {
                if (!q.empty() && q.front() < curr) {
                    q.pop_front();
                } else {
                    flag = 1;
                    break;
                }
            } else {
                flag = 1;
                break;
            }
        }
        if (!q.empty()) {
            flag = 1;
        }
        if (flag == 1) {
            cout << "No" << endl;
        } else {
            cout << "Yes" << endl;
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
import java.util.ArrayDeque;
import java.util.Deque;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            String a = scanner.next();
            String b = scanner.next();
            if (a.equals(b)) {
                System.out.println("Yes");
                continue;
            }
            int curr = -1;
            int flag = 0;
            Deque<Integer> q = new ArrayDeque<>();
            for (int i = 0; i < n; ++i) {
                if (a.charAt(i) == b.charAt(i)) {
                    if (a.charAt(i) == 'b') {
                        curr = i;
                    }
                } else if (a.charAt(i) == 'a' && b.charAt(i) == 'c') {
                    q.add(i);
                } else if (a.charAt(i) == 'c' && b.charAt(i) == 'a') {
                    if (!q.isEmpty() && q.peek() < curr) {
                        q.poll();
                    } else {
                        flag = 1;
                        break;
                    }
                } else {
                    flag = 1;
                    break;
                }
            }
            if (!q.isEmpty()) {
                flag = 1;
            }
            if (flag == 1) {
                System.out.println("No");
            } else {
                System.out.println("Yes");
            }
        }
        scanner.close();
    }
}

```

</details>

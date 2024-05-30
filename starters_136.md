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

## 3. Sum of Modes

<details>
<summary>Python</summary>

```python
from collections import defaultdict
for _ in range(int(input())):
    n = int(input())
    s = input()
    ans = (n*(n+1))//2 # as every substring will have 1 contribution
    total = 0
    d = defaultdict(int)
    d[0] = 1
    for i in s:
        if i == '1':
            total+=1
        else:
            total-=1
        ans+=d[total]
        d[total]+=1
    print(ans)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <unordered_map>
#include <string>

using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        string s;
        cin >> s;
        long long ans = (long long)n * (n + 1) / 2;
        int total = 0;
        unordered_map<int, int> map;
        map[0] = 1;
        for (char c : s) {
            if (c == '1') {
                total += 1;
            } else {
                total -= 1;
            }
            ans += map[total];
            map[total]++;
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
import java.util.HashMap;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            scanner.nextLine(); // Consume the newline
            String s = scanner.nextLine();
            long ans = (long) n * (n + 1) / 2;
            int total = 0;
            HashMap<Integer, Integer> map = new HashMap<>();
            map.put(0, 1);
            for (int i = 0; i < s.length(); i++) {
                if (s.charAt(i) == '1') {
                    total += 1;
                } else {
                    total -= 1;
                }
                ans += map.getOrDefault(total, 0);
                map.put(total, map.getOrDefault(total, 0) + 1);
            }
            System.out.println(ans);
        }
        scanner.close();
    }
}

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

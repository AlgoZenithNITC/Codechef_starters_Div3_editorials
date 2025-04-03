
## 1. Maximum Ones

<details>
<summary>Python</summary>

```python

def max_ones(N, K, S):
    S = list(S)
    for i in range(N - 1):
        if K == 0:
            break
        if S[i] == '0' and S[i + 1] == '1':
            S[i] = '1'
            K -= 1
    return S.count('1')

T = int(input())
for _ in range(T):
    N, K = map(int, input().split())
    S = input().strip()
    print(max_ones(N, K, S))


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
using namespace std;

int maxOnes(int N, int K, string S) {
    for (int i = 0; i < N - 1 && K > 0; i++) {
        if (S[i] == '0' && S[i + 1] == '1') {
            S[i] = '1';
            K--;
        }
    }
    int count = 0;
    for (char c : S) {
        if (c == '1') count++;
    }
    return count;
}

int main() {
    int T;
    cin >> T;
    while (T--) {
        int N, K;
        string S;
        cin >> N >> K >> S;
        cout << maxOnes(N, K, S) << endl;
    }
    return 0;
}

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class MaxOnes {
    public static int maxOnes(int N, int K, String S) {
        char[] arr = S.toCharArray();
        for (int i = 0; i < N - 1 && K > 0; i++) {
            if (arr[i] == '0' && arr[i + 1] == '1') {
                arr[i] = '1';
                K--;
            }
        }
        int count = 0;
        for (char c : arr) {
            if (c == '1') count++;
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            int K = sc.nextInt();
            String S = sc.next();
            System.out.println(maxOnes(N, K, S));
        }
        sc.close();
    }
}


```

</details>

## 2. Shall we play a game
<details>
<summary>Python</summary>

```python
MOD = 998244353

def compute_difference(N):
    return (pow(2, N, MOD) - 1) % MOD

T = int(input())
for _ in range(T):
    N = int(input())
    print(compute_difference(N))

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;
const int MOD = 998244353;

long long computeDifference(int N) {
    return ((1LL << N) - 1) % MOD;
}

int main() {
    int T, N;
    cin >> T;
    while (T--) {
        cin >> N;
        cout << computeDifference(N) << endl;
    }
    return 0;
}


```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class GameDifference {
    static final int MOD = 998244353;

    public static long computeDifference(int N) {
        return ((1L << N) - 1) % MOD;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            System.out.println(computeDifference(N));
        }
        sc.close();
    }
}



```

</details>

## 3.Array Operations

<details>
<summary>Python</summary>

```python
def find_max_final_element(A):
    while len(A) > 1:
        A = [max(A[i] + 1, A[i + 1], A[i + 2] + 1) for i in range(0, len(A) - 2, 2)]
    return A[0]

T = int(input())
for _ in range(T):
    N = int(input())
    A = list(map(int, input().split()))
    print(find_max_final_element(A))

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
using namespace std;

int findMaxFinalElement(vector<int> &A) {
    while (A.size() > 1) {
        vector<int> newA;
        for (size_t i = 0; i + 2 < A.size(); i += 2) {
            newA.push_back(max(A[i] + 1, max(A[i + 1], A[i + 2] + 1)));
        }
        A = newA;
    }
    return A[0];
}

int main() {
    int T, N;
    cin >> T;
    while (T--) {
        cin >> N;
        vector<int> A(N);
        for (int i = 0; i < N; i++) {
            cin >> A[i];
        }
        cout << findMaxFinalElement(A) << endl;
    }
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class ArrayOperations {
    public static int findMaxFinalElement(int[] A) {
        while (A.length > 1) {
            int newSize = (A.length - 2) / 2 + 1;
            int[] newA = new int[newSize];
            int idx = 0;
            for (int i = 0; i + 2 < A.length; i += 2) {
                newA[idx++] = Math.max(A[i] + 1, Math.max(A[i + 1], A[i + 2] + 1));
            }
            A = newA;
        }
        return A[0];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            int[] A = new int[N];
            for (int i = 0; i < N; i++) {
                A[i] = sc.nextInt();
            }
            System.out.println(findMaxFinalElement(A));
        }
        sc.close();
    }
}

```

</details>

## 4. Huh, Easy

<details>
<summary>Python</summary>

```python
def construct_strings(N, K):
    if K > N or (N > 1 and K == 0 and N % 2 == 0):
        print("-1")
        return

    pattern = "ABC"
    S = "".join(pattern[i % 3] for i in range(N))
    T = list(S)

    for i in range(K, N):
        T[i] = pattern[(ord(T[i]) - ord('A') + 1) % 3]

    print(S)
    print("".join(T))

T = int(input())
for _ in range(T):
    N, K = map(int, input().split())
    construct_strings(N, K)

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <string>
using namespace std;

void constructStrings(int N, int K) {
    if (K > N || (N > 1 && K == 0 && N % 2 == 0)) {
        cout << "-1\n";
        return;
    }

    string S = "", T = "";
    string pattern = "ABC";

    // Generate the first string S
    for (int i = 0; i < N; i++) {
        S += pattern[i % 3];
    }

    // Generate the second string T
    T = S;
    for (int i = K; i < N; i++) {
        T[i] = pattern[(T[i] - 'A' + 1) % 3]; // Shift to a different character
    }

    cout << S << "\n" << T << "\n";
}

int main() {
    int T, N, K;
    cin >> T;
    while (T--) {
        cin >> N >> K;
        constructStrings(N, K);
    }
    return 0;
}
 
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class SpecialStrings {
    public static void constructStrings(int N, int K) {
        if (K > N || (N > 1 && K == 0 && N % 2 == 0)) {
            System.out.println("-1");
            return;
        }

        char[] S = new char[N];
        char[] T = new char[N];
        char[] pattern = {'A', 'B', 'C'};

        // Generate the first string S
        for (int i = 0; i < N; i++) {
            S[i] = pattern[i % 3];
        }

        // Generate the second string T
        System.arraycopy(S, 0, T, 0, N);
        for (int i = K; i < N; i++) {
            T[i] = pattern[(T[i] - 'A' + 1) % 3]; // Shift to a different character
        }

        System.out.println(new String(S));
        System.out.println(new String(T));
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        while (T-- > 0) {
            int N = sc.nextInt();
            int K = sc.nextInt();
            constructStrings(N, K);
        }
        sc.close();
    }
}

```

</details>

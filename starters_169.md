## 1. Opposite Attract

<details>
<summary>Python</summary>

```python
def main():
    T = int(input())
    for _ in range(T):
        N = int(input())
        S = input()

        # Generate the toggled string
        T = ''.join('1' if char == '0' else '0' for char in S)

        print(T)

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp


You said:
#include <stdio.h>
#include <string.h>

int main() {
    int T;
    scanf("%d", &T);

    while (T--) {
        int N;
        scanf("%d", &N);

        char S[N + 1];
        scanf("%s", S);

        char T[N + 1];

        for (int i = 0; i < N; i++) {
            T[i] = (S[i] == '0') ? '1' : '0';
        }

        T[N] = '\0';

        printf("%s\n", T);
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

        int T = scanner.nextInt();
        while (T-- > 0) {
            int N = scanner.nextInt();
            String S = scanner.next();

            // Generate the toggled string
            StringBuilder T = new StringBuilder();
            for (int i = 0; i < N; i++) {
                T.append(S.charAt(i) == '0' ? '1' : '0');
            }

            System.out.println(T.toString());
        }

        scanner.close();
    }
}

```

</details>

## 2. Hamming Equivalent

<details>
<summary>Python</summary>

```python
def solve():
    import math

    N = int(input())
    A = []
    B = []

    # Separate positive and negative numbers
    for _ in range(N):
        x = int(input())
        if x >= 0:
            A.append(x)
        else:
            B.append(x)

    mx = 10**16
    l, h = 0, mx

    def ok(m):
        s = 0
        j = 0

        for i in range(len(A)):
            if A[i] > m:
                return False

            s += A[i]

            while s > m and j < len(B):
                s += B[j]
                j += 1
                s = max(s, A[i])

            if s > m:
                return False

        return True

    while l < h:
        m = (l + h) // 2
        if ok(m):
            h = m - 1
        else:
            l = m + 1

    for m in range(l - 1, l + 2):
        if 0 <= m <= mx and ok(m):
            print(m)
            return


test = int(input())
for _ in range(test):
    solve()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long

int32_t main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    
    auto solve = [&]()->void{
        int N ;
        cin>>N ;

        vector<int>A , B ;
        for( int i = 0 ; i < N ; i++ )
        {
           int x ;
           cin>>x ;

           if( x >= 0 )
            A.push_back(x);
           else
            B.push_back(x);
        }

        int mx = pow(10,16);
        int l = 0 ;
        int h =  mx ;

        auto ok = [&]( int m )-> bool {

            int s = 0 ;
            int j = 0 ;

            for( int i = 0 ; i < A.size() ; i++ )
            {
                if( A[i] > m )
                    return 0 ;

                s += A[i];
                
                while( s > m && j < B.size() )
                {
                    s += B[j++];
                    s = max( s , A[i] );
                }

                if( s > m )
                    return 0 ;
            }
            return 1 ;
        };

        while( l < h )
        {
            int m = (l+h)>>1 ;
            if( ok(m) )
                h = m-1 ;
            else
                l = m+1 ;
        }

        for( int m = l-1 ; m <= l+1 ; m++ )
        {
            if( m >= 0 && m <= mx && ok(m) )
            {
                cout<<m<<endl;
                return ;
            }
        }

    };
    

int test = 1 ;
cin>>test;
while(test--)
solve();
return 0;
} 
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int test = scanner.nextInt();
        while (test-- > 0) {
            solve(scanner);
        }

        scanner.close();
    }

    public static void solve(Scanner scanner) {
        int N = scanner.nextInt();
        List<Long> A = new ArrayList<>();
        List<Long> B = new ArrayList<>();

        for (int i = 0; i < N; i++) {
            long x = scanner.nextLong();
            if (x >= 0) {
                A.add(x);
            } else {
                B.add(x);
            }
        }

        long mx = (long) Math.pow(10, 16);
        long l = 0, h = mx;

        while (l < h) {
            long m = (l + h) / 2;
            if (ok(A, B, m)) {
                h = m - 1;
            } else {
                l = m + 1;
            }
        }

        for (long m = l - 1; m <= l + 1; m++) {
            if (m >= 0 && m <= mx && ok(A, B, m)) {
                System.out.println(m);
                return;
            }
        }
    }

    public static boolean ok(List<Long> A, List<Long> B, long m) {
        long s = 0;
        int j = 0;

        for (long a : A) {
            if (a > m) return false;

            s += a;

            while (s > m && j < B.size()) {
                s += B.get(j++);
                s = Math.max(s, a);
            }

            if (s > m) return false;
        }

        return true;
    }
}

```

</details>

## 3. Make k Most Frequent

<details>
<summary>Python</summary>

```python
def solve():
    n, k = map(int, input().split())
    a = list(map(int, input().split()))

    # Count frequencies of each number
    cnt = [0] * 21
    for num in a:
        cnt[num] += 1

    max_cnt = max(cnt)
    if cnt[k] == max_cnt:
        print(0)
        return

    # Prefix frequency manipulation
    cnt_pre = cnt[:]
    for i in range(n):
        max_pre = max(cnt_pre)
        if cnt_pre[k] == max_pre:
            print(1)
            return
        cnt_pre[a[i]] -= 1

    # Suffix frequency manipulation
    cnt_suff = cnt[:]
    for i in range(n - 1, -1, -1):
        max_suff = max(cnt_suff)
        if cnt_suff[k] == max_suff:
            print(1)
            return
        cnt_suff[a[i]] -= 1

    # If not possible with 1 operation
    print(2)


# Driver Code
t = int(input())
for _ in range(t):
    solve()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

#define ll long long int

void solve() {
   int n,k;
   cin >> n >> k;
   vector<int> a(n);
   vector<int> cnt(21);
   for(int i=0;i<n;i++){
       cin >> a[i];
       cnt[a[i]]++;
   }
   ll max_cnt=*max_element(cnt.begin(),cnt.end());
   if(cnt[k]==max_cnt){
       cout << 0 << '\n';
       return;
   }
   vector<int> cnt_pre=cnt;
   for(int i=0;i<n;i++){
       ll maxi_pre=*max_element(cnt_pre.begin(),cnt_pre.end());
       if(cnt_pre[k]==maxi_pre){
           cout << 1 << "\n";
           return;
       }
       cnt_pre[a[i]]--;
   }
   
   vector<int> cnt_suff=cnt;
   
   for(int i=n-1;i>=0;i--){
       ll maxi_suff=*max_element(cnt_suff.begin(),cnt_suff.end());
       if(cnt_suff[k]==maxi_suff){
           cout << 1 << "\n";
           return;
       }
       cnt_suff[a[i]]--;
   }
   
   cout << 2 << "\n";
   
   

    }


int main() {
    ios::sync_with_stdio(false);
    cin.tie(NULL);

    int t;
    cin >> t;
    while (t--) {
        solve();
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
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            solve(scanner);
        }
        scanner.close();
    }

    public static void solve(Scanner scanner) {
        int n = scanner.nextInt();
        int k = scanner.nextInt();
        int[] a = new int[n];
        int[] cnt = new int[21];

        for (int i = 0; i < n; i++) {
            a[i] = scanner.nextInt();
            cnt[a[i]]++;
        }

        int maxCnt = Arrays.stream(cnt).max().orElse(0);
        if (cnt[k] == maxCnt) {
            System.out.println(0);
            return;
        }

        // Prefix frequency manipulation
        int[] cntPre = Arrays.copyOf(cnt, cnt.length);
        for (int i = 0; i < n; i++) {
            int maxPre = Arrays.stream(cntPre).max().orElse(0);
            if (cntPre[k] == maxPre) {
                System.out.println(1);
                return;
            }
            cntPre[a[i]]--;
        }

        // Suffix frequency manipulation
        int[] cntSuff = Arrays.copyOf(cnt, cnt.length);
        for (int i = n - 1; i >= 0; i--) {
            int maxSuff = Arrays.stream(cntSuff).max().orElse(0);
            if (cntSuff[k] == maxSuff) {
                System.out.println(1);
                return;
            }
            cntSuff[a[i]]--;
        }

        // If not possible with 1 operation
        System.out.println(2);
    }
}

```

</details>
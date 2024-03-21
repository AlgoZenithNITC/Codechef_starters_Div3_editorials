## Dice Game 3

<details>
<summary>Python</summary>

```python
   def main():
    t = int(input())
    for _ in range(t):
        n = int(input())
        m = n * 6
        m += n // 2
        print(m)

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
using namespace std;

int main() 
{
    int t,n;
    cin>>t;
    while(t--){
      cin>>n;
      int m=n*6;
      m+=n/2;
      cout<<m<<endl;
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
            int m = n * 6;
            m += n / 2;
            System.out.println(m);
        }
        scanner.close();
    }
}

```

</details>

## Sale

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    for _ in range(t):
        N = int(input())
        Sales = list(map(int, input().split()))
        PSum = [0] * N
        Sum = 0
        MaxSalesOnDay = [0] * N

        for i in range(N):
            Sum += Sales[i]
            PSum[i] = Sum
            MaxSalesOnDay[i] = PSum[i] + Sales[i]

        ans = max(MaxSalesOnDay)
        print(ans)

if __name__ == "__main__":
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
    cin >> t;

    while (t--) {
        int N;
        cin >> N;
        long long Sales[N];
        long long PSum[N];
        long long Sum = 0;
        long long MaxSalesOnDay[N];

        for (int i = 0; i < N; i++) {
            cin >> Sales[i];
            Sum += Sales[i];
            PSum[i] = Sum;
            MaxSalesOnDay[i] = PSum[i] + Sales[i];
        }
        
        long long ans = *max_element(MaxSalesOnDay,MaxSalesOnDay+N);
        cout<<ans<<endl;

       
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
            int N = scanner.nextInt();
            long[] Sales = new long[N];
            long[] PSum = new long[N];
            long Sum = 0;
            long[] MaxSalesOnDay = new long[N];

            for (int i = 0; i < N; i++) {
                Sales[i] = scanner.nextLong();
                Sum += Sales[i];
                PSum[i] = Sum;
                MaxSalesOnDay[i] = PSum[i] + Sales[i];
            }

            long ans = maxElement(MaxSalesOnDay);
            System.out.println(ans);
        }
        scanner.close();
    }

    private static long maxElement(long[] arr) {
        long max = Long.MIN_VALUE;
        for (long num : arr) {
            if (num > max) {
                max = num;
            }
        }
        return max;
    }
}

```

</details>

## Permutation Disturbance

<details>
<summary>Python</summary>

```python
def solve():
    n = int(input())
    v = list(map(int, input().split()))

    cluster = 0
    individual = 0
    i = 0
    ans = 0

    while i < n:
        while i < n and v[i] != i + 1:
            i += 1

        count = 0
        while i < n and v[i] == i + 1:
            count += 1
            i += 1

        ans += (count + 1) // 2

    print(ans)

def main():
    t = int(input())
    for _ in range(t):
        solve()

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(){
  int n;
  cin>>n;
  
  vector<int> v(n);
  for(auto &it : v) cin>>it;
  
  int cluster = 0;
  int individual = 0;
  
  
  int i=0;
  int ans = 0;
  
  while(i < n){
    
    //move i until you hit a number placed at wrong index.  
    while(i<n && v[i] != i+1){
      i++;
    }
    
    int count = 0;
    //move i until elements are at wrong index. increment the count as you move.
    while(i<n && v[i] == i+1){
      count++;
      i++;
    }
    
    //Take the ceil of (count/2). 
    //Below is the equivalent to ceil(count/2)
    ans += (count+2-1)/2;
    
  }
  
  cout<<ans<<endl;
  
}

int main() 
{
    int t;
    cin>>t;
    
    while(t--)
      solve();
    return 0;
}
```

</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Main {
    static void solve() {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] v = new int[n];

        for (int i = 0; i < n; i++) {
            v[i] = scanner.nextInt();
        }

        int cluster = 0;
        int individual = 0;
        int i = 0;
        int ans = 0;

        while (i < n) {
            while (i < n && v[i] != i + 1) {
                i++;
            }

            int count = 0;
            while (i < n && v[i] == i + 1) {
                count++;
                i++;
            }

            ans += (count + 1) / 2;
        }

        System.out.println(ans);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            solve();
        }
        scanner.close();
    }
}

```

</details>

## Freedom

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    while t > 0:
        n = int(input())
        ans = 0
        freq_map = {}
        for _ in range(n):
            temp = int(input())
            if temp != 1 and (3 * temp) % (temp - 1) == 0:
                ans += freq_map.get((3 * temp) // (temp - 1), 0)
            freq_map[temp] = freq_map.get(temp, 0) + 1
        print(ans)
        t -= 1

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;
    cin>>t;
    while(t--)
    {
        int n;
        cin>>n;
        long long ans=0;
        map<int,int>map;
        for(int i=0;i<n;i++)
        {
            int temp;
            cin>>temp;
            if(temp!=1 && (3*temp)%(temp-1)==0)
            ans+=map[(3*temp)/(temp-1)];
            map[temp]++;
        }
        cout<<ans<<endl;
    }
}


```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main 
{
    public static void main(String[] args) 
    {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) 
        {
            int n = scanner.nextInt();
            long ans = 0;
            Map<Integer, Integer> freqMap = new HashMap<>();
            for (int i = 0; i < n; i++) 
            {
                int temp = scanner.nextInt();
                if (temp != 1 && (3 * temp) % (temp - 1) == 0)
                    ans += freqMap.getOrDefault((3 * temp) / (temp - 1), 0);
                freqMap.put(temp, freqMap.getOrDefault(temp, 0) + 1);
            }
            System.out.println(ans);
        }
    }
}


```

</details>

## Triangular Swaps

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    while t > 0:
        n = int(input())
        s = input()
        done = False
        count = 0
        for i in range(2, n):
            if s[i - 2] == s[i - 1] == s[i]:
                if not done:
                    done = True
                    continue
            if i - 3 >= 0:
                if not (s[i - 3] == s[i - 2] == s[i]):
                    count += 1
            else:
                count += 1
        print(count + int(done))

if _name_ == "_main_":
    main()
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() 
{
    int t;
    cin>>t;
    while(t--)
    {
        int n;
        cin>>n;
        string s;
        cin>>s;
        int done = false;
        int count=0;
        for(int i=2;i<n;i++)
        {
            if(s[i-2]==s[i-1] && s[i-1]==s[i])
            {
                if(done==0)
                done=true;
                continue;
            }
            if(i-3>=0)
            {
                if(!(s[i-3]==s[i-2] && s[i-2]==s[i]))
                count++;
            }
            else
            count++;
        }
        cout<<count+done<<endl;
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
            boolean done = false;
            int count = 0;
            for (int i = 2; i < n; i++) {
                if (s.charAt(i - 2) == s.charAt(i - 1) && s.charAt(i - 1) == s.charAt(i)) {
                    if (!done)
                        done = true;
                    continue;
                }
                if (i - 3 >= 0) {
                    if (!(s.charAt(i - 3) == s.charAt(i - 2) && s.charAt(i - 2) == s.charAt(i)))
                        count++;
                } else
                    count++;
            }
            System.out.println(count + (done ? 1 : 0));
        }
    }
}



```

</details>
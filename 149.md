## 1. Magical World

<details>
<summary>Python</summary>

```Python
t = int(input())

for _ in range(t):
    a, b, x = map(int, input().split())
    
    area_rectangle = a * b
    area_square = x * x
    
    if area_rectangle <= area_square:
        print(0)
    elif a <= area_square or b <= area_square:
        print(1)
    else:
        print(2)
```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
    cin >> t;

    while (t--) {
        int a, b, x;
        cin >> a >> b >> x;
        
        int areaRectangle = a * b;
        int areaSquare = x * x;

        if (areaRectangle <= areaSquare) {
            cout << 0 << endl;
        } 
        else if (a <= areaSquare || b <= areaSquare) {
            cout << 1 << endl;
        } 
        else {
            cout << 2 << endl;
        }
    }

    return 0;

}

```

</details>

<details>
<summary>Java</summary>

```Java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		 Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            int a = sc.nextInt();
            int b = sc.nextInt();
            int x = sc.nextInt();

            int areaRectangle = a * b;
            int areaSquare = x * x;

            if (areaRectangle <= areaSquare) {
                System.out.println(0);
            } else if (a <= areaSquare || b <= areaSquare) {
                System.out.println(1);
            } else {
                System.out.println(2);
            }
        }

	}
}

```

</details>

## 2. Easy Subarray Sum

<details>
<summary>Python</summary>
	
```Python
t = int(input())
for _ in range(t):
    n = int(input())
    v = list(map(int, input().split()))
    
    l = -1
    r = -1
    
    for i in range(n):
        if v[i] > 0:
            l = i
            break
            
    for i in range(n - 1, -1, -1):
        if v[i] > 0:
            r = i
            break
            
    if l == -1 or r == -1:
        print("0")
    else:
        cnt = 0
        for i in range(l + 1, r):
            if v[i] < 0:
                cnt += 1
        print(cnt)


```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vector<int> v(n);
        for(int i=0; i<n; i++){
            cin>>v[i];
        }
        int l=-1,r=-1;
        for(int i=0; i<n; i++){
            if(v[i]>0){
                l=i;
                break;
            }
        }
        for(int i=n-1; i>=0; i--){
            if(v[i]>0){
                r=i;
                break;
            }
        }
        if(l==-1||r==-1){
            cout<<"0"<<endl;
        }
        else{
        int cnt=0;
        for(int i=l+1; i<r; i++){
            if(v[i]<0){
                cnt++;
            }
        }
        cout<<cnt<<endl;
    }

}
}
```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.Scanner;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            int n = scanner.nextInt();
            ArrayList<Integer> v = new ArrayList<>(n);
            for (int i = 0; i < n; i++) {
                v.add(scanner.nextInt());
            }
            int l = -1, r = -1;
            for (int i = 0; i < n; i++) {
                if (v.get(i) > 0) {
                    l = i;
                    break;
                }
            }
            for (int i = n - 1; i >= 0; i--) {
                if (v.get(i) > 0) {
                    r = i;
                    break;
                }
            }
            if (l == -1 || r == -1) {
                System.out.println("0");
            } else {
                int cnt = 0;
                for (int i = l + 1; i < r; i++) {
                    if (v.get(i) < 0) {
                        cnt++;
                    }
                }
                System.out.println(cnt);
            }
        }
        scanner.close();
    }
}


```

</details>

## 3. Maximise Sum

<details>
<summary>Python</summary>
	
```Python
def compute_maximized_sum(numbers):
    total_sum = 0
    negative_count = 0
    min_abs_value = abs(numbers[0])
    
    for num in numbers:
        total_sum += abs(num)
        if num < 0:
            negative_count += 1
        if abs(num) < min_abs_value:
            min_abs_value = abs(num)
    
    if negative_count % 2 == 0:
        return total_sum
    else:
        return total_sum - 2 * min_abs_value

def solve():
    n = int(input())
    numbers = list(map(int, input().split()))
    print(compute_maximized_sum(numbers))

if __name__ == "__main__":
    t = int(input())
    for _ in range(t):
        solve()


```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

long long computeMaximizedSum(const vector<int>& numbers) {
    long long sum = 0;
    int negativeCount = 0;
    int minAbsValue = abs(numbers[0]);
    
    for (int num : numbers) {
        sum += abs(num);
        if (num < 0) negativeCount++;
        if (abs(num) < minAbsValue) {
            minAbsValue = abs(num);
        }
    }
    
    if (negativeCount % 2 == 0) {
        return sum;
    } else {
        return sum - 2LL * minAbsValue;
    }
}

void solve() {
    int n;
    cin >> n;
    vector<int> numbers(n);
    
    for (int i = 0; i < n; i++) {
        cin >> numbers[i];
    }
    
    cout << computeMaximizedSum(numbers) << endl;
}

int main() {
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
	
```Java
import java.util.*;

public class Main {
    public static long computeMaximizedSum(List<Integer> numbers) {
        long sum = 0;
        int negativeCount = 0;
        int minAbsValue = Math.abs(numbers.get(0));
        
        for (int num : numbers) {
            sum += Math.abs(num);
            if (num < 0) negativeCount++;
            if (Math.abs(num) < minAbsValue) {
                minAbsValue = Math.abs(num);
            }
        }
        
        if (negativeCount % 2 == 0) {
            return sum;
        } else {
            return sum - 2L * minAbsValue;
        }
    }

    public static void solve() {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        List<Integer> numbers = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            numbers.add(scanner.nextInt());
        }
        
        System.out.println(computeMaximizedSum(numbers));
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        while (t-- > 0) {
            solve();
        }
    }
}


```
</details>

## 4. Chef Loves Beautiful Strings (Easy Version)

<details>
<summary>Python</summary>
	
```Python
def calculate_beauty(s):
    n = len(s)
    consecutive = 0
    ones = 0
    zeros = 0
    
    for i in range(n):
        if s[i] == '1':
            ones += 1
            if zeros > 1:
                consecutive += (zeros - 1)
            zeros = 0
        else:
            zeros += 1
            if ones > 1:
                consecutive += (ones - 1)
            ones = 0
    
    if ones > 1:
        consecutive += (ones - 1)
    if zeros > 1:
        consecutive += (zeros - 1)
    
    score = 0
    differing_adjacent = 0
    
    for i in range(1, n):
        if s[i] != s[i - 1]:
            differing_adjacent += 1
    
    score = differing_adjacent * consecutive
    score += (differing_adjacent * (differing_adjacent - 1)) // 2
    
    return score

def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    
    index = 0
    T = int(data[index])
    index += 1
    results = []
    
    for _ in range(T):
        N = int(data[index])
        index += 1
        S = data[index]
        index += 1
        
        results.append(calculate_beauty(S))
    
    for result in results:
        print(result)

if _name_ == "_main_":
    main()
```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;
    cin >> t;
    
    while (t--) {
        int n;
        string s;
        cin >> n >> s;
        
        int consecutive = 0;
        int ones = 0, zeros = 0;
        
        for (int i = 0; i < n; i++) {
            if (s[i] == '1') {
                ones++;
                if (zeros > 1) consecutive += (zeros - 1);
                zeros = 0;
            } else {
                zeros++;
                if (ones > 1) consecutive += (ones - 1);
                ones = 0;
            }
        }
        
        if (ones > 1) consecutive += (ones - 1);
        if (zeros > 1) consecutive += (zeros - 1);
        
        long long score = 0;
        long long differing_adjacent = 0;
        
        for (int i = 1; i < n; i++) {
            if (s[i] != s[i - 1]) differing_adjacent++;
        }
        
        score = differing_adjacent * consecutive;
        score += (differing_adjacent * (differing_adjacent - 1LL)) / 2LL;
        
        cout << score << endl;
    }
    
    return 0;
}

```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        int t = Integer.parseInt(st.nextToken());
        
        while (t-- > 0) {
            st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
            String s = br.readLine();
            
            int consecutive = 0;
            int ones = 0, zeros = 0;
            
            for (int i = 0; i < n; i++) {
                if (s.charAt(i) == '1') {
                    ones++;
                    if (zeros > 1) consecutive += (zeros - 1);
                    zeros = 0;
                } else {
                    zeros++;
                    if (ones > 1) consecutive += (ones - 1);
                    ones = 0;
                }
            }
            
            if (ones > 1) consecutive += (ones - 1);
            if (zeros > 1) consecutive += (zeros - 1);
            
            long score = 0;
            long differingAdjacent = 0;
            
            for (int i = 1; i < n; i++) {
                if (s.charAt(i) != s.charAt(i - 1)) differingAdjacent++;
            }
            
            score = differingAdjacent * consecutive;
            score += (differingAdjacent * (differingAdjacent - 1L)) / 2L;
            
            System.out.println(score);
        }
    }
}
```
</details>

## 5. Kill Monsters (Easy Version)
<details>
<summary>Python</summary>
	
```Python
for _ in range(int(input())):
    n, x, k = map(int, input().split())
    h = list(map(int, input().split()))
    freq = [0]*501
    for y in h: freq[y] += 1

    ans = 0
    # consider multiplying once at the start
    for y in range(1, 501):
        if y < x*k and freq[y] > 0: ans += 1
    
    for i in range(n):
        # multiply after killing h[i]
        # one copy of everything < h[i]*k
        # one copy of everything >= h[i] and < x
        # careful about stuff between h[i] and min(x, h[i]*k)

        ct = 0
        if h[i] >= x: continue
        for y in range(1, 501):
            if freq[y] == 0: continue

            if y < h[i]*k: ct += 1
            if y >= h[i] and y < x: ct += 1
            if freq[y] == 1 and y >= h[i] and y < min(x, h[i]*k): ct -= 1
        ans = max(ans, ct)
    
    print(ans)

```
</details>

<details>
<summary>Cpp</summary>
	
```Cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    
    while (t--) {
        int n, x, k;
        cin >> n >> x >> k;
        
        vector<int> arr(n);
        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }
        
        unordered_map<int, int> map;
        for (int i : arr) {
            map[i]++;
        }
        
        set<int> set(arr.begin(), arr.end());
        vector<int> v(set.begin(), set.end());
        vector<int> extra(v.size() + 1);
        
        for (int i = 1; i <= v.size(); i++) {
            extra[i] = extra[i - 1] + (map[v[i - 1]] > 1);
        }
        
        int ans = lower_bound(v.begin(), v.end(), x * k) - v.begin();
        int index = lower_bound(v.begin(), v.end(), x) - v.begin();
        int mulCount = 0;
        
        for (int i = index - 1; i >= 0; i--) {
            if (v[i] * k >= x) {
                int indexAfterMult = lower_bound(v.begin(), v.end(), v[i] * k) - v.begin();
                int monstKilled = extra[index] - extra[i];
                ans = max(ans, indexAfterMult + monstKilled);
            } else {
                int indexAfterMult = lower_bound(v.begin(), v.end(), v[i] * k) - v.begin();
                int monstKilled = extra[indexAfterMult] - extra[i];
                ans = max(ans, index + monstKilled);
            }
        }
        
        cout << ans << endl;
    }
    
    return 0;
}
```
</details>

<details>
<summary>Java</summary>
	
```Java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int t = Integer.parseInt(st.nextToken());

        while (t-- > 0) {
            st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
            int x = Integer.parseInt(st.nextToken());
            int k = Integer.parseInt(st.nextToken());

            st = new StringTokenizer(br.readLine());
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) {
                arr[i] = Integer.parseInt(st.nextToken());
            }

            Map<Integer, Integer> map = new HashMap<>();
            for (int i : arr) {
                map.put(i, map.getOrDefault(i, 0) + 1);
            }

            Set<Integer> set = new TreeSet<>(map.keySet());
            int[] v = new int[set.size()];
            int idx = 0;
            for (int num : set) {
                v[idx++] = num;
            }

            int[] extra = new int[v.length + 1];
            for (int i = 1; i <= v.length; i++) {
                extra[i] = extra[i - 1] + (map.get(v[i - 1]) > 1 ? 1 : 0);
            }

            int ans = Arrays.binarySearch(v, x * k);
            if (ans < 0) {
                ans = -ans - 1;
            }

            int index = Arrays.binarySearch(v, x);
            if (index < 0) {
                index = -index - 1;
            }

            for (int i = index - 1; i >= 0; i--) {
                if (v[i] * k >= x) {
                    int indexAfterMult = Arrays.binarySearch(v, v[i] * k);
                    if (indexAfterMult < 0) {
                        indexAfterMult = -indexAfterMult - 1;
                    }
                    int monstKilled = extra[index] - extra[i];
                    ans = Math.max(ans, indexAfterMult + monstKilled);
                } else {
                    int indexAfterMult = Arrays.binarySearch(v, v[i] * k);
                    if (indexAfterMult < 0) {
                        indexAfterMult = -indexAfterMult - 1;
                    }
                    int monstKilled = extra[indexAfterMult] - extra[i];
                    ans = Math.max(ans, index + monstKilled);
                }
            }

            System.out.println(ans);
        }
    }
}
```
</details>

## 6. Kill Monsters (Hard Version)

<details>
<summary>Python</summary>

```Python
import sys
from collections import defaultdict
from bisect import bisect_left, bisect_right

mod = 998244353

def pow(a, b, m):
    if b == 0:
        return 1
    v = pow(a, b // 2, m) % m
    v = (v * v) % m
    if b & 1:
        return (v * a) % m
    return v

def solve():
    n, x, k = map(int, sys.stdin.readline().split())
    s = set()
    mp = defaultdict(int)
    
    for _ in range(n):
        h = int(sys.stdin.readline())
        s.add(h)
        mp[h] += 1
    
    h = sorted(s)
    ans = bisect_left(h, x * k)
    m = bisect_left(h, x)
    v = []
    
    for i in range(m - 1, -1, -1):
        length = bisect_left(h, h[i] * k)
        if mp[h[i]] == 1:
            v.append(-h[i])
        cnt = len(v) - bisect_right(v, -h[i] * k)
        ans = max(ans, m - i + length - cnt)
    
    print(ans)

def main():
    input = sys.stdin.read
    data = input().splitlines()
    t = int(data[0])
    index = 1
    for _ in range(t):
        solve()

if __name__ == "__main__":
    main()


```

</details>

<details>
<summary>Cpp</summary>

```Cpp
#include <bits/stdc++.h>
using namespace std ;
#define fi first
#define se second
#define int long long
const int mod=998244353;
int pow(int a,int b, int m){
    if(b==0) return 1;
    int v=pow(a,b/2,m)%m;
    v*=v; v%=m;
    if(b&1) return (v*a)%m;
    return v;
}
 
void solve(){
   int n, x, k;
    cin >> n >> x >> k;
    set<int> s;
    map<int,int> mp;
    for (int i=0; i<n; i++) {
        int h; cin >> h;
        s.insert(h);
        mp[h]++;
    }
    vector<int> h(s.begin(),s.end());
    int ans = lower_bound(h.begin(),h.end(),x*k)-h.begin();
    int m = lower_bound(h.begin(),h.end(),x)-h.begin();
    vector<int> v;
    for (int i=m-1; i>=0; i--) {
        int len = lower_bound(h.begin(),h.end(),h[i]*k)-h.begin();
        if (mp[h[i]]==1) {
            v.push_back(-1*h[i]);
        }
        int cnt = upper_bound(v.begin(),v.end(),-1*h[i]*k)-v.begin();
        cnt = v.size()-cnt;
        ans = max(ans, m-i+len-cnt);
    }
    cout << ans << '\n';
}
 
int32_t main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    clock_t start = clock();
    int t=1;
    cin>>t;
    while(t--) solve();
    clock_t end = clock();
    return 0;
}

```

</details>

<details>
<summary>Java</summary>

```Java
import java.util.*;

public class Main {
    static final int MOD = 998244353;

    static long pow(long a, long b, long m) {
        if (b == 0) return 1;
        long v = pow(a, b / 2, m) % m;
        v = (v * v) % m;
        if ((b & 1) == 1) return (v * a) % m;
        return v;
    }

    static void solve(Scanner scanner) {
        long n = scanner.nextLong();
        long x = scanner.nextLong();
        long k = scanner.nextLong();
        Set<Long> s = new TreeSet<>();
        Map<Long, Long> mp = new HashMap<>();
        
        for (long i = 0; i < n; i++) {
            long h = scanner.nextLong();
            s.add(h);
            mp.put(h, mp.getOrDefault(h, 0L) + 1);
        }
        
        List<Long> h = new ArrayList<>(s);
        long ans = Collections.binarySearch(h, x * k);
        if (ans < 0) ans = -ans - 1;
        long m = Collections.binarySearch(h, x);
        if (m < 0) m = -m - 1;
        
        List<Long> v = new ArrayList<>();
        for (long i = m - 1; i >= 0; i--) {
            long len = Collections.binarySearch(h, h.get((int) i) * k);
            if (len < 0) len = -len - 1;
            if (mp.get(h.get((int) i)) == 1) {
                v.add(-h.get((int) i));
            }
            long cnt = Collections.binarySearch(v, -h.get((int) i) * k);
            if (cnt < 0) cnt = -cnt - 1;
            cnt = v.size() - cnt;
            ans = Math.max(ans, m - i + len - cnt);
        }
        System.out.println(ans);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = 1;
        if (scanner.hasNextLong()) {
            t = scanner.nextInt();
        }
        while (t-- > 0) solve(scanner);
        scanner.close();
    }
}


```

</details>

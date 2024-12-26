## 1. Christmas Gifts

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    h, l, w = map(int, input().split())
    area = 2 * (h * l + h * w + l * w)
    print(1000 // area)

```

</details>

<details>
<summary>Cpp</summary>

```cpp

#include <iostream>
using namespace std;

int main() {
    int T;
    cin >> T;
    while (T--) {
        int H, L, W;
        cin >> H >> L >> W;
        int area = 2 * (H * L + H * W + L * W);
        cout << 1000 / area << endl;
    }
    return 0;
}



```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		Scanner scanner = new Scanner(System.in);
		int T = scanner.nextInt();
		while (T-- > 0) {
			int H = scanner.nextInt();
			int L = scanner.nextInt();
			int W = scanner.nextInt();
			int area = 2 * (H * L + H * W + L * W);
			System.out.println(1000 / area);
		}
		scanner.close();
	}
}


```

</details>

## 2. Chefland Library
<details>
<summary>Python</summary>

```python
t = int(input())

for _ in range(t):
    n = int(input())
    a = list(map(int, input().split()))
    p = {}
    for i in range(n):
        d = a[i]
        l = i + 1
        if d in p:
            p[d] = max(p[d], l)
        else:
            p[d] = l
    
    print(sum(p.values()))

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
    while(t--) {
        int n;
        cin >> n;
        int a[n];
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }
        map <int,int> m;
        for (int i = 0; i < n; i++) {
            m[a[i]] = i+1;
        }
        int sum = 0;
        for (auto i : m) {
            sum += i.second;
        }
        cout << sum << endl;
    }
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); 
        while (t-- > 0) {
            int n = sc.nextInt(); 
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }

            Map<Integer, Integer> map = new TreeMap<>(); 
            for (int i = 0; i < n; i++) {
                map.put(a[i], i + 1); 
            }

            int sum = 0;
            for (int value : map.values()) {
                sum += value; 
            }
            System.out.println(sum); 
        }
        sc.close();
    }
}


```

</details>

## 3. Distinct Power

<details>
<summary>Python</summary>

```python
t = int(input())  
for _ in range(t):
    n = int(input())  
    v = list(map(int, input().split()))  
    
    m = {v[i]: i for i in range(n)}
    sorted_m = sorted(m.items(), key=lambda x: -x[0])

    r = [0] * n
    rank = 1
    for _, idx in sorted_m:
        r[idx] = rank  
        rank += 1

    ans = n
    for i in range(1, n):
        if abs(r[i] - r[i - 1]) == 1:
            ans -= 1  

    print(ans)  

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    
	int t;
	cin>>t;
	while(t--){
	    int n;
	    cin>>n;
	    vector<int> v(n);
	    for(auto &it:v) cin>>it;
	    
	    vector<int> r(n);
	    map<int,int,greater<int>> m;
	    for(int i=0;i<n;i++) m[v[i]]=i;
	    int rank=1;
	    for(auto it:m){
	        r[it.second]=rank;
	        rank++;
	    }
	       
	    int ans=n;
	    for(int i=1;i<n;i++){
	        if(abs(r[i]-r[i-1])==1) ans--;
	    }
	    cout<<ans<<"\n";
	    
	}

}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); 
        while (t-- > 0) {
            int n = sc.nextInt(); 
            int[] v = new int[n];
            for (int i = 0; i < n; i++) {
                v[i] = sc.nextInt(); 
            }

            Map<Integer, Integer> map = new TreeMap<>(Collections.reverseOrder());
            for (int i = 0; i < n; i++) {
                map.put(v[i], i); 
            }

            int[] r = new int[n];
            int rank = 1;
            for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
                r[entry.getValue()] = rank; 
                rank++;
            }

            int ans = n;
            for (int i = 1; i < n; i++) {
                if (Math.abs(r[i] - r[i - 1]) == 1) {
                    ans--; 
                }
            }

            System.out.println(ans); 
        }
        sc.close();
    }
}


```

</details>

## 4. Costly Permutations

<details>
<summary>Python</summary>

```python
import heapq

def getCycleLengths(permutation):
    size = len(permutation)
    is_visited = [False] * size
    cycle_lengths = []

    for i in range(size):
        if not is_visited[i]:
            cycle_size = 0
            current = i
            while not is_visited[current]:
                is_visited[current] = True
                current = permutation[current] - 1
                cycle_size += 1
            cycle_lengths.append(cycle_size)
    
    return cycle_lengths

def main():
    test_cases = int(input())
    
    for _ in range(test_cases):
        n = int(input())
        permutation = list(map(int, input().split()))
        
        cycle_sizes = getCycleLengths(permutation)
        
        min_heap = cycle_sizes[:]
        heapq.heapify(min_heap)
        
        min_cost = 0
        
        while len(min_heap) > 1:
            first_smallest = heapq.heappop(min_heap)
            second_smallest = heapq.heappop(min_heap)
            min_cost += (first_smallest + second_smallest)
            heapq.heappush(min_heap, first_smallest + second_smallest)
        
        print(min_cost)

if __name__ == "__main__":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

vector<int> getCycleLengths(const vector<int>& permutation) {
    int size = permutation.size();
    vector<bool> isVisited(size, false);
    vector<int> cycleLengths;

    for (int i = 0; i < size; ++i) {
        if (!isVisited[i]) {
            int cycleSize = 0, current = i;
            while (!isVisited[current]) {
                isVisited[current] = true;
                current = permutation[current] - 1; 
                cycleSize++;
            }
            cycleLengths.push_back(cycleSize);
        }
    }
    return cycleLengths;
}

int main() {
    int testCases;
    cin >> testCases;

    while (testCases--) {
        int n;
        cin >> n;
        vector<int> permutation(n);
        for (int i = 0; i < n; ++i) {
            cin >> permutation[i];
        }

        vector<int> cycleSizes = getCycleLengths(permutation);

        priority_queue<int, vector<int>, greater<int>> minHeap(cycleSizes.begin(), cycleSizes.end());

        long long minCost = 0;

        while (minHeap.size() > 1) {
            int firstSmallest = minHeap.top(); 
            minHeap.pop();
            int secondSmallest = minHeap.top(); 
            minHeap.pop();
            minCost += (firstSmallest + secondSmallest);
            minHeap.push(firstSmallest + secondSmallest);
        }

        cout << minCost << endl;
    }

    return 0;
}



```

</details>

<details>
<summary>Java</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef {
    public static ArrayList<Integer> getCycleLengths(int[] permutation) {
        int size = permutation.length;
        boolean[] isVisited = new boolean[size];
        ArrayList<Integer> cycleLengths = new ArrayList<>();

        for (int i = 0; i < size; i++) {
            if (!isVisited[i]) {
                int cycleSize = 0;
                int current = i;
                while (!isVisited[current]) {
                    isVisited[current] = true;
                    current = permutation[current] - 1;
                    cycleSize++;
                }
                cycleLengths.add(cycleSize);
            }
        }
        return cycleLengths;
    }

    public static void main(String[] args) throws java.lang.Exception {
        Scanner sc = new Scanner(System.in);
        int testCases = sc.nextInt();

        while (testCases-- > 0) {
            int n = sc.nextInt();
            int[] permutation = new int[n];
            for (int i = 0; i < n; i++) {
                permutation[i] = sc.nextInt();
            }

            ArrayList<Integer> cycleSizes = getCycleLengths(permutation);

            PriorityQueue<Integer> minHeap = new PriorityQueue<>(cycleSizes);

            long minCost = 0;

            while (minHeap.size() > 1) {
                int firstSmallest = minHeap.poll();
                int secondSmallest = minHeap.poll();
                minCost += (firstSmallest + secondSmallest);
                minHeap.offer(firstSmallest + secondSmallest);
            }

            System.out.println(minCost);
        }

        sc.close();
    }
}

```

</details>

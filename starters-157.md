## Non-matching name

<details>
<summary>Python</summary>

```python
def main():
    # Read number of test cases
    t = int(input())
    
    while t > 0:
        t -= 1
        
        # Read lengths of S_A and S_B
        s_a, s_b = map(int, input().split())
        
        # Read the two strings S_A and S_B
        s1 = input()
        s2 = input()
        
        # Use a set to store unique characters
        unique_chars = set()
        
        # Insert all characters from s1
        for char in s1:
            unique_chars.add(char)
        
        # Insert all characters from s2
        for char in s2:
            unique_chars.add(char)
        
        # Check if we have less than 26 unique characters
        if len(unique_chars) < 26:
            print("YES")
        else:
            print("NO")

if _name_ == "_main_":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
    int t;
    cin >> t;
    while(t--)
    {
        unordered_set<char> a;
        int s_a,s_b;
        cin >> s_a >> s_b;
        string s1,s2;
        cin >> s1 >> s2;
        for(int i=0;s1[i];i++)
        {
            a.insert(s1[i]);
        }
        // cout << a.size() << " ";
        for(int i=0;s2[i];i++)
        {
            a.insert(s2[i]);
        }
        // cout << a.size();
        if(a.size() < 26)
            cout << "YES\n";
        else
            cout << "NO\n";
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
        
        // Read number of test cases
        int t = sc.nextInt();
        
        while (t-- > 0) {
            // Read lengths of S_A and S_B
            int s_a = sc.nextInt();
            int s_b = sc.nextInt();
            
            // Read strings S_A and S_B
            String s1 = sc.next();
            String s2 = sc.next();
            
            // Use a set to store unique characters
            Set<Character> uniqueChars = new HashSet<>();
            
            // Add all characters from S_A to the set
            for (int i = 0; i < s_a; i++) {
                uniqueChars.add(s1.charAt(i));
            }
            
            // Add all characters from S_B to the set
            for (int i = 0; i < s_b; i++) {
                uniqueChars.add(s2.charAt(i));
            }
            
            // Check if we have less than 26 unique characters
            if (uniqueChars.size() < 26) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }
        }
        
        sc.close();
    }
}

```

</details>

## Not-too-far Replacement

<details>
<summary>Python</summary>

```python
def main():
    # Read number of test cases
    t = int(input())
    
    for _ in range(t):
        # Read the size of the array
        n = int(input())
        arr = list(map(int, input().split()))
        
        last = arr[n]  # The last element of the array
        
        while True:
            swapped = False
            # Iterate through the array from 0 to n-1
            for i in range(n):
                if arr[i] <= 2 * last:
                    if arr[i] > last:
                        # Swap arr[i] with arr[n]
                        arr[i], arr[n] = arr[n], arr[i]
                        last = arr[n]  # Update last with the new last element
                        swapped = True
            
            # If no swap happened, break the loop
            if not swapped:
                break
        
        # Calculate the sum of the first n elements
        total_sum = sum(arr[:n])
        
        # Output the result
        print(total_sum)

if _name_ == "_main_":
    main()
    
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <cstring>
#include <cmath>
#include <map>
#include <algorithm>
#include <sstream>
using namespace std;


int main() {
   int t;
   int n;
   int curr;
   int arr[205];
   cin>>t;
   while(t--) {
      cin>>n;
      for(int i=0; i<n; i++) {
         cin>>arr[i];
      }
      cin>>curr;
      sort(arr, arr+n);
      
      int ans = 0;
      for(int i=0;i<n;i++) {
         if(arr[i] > curr && arr[i] <= 2*curr) {
            swap(arr[i], curr);
         }
         ans += arr[i];
      }
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

class Codechef {
    public static void main(String[] args) throws java.lang.Exception {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();  // Number of test cases
        for (int T = 0; T < t; T++) {
            int n = sc.nextInt();  
            int arr[] = new int[n + 1];

       
            for (int i = 0; i <= n; i++) {
                arr[i] = sc.nextInt();
            }

            int last = arr[n]; 

        while(1==1){
            boolean swapped=false;
            for (int i = 0; i < n; i++) {
                if (arr[i] <= 2 * last) {
                    if (arr[i] > last) {
                        int temp = arr[i];
                        arr[i] = arr[n];
                        arr[n] = temp;
                        last = arr[n]; 
                        swapped=true;
                    }
                }
            }
            if(swapped){
                continue;
            }else{
                break;
            }
        }

         
            int sum = 0;
            for (int i = 0; i < n; i++) {
                sum += arr[i];
            }

            // Output the result
            System.out.println(sum);
        }

        sc.close();
    }
}

```

</details>

## Small, Smaller, Smallest

<details>
<summary>Python</summary>

```python
def main():
    # Read the number of test cases
    t = int(input())
    
    for _ in range(t):
        # Read the integer n
        n = int(input())
        
        # Read the binary string
        s = input().strip()
        
        # Count the number of '1's in the string
        count_ones = s.count('1')
        
        # If there are no '1's, output n
        if count_ones == 0:
            print(n)
        else:
            # If the number of '1's is even, print 0, otherwise print 1
            if count_ones % 2 == 0:
                print(0)
            else:
                print(1)

if _name_ == "_main_":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

void solve()
{
    ll n;
    cin >> n;
    string s;
    cin >> s;
    int count=0;
    for(int i=0; i<n; i++)
    {
        count += (s[i]=='1');
    }
    if (count&1)
    {
        cout << 1 << endl;
    }
    else if (count>0)cout << 0 << endl;
    else cout << n << endl;
}

int main()
{
    ios_base::sync_with_stdio(0);cin.tie(0);cout.tie(0);    
    int tc=1;
    cin>>tc;
    while(tc--)
    {
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



import java.lang.*;

import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		
	    Scanner sc = new Scanner(System.in);
	    int t=sc.nextInt();
	    for(int T=0;T<t;T++){
	        int n=sc.nextInt();
	        sc.nextLine();
	        String s=sc.nextLine();
	        int countOnes=0;
	        for(char i:s.toCharArray()){
                if(i=='1'){
                    countOnes++;
                }
		    }
		    if(countOnes==0){
		        System.out.println(n);
		    }
		    else{
		    if(countOnes%2==0){
		        System.out.println(0);
		    }else{
		        System.out.println(1);
		    }
		    }
	    }


	}
}

```

</details>

## Normal is Good (Easy)

<details>
<summary>Python</summary>

```python
def solve():
    # Read the size of the array
    n = int(input())
    
    # Read the array
    v = list(map(int, input().split()))
    
    # Initialize variables
    length = 1
    ans = 0
    i = 1
    
    # Traverse the array
    while i < n:
        if v[i] == v[i - 1]:
            length += 1
        else:
            # Calculate sum of subarrays of length 'length'
            ans += (length * (length + 1)) // 2
            length = 1
        i += 1
    
    # For the last segment
    ans += (length * (length + 1)) // 2
    
    # Output the result
    print(ans)

def main():
    # Read the number of test cases
    tc = int(input())
    
    for _ in range(tc):
        solve()

if _name_ == "_main_":
    main()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
#define mod 1000000007
#define endl '\n'
#define f(i, n) for (int i = 0; i < n; i++)
#define read(v) for(auto &it :v){ cin>> it ;}
#define int long long
using namespace std;

void solve();
void init_sublime()
{
#ifndef ONLINE_JUDGE
    freopen("E:/Engineering/SEM-5/COMPETITIVE PROGRAMMING/sublime/input.txt", "r", stdin);
    freopen("E:/Engineering/SEM-5/COMPETITIVE PROGRAMMING/sublime/output.txt", "w", stdout);
#endif
}

int32_t main()
{
    init_sublime();
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int tc = 1;
    cin >> tc;
    while (tc--)
    {
        solve();
    }
}

void solve()
{
    int n;
    cin >> n;
    vector<int>v(n);
    read(v);
    int len = 1;
    int i = 1;
    int ans = 0;
    while (i < n)
    {
        // cout << "HRE" << endl;
        if (v[i] == v[i - 1])
            len++;
        else
        {
            ans += (len * (len + 1)) / 2;
            len = 1;
        }
        i++;
    }
    ans += (len * (len + 1)) / 2;

    cout << ans << endl;
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
        
        // Read number of test cases
        int tc = sc.nextInt();
        
        // Run test cases
        while (tc-- > 0) {
            solve(sc);
        }
        
        sc.close();
    }
    
    static void solve(Scanner sc) {
        // Read the size of the array
        int n = sc.nextInt();
        
        // Read the array
        int[] v = new int[n];
        for (int i = 0; i < n; i++) {
            v[i] = sc.nextInt();
        }
        
        // Initialize variables
        int length = 1;
        int ans = 0;
        int i = 1;
        
        // Traverse the array
        while (i < n) {
            if (v[i] == v[i - 1]) {
                length++;
            } else {
                // Calculate sum of subarrays of length 'length'
                ans += (length * (length + 1)) / 2;
                length = 1;
            }
            i++;
        }
        
        // For the last segment
        ans += (length * (length + 1)) / 2;
        
        // Output the result
        System.out.println(ans);
    }
}

```

</details>



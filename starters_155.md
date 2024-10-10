## Chef and Parole

<details>
<summary>Python</summary>

```python
x = int(input())
print("YES" if x >= 7 else "NO")
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int x;
	cin>>x;
	x>=7 ? cout<<"YES\n" : cout<<"NO\n";
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
        int x = scanner.nextInt();
        System.out.println(x >= 7 ? "YES" : "NO");
        scanner.close();
    }
}
```

</details>

## Rectangled

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n = int(input())
    if n % 2 == 1:
        n -= 1
    result = n // 4
    if n % 4 == 0:
        print(result * result)
    else:
        print(result * (result + 1))
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
	while(t--)
	{
	    int n;
	    cin>>n;
	    if(n%2==1)
	    {
	        n--;
	    }
	    int result=n/4;
	    if(n%4==0)
	    {
	        cout<<result*result<<"\n";
	    }
	    else
	    {
	        cout<<result*(result + 1)<<"\n";
	    }
	}
    return 0;
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
            if (n % 2 == 1) {
                n--;
            }
            int result = n / 4;
            if (n % 4 == 0) {
                System.out.println(result * result);
            } else {
                System.out.println(result * (result + 1));
            }
        }
        
        scanner.close();
    }
}
```

</details>

## GCD to 1 (Easy)

<details>
<summary>Python</summary>

```python
import sys

def main():
    t = int(input())
    
    for _ in range(t):
        n = int(input())
        m = int(input())
        
        mat = [[2 for _ in range(m)] for _ in range(n)]
        
        i = 0
        j = 0
        
        while i < n or j < m:
            if i < n and j < m:
                mat[i][j] = 3
                i += 1
                j += 1
            elif i < n:
                mat[i][j-1] = 3
                i += 1
            else:
                mat[i-1][j] = 3
                j += 1
        
        for row in mat:
            print(*row)

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
	cin>>t;
	
	while(t--){
	    int n,m;
	    cin>>n;
	    cin>>m;
	    
	    vector<vector<int>>mat(n,vector<int>(m,2));
	    
	    int i = 0;
	    int j = 0;
	    
	    while(i<n || j<m){
	        if(i<n && j<m)
	        mat[i++][j++] = 3;
	        else if(i<n)
	        mat[i++][j-1] = 3;
	        else 
	        mat[i-1][j++] = 3;
	    }
	    
	    for(int i=0;i<n;i++){
	        for(int j = 0;j<m;j++){
	            cout<<mat[i][j]<<" ";
	        }
	        cout<<endl;
	    }
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
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        
        while (t-- > 0) {
            int n = scanner.nextInt();
            int m = scanner.nextInt();
            
            int[][] mat = new int[n][m];
            for (int[] row : mat) {
                Arrays.fill(row, 2);
            }
            
            int i = 0;
            int j = 0;
            
            while (i < n || j < m) {
                if (i < n && j < m)
                    mat[i++][j++] = 3;
                else if (i < n)
                    mat[i++][j-1] = 3;
                else 
                    mat[i-1][j++] = 3;
            }
            
            for (i = 0; i < n; i++) {
                for (j = 0; j < m; j++) {
                    System.out.print(mat[i][j] + " ");
                }
                System.out.println();
            }
        }
        
        scanner.close();
    }
}

```

</details>

## GCD to 1 (Hard)

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n, m = map(int, input().split())
    
    # Initialize the matrix with 2
    a = [[2] * m for _ in range(n)]
    
    # Set the diagonal elements to 3
    for i in range(max(n, m)):
        r, c = min(n - 1, i), min(m - 1, i)
        a[r][c] = 3
    
    # Print the matrix
    for row in a:
        print(*row)
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n, m;
        cin >> n >> m;
        
        // Initialize the matrix with 2
        vector<vector<int>> a(n, vector<int>(m, 2));
        
        // Set the diagonal elements to 3
        for (int i = 0; i < max(n, m); i++) {
            int r = min(n - 1, i);
            int c = min(m - 1, i);
            a[r][c] = 3;
        }
        
        // Print the matrix
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                cout << a[i][j] << " ";
            }
            cout << endl;
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();  // Number of test cases
        
        while (t-- > 0) {
            int n = sc.nextInt();
            int m = sc.nextInt();
            
            // Initialize the matrix with 2
            int[][] a = new int[n][m];
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    a[i][j] = 2;
                }
            }
            
            // Set the diagonal elements to 3
            for (int i = 0; i < Math.max(n, m); i++) {
                int r = Math.min(n - 1, i);
                int c = Math.min(m - 1, i);
                a[r][c] = 3;
            }
            
            // Print the matrix
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    System.out.print(a[i][j] + " ");
                }
                System.out.println();
            }
        }
        
        sc.close();
    }
}
```

</details>

## Replace with First

<details>
<summary>Python</summary>

```python
def main():
    t = int(input())
    for _ in range(t):
        n, m = map(int, input().split())
        s = input().strip()
        t = input().strip()
        
        if s[0] != t[0]:
            print(-1)
        else:
            if s == t:
                print(0)
            else:
                a = 0
                for i in range(min(n, m)):
                    if s[i] == t[i]:
                        a += 1
                    else:
                        break
                
                b = 0
                for i in range(min(n, m)):
                    if s[n - i - 1] == t[m - i - 1]:
                        b += 1
                    else:
                        break
                if a + b >= min(n, m):
                    print(1)
                else:
                    print(2)

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
    int t;
    cin>>t;
    while(t--){
        int n, m;
        cin>>n>>m;
        string s, t;
        cin>>s;
        cin>>t;
        if(s[0] != t[0]){
            cout<<-1<<"\n";
        }else{
            if(s == t){
                cout<<0<<"\n";
            }else{
                int a = 0;
                for(int i = 0; i < min(n, m); i++){
                    if(s[i] == t[i]){
                        a++;
                    }else{
                        break;
                    }
                }
                int b = 0;
                for(int i = 0; i < min(n, m); i++){
                    if(s[n - i - 1] == t[m - i - 1]){
                        b++;
                    }else{
                        break;
                    }
                }
                if(a + b >= min(n, m)){
                    cout<<1<<"\n";
                }else{
                    cout<<2<<"\n";
                }
            }
        }
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();  // Test cases
        
        while (t-- > 0) {
            int n = sc.nextInt();
            int m = sc.nextInt();
            String s = sc.next();  // String s
            String u = sc.next();  // Renamed second string to u to avoid conflict
            
            if (s.charAt(0) != u.charAt(0)) {
                System.out.println(-1);
            } else {
                if (s.equals(u)) {
                    System.out.println(0);
                } else {
                    int a = 0;
                    for (int i = 0; i < Math.min(n, m); i++) {
                        if (s.charAt(i) == u.charAt(i)) {
                            a++;
                        } else {
                            break;
                        }
                    }
                    
                    int b = 0;
                    for (int i = 0; i < Math.min(n, m); i++) {
                        if (s.charAt(n - i - 1) == u.charAt(m - i - 1)) {
                            b++;
                        } else {
                            break;
                        }
                    }
                    
                    if (a + b >= Math.min(n, m)) {
                        System.out.println(1);
                    } else {
                        System.out.println(2);
                    }
                }
            }
        }
        
        sc.close();
    }
}
```

</details>

## 1. Technex Tickets

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n = int(input())
    ans = 0
    while n > 3:
        n -= 2
        ans += 1
    ans += 1 if n == 1 or n == 3 else 2
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
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        int ans = 0;
        while (n > 3) {
            n -= 2;
            ans++;
        }
        if (n == 1 || n == 3)
            ans += 1;
        else
            ans += 2;
        cout << ans << endl;
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
            int ans = 0;
            while (n > 3) {
                n -= 2;
                ans++;
            }
            ans += (n == 1 || n == 3) ? 1 : 2;
            System.out.println(ans);
        }
        sc.close();
    }
}


```

</details>

## 2. Make same

<details>
<summary>Python</summary>

```python

def solution():
    n = int(input())
    s1, s2, s3 = input(), input(), input()

    zeroes1, ones1 = s1.count('0'), s1.count('1')
    zeroes2, ones2 = s2.count('0'), s2.count('1')
    zeroes3, ones3 = s3.count('0'), s3.count('1')

    if (zeroes1 + zeroes2 + zeroes3) % n != 0:
        print(-1)
        return

    ans1 = min(min(zeroes2, ones2), min(zeroes3, ones3))
    ans2 = min(min(zeroes1, ones1), max(min(zeroes2, ones2), min(zeroes3, ones3)))
    print(ans1 + ans2)


t = int(input())
for _ in range(t):
    solution()

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;

void solution(){
    int n;
    cin>>n;
    string s1,s2,s3;
    cin>>s1;
    cin>>s2;
    cin>>s3;
    
    int zeroes1=0;
    int ones1=0;
    int zeroes2=0;
    int ones2=0;
    int zeroes3=0;
    int ones3=0;
    
    for(int i=0;i<n;i++){
        if(s1[i]=='0') zeroes1++;
        if(s1[i]=='1') ones1++;
        
        if(s2[i]=='0') zeroes2++;
        if(s2[i]=='1') ones2++;
        
        if(s3[i]=='0') zeroes3++;
        if(s3[i]=='1') ones3++;
    }
    
    if((zeroes1+zeroes2+zeroes3)%n != 0){
        cout<<-1<<endl;
        return;
    }
    int ans1=min(min(zeroes2,ones2),min(zeroes3,ones3));
    int ans2=min(min(zeroes1,ones1),max(min(zeroes2,ones2),min(zeroes3,ones3)));
    cout<<ans1+ans2<<endl;
}

int main() {
	// your code goes here
	int t;
	cin>>t;
	while(t--){
	    solution();
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
            solution(sc);
        }
        sc.close();
    }

    private static void solution(Scanner sc) {
        int n = sc.nextInt();
        String s1 = sc.next(), s2 = sc.next(), s3 = sc.next();

        int zeroes1 = 0, ones1 = 0;
        int zeroes2 = 0, ones2 = 0;
        int zeroes3 = 0, ones3 = 0;

        for (int i = 0; i < n; i++) {
            if (s1.charAt(i) == '0') zeroes1++;
            if (s1.charAt(i) == '1') ones1++;
            if (s2.charAt(i) == '0') zeroes2++;
            if (s2.charAt(i) == '1') ones2++;
            if (s3.charAt(i) == '0') zeroes3++;
            if (s3.charAt(i) == '1') ones3++;
        }

        if ((zeroes1 + zeroes2 + zeroes3) % n != 0) {
            System.out.println(-1);
            return;
        }

        int ans1 = Math.min(Math.min(zeroes2, ones2), Math.min(zeroes3, ones3));
        int ans2 = Math.min(Math.min(zeroes1, ones1), Math.max(Math.min(zeroes2, ones2), Math.min(zeroes3, ones3)));
        System.out.println(ans1 + ans2);
    }
}

```

</details>

## 3. Alternate It!

<details>
<summary>Python</summary>

```python
def check(s):
    return all(s[i] != s[i + 1] for i in range(len(s) - 1))

t = int(input())
for _ in range(t):
    s = input()
    a, b = s.count('1'), s.count('0')

    if a == b:
        print(0 if check(s) else 1)
    else:
        count = abs(a - b)
        op = count // 2

        if op == 0:
            print(0 if check(s) else 1)
        elif op == 1:
            print(2)
        else:
            print(3)


```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

bool check(string s){
    for(int i=0;i<s.size()-1;i++){
        if(s[i]==s[i+1])
        return false;
    }
    return true;
}
int main() {
	// your code goes here
    int t;
    cin>>t;
    while(t--){
        
        string s;
        cin>>s;
        
        int a=0;
        int b=0;
        for(int i=0;i<s.size();i++){
            if(s[i]=='1'){
                a++;
            }
            else{
                b++;
            }
        }
        
        if(a==b){
            if(check(s)==true)
            cout<<0<<endl;
            
            else
            cout<<1<<endl;
        }
        
        else{
            int count=abs(a-b);
            int op=count/2;
            
            if(op==0){
                if(check(s)==true){
                    cout<<0<<endl;
                }
                else{
                    cout<<1<<endl;
                }
            }
            
            if(op==1){
                cout<<2<<endl;
            }
            
            if(op>=2){
                cout<<3<<endl;
            }
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            String s = sc.next();
            int a = 0, b = 0;

            for (char c : s.toCharArray()) {
                if (c == '1') a++;
                else b++;
            }

            if (a == b) {
                System.out.println(check(s) ? 0 : 1);
            } else {
                int count = Math.abs(a - b);
                int op = count / 2;

                if (op == 0) {
                    System.out.println(check(s) ? 0 : 1);
                } else if (op == 1) {
                    System.out.println(2);
                } else {
                    System.out.println(3);
                }
            }
        }
        sc.close();
    }

    private static boolean check(String s) {
        for (int i = 0; i < s.length() - 1; i++) {
            if (s.charAt(i) == s.charAt(i + 1)) return false;
        }
        return true;
    }
}

```

</details>

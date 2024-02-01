# Codechef_starters_117_Div3

<!-- First Question -->

# Judged

<details>
<summary>Python</summary>

```python
# Your Python code goes here
t = int(input())

while t > 0:
    cnt = 0
    for i in range(5):
        x = int(input())
        if x == 1:
            cnt += 1
    
    if cnt >= 4:
        print("YES")
    else:
        print("NO")
    
    t -= 1

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
	cin>>t;
	while(t--)
	{ int cnt=0;
	    for(int i=0;i<5;i++)
	    {
	        int x;
	        cin>>x;
	        if(x==1)cnt++;
	       
	    }
	    if(cnt>=4) cout<<"YES"<<endl;
	    else cout<<"NO"<<endl;
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

        while (t > 0) {
            int cnt = 0;
            for (int i = 0; i < 5; i++) {
                int x = scanner.nextInt();
                if (x == 1) {
                    cnt++;
                }
            }

            if (cnt >= 4) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }

            t--;
        }
    }
}

```

</details>

<!-- Second Question -->

# Cookie Day

<details>
<summary>Python</summary>

```python
# Your Python code goes here
t = int(input())

while t > 0:
    n, k = map(int, input().split())
    flag = 0
    mrem = float('inf')
    rem = 0

    for i in range(n):
        x = int(input())
        if x >= k:
            flag = 1
            rem = x % k
            mrem = min(mrem, rem)

    if flag == 0:
        print("-1")
    else:
        print(mrem)

    t -= 1

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
	cin>>t;
	while(t--)
	{
	    int n,k;
	    cin>>n>>k;
	    int flag=0;
	    int mrem=INT_MAX;
	    int rem=0;
	    for(int i=0;i<n;i++)
	    {
	        int x;
	        cin>>x;
	        if(x>=k){
	            flag=1;
	            rem=x%k;
	            mrem=min(mrem,rem);}
	    }
	    if(flag==0){cout<<"-1"<<endl;}
	    else{cout<<mrem<<endl;}
	    
	}

}

```

</details>
<!-- Java -->
<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t > 0) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            int flag = 0;
            int mrem = Integer.MAX_VALUE;
            int rem = 0;

            for (int i = 0; i < n; i++) {
                int x = scanner.nextInt();
                if (x >= k) {
                    flag = 1;
                    rem = x % k;
                    mrem = Math.min(mrem, rem);
                }
            }

            if (flag == 0) {
                System.out.println("-1");
            } else {
                System.out.println(mrem);
            }

            t--;
        }
    }
}

```

</details>

<!-- Third Quesion -->

# Another Good String

<details>
<summary>Python</summary>

```python
t = int(input())

while t > 0:
    n, k = map(int, input().split())
    flag = 0
    mrem = float('inf')
    rem = 0

    for i in range(n):
        x = int(input())
        if x >= k:
            flag = 1
            rem = x % k
            mrem = min(mrem, rem)

    if flag == 0:
        print("-1")
    else:
        print(mrem)

    t -= 1

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
	cin>>t;
	while(t--)
	{
	    int n,k;
	    cin>>n>>k;
	    string s;
	    cin>>s;
	    int ans=INT_MIN;int flag=0;
	    int cnt=1;char last=s[n-1];//int lcnt=1;
	    for(int i=1;i<n;i++)
	    {
	    if(s[i]==s[i-1]){ cnt++;
	                     ans=max(ans,cnt);}
	   else cnt=1;                 
	  
	   	    }
	 //  cout<<last<<lcnt<<endl;
	    cout<<(ans==INT_MIN?1:ans)<<" ";
	    while(k--)
	    {
	        char c;
	        cin>>c;
	      // cout<<last<<(c==last)<<lcnt<<" ";
	        if(c!=last){cnt=1;ans=max(ans,cnt);cout<<ans<<" ";}
	    if(c==last){cnt++;ans=max(ans,cnt);cout<<ans<<" ";}
	    last=c;
	      // cout<<la<<" ";
	    }
	    
	  cout<<endl;  
	    
	}

}

```

</details>

<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t > 0) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            int flag = 0;
            int mrem = Integer.MAX_VALUE;
            int rem = 0;

            for (int i = 0; i < n; i++) {
                int x = scanner.nextInt();
                if (x >= k) {
                    flag = 1;
                    rem = x % k;
                    mrem = Math.min(mrem, rem);
                }
            }

            if (flag == 0) {
                System.out.println("-1");
            } else {
                System.out.println(mrem);
            }

            t--;
        }
    }
}

```

</details>

<!-- Fourth Question -->

# K odd sum

<details>
<summary>Python</summary>

```python
t = int(input())

while t > 0:
    n, k = map(int, input().split())
    odd = [i for i in range(1, n + 1) if i % 2 == 1]
    even = [i for i in range(1, n + 1) if i % 2 == 0]

    print(odd[-1], end=" ")
    odd.pop()

    i = 0
    flip = 1
    while i < k - 1:
        flip = not flip
        if flip:
            print(odd[-1], end=" ")
            odd.pop()
        else:
            print(even[-1], end=" ")
            even.pop()
        i += 1

    if not flip:
        odd, even = even, odd

    print(*odd, *even)
    t -= 1

```

</details>

<details>
  	<summary>C++</summary>
  

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
	int t;
	cin>>t;
	while(t--)
	{
	    int n,k;
	    cin>>n>>k;
	    vector<int>odd,even;
	    for(int i=1;i<=n;i++)
	    {
	        if(i%2)odd.push_back(i);
	        else even.push_back(i);
	    }
	    cout<<odd.back()<<" "; 
	    odd.pop_back();
	    int i=0;
	    int flip=1;
	    while(i<k-1)
	    {
	       flip=!flip;
	       if(flip)
	        {
	            cout<<odd.back()<<" ";
	            odd.pop_back();
	        }
	        else
	        {
	            cout<<even.back()<<" ";
	            even.pop_back();
	        }
	        i++;
	    }
	    if(!flip)swap(odd,even);
	    
	        for(auto it:odd)cout<<it<<" ";
	        for(auto it:even)cout<<it<<" ";
	    cout<<endl;
	}
	

}

```

</details>

<details>

	<summary>JAVA</summary>

  

```java
import java.util.Scanner;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t > 0) {
            int n = scanner.nextInt();
            int k = scanner.nextInt();
            ArrayList<Integer> odd = new ArrayList<>();
            ArrayList<Integer> even = new ArrayList<>();

            for (int i = 1; i <= n; i++) {
                if (i % 2 == 1) {
                    odd.add(i);
                } else {
                    even.add(i);
                }
            }

            System.out.print(odd.get(odd.size() - 1) + " ");
            odd.remove(odd.size() - 1);

            int i = 0;
            boolean flip = true;
            while (i < k - 1) {
                flip = !flip;
                if (flip) {
                    System.out.print(odd.get(odd.size() - 1) + " ");
                    odd.remove(odd.size() - 1);
                } else {
                    System.out.print(even.get(even.size() - 1) + " ");
                    even.remove(even.size() - 1);
                }
                i++;
            }

            if (!flip) {
                ArrayList<Integer> temp = odd;
                odd = even;
                even = temp;
            }

            for (int num : odd) {
                System.out.print(num + " ");
            }
            for (int num : even) {
                System.out.print(num + " ");
            }

            System.out.println();
            t--;
        }
    }
}

```

</details>

<!-- Fifth Question -->

# Unalike GCD & LCM

<details>
<summary>Python</summary>
  

```python
modd = 1000000007

def primedivisors(n):
    primes = []
    for i in range(2, int(n**0.5) + 1):
        cnt = 0
        while n % i == 0:
            n //= i
            cnt += 1
        if cnt != 0:
            primes.append(cnt)
    
    if n > 1:
        primes.append(1)
    
    return primes

t = int(input())

while t > 0:
    n, q = map(int, input().split())
    primes = primedivisors(n)
    
    while q > 0:
        p = int(input())
        ans = 1
        
        if p == 1:
            print(1)
            q -= 1
            continue
        else:
            for it in primes:
                if it % p == 0:
                    ans = (ans * 2) % modd
        
        print(ans)
        q -= 1
    
    t -= 1

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;
const int modd=1000000007;
vector<int> primedivisors(int n)
{
    int cnt=0;
	    vector<int>primes;
	    for(int i=2;i*i<=n;i++)
	    {
	        int cnt=0;
	        while(n%i==0)
	        {
	            n=n/i;
	           // flag=1;
	            cnt++;
	        }
	        
	        if(cnt!=0){primes.push_back(cnt);}
	    }
	 return primes;
}

int main() {
	// your code goes here
	int t ;
	cin>>t;
	while(t--)
	{
	    int n,q;
	    cin>>n>>q;
	 // for(auto it:primes)cout<<it<< ""
	 vector<int>primes=primedivisors(n);
	  while(q--)
	  {
	      int p;
	      cin>>p;int ans=1;
	      if(p==1){cout<<1<<endl;continue;}
	      else{
	      for(auto it:primes)
	      { //int y1=0;int y2=0;
	          if((it%p)==0) 
	         
	              ans=(ans*2)%modd;
	          
	      }
	      cout<<ans<<endl;
	  }
	 
	}
}
}

```

</details>

<details>
<summary>Java</summary>

```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    static final int modd = 1000000007;

    static ArrayList<Integer> primedivisors(int n) {
        ArrayList<Integer> primes = new ArrayList<>();
        for (int i = 2; i * i <= n; i++) {
            int cnt = 0;
            while (n % i == 0) {
                n /= i;
                cnt++;
            }
            if (cnt != 0) {
                primes.add(cnt);
            }
        }
        if (n > 1) {
            primes.add(1);
        }
        return primes;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t > 0) {
            int n = scanner.nextInt();
            int q = scanner.nextInt();
            ArrayList<Integer> primes = primedivisors(n);

            while (q > 0) {
                int p = scanner.nextInt();
                int ans = 1;

                if (p == 1) {
                    System.out.println(1);
                    q--;
                    continue;
                } else {
                    for (int it : primes) {
                        if (it % p == 0) {
                            ans = (int) ((long) ans * 2 % modd);
                        }
                    }
                }

                System.out.println(ans);
                q--;
            }

            t--;
        }
    }
}

```

</details>

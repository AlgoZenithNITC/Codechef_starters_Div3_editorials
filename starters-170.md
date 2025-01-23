## Minimum Bottles

<details>
<summary>Python</summary>

```python
import math
if _name_ == "_main_":
  t = int(input())
  while(t):
    n, k = map(int,input().split())
    sum = 0
    arr = list(map(int,input().split()))
    for water in arr:
        sum += water
    print(math.ceil(sum / k))
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
    while(t--){
        int n,k;
        cin>>n>>k;
        int sum = 0;
        for(int i = 0; i < n; i++){
            int x;
            cin>>x;
            sum += x;
        }
        cout<<ceil((double)sum / (double)k)<<endl;
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
	  Scanner sc=new Scanner(System.in);
	  int t=sc.nextInt();
	  for(int i=0;i<t;i++){
	      int n=sc.nextInt();
	      
	      int x=sc.nextInt();
	      int a[]= new int[n];
	      for(int j=0;j<n;j++){
	          a[j]=sc.nextInt();
	      }
	      int count=0;
	      int y=0;
	  for(int j=0;j<n;j++){
	    count=count+a[j];
	  }
	if(count%x==0){
	    System.out.println(count/x);
	}
	else{
	    System.out.println(count/x+1);
	}
	  }

	}
}

```

</details>

## Monster Monster

<details>
<summary>Python</summary>

```python
t = int(input())  # Read number of test cases
for _ in range(t):
    n, x = map(int, input().split())  # Read number of monsters and the HP increase per day
    v = list(map(int, input().split()))  # Read the initial HP stats of the monsters
    v.sort(reverse=True)  # Sort the HP list in descending order
    sum_hp = 0
    maxi = float('-inf')
    for i in range(1, n):
        sum_hp += x  # HP increases by X each day
        maxi = max(sum_hp + v[i], maxi)  # Calculate the maximum required attack power
    print(max(maxi, v[0]))  # Output the result: max of the first monster's HP and calculated max
```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes herei
	int t;
	cin >> t;
	while(t--){
	    long long n, x;
	    cin >> n >> x;
	    vector<long long> v(n);
	    for(int i = 0; i < n; i++)
	    {
	        cin >> v[i];
	    }
	    sort(v.rbegin(), v.rend());
	    long long sum = 0, maxi = INT_MIN;
	    for(int i = 1; i < n; i++){
	        sum += x;
	        maxi = max(sum + v[i], maxi);
	    }
	    cout << max(maxi, v[0]) << endl;
	}
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
    public static void main(String[] args) throws java.lang.Exception {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        for (int i = 0; i < t; i++) {
            int n = sc.nextInt();
            int x = sc.nextInt();
            
            int arr[] = new int[n];
            for (int j = 0; j < n; j++) {
                arr[j] = sc.nextInt();
            }
            
            Arrays.sort(arr);
            for (int j = 0; j < n / 2; j++) {
                int temp = arr[j];
                arr[j] = arr[n - j - 1];
                arr[n - j - 1] = temp;
            }
            
            long max = arr[0];
            for (int k = 1; k < n; k++) {
                long tmp = arr[k] + k * (long) x;
                max = Math.max(max, tmp);
            }
            System.out.println(max);
        }
    }
}

```

</details>

## Crazy Jumping Frogs

<details>
<summary>Python</summary>

```python
t = int(input())
for _ in range(t):
    n = int(input())
    a = list(map(int, input().split()))
    cnt = 0
    cntt = 0
    for i in range(n):
        if a[i] % 2 == 0:
            cnt += 1
        else:
            cntt += 1
    print(max(cnt, cntt))

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
	    int n;
	    cin >> n;
	    vector<int> a(n);
	    for(int i = 0; i < n; i++)
	    {
	        cin >> a[i];
	    }
	    int cnt = 0, cntt = 0;
	    for(int i = 0; i < n; i++)
	    {
	        if(a[i] % 2 == 0) cnt++;
	        else cntt++;
	    }
	    cout << max(cnt, cntt)<< endl;
	}
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
		// your code goes here
		 Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int n = sc.nextInt();
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }
            int cnt = 0, cntt = 0;
            for (int i = 0; i < n; i++) {
                if (a[i] % 2 == 0) cnt++;
                else cntt++;
            }
            System.out.println(Math.max(cnt, cntt));
        }
        sc.close();

	}
}

```

</details>

## qUiRkY qUesTs (Easy)

<details>
<summary>Python</summary>

```python
for _ in range(int(input())):
    n=int(input())
    a=list(map(int,input().split()))
    ans1=sum(a)
    ans2=n*n
    ans3=0
    a.sort(reverse=1)
    x=0
    for i in range(n):
        x+=a[i]
        ans3=max(ans3, x + ((n-i-1)*(n-i-1))) 
    print(max(ans1,ans2,ans3))

```

</details>

<details>
<summary>Cpp</summary>

```cpp
#include<bits/stdc++.h>
#define ll long long int
using namespace std;
int main(){

 ios::sync_with_stdio(false);
 cin.tie(nullptr); 


   int test;
   cin>>test;
   while (test--)
   {
       ll n;
       cin>>n;
       ll arr[n];
       ll sum = 0;
       for (int i = 0; i <n; i++)
       {
          cin>>arr[i];
          sum+=arr[i];
       }


        ll ans = sum;

       sort(arr,arr+n);


       for (ll i = 0; i<n; i++)
       {
           sum-=arr[i];
           ll temp = ((i+1)*(i+1))+sum;
           ans = max(ans,temp);
       }


       cout<<ans<<"\n";
       
       
       
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
		// your code goes here
		Scanner in =new Scanner(System.in);
		int t=in.nextInt();
		while(t-->0){
		   int a=in.nextInt();
		   long arr[]=new long[a];
		   for(int i=0;i<a;i++){
		       arr[i]=in.nextLong();
		   }
		   long sum=0;
		   Arrays.sort(arr);
		   int i=0;
		    for( i=0;i<a;i++){
		       sum=Math.max((i+1L)*(i+1L),sum+arr[i]);
		   }
		   sum=Math.max(sum,(long)a*a);
		   System.out.println(sum);
		   
		}

	}
}

```

</details>


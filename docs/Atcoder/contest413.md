[contest413](https://atcoder.jp/contests/abc413)

### A

> 先求和，然后比大小

```c++
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
#define int long long
const int N = 110;
int n , m ,t;
void solve() {
    int sum = 0;
    cin >> n>> m;for (int i = 1;i <= n;i++){cin >> t;sum+=t;}
    if (sum > m)cout << "No";
    else cout << "Yes" ;
}
signed main() {
    solve();return 0;
}
```

### B

> 暴力求解，求出所有可能，并消去相同的结果

```c++
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
int n,num = 0;
string s[110];
string ss[11000];
bool check(string t) {
    for (int i = 1;i <= num;i++) {
        if (ss[i] == t)return false;
    }
    return true;
}
void solve() {
    cin >> n;
    for (int i = 1;i <= n;i++)cin >> s[i];
    for (int i = 1;i < n;i++) {
        for (int j = i +1 ;j <= n;j++) {
            string t;t = s[i]+s[j];if (check(t))ss[++num] = t;
            t = s[j] + s[i];if (check(t))ss[++num] = t;
        }
    }
    cout << num;
}
signed main() {
    solve();return 0;
}
```

### C

> 开两个数组分别存c和x，从头开始计算c的累加和，与k比较，子结论相乘，输出结果，更新第c[i]的值，保证下一次从c[i]开始计算

```c++
#include <iostream>
#include <algorithm>
using namespace std;
const int N = 2e5+10;
#define int long long
int q,a[N],b[N],num = 0;
void solve() {
    cin >> q;int flag = 1;
    while (q--) {
        int x,k;cin >> x;
        if (x == 1) {
            ++num;cin >> a[num] >> b[num];
        }
        else {
            cin >> k;int sum = 0,numm = 0;
            for (int i = flag;i <= num;i++) {
                numm += a[i];
                if (numm < k){sum+=a[i] * b[i];continue;}
                else {
                    int t = a[i];
                    flag = i;
                    a[flag] = numm - k;
                    sum += (t-a[flag]) * b[i];
                    break;
                }
            }
            cout << sum << endl;
        }
    }
}
signed main() {
    solve();return 0;
}
```

### D

> 对给定序列按照绝对值从小到大排序，特殊讨论所有元素的绝对值均相同的特殊情况

```c++
#include <iostream>
#include <algorithm>
#include <cstring>
#include <cmath>
using namespace std;
#define int long long
const int N = 2e5+10;
int t,n;
struct Node{
    int x;
    int flag = 0;
    bool operator<(const Node &other) const {
        return x < other.x; // 按x升序排列
    }
}a[N];
void solve() {
    int x = 0,y = 0;
    cin >> n;for (int i = 1;i <= n;i++)a[i].flag = 0;
    for (int i = 1;i <= n;i++) {
        cin >> a[i].x;if (a[i].x < 0){x++;a[i].flag = 1;a[i].x = abs(a[i].x);}else{y++;}
    }
    int num=abs(a[1].x);
    int flag=1;
    for(int i=2;i<=n;i++)
        if(abs(a[i].x)!=num){
            flag=0;
            break;
        }
    if(flag){
        if(x==y||abs(x-y)==1||x==n||y==n) cout<<"Yes" << endl;
        else cout<<"No" << endl;return;
    }
    flag = 0;sort(a+1,a+n+1);
    for (int i = 1;i <= n;i++) {
        if(a[i].flag)a[i].x = 0 - a[i].x;
    }
    for (int i = 3;i <= n;i++) {
        if(a[i].x * a[1].x == a[i-1].x * a[2].x)continue;
        else {
            flag = 1;cout << "No" << endl;return;
        }
    }
    if (flag == 0)cout << "Yes" << endl;
}
signed main() {
    cin >> t;while (t--)solve();return 0;
}
```


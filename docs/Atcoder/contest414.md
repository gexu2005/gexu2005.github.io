### A

> 统计包含区间【L～R】区间个数，输出。

```c++
#include <iostream>
#include <algorithm>
#include <cstring>
using namespace std;
#define int long long
const int N = 1010;
int n,x,y,xx,yy;
void solve(){
    int num = 0;cin >> n >> x >> y;
    for (int i = 1;i <= n;i++) {
        cin >> xx >> yy;if (xx <= x && yy >= y)num++;
    }
    cout << num ;
}
signed main(){
    solve();return 0;
}
```

### B

> 避免超时，先进行长度的计算，如果添加后的长度小于100，再添加，大于100直接continue，最后输出结果即可。

```c++
#include <iostream>
#include <algorithm>
#include <cstring>
#include <string>
using namespace std;
#define int long long
string s;
void solve() {
    int n;cin >> n;
    string c;int num = 0,cnt = 0;
    while (n--) {
        cin >> c >> num;
        if (cnt > 100)continue;
        else cnt+=num;
        if (cnt > 100)continue;
        else for (int i = 0;i < num;i++)s+=c;
    }
    if (cnt > 100)cout << "Too Long";
    else cout << s;
}
signed main() {
    solve();return 0;
}
```

### C

> 优化求解回文数的方式，对于大于二位以上的数字，采取先求解偶数位数回文数，在求解奇数位数回文数的方式，将时间复杂度优化到O(sqrt(n)),具体代码如下：

```c++
#include <iostream>
#include <algorithm>
#include <cstring>
#include <string>
using namespace std;
#define int long long
int a,n,sum = 0;
const string digits = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
bool isPds(int num) {
    string s = to_string(num);
    string rev = s;
    ranges::reverse(rev);
    return s == rev;
}
bool ispd(string a) {
    string b = a;ranges::reverse(a);
    return b == a;
}
string ct(int num) {
    string result;
    if (n == 0)return "0";
    while (num > 0) {
        result += digits[num%a];
        num/=a;
    }
    return result;
}
bool check(int u) {
    if (isPds(u)) {
        if (ispd(ct(u)))return true;
    }
    return false;
}
void solve() {
    cin >> a >> n;
    for (int i = 1;i <= n;i++) {
        if (i >= 10)break;
        if (i < 10 && check(i))sum+=i;
    }
    for (int i = 1;;++i) {
        string s = to_string(i);
        string revs(s.rbegin(),s.rend());
        if (s.length() <= 9) {
            int ep = stoll(s + revs);
            if (ep > n)break;
            else if (check(ep))sum+=ep;
        }
        else break;
        if (s.length() <= 7) {
            for (char mid = '0'; mid <= '9'; ++mid) {
                int op = stoll(s + mid + revs);
                if (op > n) continue;
                else if(check(op))sum+=op;
            }
        }
        else break;
    }
    cout << sum;
}
signed main() {
    solve();return 0;
}


```

### D

> 将问题简化为用总长度减去m个最大的间隔。可以简单的理解为，我们有m个基站，那么多个房屋之间具有不同的距离，我们可以有权选择m个间隔不覆盖，只覆盖除了这m个间隔以外的地方，这样也可以保证所有的房子都会被基站覆盖到。

```c++
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;
const int N = 5e5+10;
#define int long long
int x[N],y[N];
int n,m;
void solve() {
    cin >> n >> m;for (int i = 1;i <= n;i++)cin >> x[i];
    if (n <= m){cout << "0";return;}
    sort(x+1,x+n+1);
    for(int i = 1;i < n;i++)y[i] = x[i + 1]-x[i];
    int result = x[n] - x[1];
    sort(y+1,y+n);
    for(int i = n-1;i >=n - m + 1;--i)result -= y[i];
    cout << result << endl;
}
signed main() {
     solve();return 0;
}

```


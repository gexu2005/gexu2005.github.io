# A
> 冒泡排序
```C++
#include <iostream>
#include <algorithm>
using namespace std;
#define int long long
const int N = 1e5+10;
int n,a[N];
void solve(){
    cin >> n;for(int i = 1;i <= n;i++)cin >> a[i];
    for(int i = 1;i < n;i++){
        for (int j = 1;j < n - i;j++){
            if(a[j] > a[j + 1]){
                int temp = a[j];a[j] = a[j + 1];a[j + 1] = temp;
            }
        }
    }
}
signed main(){int _;cin >> _;while(_--)solve();return 0;}
```
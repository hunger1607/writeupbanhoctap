# DEADLINE LƯU ĐỒ THUẬT TOÁN
"Món quà" đầu tiên mà các anh chị tặng mình khi mới vào Ban học tập -_-
![image](https://user-images.githubusercontent.com/88484431/140250344-2a1ec725-3cc9-4676-b4c0-8720f3ea6773.png)

## Bài 1

## Ý tưởng
Với một tâm hồn ngây thơ trong sáng thì mình đã từng nghĩ: dùng vòng for là được chứ gì đâu :D cơ mà làm vậy thì tốn mất 10 lần nhân, như thế thì không kinh tế lắm :/ 

Ta thấy: 
```bash
• x^11 = x^6 * x^5;
• x^6 = x^3 * x^3;   x^5 = x^3 * x^2;
• x^3 = x^2 * x;
```
Vậy ta cần tính x^2, x^3, x^5, và x^6. Tổng cộng ta có 5 lần nhân.

Note: 
## Lưu đồ 

## Code
```c++
#include <iostream>

using namespace std;

int main()
{
    int x;
    cout << "x = "; cin >> x;
    int x2 = x * x; //1 lan
    int x3 = x2 * x; //2 lan
    int x5 = x3 * x2; //3 lan
    int x6 = x3 * x3; //4 lan
    int x11 = x5 * x6; // 5 lan
    cout << x11;
    return 0;
}
```

## Bài 2
![image](https://user-images.githubusercontent.com/88484431/140286046-640c00f0-d209-41df-a242-26f1b49e8c85.png)
## Ý tưởng
Ta sẽ tìm cách tách từng chữ số của n ra rồi cộng lại với nhau, bằng cách chia lấy dư n cho 10. Sau khi chia, ta cần loại bỏ chữ số vừa sử dụng ra để tiếp tục tính toán, bằng cách lấy n chia nguyên cho 10.
## Lưu đồ

## Code
```c++
#include <iostream>

using namespace std;

int main()
{
    int n, sum = 0;
    cout << "n = "; cin >> n;
    while(n != 0)
    {
        sum += n % 10;
        n /= 10;
    }
    cout << sum;
    return 0;
}
```
## Bài 3
![image](https://user-images.githubusercontent.com/88484431/140250826-90f9cafd-51e5-4da8-bd87-e2df19773733.png)
## Ý tưởng
Tạo một vòng lặp chạy từ 1 đến n, trên tử sẽ là x^i, dưới mẫu sẽ là tổng các số từ 1 đến i.
## Lưu đồ

## Code
Để tiện hơn, ta viết một hàm ```sum()```, dùng để tính tổng các số từ 1 đến i, và hàm ```myPow()``` dùng để tính lũy thừa (mấy anh không cho xài thư viện :<). 
Đồng thời, hàm ```sum()``` và ```myPow()``` phải trả về số thực, để khi chia ta được kết quả là số thực
```c++
#include<iostream>

using namespace std;

double sum(int index)
{
    int res = 0;
    for(int k = 1; k <= index; ++k) res += k;
    return res;
}
double myPow(int base, int hat)
{
    int res = 1;
    for(int k = 1; k <= hat; ++k) res *= base;
    return res;
}

int main()
{
    int x, n;
    double result = 0;
    cout << "x = "; cin >> x;
    cout << "n = "; cin >> n;
    for(int i = 1; i <= n; ++i) result += myPow(x, i) / sum(i);
    cout << result; 
    return 0;
}
```
## Bài 4
![image](https://user-images.githubusercontent.com/88484431/140286914-dd0f130a-c3bb-48c5-b7c2-0e4e993e4aa7.png)
## Ý tưởng
Tạo một vòng lặp chạy từ 1 đến n, mỗi bước lặp sẽ cộng thêm vào tổng ```((-1)^i) * x^(2*i))```
## Lưu đồ

## Code
Sử dụng lại hàm ```myPow()``` từ bài 3 (lần này thì không cần số thực nữa :3)
```c++
#include<iostream>

using namespace std;

int myPow(int base, int hat)
{
    int res = 1;
    for(int k = 1; k <= hat; ++k) res *= base;
    return res;
}

int main()
{
    int x, n;
    int result = 0;
    cout << "x = "; cin >> x;
    cout << "n = "; cin >> n;
    for(int i = 1; i <= n; ++i) result += myPow(-1, i) * myPow(x, 2*i);
    cout << result; 
    return 0;
}
```
## Bài 5
![image](https://user-images.githubusercontent.com/88484431/140299523-939f963c-5c91-40b5-b7fb-b8ea8a702bb8.png)
## Ý tưởng
Ta sẽ tính từ trong ra ngoài, từ cái nhỏ nhất trước. Với mỗi bước lặp, ta sẽ lấy căn bậc hai của tổng hiện tại, rồi cộng thêm số mới vào. Sau khi lặp xong, lấy căn của tổng có được và ta sẽ có kết quả.
## Lưu đồ

## Code
Các anh cho xài hàm ```sqrt()``` thì mình xài thôi :v bạn nào muốn tìm hiểu thì có thể vào [đây](https://nguyenvanhieu.vn/tim-can-bac-hai-khong-dung-sqrt/)
```c++
#include<iostream>
#include<math.h>

using namespace std;
int myPow(int base, int hat)
{
    int res = 1;
    for(int k = 1; k <= hat; ++k) res *= base;
    return res;
}
int main()
{
    int x, n;
    int result = 0;
    cout << "x = "; cin >> x;
    cout << "n = "; cin >> n;
    for(int i = 1; i <= n; ++i) result += sqrt(result) + myPow(x, i);
    cout << sqrt(result); 
    return 0;
}
```
## Bài 6
![image](https://user-images.githubusercontent.com/88484431/140302973-f7996775-fc9b-42c4-84df-7f18e40f1594.png)
Qua tìm hiểu và được các anh giải thích thì mình có cách giải bài này như sau:
• Tính tổng với độ chính xác 10^-6 nghĩa là số hạng nhỏ nhất trong dãy không bé hơn ```10^-6```. Vì vậy, ta khởi tạo một biến ```epsilon = 1```, là độ chính xác hiện tại của tổng
• Dùng vòng lặp tính tổng ```1 + 1/2 + 1/3 + ... + 1/i +.... ```sau mỗi bước lặp, cập nhật lại ```epsilon = 1 / i```. Vòng lặp sẽ kết thúc khi epsilon < 10^-6.
## Lưu đồ
Với ý tưởng trên, ta thấy rằng không cần phải đưa n vào chương trình như đề bài đã cho :> 

## Code
```c++
#include<iostream>

using namespace std;

int main()
{
    float i = 1;
    float result = 0, epsilon = 1;
    while(epsilon >= 0.000001)
    {
        epsilon = 1 / i;
        result += epsilon;
        i++;
    }
    cout << result; 
    return 0;
}
```
## Bài 7
![image](https://user-images.githubusercontent.com/88484431/140304104-83759961-11cc-43f6-9465-cf957a292454.png)
## Ý tưởng
Đây là công thức truy hồi của dãy số. Dựa vào số liền trước trong dãy, ta có thể tính được số liền sau nó.

Dùng một vòng lặp chạy từ 2 đến n (do đã biết trước số đầu tiên), với mỗi bước tính toán, ta lưu kết quả hiện tại vào một biến ```prev```, rồi sử dụng nó làm a(n-1) trong bước tiếp theo.

## Lưu đồ

## Code
```c++
#include<iostream>

using namespace std;
int myPow(int base, int hat)
{
    int res = 1;
    for(int k = 1; k <= hat; ++k) res *= base;
    return res;
}

int main()
{
    int prev = -2, n, result = prev;
    cout << "n = "; cin >> n;
    for(int i = 2; i <= n; ++i) result = 5 * prev + 2 * myPow(3, i) - 6 * myPow(7, i) + 12;
    cout << result; 
    return 0;
}
```
## Bài 8
![Uploading image.png…]()
## Ý tưởng
Well, nhìn vào bài này là mình thấy ngay rằng phải if else đến chet rồi :)))

Tam giác có các loại: Tam giác thường, tam giác cân, tam giác vuông cân, tam giác vuông, tam giác đều (các trường hợp tam giác tù, tam giác nhọn khá phức tạp, mình không xét đến ở đây)

Ta thấy rằng, việc xét các trường hợp
```
• Đầu tiên, ta so sánh 3 cạnh của tam giác. Nếu chúng bằng nhau thì đó là tam giác đều, ngược lại, ta sẽ tiếp tục xét
• Tiếp theo, kiểm tra xem 3 cạnh của tam giác có thỏa mãn hệ thức Pytago hay không. 
    - Trường hợp thỏa mãn: tiếp tục kiểm tra xem có hai cạnh nào của tam giác bằng nhau không. Nếu có, tam giác đang xét là tam giác vuông cân, ngược lại, đó là tam giác vuông
    - 

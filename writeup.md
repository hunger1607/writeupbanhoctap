# DEADLINE LƯU ĐỒ THUẬT TOÁN
"Món quà" đầu tiên mà các anh chị tặng mình khi mới vào Ban học tập -_-

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/rickroll.jpg" width="500"/>
</p>

## Bài 1
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau1.png)
## Ý tưởng
Với một tâm hồn ngây thơ trong sáng thì mình đã từng nghĩ: dùng vòng for là được chứ gì đâu :D cơ mà làm vậy thì tốn mất 10 lần nhân, như thế thì không kinh tế lắm :/ 

Ta thấy: 
```bash
• x^11 = x^6 * x^5;
• x^6 = x^3 * x^3;   x^5 = x^3 * x^2;
• x^3 = x^2 * x;
```
Vậy ta cần tính ```x^2, x^3, x^5```, và ```x^6```. Tổng cộng ta có ```5``` lần nhân.

## Lưu đồ 
<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau1.png" width="250"/>
</p>


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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau2.png)
## Ý tưởng
Ta sẽ tìm cách tách từng chữ số của ```n``` ra rồi cộng lại với nhau, bằng cách chia lấy dư ```n``` cho ```10```. Sau khi chia, ta cần loại bỏ chữ số vừa sử dụng ra để tiếp tục tính toán, bằng cách lấy ```n``` chia nguyên cho ```10```.
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau2.png" width="370"/>
</p>

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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau3.png)
## Ý tưởng
Tạo một vòng lặp chạy từ ```1``` đến ```n```, trên tử sẽ là ```x^i```, dưới mẫu sẽ là tổng các số từ ```1``` đến ```i```.
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau3.png" width="370"/>
</p>

## Code
Để tiện hơn, ta viết một hàm ```sum()```, dùng để tính tổng các số từ 1 đến i, và hàm ```myPow()``` dùng để tính lũy thừa. 
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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau4.png)
## Ý tưởng
Tạo một vòng lặp chạy từ 1 đến n, mỗi bước lặp sẽ cộng thêm vào tổng ```((-1)^i) * x^(2*i))```
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau4.png" width="370"/>
</p>

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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau5.png)
## Ý tưởng
Ta sẽ tính từ trong ra ngoài, từ cái nhỏ nhất trước. Với mỗi bước lặp, ta sẽ lấy căn bậc hai của tổng hiện tại, rồi cộng thêm số mới vào. Sau khi lặp xong, lấy căn của tổng có được và ta sẽ có kết quả.
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau5.png" width="370"/>
</p>

## Code
Bạn nào muốn tìm hiểu thêm về hàm ```sqrt()``` thì có thể truy cập vào [đây](https://nguyenvanhieu.vn/tim-can-bac-hai-khong-dung-sqrt/)
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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau6.png)
Qua tìm hiểu và được các anh giải thích thì mình có cách giải bài này như sau:
• Tính tổng với ```độ chính xác 10^-6``` nghĩa là số hạng nhỏ nhất trong dãy không bé hơn ```10^-6```. Vì vậy, ta khởi tạo một biến ```epsilon = 1```, là độ chính xác hiện tại của tổng
• Dùng vòng lặp tính tổng ```1 + 1/2 + 1/3 + ... + 1/i +.... ```sau mỗi bước lặp, cập nhật lại ```epsilon = 1 / i```. Vòng lặp sẽ kết thúc khi ```epsilon < 10^-6```.
## Lưu đồ
Với ý tưởng trên, ta thấy rằng không cần phải đưa ```n``` vào chương trình như đề bài đã cho 

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau6.png" width="370"/>
</p>

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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau7.png)
## Ý tưởng
Đây là công thức truy hồi của dãy số. Dựa vào số liền trước trong dãy, ta có thể tính được số liền sau nó.

Dùng một vòng lặp chạy từ ```2``` đến ```n``` (do đã biết trước số đầu tiên), với mỗi bước tính toán, ta lưu kết quả hiện tại vào một biến ```prev```, rồi sử dụng nó làm ```a(n-1)``` trong bước tiếp theo.

## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau7.png" width="370"/>
</p>

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
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau8.png)
## Ý tưởng
Well, nhìn vào bài này là mình thấy ngay rằng phải if else đến chet rồi :)))

Tam giác có các loại: Tam giác thường, tam giác cân, tam giác vuông cân, tam giác vuông, tam giác đều (các trường hợp tam giác tù, tam giác nhọn khá phức tạp, mình không xét đến ở đây)

Ta thấy rằng, nếu một tam giác là tam giác đều thì không thể là tam giác vuông và ngược lại. Vì thế, để đơn giản các bước xét hơn, ta sẽ bắt đầu xét từ trường hợp tam giác đều, rồi loại trừ dần các trường hợp khác.

+ Đầu tiên, ta so sánh 3 cạnh của tam giác. Nếu chúng bằng nhau thì đó là tam giác đều, ngược lại, ta sẽ tiếp tục xét;

+ Tiếp theo, kiểm tra xem 3 cạnh của tam giác có thỏa mãn hệ thức Pytago hay không

  - Trường hợp thỏa mãn: tiếp tục kiểm tra xem có hai cạnh nào của tam giác bằng nhau không. Nếu có, tam giác đang xét là tam giác vuông cân, ngược lại, đó là tam giác vuông;
    
  - Trường hợp không thỏa mãn: lại tiếp tục kiểm tra xem có hai cạnh nào của tam giác bằng nhau không. Nếu có, tam giác đang xét là tam giác cân, ngược lại, đó là tam giác thường.

## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau8.png" width="370"/>
</p>

## Code
```c++
#include<iostream>

using namespace std;

int main()
{
    int x, y, z; 
    cin >> x >> y >> z;
    x *= x; y *= y; z *= z; //gon hon khi tinh toan he thuc pytago
    int square = 0, equal3 = 0, equal2 = 0;
    if(x == y && y == z) equal3 = 1;  //kiem tra 3 canh bang nhau
    if(x == y || y == z || x == z) equal2 = 1;  //kiem tra 2 canh bang nhau
    if(x == y + z || y == z + x || z == x + y) square = 1; //kiem tra he thuc pytago
    if(equal3) cout << "Tam giac deu";
    else 
    {
        if(square)      
        {
            if(equal2) cout << "Tam giac vuong can";
            else cout << "Tam giac vuong";
        }
        else
        {
            if(equal2) cout << "Tam giac can";
            else cout << "Tam giac thuong";
        }
    }
    return 0;
}
```
Mình sử dụng 3 biến ```equal3```, ```equal2``` và ```square``` để làm phần if đơn giản hơn, thay vì so sánh trực tiếp trong câu lệnh.
## Bài 9
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau9.png)
## Ý tưởng
Số chính phương là bình phương của một số nguyên. Vì vậy, nếu có một số nào đó bình phương lên mà bằng n thì n là số chính phương.

Do đó, ta có thể kiểm tra bằng cách tạo một biến ```tmp = 1```, rồi kiểm tra xem ```tmp^2``` có lớn hơn hoặc bằng n hay không. Nếu không, ta tăng giá trị của ```tmp``` lên 1. Khi kết thúc vòng lặp, nếu ```tmp == n``` thì n là số chính phương.
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau9.png" width="370"/>
</p>

## Code
```c++
#include<iostream>

using namespace std;

int main()
{
    int n, tmp = 1;
    cin >> n;
    while(tmp * tmp < n) tmp++;
    if(tmp * tmp == n) cout << n << " la so chinh phuong";
    else cout << n << " khong la so chinh phuong";
    return 0;
}
```
## Bài 10
![image](https://github.com/hunger1607/writeupbanhoctap/blob/main/cau10.png)
## Ý tưởng
Tương tự như bài 9, ta cũng sẽ khởi tạo một biến ```tmp = 1```. Với mỗi lần lặp, ta kiểm tra xem ```tmp``` đã lớn hơn hoặc bằng n chưa, nếu chưa thì ```tmp *= 5```. Sau khi lặp xong, nếu ```tmp == n``` thì n thỏa mãn yêu cầu đề bài.
## Lưu đồ

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/luudo/cau10.png" width="370"/>
</p>

## Code
```c++
#include<iostream>

using namespace std;

int main()
{
    int n, tmp = 1;
    cin >> n;
    while(tmp < n) tmp *= 5;
    if(tmp == n) cout << n << " thoa man";
    else cout << n << " khong thoa man";
    return 0;
}
```
# KẾT
Đây là writeup đầu tiên của mình, nên chắc chắn sẽ không thể không có thiếu sót. Mong các anh, chị trong ban và các bạn thông cảm :v Cảm ơn mọi người đã xem.

<p align="center">
  <img src="https://github.com/hunger1607/writeupbanhoctap/blob/main/saygoodbye.jpg" width="500"/>
</p>

# DEADLINE LƯU ĐỒ THUẬT TOÁN
"Món quà" đầu tiên mà các anh chị tặng mình khi mới vào Ban học tập -_-
![image](https://user-images.githubusercontent.com/88484431/140250344-2a1ec725-3cc9-4676-b4c0-8720f3ea6773.png)

## Bài 1
![image](https://user-images.githubusercontent.com/88484431/140250826-90f9cafd-51e5-4da8-bd87-e2df19773733.png)
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
![Uploading image.png…]()
## Ý tưởng
Ta sẽ tách từng chữ số của n ra bằng cách chia lấy dư cho 10, rồi loại bỏ chữ số đó ra bằng cách chia nguyên cho 10.
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
![Uploading image.png…]()
## Ý tưởng

## 콘솔 입력 cin
### cin
- 기존 C의 입출력 스타일
```C
#include <iostream>
int main() {
    int x;

    scanf("%d", &x);

    printf("%d", x);
}
```
- C++의 입력스타일
```C++

// 임베디드 디버깅
// UART PIN 2개
// SHELL > print abc

#include <iostream>
int main() {
    int x, y;

    std::cin >> x >> y;
    std::cout << x + y;

    return 0;
}
```
- 이런 스타일은 실제로 개발에 사용하지 않고 테스트에 사용많이 함.

```C++
#include <iostream>
#include <string> // string 

using std::cin;

int main() {
    
    std::string str, str2;

    cin >> str >> str2;

    return 0;
}
```
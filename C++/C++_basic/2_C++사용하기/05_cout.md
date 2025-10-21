## 콘솔 출력 cout
### cout
- cin은 콘솔화면에서 디버깅 용도로 사용됨
- cout도 마찬가지로 실제 개발환경에서는 디버깅용으로 자주 사용되지 않음. 로그를 더 많이 사용한다.
- 대신 프로그래밍 훈련할 때 자주 사용된다.

### 16진수 출력 1
- 대문자 출력시 uppercase를 사용
- Cppreference.com 에서 많은 문법을 찾아 사용 (예시 cpprefrence hex cout)

```C++
#include <iostream>

int main(){
    int n = 2748;

    std::cout << std::hex << n << std::endl; // abc

    std::cout << std::uppercase << std::hex << n << std::endl; //ABC
}
```
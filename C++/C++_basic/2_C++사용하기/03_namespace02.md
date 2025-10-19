## namespace
### [참고]AUTOSAR 권장사항
1. using-directive는 아예 사용하지 말자.
    - ex. using namespace 사용 금지
2. 가독성을 위한다면, using-declaration 까지는 허용
    - std의 모든 객체가 아닌, 정확히 std::cout만 "std::"를 생략할 수 있다.
3. Header 파일에는 using-declaration을 쓰지말자.

### 중첩 namespace
- namespace 내부에 namespace로 관리 가능
```C++
#include <iostream>
#include <string>

using std::string;

namespace kfc{
    namespace bbq{
        namespace chicken{
            int x
        }
    }
}

//namespace alias
namespace kbc == kfc:bbq::chicken;

int main(){
    kfc::bbq::chicken::x = 20;
    kbc::x = 50;
    return 0;
}
```

### 가독성을 위한 namespace 축약 - 방법1
- namespace alias를 만든다.
- using declaration을 사용한다.
- 실제 namesapce 사용 예시
    - https://en.cppreference.com/w/cpp/chrono


### namespace 중복하여 여러번 사용 가능
- t1과 t2는 같은 namespace에 존재
- 헤더파일을 쓸 때 유용함.
- 헤더파일을 하는건 그냥 main.h의 전체 내용을 복사해서 위에 붙여놓는 것과 같은 동작을 한다.

```C++
//main.h
namespace BTS{
    void run();
}

```

```C++
#include <iostream>
#include "main.h"

namespace BTS{
    void run() {
        std::cout << "HUHUHU"
    }
}
namespace Name {
    int t1;
}

namespace Name {
    int t2;
}

// 위의 두 개가 아래와 같은 표현이다.
namespace Name {
    int t1;
    int t2;
}
```


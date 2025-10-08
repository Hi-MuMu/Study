# 콘솔 입력과 출력

## namespace
### 사전 약속
- 이 강의는 AUTOSAR 컨벤션을 따름. (안정성을 엄청 강조하는 컨벤션)
- Google C++ Coding Guide
- return 0; 를 무조건 쓸 예정
```C++
#include <stdio.h>  // C언어용 라이브러리
#include <iostream> // C++용 라이브러리
```
### std namespace
- C++ 표준 Library를 사용할 때 마다, "Standard(표준)" 이라는 의미의 std::라는 키워드를 붙여줘야 한다.
```C++
    #include "kfc.h" // ""는 사설 라이브러리
```

### namespace
- 프로그램의 규모가 커질수록 Library끼리 변수 이름, 함수, 클래스 등 "Name Collision(이름충돌)"이 발생할 수 있기에 Namespace라는 이름으로 그룹핑 할 수 있는 문법이 탄생
```C++
namespace KFC{
    void print() {
        int a = 10;
    }
}

namespace ABC {
    void print() {
        int t = 20;
    }

int main() {
    int a = KFC::print()
    int b = ABC::print()
}
}
```
- 위 처럼 같은 함수 명이지만 다른 함수이므로 네임스페이스로 분리하기 위해 사용
- 만약 네임스페이스가 없으면 어떤 함수가 사용될지 모호함
- 수많은 라이브러리를 사용할 때 충돌을 방지해줌

### namespace 접근법
- 위 예시 처럼 KFC와 ABC의 Print 클래스는 서로 다름
- 변수 / struct도 사용이 가능하다. 아래는 예시
```C++
namespace kfc {
    int a = 10;
    int getsum(int a, int b){
        return a + b;
    }

    struct Node{ // 다른 언어에서 클래스로 보면 됨
        int x, y;
    };
}

int main() {
    kfc::a = 500; // 네임스페이스를 쓰고 ::사용하면 된다.
    return 0;
}
```
- C++ 공식 Library들은 std라는 namespace로 묶여있다. (String 등)
```C++
#include <iostream>
#include <string> // C++에 생긴 String 라이브러리
int main() {
    // 기존 C의 문자열 방식
    // char buf[3] = "AB";
    // const char* str = "WERWE"

    std::string str = "HiHi";
    std::cout << str;

    return 0;
}
```
### namespace 사용법
- C++의 여러 Library를 사용할 때 고유의 namespace를 사용하곤 한다.
```C++
#include <opencv2/opencv.hpp>
#include <iostream>

int main() {
    // 이미지 불러오기
    cv::Mat image = cv::imread("example.jpg")

    if (image.empty()) {
        std::cerr << "이미지를 불러올 수 없습니다!" << std::endl;
        return -1;
    }

    // 윈도우 생성 후 이미지 표시
    cv::imshow("Display Window", image);
    cv::waitKey(0); // 키 입력 대기
}

```
### using-directive 비권장
- using namepace std;를 쓰면 std에 속한 모든 객체들에 대해, 매번 std::를 안써줘도 된다.
```C++
#include <iostream>

// using namespace std; //using directive // 이거 비추천임

// C++ 문법에 대한 용어를 암기하는게 중요함(구글 컨벤션 따를 때나 오토사에 자주 나옴)

using std::cout; //using declaration // cout 생략 // 이것도 말 많은데 우리는 사용함

int main() {
    cout << "A";
    cout << "B";
    cout << "C";
    cout << "D";

    return 0;

}
```

### using directive 남용으로 인한 이름충돌 예시1
- 이름충돌의 두 가지 예시 코드
```C++
namespace ABC{
    int x;
}

namespace BTS {
    int x;
} 

int main() {
    using namespace ABC;
    using namespace BTS;
    x = 100; // 오류 발생
}
```
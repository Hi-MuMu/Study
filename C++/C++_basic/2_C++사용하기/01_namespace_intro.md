# 콘솔 입력과 출력

- C++에서는 printf 대신 std::cout 사용을 권장한다.
- 콘솔 출력명령어를 사용할 때는 std라는 namespace를 사용한다.
- 이번 챕터에서는 namespace을 시작으로 std::cin, std::cout을 학습한다.

```C++
#include <iostream>

void main() {

	int x;

	std::cin >> x;
	std::cout << "Hello World \n";
	std::cout << x;

}

```
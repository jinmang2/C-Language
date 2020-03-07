# 혼공C 5주차 기본/선택 미션
- 저자: [MyungHoon-Jin](https://github.com/jinmang2)
- #혼공단 #혼공C
## 기본 미션
- 직접 정리한 키워드 정리 공유

### 배열에 대한 키워드 정리
#### 8-1. 배열의 선언과 사용
- **배열(array)**: 같은 형태의 많은 데이터를 반복문으로 처리하기 위해 메모리에 연속적으로 저장해놓고 쪼개서 사용하는 방법
- **배열의 선언**: 배열은 한번에 변수를 여러 개(연속적으로) 선언
    - ex) ` int ary[5];`
- **배열 요소(element)**: 배열의 나누어진 조각, 배열명에 첨자(index)를 붙여 표현
- **배열의 사용**
    - 배열을 선언: []안의 숫자는 배열 요소의 수 `int ary[5]; `
    - 배열 요소를 사용: []안의 숫자는 index `ary[0] = 10;`
- **배열 초기화**
    - 선언과 동시에 {}로 묶어 초기화
    - 선언 시 최초 한 번만 가능
    - 초기화하고 남는 부분은 전부 0으로 초기화
    - 초기화를 하지 않으면 쓰레기값(dummy value)로 채워짐
    - ex) `int ary[1000] = {0};`
- 배열은 주로 반복문으로 처리
- 배열 전체의 크기를 구할 때 `sizeof` 연산자를 사용

#### 8-2. 문자를 저장하는 배열
- **char형 배열의 선언과 초기화**: 저장할 문자열의 길이보다 최소한 하나 이상 크게 배열을 선언
- `scanf` 함수는 사용자가 입력한 문자열 다음에 자동으로 널 문자를 추가해 문자열의 끝을 표시
- **주의할 점**
    - 배열의 크기는 최대한 넉넉하게 선언
    - 배열 요소의 개수는 최소한 '문자열 길이+1'여야 함
- **문자열 대입**: 대입연산자말고 `<string.h>`의 `strcpy` 함수를 사용
- `gets`, `puts`: 문자열 전용 입출력 함수 in `<stdio.h>`
    - `gets`와 `scanf`와의 차이점: 문자열 중간에 빈칸이 있어도 그대로 입력받음
    - `puts`는 끝에 \n을 붙여서 출력
    - `gets` 함수는 입력할 배열의 크기를 검사하지 않음.
    - 배열의 크기보다 긴 문자열을 입력하면 배열을 벗어난 메모리 영역을 침범할 가능성이 존재
    - 컴파일러에 따라 시스템 안전성 문제 때문에 컴파일을 제한하기도 함

## 선택 미션
- 널 문자의 정의, 용도와 사용법 공유

>### Null Character
>- `char`형 배열에 저장된 0을 Null character라고 정의
>- 즉, ASCII 코드값이 0인 문자
>- 문자열의 끝을 표시하는 용도로 사용
>- `char`형 배열을 선언하고 초기화하지 않은 경우, 반드시 마지막 문자 다음에는 널 문자를 대입해야 함
>- https://noirstar.tistory.com/16를 참고, 내용을 추가
>- **NULL, 0**
>>- NULL은 헤더파일에 정의도니 매크로로 **null pointer constant**
>>- 컴파일러에 의해 (void*)0으로 정의
>>- 포인터 변수 초기화에 사용
>- **NUL, \0**
>> ![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile10.uf.tistory.com%2Fimage%2F2576DC4A593BD7F4153E81)
>>- 우리가 다루고자하는 Null 문자가 바로 이것!
>>- 자동으로 초기화된 문자열 다음에 null문자(\0)이 삽입
>>- \0과 0에 해당하는 아스키코드값은 다름! 위 둘은 확실하게 다른 것!

## 번외
### 8장 도전 실전 예제, 대소문자 변환 프로그램
키보드로부터 문장을 입력받은 후에 대문자를 찾아 소문자로 바꾸는 프로그램을 작성하세요. 바뀐 문장과 바뀐 문자의 수도 함께 출력합니다.

```c
#include <stdio.h>                              // 표준 입출력
/*
    #define _CRT_SECURE_NO_WARNINGS
    아래 링크 참고! 보안 상의 이유로 gets, scanf 등의 함수를 compile 단에서 막아놓음
    https://gall.dcinside.com/board/view/?id=programming&no=526977
    https://stackoverflow.com/questions/2843073/warninggets-function-is-dangerous
*/

int main(void){
    char arr[80] = { 0 };                       // 배열을 0으로 초기화
                                                // 넉넉하게 80*1 byte만큼 메모리 공간을 잡아줌
    int n = 0;                                  // 바뀐 문자의 수 세기
    int count, i;                               // 배열의 크기와 loop을 돌 i 선언
    
    printf("문장 입력 : ");
    gets_s(arr);                                // 문장을 띄어쓰기까지 포함하여 입력받음
    count = sizeof(arr) / sizeof(arr[0]);       // loop을 돌 문자의 수를 받아옴
    
    for (i = 0; i < count; i += 1) {
        if (arr[i] == '\0') break;              // Null character일 경우 break
        if (arr[i] >= 'A' && arr[i] <= 'Z') {
            arr[i] += 32;                       // 대문자일 경우 ASCII 코드 상에서 소문자랑 32만큼 차이남
            n += 1;                             // 소문자로 변경하고 횟수를 셈
        }
    }
    
    printf("바뀐 문장 : %s\n", arr);
    printf("바뀐 문자의 수 : %d", n);
    
    return 0;
}
```
```
문장 입력 : DON'T Worry, Be Happy~
바뀐 문장 : don't worry, be happy~
바뀐 문자의 수 : 7
```

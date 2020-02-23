# 혼공C 3주차 기본/선택 미션
- 저자: [MyungHoon-Jin](https://github.com/jinmang2)
- #혼공단 #혼공C
## 기본 미션
- 혼공 용어 노트에 용어 추가 등의 노트 활용 인증샷

<img src="https://github.com/jinmang2/HonGongC/blob/master/img/5-1.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/5-2.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/6-1.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/6-2.jpg?raw=true?raw=true" >

## 선택 미션
- 123쪽 크리스마스 예문을 코드로 표현한다면?

```c
// '크리스마스 때까지 여자친구가 없으면'
// 친구가 '소개팅을 주선해준다'고 했습니다.
// 구라이므로 거르면 됩니다.

#include <stdio.h>
#include <time.h> // 출처: https://korbillgates.tistory.com/100

int main(void){

    time_t t = time(NULL);
    struct tm tm = *localtime(&t);
    
    // 현재 날짜에 대한 정보를 int로 저장
    int this_year  = tm.tm_year+1900;
    int this_month = tm.tm_mon+1;
    int this_date  = tm.tm_mday;
    
    // 친구가 장난질한 크리스마스에 대한 정보를 int로 저장
    int xmas_year  = this_year;
    int xmas_month = 12;
    int xmax_date  = 25;
    
    // 여자친구를 사귀고 있는지 여부를 저장
    // 이는 있을 수 없는 일이야
    int girl_friend 1;
    
    // chris-mas가 다가왔는지 두근두근거리는 마음으로 확인해 봅시다.
    if (this_year == xmax_year) {
        // 친구놈이 연도로 장난질했을 수도 있기 때문에 검사
        if (this_month == xmas_month) { 
            // 12월인지 체크
            if (this_date >= 25) {
                // 25일이 지났는지도 체크..!
                // 친구놈에게 소개시켜달라고 재촉
                printf("약속의 날이다. 소개팅 주선해줘라.\n");
                if (girl_friend) {
                    // 여자친구가 있어도 뻔뻔하게 주장해봅시다. 그러면 친구는
                    return "여친있는 놈이 --!!";
                }
                else {
                    // 이 놈은 애초에 여소해줄 마음이 없었습니다.
                    // 뭐라 하는지 들어봅시다.
                    return "그걸 믿었냐? ㅋ";
                }
            }
        }
    }
    // 아직 크리스마스가 오지 않았다면 당신은 계속해서 농락당하고 있겠죠.
    return "친구야 크리스마스까지 조금만 참으렴 ㅠㅠ"
}
```

## 번외
#### 5장 도전 실전 예제, 계산기 프로그램
- 키보드로 수식을 입력하면 계산 결과를 출력하는 프로그램을 작성하세요. 정수 사칙연산만 입력합니다.

```c
#include <stdio.h>

int main(void) {
    int a, b;
    char operation;
    
    printf("사칙연산 입력(정수) : ");
    scanf("%d%c%d", &a, &operation, &b);
    
    if (operation == '+') {
        printf("%d %c %d = %d", a, operation, b, a + b);
    }
    else if (operation == '-') {
        printf("%d %c %d = %d", a, operation, b, a - b);
    }
    else if (operation == '*') {
        printf("%d %c %d = %d", a, operation, b, a * b);
    }
    else if (operation == '/') {
        printf("%d %c %d = %d", a, operation, b, a / b);
    }
    else {
        printf("올바른 연산기호를 입력하세요.");
    }
    return 0;
}
```
```
// 실행결과1
사칙연산 입력(정수) : 11/3
11 / 3 = 3

// 실행결과2
사칙연산 입력(정수) : 10-6
10 - 6 = 4
```

#### 6장 도전 실전 예제, 소수(prime number) 출력 프로그램
- 2 이상의 정수를 입력하여 2부터 입력한 수까지의 모든 소수를 출력합니다. 단, 한 줄에 5개씩 5칸 간격으로 출력합니다.
- 하나의 정수가 소수인지를 판단해서 출력하는 과정은 다음과 같습니다.
    ```
    1. 일단 소수라고 가정한다.
    2. 2부터 그 정수보다 하나 작은 수까지 하나라도 나누어 떨어지면 가정을 취소한다.
    3. 1.의 가정이 2.에서 바뀌지 않았으면 그 정수를 출력한다.
    ```
- 위 1\~3까지의 과정은 하나의 정수에 대해서 소수를 판별하는 과정이고 어떤 수까지의 모든 수를 판별하기 위해서는 1\~3까지의 과정을 다시 반복합니다.

```c
#include <stdio.h>
#include <math.h>

int main(void) {
    int n, i, j;
    int is_prime = 1;
    int t = 0;
    
    printf("2 이상의 정수를 입력하세요 : ");
    scanf("%d", &n);
    
    for (i = 2; i < n + 1; i++) {
        for (j = 2; j < (int)sqrt(i) + 1; j++) {
            if (i % j == 0) {
                is_prime = 0;
                break;
            }
        }
        if (is_prime == 1) {
            printf("%2d     ", i);
            t += 1;
            if (t % 5 == 0) {
                printf("\n");
            }
        }
        is_prime = 1;
    }
    return 0;
}
```
```
// 실행결과
2 이상의 정수를 입력하세요 : 100
 2      3      5      7     11
13     17     19     23     29
31     37     41     43     47
53     59     61     67     71
73     79     83     89     97
```

# 혼공C 5주차 기본/선택 미션
- 저자: [MyungHoon-Jin](https://github.com/jinmang2)
- #혼공단 #혼공C
## 기본 미션
- 포인터 내용 블로깅 하기
    - https://jinmang2.github.io/c/what_is_pointer/

## 선택 미션
- 	나만의 언어로 포인터 정의하기
    ```
    Def. Pointer
        Variable whose value is the address of another variable
        That is, (with const)
            짝사랑
            연락처를 알고 (주솟값의 첫번째 값)
            그녀가 뭘 좋아하는지 알고 (변수의 크기)
            언제든 이를 바탕으로 대쉬하고 도전하지만 (*pointer로 접근)
            나로는 아직 마음을 돌릴 수 없는 (const *pa ... 간접 참조 연산자로는 변경 불가)
            이를 깨려면 const로 define하는 것이 아닌
            int *pa;와 같이 정의하여
            변칙적인 매력을 보여줘야겠지?
    ```

## 번외
### 9장 도전 실전 예제, 미니 정렬 프로그램
키보드로 실수 3개를 입력한 다음 큰 숫자부터 작은 숫자로 정렬한 뒤 출력하는 프로그램을 작성합니다. 다음 코드와 출력 결과를 참고하여 `line_up` 함수를 작성하세요. `line_up` 함수에는 이미 정의된 `swap` 함수를 호출하여 구현하세요.

```c
/*
    Authored by MyungHoon-Jin
    github.com/jinmang2
*/

#include <stdio.h>  // Standard Input & Output Library

// Declare Functions
void swap(double* pa, double* pb);
void line_up(double* maxp, double* midp, double* minp);

// Define main function
int main(void){
    
    double max, mid, min;   // Declare double variable
    
    printf("실수값 3개 입력 : ");
    scanf_s("%lf%lf%lf", &max, &mid, &min);     // Input by left-value
    line_up(&max, &mid, &min);                  // Use pointer(variable's left-value),
                                                // Line up as following; MAX-MID-MIN
    printf("정렬된 값 출력  : %.1lf, %.1lf, %.1lf", max, mid, min);
    
    return 0;
}

void swap(double *pa, double *pb){
    
    double temp;        // Declare temp variable
    
    temp = *pa          // Using unary-indirection operation, swap *pa with *pb
    *pa = *pb
    *pb = temp
}

void line_up(double *max, double *midp, double *minp){
    
    if (*maxp < *midp) swap(maxp, midp);
    if (*maxp < *minp) swap(maxp, minp);
    if (*midp < *minp) swap(midp, minp);
    
}
```

```
실수값 3개 입력 : 2.7 1.5 3.4
정렬된 값 출력  : 3.4, 2.7, 1.5
```


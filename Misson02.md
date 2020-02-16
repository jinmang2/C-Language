# 혼공C 2주차 기본/선택 미션
- 저자: [MyungHoon-Jin](https://github.com/jinmang2)
- #혼공단 #혼공C
## 기본 미션
- 확인문제 책에 푼 인증샷

#### 3-1 확인문제
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/3-1-1.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/3-1-2.jpg?raw=true?raw=true" >

#### 3-2 확인문제
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/3-2-1.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/3-2-2.jpg?raw=true?raw=true" >

#### 4-1 확인문제
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/4-1-1.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/4-1-2.jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/4-1-3.jpg?raw=true?raw=true" >

#### 4-2 확인문제
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/4-2-1(수정).jpg?raw=true?raw=true" >
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/4-2-2.jpg?raw=true?raw=true" >

## 선택 미션
- 4장 도전 실전 문제 풀이

#### Q) 체중관리 프로그램
체중(kg)과 키(cm)를 입력하여 BMI(신체질량지수)를 구한 후에 BMI의 값이 20.0 이상 25.0 미만이면 "표준입니다"를 출력하고 그렇지 않으면 "체중관리가 필요합니다"를 출력합니다.

BMI는 표준체중, 저체중, 과체중을 판별하는 수치로 몸무게를 키의 제곱으로 나누어 구합니다.

이때 키는 미터(m) 단위로 계산합니다.

```c
/*
    Author : MyungHoon Jin
    Title  : BMI를 활용한 체중관리 프로그램
    Date   : 2020.02.16
*/
#include <stdio.h>  // 표준 입출력, printf를 사용하기 위해
#include <math.h>   // 수학 도구 모음, pow를 사용하기 위해

int main(void) {
    double weight;                         // 입력받을 몸무게 변수를 double로 선언
    double height_cm, height_m;            // 입력받은 키(cm)와 미터(m)로 변환할 변수를 double로 선언
    double BMI;                            // 체중관리의 기준으로 활용할 BMI 변수를 double로 선언
    
    printf("몸무게(kg)와 키(cm) 입력 : ");
    scanf("%lf%lf", &weight, &height_cm);  // 몸무게(kg)와 키(cm) 입력받기
    
    height_m = height_cm / 100.0;          // 키(cm)를 키(m)로 변환
    BMI = weight / (pow(height_m, 2.0));   // BMI = 몸무게 / (키의 제곱) 계산
    
    // 20 <= BMI < 25 일 경우 "표준입니다." 출력, 아닐 경우 "체중관리가 필요합니다."
    // 를 삼항 연산자를 활용하여 출력.
    printf("%s\n", ((BMI >= 20.0) && (BMI < 25.0)) ? "표준입니다." : "체중관리가 필요합니다.");
    
    return 0;
}
```
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/실행화면.PNG?raw=true" >

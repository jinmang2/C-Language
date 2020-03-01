# 혼공C 4주차 기본/선택 미션
- 저자: [MyungHoon-Jin](https://github.com/jinmang2)
- #혼공단 #혼공C
## 기본 미션
- 직접 표로 핵심 포인트 정리 공유

#### 표 7-1 함수의 3자기 상태
| 구분              | 예시                                                     | 설명                                                                                     |
|-------------------|----------------------------------------------------------|------------------------------------------------------------------------------------------|
| 함수 정의         | `int sum(int a, int b){` <br>` ` ` ` ` ` `return a + b;` <br>`}` | 함수의 형태를 알린다.<br>함수 원형에 세미콜론을 붙인다.                                  |
| 함수 호출 및 반환 | `sum(10, 20)`                                            | 함수를 만든다.<br>반환값의 형태, 이름, 매개변수를 표시하고<br>블록 안에 기능을 구현한다. |
| 함수 선언         | `int sum(int a, int b);`                                 | 함수를 사용한다.<br>함수에 필요한 값을 인수로 준다.                                      |

#### 표 7-2 다양한 함수의 형태

<table>
    <tr>
        <th>형태</th>
        <th>구분</th>
        <th>설명</th>
    </tr>
    <tr>
        <td rowspan="2">매개변수가 없는 경우</td>
        <td>선언</td>
        <td><code>int get_num(void);</code> 또는 <code>int get_num();</code></td>
    </tr>
    <tr>
        <td>특징</td>
        <td>호출할 때 인수 없이 괄호만 사용한다.</td>
    </tr>
    <tr>
        <td rowspan="2">반환형이 없는 경우</td>
        <td>선언</td>
        <td><code>void print_char(char ch, int count);</code></td>
    </tr>
    <tr>
        <td>특징</td>
        <td>반환할 때 <code>return</code>문을 쓰지 않거나 <code>return</code>문만 사용한다.<br>호출 문장을 수식의 일부로 쓸 수 없다.</td>
    </tr>
    <tr>
        <td rowspan="2">반환형, 매개변수 모두 없는 경우</td>
        <td>선언</td>
        <td><code>void print_title(void);</code></td>
    </tr>
    <tr>
        <td>특징</td>
        <td>두 가지 경우의 특징을 모두 포함한다.</td>
    </tr>
</table>

#### 표 7-3 재귀호출 함수

<table>
    <tr>
        <th>형태</th>
        <th>구분</th>
        <th>설명</th>
    </tr>
    <tr>
        <td rowspan="2">재귀호출 함수</td>
        <td>선언</td>
        <td><code>void fruit() { ...  fruit()  ... }</code></td>
    </tr>
    <tr>
        <td>특징</td>
        <td>함수 안에 재귀호출을 멈추는 조건이 있어야 한다.</td>
    </tr>
</table>


## 선택 미션
- 198쪽 7-5 예제 테스트해보고 apple을 출력하다가 종료되는 사진 스크린샷.
- 왜 종료되는지도 함께 공유

```c
#include <stdio.h>

void fruit(void);           // 함수 선언

int main(void){
    fruit();                // 함수 호출
    return 0;
}

void fruit(void){           // 재귀호출 함수 정의
    printf("apple\n");
    fruit();                // 자신을 다시 호출
}
```
<img src="https://github.com/jinmang2/HonGongC/blob/master/img/7-1.PNG?raw=true" >

### 왜 종료되는가?
- [Stack Overflow](https://en.wikipedia.org/wiki/Stack_overflow)
- call stack 포인터가 stack bound를 초과했을 때 발생
- 함수는 호출만으로도 일정 크기의 메모리를 사용
- 무한 호출시 프로그램 하나가 쓸 수 있는 메모리(해당 프로세스에 할당된 스택 메모리)를 모두 사용하여 강제 종료

## 번외
### 7장 도전 실전 예제, 1부터 10까지의 합 계산(재귀호출 사용)
1부터 일정 수(n)까지의 합을 재귀호출을 사용해서 작성해보세요. 1부터 일정 수(n)까지의 합을 구하는 재귀호출 함수를 만들고 호출하여 구현합니다.

```c
#include <stdio.h>              // 표준 입출력 라이브러리

int rec_func(int n);            // 함수 선언

void main(void){                // argument, return 전부 없음(void)
    int n = 10;                 // 예제의 값 10 설정
    int result;                 // 결과값을 저장할 변수 선언
    result = rec_func(n);       // n까지의 합을 구하는 함수를 실행
                                // result에 그 결과를 저장
    printf("%d", result);       // 결과 출력
}

int rec_func(int n){
    if (n == 0) return 0;       // 재귀 종료 조건 설정
    int res = n;                // 결과값을 저장할 변수 선언
                                // 근데 이렇게 해도 되려나?
                                // 누수되는 메모리가 존재하지 않을까?
                                // 아니면 스택해제되면서 알아서 정리하려나?
                                // 공부할게 많구만!!
    res += rec_func(n - 1);     // 재귀 호출하여 값을 저장
    return res;                 // 결과값 반환
}
```
```
55
```

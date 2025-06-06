# Step 1: 프로그래밍 기초

## 1. Hello, World 출력하기

모든 프로그래밍 언어의 첫 걸음은 "Hello, World!" 출력이다.
아래 코드를 따라 실행해보고 결과를 확인해보자.

```
#include <stdio.h> // 표준 입출력 라이브러리

int main() {
    printf("Hello, World!\n"); // 화면에 텍스트 출력
    return 0; // 프로그램 종료
}
```

#### 설명
- #include <stdio.h> : 입출력 함수(예: printf)를 사용하기 위한 선언이다.
- main() : 프로그램의 시작 지점이다.
- printf : 화면에 문자열을 출력한다.
- return 0 : 프로그램이 정상 종료되었음을 알린다.

## 2. 변수와 데이터 타입

#### 1. 정수형 데이터 타입

- short : 2바이트, -32,768 ~ 32,767
- int : 4바이트, -2,147,483,648 ~ 2,147,483,647
- long : 4바이트, -2,147,483,648 ~ 2,147,483,647
- long long : 8바이트, -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807

```
#include <stdio.h>

int main() {
    short s = 32767;          // short 최대값
    int i = 2147483647;       // int 최대값
    long l = 2147483647;      // long 최대값
    long long ll = 9223372036854775807; // long long 최대값

    printf("short: %d\n", s);
    printf("int: %d\n", i);
    printf("long: %ld\n", l);
    printf("long long: %lld\n", ll);

    return 0;
}
```


#### 2. 실수형 데이터 타입

- float : 4바이트, ±3.4E-38 ~ ±3.4E+38, 소수점 6~7자리
- double : 8바이트, ±1.7E-308 ~ ±1.7E+308, 소수점15~16자리
- long double : 12바이트 또는 16바이트, 더 큰 범위, 소수점12~20자리
```
#include <stdio.h>

int main() {
    float f = 3.141592f;      // float은 소수점 6~7자리까지 정확
    double d = 3.141592653589; // double은 소수점 15~16자리까지 정확
    long double ld = 3.141592653589793238L;

    printf("float: %.7f\n", f);
    printf("double: %.15f\n", d);
    printf("long double: %.20Lf\n", ld);

    return 0;
}
```



#### 3. 문자형 데이터 타입

- char : 1바이트, -128 ~ 127
```
#include <stdio.h>

int main() {
    char letter = 'A'; // 문자
    char ascii = 65;   // ASCII 코드 값

    printf("문자: %c\n", letter);
    printf("ASCII 코드로 문자: %c\n", ascii);
    printf("ASCII 값: %d\n", letter);

    return 0;
}
```
- C언어에는 Python이나 Java 같은 고수준 언어의 string 타입은 없지만, 문자열을 다룰 수 있는 방법이 있다. 문자열은 문자의 배열(character array)로 구현되며, 항상 **null 문자(\0)**로 끝난다. 이 null 문자가 문자열의 끝을 표시하는 역할을 한다.

##### 1. 문자열 선언과 초기화
- 문자열은 char 배열로 선언된다.
```
#include <stdio.h>

int main() {
    char str1[] = "Hello"; // 문자열 초기화
    char str2[6] = "World"; // 배열 크기를 지정하여 초기화
    char str3[6] = {'H', 'e', 'l', 'l', 'o', '\0'}; // 문자 배열로 직접 초기화

    printf("str1: %s\n", str1);
    printf("str2: %s\n", str2);
    printf("str3: %s\n", str3);

    return 0;
}
```
+ 문자열은 char 배열로 선언하며, 마지막에 \0(null 문자)을 자동으로 추가한다.
+ 배열 크기를 지정할 때는 문자열 길이보다 1만큼 크게 해야 한다(마지막 null 문자를 포함하기 위해).
+ 문자열은 "%s"를 사용하여 출력한다.

##### 2. 문자열 입력받기
- C언어에서는 문자열 입력을 받기 위해 scanf와 gets를 사용할 수 있다.
+ scanf를 사용한 문자열 입력
    ```
    #include <stdio.h>

    int main() {
        char name[20];

        printf("이름을 입력하세요: ");
        scanf("%s", name); // 공백 전까지 입력받음
        printf("입력된 이름: %s\n", name);

        return 0;
    }
    ```
    - scanf는 공백 전까지만 입력을 받는다.
    예: "John Doe"를 입력하면 John만 저장된다.

+ gets를 사용한 문자열 입력
    ```
    #include <stdio.h>

    int main() {
        char name[20];

        printf("이름을 입력하세요: ");
        getchar(); // 버퍼 초기화 (필요한 경우 추가)
        gets(name); // 공백 포함 입력받음
        printf("입력된 이름: %s\n", name);

        return 0;
    }
    ```
    - gets는 입력된 문자열의 길이를 제한하지 않기 때문에 버퍼 오버플로우 위험이 있다.
    
+ fgets를 사용한 문자열 입력 (추천)
    ```
    #include <stdio.h>

    int main() {
        char name[20];

        printf("이름을 입력하세요: ");
        fgets(name, sizeof(name), stdin); // 최대 입력 크기를 지정
        printf("입력된 이름: %s\n", name);

        return 0;
    }
    ```
    - fgets는 입력 길이를 제한할 수 있어 안전하다.
    - 입력 후 줄바꿈 문자가 포함될 수 있으므로 제거가 필요하다.

##### 3. 문자열 처리 함수
- 문자열을 다룰 때 자주 사용하는 함수들은 <string.h>에 정의되어 있다.
    + strlen : 문자열 길이를 반환 / strlen("Hello") → 5
    + strcpy : 문자열 복사 / strcpy(dest, src)
    + strcat : 문자열 연결 / strcat(str1, str2)
    + strcmp : 문자열 비교(같으면 0 반환) / strcmp("abc", "abc") → 0
    + strchr : 특정 문자 검색 (포인터 반환) / strchr("abc", 'b') → 주소
    + strstr : 특정 문자열 검색 (포인터 반환) / strstr("hello", "lo") → 주소

##### 4. 문자열과 배열의 차이
- 문자열은 null 문자로 끝나는 문자 배열이다.
- 문자 배열은 null 문자가 없을 수 있어 문자열 함수 사용 시 오류가 발생할 수 있다.
    ```
    #include <stdio.h>

    int main() {
        char arr[] = {'H', 'e', 'l', 'l', 'o'}; // null 문자 없음
        char str[] = "Hello";                   // null 문자 포함

        printf("arr: %s\n", arr);  // 출력 오류 가능
        printf("str: %s\n", str);  // 정상 출력

        return 0;
    }
    ```


#### 4. 논리형 데이터 타입 
- c언어에는 논리형 bool 타입이 있지만, C99 이후 표준에서 지원된다.   
헤더 파일 <stdbool.h>를 추가하면 사용할 수 있다.

+ _Bool 또는 bool : 1바이트, true(1), false(0)
    ```
    #include <stdio.h>
    #include <stdbool.h>

    int main() {
        bool flag = true; // true = 1
        bool condition = false; // false = 0

        printf("flag: %d\n", flag);
        printf("condition: %d\n", condition);

        return 0;
    }
    ```

#### 5. void 타입
- void는 아무것도 반환하지 않거나 포인터에서 사용될 때 쓰인다.
+ 함수 반환값이 없을 때 
    ```
    void printHello() {
    printf("Hello, World!\n");
    }
    ```
+ void 포인터 : 다양한 데이터 타입을 가리킬 수 있는 포인터다.
    ```
    void* ptr;
    ```

## 3. 입력/출력 함수

### 1. 출력 함수

#### (1) printf 함수
- 형식 지정자(Format Specifiers)
    1. 정수형 데이터 타입
         + short : %hd , short 정수 출력
         + int : %d 또는 %i , int 정수 출력
         + long : %ld , long 정수 출력
         + long long : %ld , long long 정수 출력
         + 부호없는 정수(unsigned): %u , unsigned int(양수 전용 출력)
         + 8진수 : %o , 8진수(Octal) 출력
         + 16진수 : %x 또는 %X , 16진수(Hexadecimal)로 출력 (소문자/대문자)
         ```
        #include <stdio.h>

        int main() {
            int a = 255;
            unsigned int b = 255;

            printf("10진수: %d\n", a);
            printf("부호 없는 정수: %u\n", b);
            printf("8진수: %o\n", a);
            printf("16진수 (소문자): %x\n", a);
            printf("16진수 (대문자): %X\n", a);

            return 0;
        }
         ```

    2. 실수형 데이터 타입
        + float : %f , float 실수 출력(소수점 아래 6자리 기본)
        + double : %lf , double 실수 출력
        + long double : %Lf , long double 실수 출력
        + 과학적 표기법 : %e 또는 %E , 지수 표기법(Exponential) 출력 (1.23e+02)
        ```
        #include <stdio.h>

        int main() {
            float pi = 3.141592f;
            double bigPi = 3.14159265358979;

            printf("float: %f\n", pi);
            printf("double: %.15lf\n", bigPi); // 소수점 15자리까지 출력
            printf("과학적 표기법: %e\n", bigPi);

            return 0;
        }
        ```

    3. 문자형 데이터 타입
        - char : %c , 단일 문자 출력
        - char[] : %s , 문자열 출력
        ```
        #include <stdio.h>

        int main() {
            char ch = 'A';
            char str[] = "Hello";

            printf("문자: %c\n", ch);
            printf("문자열: %s\n", str);

            return 0;
        }
        ```
    
    4. 특수 문자 출력
        + \n : 줄바꿈
        + \t : 탭(Tab)
        + \\\ : 백슬래시(\\) 출력
        + \\" : 큰따옴표(")  출력
        + \\' : 작은따옴표(') 출력
        + \0 : 문자열 종료 (Null)
    
    5. 출력 형식 조정(폭과 정렬)
        - 형식 지정자에는 출력 폭, 정렬, 소수점 자리수 등을 조정하는 옵션이 있다.
        - 폭 : %5d , 최소 5칸 확보 및 오른쪽 정렬
        - 왼쪽 정렬 : %-5d , 최소 5칸 확보 및 왼쪽 정렬
        - 0으로 채우기 : %05d , 빈 칸을 0으로 채움
        - 소수점 자리수 : %.2f , 소수점 둘째자리까지 출력
        - 폭 + 소수점 : %8.2f 전체 8자리, 소수점 둘째자리까지 출력
        ```
        #include <stdio.h>
        int main(){
            int num = 42;
            float pi = 3.141592;

            printf("기본 출력: [%d]\n", num);
            printf("오른쪽 정렬 (5칸): [%5d]\n", num);
            printf("왼쪽 정렬 (5칸): [%-5d]\n", num);
            printf("0으로 채우기 (5칸): [%05d]\n", num);

            printf("소수점 2자리: %.2f\n", pi);
            printf("전체 8자리, 소수점 2자리: %8.2f\n", pi);

            return 0;
        }
        ```
        출력결과
        ```
        기본 출력: [42]
        오른쪽 정렬 (5칸): [   42]
        왼쪽 정렬 (5칸): [42   ]
        0으로 채우기 (5칸): [00042]
        소수점 2자리: 3.14
        전체 8자리, 소수점 2자리:     3.14
        ```
#### (2) puts 함수
- 문자열을 출력하고 자동으로 줄바꿈을 추가하는 간단한 출력함수
    ```
    #include <stdio.h>

    int main() {
        puts("Hello, World!"); // 자동 줄바꿈 추가
        puts("C Programming");

        return 0;
    }
    ```
#### (3) putchar 함수
- 문자 한 개를 출력할 때 사용하는 함수
    ```
    #include<stdio.h>
    int main(){
        char ch = 'A';

        putchar(ch);
        putchar('\n');

        return 0;
    }
    ```

### 2. 입력 함수

#### (1) scanf 함수
- scanf("형식 문자열", &변수);
- 변수 앞에 &(주소 연산자)를 반드시 붙여야 한다.
- 여러 값을 입력받을 때는 형식 지정자 순서에 맞게 입력해야 한다.

## 4. 기본 연산자 (Operators)

### 1. 산술 연산자
- \+ : 덧셈 
- \- : 뺄셈
- \* : 곱셈
- \/ : 나눗셈(몫) << 정수끼리 나누면 정수의 결과가 나옴
- \% : 나머지 연산 << 정수형에만 사용 가능

### 2. 대입 연산자

- = : 대입 
- += : 덧셈 후 대입
- -= : 뺄셈 후 대입
- *= : 곱셈 후 대입
- /= : 나눗셈 후 대입
- %= : 나머지 후 대입

### 3. 증감 연산자

- \++ : 1 증가
- \-- : 1 감소
- 전위형과 후위형 차이 이해하기
    ```
    #include <stdio.h>

    int main(){
        int a = 5, b;

        b = ++a; //전위형: a를 먼저 증가시키고 b에 대입
        printf("전위형 (++a): a = %d, b = %d\n", a, b);
        // a = 6 , b = 6

        a = 5;
        b = a++; // 후위형: b에 먼저 a를 대입하고 a를 증가
        printf("후위형 (a++): a = %d, b = %d\n", a, b);
        // a = 6 , b = 5

        return 0;
    }
    ```

### 4. 관계 연산자
- 두 값을 비교할 때 사용하는 연산자, 결과는 참(1) 또는 거짓(0)
- == : 같다
- != : 같지 않다
- \> : 크다
- \< : 작다
- \>= : 크거나 같다
- \<= : 작거나 같다

### 5. 논리 연산자
- && : and 
- || : or  ,  **하나라도 조건이 참이면 결과가 참** 
- ! :  not , 조건식의 결과를 반대로 뒤집는다.

### 6. 비트 연산자
- 정수형 데이터에서만 사용할 수 있음.

    >a = 5 (0101) , b = 3 (0011)


    1. **&** : 비트 AND  ,  a & b  >> 0001
        - 각 비트가 모두 1인 경우에만 결과 비트가 1이 된다.
        - 비트 마스킹에 자주 사용
    
    2. **|** : 비트 OR ,  a | b >> 0111
        - 각 비트 중 하나라도 1이면 결과 비트가 1이 된다.
        
    3. **^** : 비트 XOR , a ^ b >> 0110
        - 각 비트가 서로 다르면 결과 비트가 1이 된다.
        - XOR은 두 값을 교환하는 데 사용할 수 있다.
        - 예제: 값 교환
            ```
            a = a ^ b;
            b = a ^ b;
            a = a ^ b;
            ```

    4. **~** : 비트 NOT , ~a >> 11111010 
        - ~a 는 a의 모든 비트를 반전한다.
        - 즉, 1 -> 0 , 0 -> 1 로 바뀐다.
        - 원래 숫자 5 (00000101)
        - ~a : 11111010 (-6)
        - **2의 보수란?**
            + 정수를 비트로 표현하는 방법 중 하나로, 음수를 나타낼 때 사용
            + 보수의 계산 방법
                1. 2진수로 변환한다.
                2. 1의 보수를 구한다.
                    - 모든 비트를 반전(0 <-> 1)시킨다.
                3. 1을 더한다.
                ```
                예제 1: 5의 2의 보수 구하기 (8비트 기준)
                    1. 5를 이진수로 표현:
                        5 = 00000101
                    2. 1의 보수 구하기:
                        (모든 비트를 반전한다)
                        00000101 -> 11111010 
                    3. 1을 더하기:
                        11111010 + 1 = 11111011
                    
                    결과적으로 11111011은 -5를 나타냄.
                ```
                + 2의 보수 표현에서, 가장 왼쪽 비트(MSB)가 부호 비트로 사용됨.
                + 8비트 정수 범위
                    - 양수 : 00000000 ~ 01111111 (0~127)
                    - 음수 : 10000000 ~ 11111111 (-128 ~ -1)
                    - 11111111 : -1
                    - 10000000 : -128

    5. 왼쪽 시프트 (<<)
        - 비트를 왼쪽으로 n번 이동시키고, 오른쪽의 빈 자리는 0으로 채운다.
        - 각 비트가 2진수에서 한 자리씩 왼쪽으로 이동하기 때문에, 값이 2배씩 증가한다.
        ```
        #include <stdio.h>

        int main() {
            int a = 5;  // 0101
            int result = a << 1;

            printf("a << 1 = %d\n", result);  // 결과: 1010 (10)

            return 0;
        }
        ```
        - 왼쪽 시프트의 일반 공식은 : a x 2n(2의 n제곱)
        - 왼쪽 시프트를 너무 많이 하면 비트가 손실되고 값이 달라질 수 있다.
        - 왼쪽 시프트는 곱하기 연산을 빠르게 처리할 수 있다. (예 : a * 8은 a << 3으로 대체 가능)
    
    6. 오른쪽 시프트 (>>)
        - 모든 비트를 오른쪽으로 이동하며, 왼쪽 빈 자리는 부호 비트로 채운다.
        - 예제 1 : 양수의 오른쪽 시프트
            1. 숫자 : 20 , 2진수 : 00010100 (8비트 기준)
            2. 20 >> 1 (1칸 이동)
            3. 00001010 (1비트 이동, 오른쪽 비트는 버림)
            4. 결과 10
        - 예제 2 : 음수의 오른쪽 시프트
            1. 숫자 : -20 , 2진수 : 11101100
            2. -20 >> 1 (1칸 이동)
            3. 11110110
            4. 결과 - 10
        - 오른쪽 시프트의 일반 공식은 : a를 2n(2의 n제곱)으로 나눈 몫
        - 정수 나눗셈과 동일하지만, 나머지는 버린다(내림).
    
    7. 비트 연산 활용 예제
        1. 특정 비트 확인
            - 주어진 값에서 특정 비트가 1인지 확인하려면 비트 AND 를 사용한다.
            ```
            #include <stdio.h>

            int main() {
                int num = 5;       // 5 = 00000101
                int mask = 1 << 2; // 2^2 = 4 = 00000100

                if (num & mask) {
                    printf("3번째 비트는 1입니다.\n");
                } else {
                    printf("3번째 비트는 0입니다.\n");
                }

                return 0;
            }
            // 출력 결과 : 3번째 비트는 1입니다.
            00000101
            & 00000100
            ----------
            00000100  →  결과가 0이 아니므로 비트는 1

            ```
        
        2. 특정 비트 설정
            - 숫자에서 특정 위치의 비트를 1로 설정하고 싶을 때 사용
            ```
            #include <stdio.h>

            int main() {
                int num = 5;       // 5 = 00000101
                int mask = 1 << 1; // 2^1 = 2 = 00000010

                num = num | mask;  // OR 연산으로 2번째 비트를 1로 설정
                printf("결과: %d\n", num); // 7 = 00000111

                return 0;
            }
            ```

        3. 특정 비트 초기화
            - 숫자에서 특정 위치의 비트를 0으로 초기화 하고 싶을 때 사용.
            - 비트 AND (&) 연산과 비트 NOT (~) 연산을 조합.
            - 초기화하려는 비트만 0이고 나머지는 1인 마스크를 생성
            - 예) 2번째 비트를 초기화하려면 11111101 와 AND 연산
            - 원래 숫자와 마스크를 AND 연산하면 해당 비트가 0으로 설정됨.
            ```
            #include <stdio.h>

            int main() {
                int num = 7;       // 7 = 00000111
                int mask = ~(1 << 1); // ~2 = ~00000010 = 11111101

                num = num & mask;  // AND 연산으로 2번째 비트를 0으로 초기화
                printf("결과: %d\n", num); // 5 = 00000101

                return 0;
            }
            ```
        
        4. 특정 비트 반전
            - 숫자에서 특정 위치의 비트를 0 <-> 1로 반전하고 싶을 때 사용.
            - 비트 XOR (^) 연산을 사용 (각 비트가 서로 다르면 결과 비트가 1)
            - 반전하려는 비트의 위치에 해당하는 마스크 생성
            - 원래 숫자와 마스크를 XOR 연산하면 해당 비트가 반전.
            ```
            #include <stdio.h>
            
            int main(){
                int num = 5; // 5 = 00000101
                int mask = 1 << 1; 2 = 00000010

                num = num ^ mask; // XOR 연산으로 2번째 비트를 반전
                printf("결과: %d\n", num); // 7 = 00000111

                num = num ^ mask; // 다시 XOR 연산으로 원래 값 복원
                printf("복원: %d\n", num); // 5 = 00000101

                return 0;
            }
            ```
        
    
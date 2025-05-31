# Step 2: 조건문과 반복문

## 1. 조건문 (Conditional Statements)

### 1-1. if문
- 특정 조건이 참(true)일 때만 실행되는 코드 블록
    ```
    #include <stdio.h>

    int main() {
        int num;

        printf("숫자를 입력하세요: ");
        scanf("%d", &num);

        if (num > 0) {  // num이 0보다 크면 실행
            printf("입력한 숫자는 양수입니다.\n");
        }

        return 0;
    }
    ```
### 1-2. else 추가
- 
# **문자열 덧셈 계산기**

## 💡 미션 설명

이 미션은 사용자가 입력한 문자열에서 숫자를 추출하여 합계를 계산하는 **문자열 덧셈 계산기**를 구현하는 미션입니다. 쉼표(`,`)와 콜론(`:`)을 기본 구분자로 사용하여 숫자를 분리하며, 사용자가 커스텀 구분자를 지정할 수도 있습니다. 빈 문자열은 0을 반환하고, 음수 또는 유효하지 않은 입력에 대해서는 `[ERROR]` 메시지를 출력합니다.

## 🔎 **기능 구현 목록**

1. 빈 문자열 처리
    - 입력이 빈 문자열일 경우, 0을 반환한다.
    - `“”` ⇒ `결과 : 0`
2. 기본 구분자(쉼표, 콜론)로 문자열을 전달하는 경우 문자열 분리 및 합산
    - 쉼표(,) 또는 콜론(:)을 구분자로 하여 문자열을 분리하고, 각 숫자의 합을 반환한다.
    - `“1,2,3”` ⇒ `결과 : 6`, `“1,2:3”` ⇒ `결과 : 6`
3. 커스텀 구분자 지정 기능
    - 문자열 앞에 “//”와 “\n” 사이에 위치한 문자를 커스텀 구분자로 지정한다.
    - 커스텀 구분자로 전달된 문자열을 분리하고, 각 숫자의 합을 반환한다.
    - 기본 구분자(쉼표, 콜론) 기능도 유지한다.
    - `“//#\n1#2#3”` ⇒ `결과 : 6`, `“//#\n1#2:3”` ⇒ `결과 : 6`
4. 사용자가 잘못된 값을 입력할 경우
    - 숫자가 아닌 입력
        - `[ERROR] 숫자 이외의 값이 포함되어 있습니다.`
        - `“abc”`, `“1,a,b”`
    - 음수 입력
        - `[ERROR] 양수 이외의 값이 포함되어 있습니다.`
        - `“//@\n1:-2:3”`
    - 빈 숫자 입력
        - `[ERROR] 구분자 사이에 숫자가 없습니다.`
        - `"1,,3", "1:2:"`
    - 커스텀 구분자의 형식이 잘못된 경우
        - `[ERROR] 잘못된 커스텀 구분자 형식입니다.`
        - `"//\n1:2:3”`, `"//;\1;2;3”`
    - 허용되지 않은 구분자 사용
        - `[ERROR] 허용되지 않은 구분자가 사용되었습니다.`
        - `"1#2*3”`
    - 커스텀 구분자 지정 후 숫자 생략
        - `[ERROR] 덧셈할 숫자가 없습니다.`
        - `"//;\n”`
    - 숫자 범위 초과
        - `[ERROR] 숫자가 허용된 범위를 초과했습니다.`
        - `"1,9007199254740992”`

## ✅ **과제 제출 전 체크 리스트**

### **기본 기능 구현 체크리스트**

1. **빈 문자열 처리**
    - [ ]  빈 문자열이 입력된 경우, 0을 반환하는가?
    - [ ]  `" "`와 같은 빈 문자열은 제대로 처리되었는가?
2. **기본 구분자(쉼표, 콜론)로 문자열 분리 및 합산**
    - [ ]  쉼표(`,`)와 콜론(`:`)을 구분자로 문자열을 분리하고 합산하는가?
    - [ ]  여러 구분자가 함께 사용된 경우도 처리되었는가? (예: `"1,2:3"` ⇒ `결과 : 6`)
3. **커스텀 구분자 지정 기능**
    - [ ]  문자열 앞에 `"//"`와 `"\n"` 사이의 커스텀 구분자를 제대로 처리하는가?
    - [ ]  커스텀 구분자와 기본 구분자가 혼합된 경우를 처리하는가?
    - [ ]  커스텀 구분자에 특수 문자가 들어가도 제대로 동작하는가? (예: `"//#\n1#2#3"` ⇒ `결과 : 6`)
4. **에러 처리 기능**
    - [ ]  숫자가 아닌 값이 포함된 경우 `[ERROR]` 메시지를 출력하는가? (예: `"abc"`, `"1,a,3"`)
    - [ ]  음수가 포함된 경우 `[ERROR]` 메시지를 출력하는가? (예: `"//@\n1:-2:3"`)
    - [ ]  구분자 사이에 빈 값이 들어간 경우 `[ERROR]` 메시지를 출력하는가? (예: `"1,,3"`)
    - [ ]  커스텀 구분자의 형식이 잘못된 경우 `[ERROR]` 메시지를 출력하는가? (예: `"//\n1:2:3"`)
    - [ ]  허용되지 않은 구분자가 사용된 경우 `[ERROR]` 메시지를 출력하는가? (예: `"1#2*3"`)
    - [ ]  커스텀 구분자 지정 후 숫자가 없는 경우 `[ERROR]` 메시지를 출력하는가? (예: `"//;\n"`)
    - [ ]  숫자가 범위를 초과한 경우 `[ERROR]` 메시지를 출력하는가? (예: `"1,9007199254740992"`)

### **입출력 및 결과 출력 체크리스트**

- [ ]  사용자로부터 입력을 받을 때 `@woowacourse/mission-utils`의 `Console.readLineAsync()`를 사용하였는가?
- [ ]  결과를 출력할 때 `Console.print()`를 사용하였는가?
- [ ]  결과가 예상대로 출력되는가? (예: `"1,2,3"` ⇒ `결과 : 6`)
- [ ]  모든 사용자 입력에 대한 적절한 응답을 출력하는가? (에러 메시지 포함)

### **프로그래밍 요구 사항 체크리스트**

- [ ]  Node.js 20.17.0 버전 이상이며 아래 명령을 입력하여 패키지를 설치한 후 실행하는 데 문제가 없는가?

```jsx
npm install
npm run test
npm run start
```

- [ ]  프로그램의 시작점이 `App.js`의 `run()` 메서드로 되어 있는가?
- [ ]  프로그램 종료 시 `process.exit()`를 호출하지 않았는가?
- [ ]  제공된 `package.json` 파일을 변경하지 않았는가?
- [ ]  외부 라이브러리를 사용하지 않고 구현하였는가?

### **테스트 체크리스트**

- [ ]  구현한 모든 기능에 대해 테스트 케이스를 작성하였는가?
- [ ]  모든 테스트 케이스가 성공하는가?
- [ ]  예외 상황에 대한 테스트도 제대로 처리하였는가? (에러 메시지 출력 등)

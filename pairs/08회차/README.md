# TDD
> Test-Driven Development, 테스트 주도 개발

# 👊 챕터 1
## 🔖 TDD의 리듬
1. 테스트를 빠르게 추가합니다.
2. 모든 테스트를 실행하고 실패하는지 확인합니다.
3. 코드를 수정합니다.
4. 모든 테스트를 실행하고 전부 성공하는지 확인합니다.
5. 리팩토링을 진행합니다.

<br>

## 🔖 코드 작성
1. 객체를 생성하기 전에 테스트를 먼저 작성합니다.
2. 메서드의 완벽한 인터페이스에 대해 상상해보세요!
   - 인터페이스가 외부에서 어떤 식으로 보일지 테스트 코드에 반영하세요.
3. 실제 구현이 아닌 외부에서의 API 형태를 고민하세요.
4. 테스트를 작성하면서 생기는 의문과 문제들은 기록하세요.
5. Stub Function을 구현합니다.
   - 스텁 함수는 가짜 함수(속이 빈)로서 단위 테스트 과정에서 아래의 경우 사용됩니다.
     1. 구현이 되지 않은 함수거나 라이브러리에서 제공하는 함수
     2. 함수가 반환하는 값을 임의로 생성
     3. 복잡한 논리 흐름을 가지는 경우 테스트를 단순화할 목적으로 사용
   - 컴파일만 될 수 있게 최소한으로 구현합니다.
6. 문제의 변형이 필요합니다. 즉, 목적을 단순화 해야 합니다.
   - `특정 기능을 구현하는 것`이 아닌 `테스트를 통과 시키는 것`으로 바꾸세요.
   - 테스트를 잛게 쪼개어 `단계`를 정의하세요.
7. 테스트를 통과할 입력 값에 대한 일반화가 필요합니다.

<br>

## 🔖 의존성과 중복
> 테스트와 코드 사이에는 `한 쪽이 수정되면 반드시 다른 한 쪽도 수정 해야 하는` **의존성**이 존재합니다.

- 동일한 문장, 코드, 기능이 반복되는 것을 `중복`이라고 합니다.
- 중복을 하나로 통합시키는 작업에는 `객체`를 이용하세요.
- 중복을 제거한다는 것은 `의존성`도 제거하는 것입니다. TDD의 규칙에 중복 제거가 있는 이유죠.

<br>

정리하자면, `TDD`의 핵심은 시작부터 이런 단계를 거치는 것이 아닙니다. 문제가 발생하거나 특정 상황에 맞닥뜨리면 이런 단계로 쪼개어 해결하는 것이죠.

<br>

# 👊 챕터 2
## 🔖 테스트 케이스
1. +, -, x, /, %, +/-, .



/**
 * 아벤님 회고
 * 1. 우선 순위를 못 찾는다.
 *  => 우선 순위를 찾는 기능을 구현해야 한다.
 * 2. findIndex 로직의 수정이 필요해 보인다.
 *  => 해당 함수는 첫 번째 동일한 값만 찾으므로
 *     다른 위치의 동일 연산자에 대해 탐색하도록 수정이 필요하다.
 *
 * ===> 의존하는 느낌이 있다. 생각을 하고 의견을 냈어야 했는데 조금 부족했었다.
 * ===> 회고로 나온 개선이 필요한 부분에 대해서 의견 생각해오기,
 *      의견을 듣고 혼자서도 전개가 가능하다고 확신할 때 '네'라고 답하기,
 *
 *
 * 파랑 회고
 * 1. 음수 처리가 필요하다.
 *  => 정규표현식으로 parse하는 부분에서 음수가 들어오게 되면 로직이 틀어진다.
 * 2. 실시간으로 연산을 반영해야 한다.
 *  => 구조, 데이터 flow가 정립되어야 한다.
 * 3. for문을 개선시켜야 한다.
 *  => 연산식이 얼마나 입력될 지 모르므로 for-break는 유연성이 떨어진다.
 *
 * ===> 테스트케이스 수립이 약하다. 사전 협의 없이 생각을 진행한 것... 태도가 안 좋다.
 * ===> 객체 제어, 반복문이나 functional Component에 대해 공부하기
 *      개선해야 하는 부분과 확장이 필요한 부분을 정리하기
 *      테스트 케이스를 진행할 스텁 함수 구현에 대해 생각해보기
 *      7회차 내용을 기준으로 README를 정리해서 회차별 진행도를 시각화하기
 */


parse 부분
- 한 번 돌고 나면 break로 종료된다.
- 여러 연산자를 고려하지 않고 작성했기에 operators를 Object 형태로 둔다. *, %, / 연산자를 2로, +, -를 1로 우선 순위를 둔다.
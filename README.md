# 미션 - 숫자 야구 게임

## 🛠️️ 주요 성공 시나리오와 구현할 기능 목록

#### 1. 게임이 시작된다.

- 게임을 시작하는 기능

#### 2. Computer가 자신의 숫자를 랜덤으로 지정한다.

- 서로 다른 수로 이루어진 3자리 수 생성

#### 3. Player는 정답을 맞힐 때까지 숫자를 입력한다.

- 사용자에게 숫자를 요청하고 받는 기능
- 숫자의 유효성 검사 (IllegalArgumentException을 발생)
    - [예외] 3자리 숫자가 아닌 경우
    - [예외] 각 자리의 숫자가 1~9 사이가 아닌 경우
    - [예외] 각 자리의 숫자가 중복되었을 경우
- 3개의 숫자를 입력 받고 관리하는 기능
- 게임의 진행 상태 관리 기능(정답을 맞출 때까지 해당 과정을 반복해야 한다.)

#### 4. 입력 시에 정답을 맞히기 위한 힌트가 제공된다.

- Player의 숫자와 비교하여 힌트 생성하는 기능
    - 볼 카운트 생성
    - 스트라이크 카운트 생성
- 힌트 메세지를 출력

#### 5. Player가 정답을 맞힌다면 게임을 종료한다.

- 정답 판별 기능
- 성공 메세지 출력

#### 6. Player는 게임을 다시 시작할 것인지 선택한다.

- 사용자에게 게임 종료 및 재시작 요청을 받는 기능
- 게임 재시작 요청 유효성 검사 (IllegalArgumentException을 발생)
    - [예외] 1, 2가 아닌 숫자를 입력했을 경우
- 게임 종료 혹은 다시 시작을 선택하는 기능

#### 7. Player가 게임을 종료할 때까지 반복한다.

- 게임에 종료 요청이 오지 않는다면 게임을 반복하는 기능

<br>

## ✔️ 확장

랜덤 숫자

- 1~9 사이의 중복되지 않은 3자리 숫자이다.

숫자 입력

- 1~9 사이의 중복되지 않은 숫자 3자리를 입력해야 한다.

힌트 제공

- 힌트는 "0볼 0스트라이크" 형태로 주어진다.
- 해당되는 볼이 없다면 "0스트라이크" 형태로 주어진다.
- 해당되는 스트라이크가 없다면 "0볼" 형태로 주어진다.
- 해당되는 볼과 스트라이크가 모두 없다면 힌트는 "낫싱"으로 주어진다.

게임 재시작

- 게임 재시작 요청은 1, 게임 종료 요청은 2이다.

예외처리

- IllegalArgumentException이 발생하면 어플리케이션을 종료한다.

<br>
<br>

## 🔍 진행방식

- 미션은 **기능 요구사항, 프로그래밍 요구사항, 과제 진행 요구사항** 세 가지로 구성되어 있다.
- 세 개의 요구사항을 만족하기 위해 노력한다. 특히 기능을 구현하기 전에 기능 목록을 만들고, 기능 단위로 커밋 하는 방식으로 진행한다.

## ✉️ 미션 제출 방법

- 미션 구현을 완료한 후 GitHub을 통해 제출해야 한다.
    - GitHub을 활용한 제출 방법은 [프리코스 과제 제출 문서](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse) 를 참고해
      제출한다.
- GitHub에 미션을 제출한 후 [우아한테크코스 지원 플랫폼](https://apply.techcourse.co.kr) 에 접속하여 프리코스 과제를 제출한다.
    - 자세한 방법은 [링크](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse#제출-가이드) 를 참고한다.
    - **Pull Request만 보내고, 지원 플랫폼에서 과제를 제출하지 않으면 최종 제출하지 않은 것으로 처리되니 주의한다.**

## ✔️ 과제 제출 전 체크리스트 - 0점 방지

- 터미널에서 `java -version`을 실행해 자바 8인지 확인한다. 또는 Eclipse, IntelliJ IDEA와 같은 IDE의 자바 8로 실행하는지 확인한다.
- 터미널에서 맥 또는 리눅스 사용자의 경우 `./gradlew clean test`, 윈도우 사용자의 경우 `gradlew.bat clean test` 명령을 실행했을 때 모든 테스트가 통과하는지 확인한다.

---

## 🚀 기능 요구사항

기본적으로 1부터 9까지 서로 다른 수로 이루어진 3자리의 수를 맞추는 게임이다.

- 같은 수가 같은 자리에 있으면 스트라이크, 다른 자리에 있으면 볼, 같은 수가 전혀 없으면 포볼 또는 낫싱이란 힌트를 얻고, 그 힌트를 이용해서 먼저 상대방(컴퓨터)의 수를 맞추면 승리한다.
    - 예) 상대방(컴퓨터)의 수가 425일 때
        - 123을 제시한 경우 : 1스트라이크
        - 456을 제시한 경우 : 1볼 1스트라이크
        - 789를 제시한 경우 : 낫싱
- 위 숫자 야구 게임에서 상대방의 역할을 컴퓨터가 한다. 컴퓨터는 1에서 9까지 서로 다른 임의의 수 3개를 선택한다. 게임 플레이어는 컴퓨터가 생각하고 있는 3개의 숫자를 입력하고, 컴퓨터는 입력한 숫자에 대한
  결과를 출력한다.
- 이 같은 과정을 반복해 컴퓨터가 선택한 3개의 숫자를 모두 맞히면 게임이 종료된다.
- 게임을 종료한 후 게임을 다시 시작하거나 완전히 종료할 수 있다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨 후 애플리케이션은 종료되어야 한다.
- 아래의 프로그래밍 실행 결과 예시와 동일하게 입력과 출력이 이루어져야 한다.

<br>

## ✍🏻 입출력 요구사항

### ⌨️ 입력

- 3자리의 수
- 게임이 끝난 경우 재시작/종료를 구분하는 1과 2 중 하나의 수

### 🖥 출력

- 입력한 수에 대한 결과를 볼, 스트라이크 개수로 표시

```
1볼 1스트라이크
```

- 하나도 없는 경우

```
낫싱
```

- 3개의 숫자를 모두 맞힐 경우

```
3스트라이크
3개의 숫자를 모두 맞히셨습니다! 게임 종료
```

### 💻 프로그래밍 실행 결과 예시

```
숫자를 입력해주세요 : 123
1볼 1스트라이크
숫자를 입력해주세요 : 145
1볼 
숫자를 입력해주세요 : 671
2볼 
숫자를 입력해주세요 : 216
1스트라이크 
숫자를 입력해주세요 : 713
3스트라이크 
3개의 숫자를 모두 맞히셨습니다! 게임 종료
게임을 새로 시작하려면 1, 종료하려면 2를 입력하세요.
1
숫자를 입력해주세요 : 123
1볼
… 
```

<br>

---

## 🎱 프로그래밍 요구사항

- 프로그램을 실행하는 시작점은 `Application`의 `main()`이다.
- JDK 8 버전에서 실행 가능해야 한다. **JDK 8에서 정상 동작하지 않을 경우 0점 처리**한다.
- 자바 코드 컨벤션을 지키면서 프로그래밍한다.
    - https://naver.github.io/hackday-conventions-java
- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메소드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메소드)가 한 가지 일만 하도록 최대한 작게 만들어라.

### 프로그래밍 요구사항 - Randoms, Console

- JDK에서 기본 제공하는 Random, Scanner API 대신 `camp.nextstep.edu.missionutils`에서 제공하는 `Randoms`, `Console` API를 활용해 구현해야 한다.
    - Random 값 추출은 `camp.nextstep.edu.missionutils.Randoms`의 `pickNumberInRange()`를 활용한다.
    - 사용자가 입력하는 값은 `camp.nextstep.edu.missionutils.Console`의 `readLine()`을 활용한다.
- 프로그램 구현을 완료했을 때 `src/test/java` 디렉터리의 `ApplicationTest`에 있는 모든 테스트 케이스가 성공해야 한다. **테스트가 실패할 경우 0점 처리한다.**

<br>

---

## 📈 과제 진행 요구사항

- 미션은 [java-baseball-precourse](https://github.com/woowacourse/java-baseball-precourse) 저장소를 Fork/Clone해 시작한다.
- **기능을 구현하기 전에 java-baseball-precourse/README.md 파일에 구현할 기능 목록을 정리**해 추가한다.
- **Git의 커밋 단위는 앞 단계에서 README.md 파일에 정리한 기능 목록 단위**로 추가한다.
    - [AngularJS Commit Message Conventions](https://gist.github.com/stephenparish/9941e89d80e2bc58a153) 참고해 commit log를
      남긴다.
- 과제 진행 및 제출 방법은 [프리코스 과제 제출 문서](https://github.com/woowacourse/woowacourse-docs/tree/master/precourse) 를 참고한다.

<br>

---

## 📝 License

This project is [MIT](https://github.com/woowacourse/java-baseball-precourse/blob/master/LICENSE) licensed.

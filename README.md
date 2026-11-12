# AX 기획서 (ax-prd)

업무진단에서 고른 AX 과제 하나를 문답으로 정리해 PRD(개발기획서) 마크다운 파일로 만드는 Claude 스킬입니다.

개발자가 아닌 사람을 위해 만들었습니다. 협동조합, 사회적기업, 비영리 조직의 실무자와 그 조직을 돕는 컨설턴트가 자기 업무의 말로 답하면, 개발자나 AI 개발 도구에게 그대로 넘길 수 있는 문서가 나옵니다.

## 무엇을 하나

1. 진단 자료(엑셀 워크시트, 메모)를 먼저 읽습니다. 자료에 있는 것은 다시 묻지 않습니다.
2. 이해한 내용을 되돌려 말하고 틀린 곳을 고칩니다.
3. 빠진 것만 한 번에 하나씩, 일곱 개 안에서 묻습니다.
4. 바뀐 업무를 단계로 적고, 단계마다 가장 가벼운 해결 방법을 제안합니다.
5. 설정만으로 끝나는 부분과 개발해야 하는 부분을 가릅니다.
6. `PRD_<과제명>.md`를 쓰고, 열 가지로 스스로 점검한 뒤, 확인이 필요한 것을 목록으로 넘깁니다.

모르는 숫자와 이름은 지어내지 않고 `[확인 필요: 무엇을, 누구에게]`로 남깁니다.

## 설치

### Claude 데스크톱 앱, claude.ai

1. [ax-prd.zip](https://github.com/dosankim/ax-prd/releases/latest/download/ax-prd.zip)을 내려받습니다.
2. Claude의 설정에서 스킬 메뉴를 열고 ZIP 파일을 올립니다. 메뉴의 위치와 이름은 앱 버전에 따라 다를 수 있습니다.
3. 스킬을 켭니다.

### Claude Code

```bash
git clone https://github.com/dosankim/ax-prd ~/.claude/skills/ax-prd
```

## 쓰는 법

진단 자료가 든 폴더를 연결하거나 파일을 올린 뒤 이렇게 말합니다.

```
이 과제 PRD 써 줘
```

자료가 없어도 됩니다. 바꾸려는 업무를 말로 설명하면 거기서 시작합니다.

이미 쓴 PRD가 있으면 이렇게 말합니다.

```
이 PRD 검토해 줘
```

## PRD에 들어가는 것

한 줄 요약 / 1. 과제 / 2. 쓰는 사람 / 3. 지금의 업무와 문제 / 4. 바뀐 업무(단계, 담당, 방법, 사람이 확인하는 곳) / 5. 설정으로 끝나는 부분과 개발할 부분 / 6. 완료 기준과 필수 기능(다섯 개 이내) / 7. 이번에 하지 않는 것 / 8. 시험 자료(정상, 예외, 경계) / 9. 자료와 개인정보 / 10. 가치 점검 / 11. 다음 단계에서 할 일 / 확인이 필요한 것 / 스킬이 정한 것

다 쓴 모습은 두 편이 있습니다. 가상의 조직과 숫자입니다.

- [개발할 부분이 있는 경우](examples/prd-catering-order.md)
- [설정만으로 끝나는 경우](examples/prd-grant-search.md)

## 해결 방법 일곱 가지

단계마다 가벼운 것부터 차례로 맞는지 봅니다.

| 순서 | 방법 | 한 줄 설명 |
|---|---|---|
| 1 | 사람이 그대로 한다 | 바꾸지 않는다 |
| 2 | 파일 작업 | AI가 폴더의 파일을 읽고 새 파일을 만든다 |
| 3 | 연결 | AI가 메일, 캘린더, 드라이브를 읽고 초안을 만든다 |
| 4 | 웹사이트 작업 | AI가 브라우저로 웹사이트를 읽고 입력한다 |
| 5 | 예약 실행 | 정해 둔 시각에 자동으로 실행한다 |
| 6 | 컴퓨터 직접 조작 | AI가 화면을 보고 프로그램을 다룬다 |
| 7 | 개발 | 새 프로그램이나 화면을 만든다 |

고르는 기준은 [references/methods.md](references/methods.md)에 있습니다.

## 파일 구성

```
ax-prd/
├── SKILL.md                      스킬 본문
├── references/
│   ├── from-diagnosis.md         진단 양식의 어느 칸이 PRD의 어디로 가는지
│   ├── interview.md              물을 내용과 묻는 법
│   ├── methods.md                해결 방법 일곱 가지와 고르는 기준
│   └── quality-check.md          점검 열 가지와 보고 형식
├── assets/
│   └── prd-template.md           PRD의 빈 틀
└── examples/
    ├── diagnosis-catering-order.md   입력 예시 (가상)
    ├── prd-catering-order.md       결과 예시: 개발할 부분이 있는 경우 (가상)
    └── prd-grant-search.md       결과 예시: 설정만으로 끝나는 경우 (가상)
```

## 참고한 것

구조와 문답 방식을 정할 때 아래 공개 스킬을 읽고 참고했습니다. 문장을 옮겨 오지는 않았습니다.

- [obra/superpowers](https://github.com/obra/superpowers)의 brainstorming: 먼저 읽고 나서 묻기, 한 번에 하나만 묻기, 되돌려 말하기, 처음 보는 사람의 눈으로 다시 읽기
- [anatasof/NatPRD](https://github.com/anatasof/NatPRD): 모르는 것을 지어내지 않고 표시해 두는 규칙, 쓴 뒤의 점검
- [github/awesome-copilot](https://github.com/github/awesome-copilot)의 prd: 눈으로 확인할 수 있는 완료 기준, 하지 않는 것 적기
- [garrytan/gstack](https://github.com/garrytan/gstack)의 office-hours: 만들기 전에 전제를 묻는 진행

진단 양식의 번호(A-5, A-7, A-10 등)는 「협동조합 AX 컨설팅 양식」의 것을 따랐습니다.

## 라이선스

MIT

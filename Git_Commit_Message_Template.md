# Git 커밋 메시지 템플릿

여러 레퍼런스 참고해서 나만의 커밋 메시지 템플릿 완성

```text
#######################################################
# ------- 제목(SUBJECT) -------
# |<---  <커밋 타입>: <제목> | 50 글자 이내  --->|
# (예) docs(guide): updated fixed docs from Google Docs


# ------- 본문(BODY) -------
# |<---  (선택) 무엇을, 왜 했는가 | 한 줄 72 글자 이내  --->|
# (예)
# Couple of typos fixed:
# - indentation
# - batchLogbatchLog -> batchLog


# ------- 꼬리말(FOOTER) -------
# |<---  (선택) <키워드> #<이슈 번호> | (선택) 주요 변경 내역(Breaking Changes)  --->|
# (예) Closes #7, #35


#######################################################
#   ------- [COMMIT TYPE LIST] -------
#   | COMMIT_TYPE | SUMMARY            | DESCRIPTION                         |
#   | ----------- | ------------------ | ----------------------------------- |
#   | feat        | 기능               | 새로운 기능 추가                    |
#   | fix         | 버그               | 버그 해결                           |
#   | docs        | 문서               | 문서 추가                           |
#   | test        | 테스트             | 테스트 코드 추가                    |
#   | refactor    | 코드 리팩토링      | 기능 변경 없이 코드 내부 구조 변경  |
#   | style       | 스타일             | 코드 형식((예)세미콜론 추가)        |
#   | chore       | 기타 변경사항      | 빌드 스크립트/패키지 매니저 수정    |
#   | design      | 디자인             | 사용자 UI 디자인(예>CSS) 변경       |
#   | post        | 포스트             | 포스트 추가                         |
#   | rename      | 파일/폴더명 수정   | 파일/폴더명 수정/이동만 하는 경우   |
#   | remove      | 파일 삭제          | 파일 삭제만 하는 경우               |        
#######################################################
#   ------- [CHECKLIST] -------
#   - 제목(SUBJECT)
#         - 명령문
#         - 첫 글자 대문자
#         - 끝에 마침표(.) 금지
#         - 과거 시제 금지 (예) Fixed -> Fix
#         - 50 글자 이내
#   - 본문(BODY) - (선택 사항)
#         - 제목과 본문을 한 줄 띄워 분리
#         - 여러 줄 메시지를 작성할 때 글머리 기호 "-" 사용
#         - 어떻게(How) 보다 무엇을(What), 왜(Why) 로 설명
#         - 한 줄 72 글자 이내
#   - 꼬리말(FOOTER) - (선택 사항)
#         - Issue 종료 키워드 - 각 키워드마다 기능 차이 없음, 문법/맥락 맞게 사용
#                - Close, Closese, Closed: 일반 개발 이슈
#                - Fix, Fixes, Fixed: 버그 픽스나 핫 픽스 이슈
#                - Resolve, Resolves, Resolved: 문의/요청 사항에 대응한 이슈
#         - Issue Tracker Id 작성
#         - 주요 변경 내역(Breaking Changes) 작성
#                BREAKING CHANGE: <주요 변경 내역 요약>
#                <BLANK LINE>
#                <변경점 + 마이그레이션 지시>
#                <BLANK LINE>
#                <BLANK LINE>
#                Fixes #<이슈번호>
#######################################################
# For updated templates, visit: https://github.com/HRPzz
# License CC
#######################################################
```

## 커밋 메시지 템플릿 설정

1. 커밋 메시지 템플릿 텍스트 파일 생성

```bash
touch .gitmessage.txt
```

2. 템플릿 작성

```bash
vim .gitmessage.txt  # 커밋 메시지 템플릿 작성하고 저장
```

3. 템플릿 설정

```bash
git config —global commit.template .gitmessage.txt
```

4. 커밋

```bash
git add .
git commit  # COMMIT_EDITMSG (커밋 메시지 템플릿 편집 창) 에서 커밋 메시지 작성
git push
```

## 커밋 메시지 예시

```text
style($location): add couple of missing semi colons
```

```text
docs(guide): updated fixed docs from Google Docs

Couple of typos fixed:
- indentation
- batchLogbatchLog -> batchLog
- start periodic checking
- missing brace

Close #351
```

```text
feat($compile): simplify isolate scope bindings

Changed the isolate scope binding options to:
  - @attr - attribute binding (including interpolation)
  - =model - by-directional model binding
  - &expr - expression execution binding

This change simplifies the terminology as well as
number of choices available to the developer. It
also supports local name aliasing from the parent.

BREAKING CHANGE: isolate scope bindings definition has changed and
the inject option for the directive controller injection was removed.

To migrate the code follow the example below:

Before:

scope: {
  myAttr: 'attribute',
  myBind: 'bind',
  myExpression: 'expression',
  myEval: 'evaluate',
  myAccessor: 'accessor'
}

After:

scope: {
  myAttr: '@',
  myBind: '@',
  myExpression: '&',
  // myEval - usually not useful, but in cases where the expression is assignable, you can use '='
  myAccessor: '=' // in directive's template change myAccessor() to myAccessor
}

The removed `inject` wasn't generaly useful for directives so there should be no code using it.
```

## [참고] Git Commit Convention

- 커밋 메시지 템플릿 대략적인 구조

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

- 커밋 메시지 템플릿 기본 - 한국어

```text
# <타입> : <제목> 형식으로 작성하며 제목은 최대 50글자 정도로만 입력
# 제목을 아랫줄에 작성, 제목 끝에 마침표 금지, 무엇을 했는지 명확하게 작성

################
# 본문(추가 설명)을 아랫줄에 작성

################
# 꼬릿말(footer)을 아랫줄에 작성 (관련된 이슈 번호 등 추가)

################
# feature : 새로운 기능 추가
# fix : 버그 수정
# docs : 문서 수정
# test : 테스트 코드 추가
# refactor : 코드 리팩토링
# style : 코드 의미에 영향을 주지 않는 변경사항
# chore : 빌드 부분 혹은 패키지 매니저 수정사항
################
```

- 커밋 메시지 템플릿 기본 - 영어

```text
# <type>: <subject>
##### Subject 50 characters ################# -> |


# Body Message
######## Body 72 characters ####################################### -> |

# Issue Tracker Number or URL

# --- COMMIT END ---
# Type can be
#   feat    : new feature
#   fix     : bug fix
#   refactor: refactoring production code
#   style   : formatting, missing semi colons, etc; no code change
#   docs    : changes to documentation
#   test    : adding or refactoring tests
#             no productin code change
#   chore   : updating grunt tasks etc
#             no production code change
# ------------------
# Remember me ~
#   Capitalize the subject line
#   Use the imperative mood in the subject line
#   Do not end the subject line with a period
#   Separate subject from body with a blank line
#   Use the body to explain what and why vs. how
#   Can use multiple lines with "-" for bullet points in body
# ------------------
```

## 참고 링크

- [깃 커밋 템플릿 만들어서 간편하게 커밋해보자!][git_commit_msg_template_1]
- [[Git] 커밋 메시지 템플릿 설정하기][git_commit_msg_template_2]
- [[Git] git commit message template 깃 커밋 템플릿 작성하기][git_commit_msg_template_3]
- [좋은 git 커밋 메시지를 작성하기 위한 8가지 약속][git_commit_msg_template_4]
- [[Git] 커밋 메시지 규약 정리 (the AngularJS commit conventions)][git_commit_msg_template_5]

[git_commit_msg_template_1]: https://jihyun-hamster.tistory.com/132
[git_commit_msg_template_2]: https://velog.io/@bky373/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%ED%85%9C%ED%94%8C%EB%A6%BF
[git_commit_msg_template_3]: https://kkangsg.tistory.com/95
[git_commit_msg_template_4]: https://velog.io/@outstandingboy/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B7%9C%EC%95%BD-%EC%A0%95%EB%A6%AC-the-AngularJS-commit-conventions
[git_commit_msg_template_5]: https://djkeh.github.io/articles/How-to-write-a-git-commit-message-kor/

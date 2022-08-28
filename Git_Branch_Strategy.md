# Git 브랜치 전략

## Git 브랜치 전략 사진

![](https://techblog.woowahan.com/wp-content/uploads/img/2017-10-30/git-flow_overall_graph.png)

![](https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg?cdnVersion=696)

- Git Flow
  - 항상 존재하는 메인(=중심) 브랜치: main, develop
  - 필요에 따라 생성하는 브랜치: feature, hotfix, release
    - merge 된 feature, hotfix, release 브랜치 삭제

- **main**: 현재 릴리즈되고 있는 브랜치
  - release 브랜치에서 merge 끝난 상태 => 버전 태그 필요(e.g. v1.0, v0.2)
  - 배포 가능한 상태만 관리
  - _hotfix_ 브랜치: 배포한 버전에서 급하게 수정할 필요가 있을 때 main 브랜치에서 분리하는 브랜치
    - 변경사항은 develop 브랜치에도 merge 해야 함
    - merge 끝나면 삭제
  - **develop** 브랜치: 개발된 기능이 추가된 브랜치
    - 다음에 배포할 것을 개발
    - 통합 브랜치 역할
    - _feature_ 브랜치: 기능을 개발하고 있는 브랜치
      - 생성 전 develop 브랜치를 반드시 pull 받아야 함
      - develop 브랜치 안에서 생성
      - 보통 개발자 저장소에만 있는 브랜치, origin 에는 push하지 않음
      - 작업 끝난 후 develop 브랜치로 merge
      - merge 끝나면 삭제
      - 주의
        - 하나의 클래스를 여러 명이 건들지 않게 진행
        - 코드리뷰 때 코드 충돌 확인
        - 코드 충돌 발생할 경우 merge 하는 사람, 코드 작성한 사람과 함께 해결
    - _release_ 브랜치: 배포 전 준비를 하는 브랜치
      - QA 진행하면서 발생한 버그는 release 브랜치에서 수정함
      - QA 무사히 끝나면 release 브랜치를 main과 develop 브랜치로 merge
      - merge 끝나면 삭제

## Git Repository 구성

![](https://techblog.woowahan.com/wp-content/uploads/img/2017-10-30/github-flow_repository_structure.png)

## GitHub 브랜치 전략

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsdBbR%2FbtrcStJorVL%2Fxod1cfgCDDspfnxBzNuaqk%2Fimg.png)

- GitHub Flow
  - Git Flow 에 비해 간단함
  - Main 브랜치를 Release 브랜치로 사용
  - 나머지 브랜치는 Pull Request 하여 사용함

## 참고 링크

- [우아한 형제들 기술 블로그](https://techblog.woowahan.com/2553/)
- [협업을 위한 Git Flow 설정하기](https://overcome-the-limits.tistory.com/7)
- [Git Branch Strategy(깃 브랜치 전략)](https://velog.io/@rafael/Git-Branch-Strategy%EA%B9%83-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5)
- [Git 브랜치 전략](https://velog.io/@jinuku/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5)
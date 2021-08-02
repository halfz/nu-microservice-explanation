# 멀티스프린트팀을 위한 Front 마이크로 서비스 도입기


## 서비스 설명
넥스트유니콘은 스타트업과 투자자를 연결시키는 온라인 플랫폼 서비스부터, 데모데이를 온라인에서 가능케한 "유니콘LIVE", 스타트업이 PR을 쉽게하는 "뉴스룸" 서비스로 이루어져있음 (발표시까지 유니콘HR 신규오픈 예정)


## 초기의 프로젝트 구조 및 상태
개발인원 5명(프론트 3명)
초기 폴더구조 (초기 폴더구조 코드 첨부 필요)
- components
- containers
- redux
- utils
-> 소규모 팀에 어울림, 빠른 개발가능, 서로 유기적으로 연결되어있음. 커뮤니케이션 코스트가 적음


## 두개의 스프린트 팀
개밸인원 11명(프론트 6명)
-> 2개의 팀으로 분리
스프린트를 각각 가져가게됨


## 문제가 부각됨
  - Conflict
  - Code 파편화
  - 커뮤니케이션 이슈


## 해결책 1 - 디자인 시스템
  ### NU Design System
  - 1차적으로 시각 컴포넌트에만 집중
  - redux 등 데이터 연결고리를 끊어내어 제작
  - 디자인 시스템은 Cross-team PR을 통해 코드스타일을 최대한 유지


## 해결책 2 - Structuring
  ### 폴더 구조 개선
  - @designSystem
  - @sharedUtils
  - @sharedRedux
  - service1
  - @sharedComponents
  - @sharedUtils 
  - @redux
  - page1
  - @components
  - @utils
  - page2
    - @components
    - @utils
  ...
  - lint를 통해 @ prefix폴더는 해당폴더 및 하위폴더에서만 쓸수 있게함
  - 영향범위가 예측가능해짐
  - Sprint team 간의 code conflict 최소화


## 해결책 3 - Lint & CI
  - 폴더 구조에 대한 Lint -> 컴포넌트들이 영향범위 예측가능하게 작성됨
  - PR날릴때 bitbucket pipeline(github action 같은 것)을 이용해, 공용 컴포넌트가 수정되었을때, Cross team간에 slack noti가 감
  - QA시에 참고해야하는 컴포넌트들도 자동으로 정리할수 있었음!


## 앞으로 해야할 일 - microservice 따로 빌드
  - 공용으로쓰는 것들을 한번 빌드하고 microservice가 수정될때마다 따로 빌드하게해 빌드 타임을 줄임
  - sandbox모드 서비스
  - 다른 서비스에 영향범위가 zero인 서비스
  - lean하게 내부 자원들(api사용 utils, designSystem)을 사용하여, MVP 실험을 가능하게.

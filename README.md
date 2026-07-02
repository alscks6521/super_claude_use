# super_claude_use
슈퍼클로드 사용서


# 🚀 SuperClaude 완전 이해 가이드

[[Super_Claude_주명령어]]
## 목차

1. [[#SuperClaude가 뭔지.]]
2. [[#어떻게 작동?]]
3. [[#설치 방법]]
4. [[#4가지 핵심 구성요소]]
5. [[#언제 써야?]]
6. [[#실전 워크플로우]]
7. [[#4주 학습 로드맵]]

---

## SuperClaude가 뭔자.

한마디로 **Claude Code를 업그레이드해주는 설정 프레임워크**야.

Claude Code 자체를 바꾸는 게 아니라, `.md` 파일들로 Claude의 행동 방식을 미리 세팅해두는 거임.  
그래서 `/sc:implement` 같은 커맨드를 치면, Claude가 그 `.md` 파일을 읽고 훨씬 체계적으로 반응하는 방식.

> 비유하자면: Claude Code = 스마트폰, SuperClaude = 최적화된 앱 설정 프로필

---

## 어떻게 작동?

```
내가 /sc:커맨드 입력
       ↓
Claude Code가 설치된 .md 행동 파일 읽음
       ↓
해당 커맨드에 맞는 행동 패턴 활성화
       ↓
MCP 서버 연동 (설치한 경우)
       ↓
훨씬 구조적이고 전문적인 응답 나옴
```

**핵심**: `/sc:` 앞에 붙이는 것만으로 Claude가 전문가 모드로 전환됨

---

## 설치 방법

```bash
# pipx 권장 (이미 설치했으니 이걸로)
pipx install SuperClaude
SuperClaude install
```

설치하면 `~/.claude/` 폴더에 `.md` 행동 파일들이 저장됨.  
한 번만 설치하면 모든 프로젝트에서 자동 적용.

---

## 4가지 핵심 구성요소

### [[#커맨드 30개]]

### [[#AI 에이전트 20개]]

### [[#행동 모드 7개]]

### [[#MCP 서버 8개]]

---

### 커맨드 30개

`/sc:` 로 시작하는 슬래시 커맨드들. 자주 쓰는 것들:

|커맨드|용도|
|---|---|
|`/sc:brainstorm`|기획, 아이디어 정리|
|`/sc:analyze`|코드/구조 분석|
|`/sc:implement`|기능 구현|
|`/sc:test`|테스트 작성|
|`/sc:workflow`|구현 로드맵 생성|
|`/sc:load`|프로젝트 구조 불러오기|
|`/sc:save`|세션 저장|
|`/sc:review`|코드 리뷰|
|`/sc:fix`|버그 수정|
|`/sc:document`|문서 자동 작성|

---

### AI 에이전트 20개

`@agent-이름` 형식으로 호출하는 도메인 전문가들.  
특정 분야가 필요할 때 해당 에이전트를 부르면 그 분야에 특화된 응답을 해줌.

|에이전트|전문 분야|
|---|---|
|`@agent-architect`|시스템 설계|
|`@agent-frontend`|UI/UX 구현|
|`@agent-backend`|서버/API|
|`@agent-security`|보안 검토|
|`@agent-qa`|테스트/품질|
|`@agent-devops`|배포/인프라|

**사용 예시**

```
@agent-security "이 로그인 코드 보안 취약점 있어?"
@agent-frontend "이 컴포넌트 구조 어때?"
```

---

### 행동 모드 7개

Claude의 사고 방식 자체를 바꾸는 모드들.  
커맨드와 조합해서 쓰면 더 강력해짐.

|모드|설명|
|---|---|
|브레인스토밍|질문 중심으로 아이디어 탐색|
|오케스트레이션|여러 툴을 효율적으로 조율|
|태스크 관리|체계적인 작업 분리|
|딥 리서치|자율 웹 리서치|
|토큰 절약|컨텍스트 30~50% 절약|
|비즈니스 패널|멀티 전문가 관점 분석|
|인트로스펙션|메타 인지 분석|

---

### MCP 서버 8개

설치하면 성능이 2~3배 올라가는 외부 툴 연동. **선택사항**이지만 쓰면 확실히 달라짐.

|서버|역할|효과|
|---|---|---|
|Serena|코드 이해|실행 속도 2~3배 향상|
|Sequential|단계적 추론|토큰 30~50% 절약|
|Tavily|웹 검색|`/sc:research` 강화|
|Context7|공식 문서 조회|최신 문서 참조|
|Playwright|브라우저 자동화|E2E 테스트|
|Magic|UI 컴포넌트 생성|프론트엔드 강화|

```bash
# MCP 서버 설치
superclaude mcp --list       # 사용 가능한 서버 확인
superclaude mcp              # 인터랙티브 설치
superclaude mcp --servers tavily context7  # 특정 서버만 설치
```

---

## 언제 써야?

### ✅ SuperClaude 커맨드 쓸 때

- 처음부터 끝까지 기능 하나를 제대로 만들 때
- 아키텍처 설계처럼 체계가 필요할 때
- 보안, 테스트 등 전문 영역이 필요할 때
- 긴 프로젝트에서 세션 이어가며 작업할 때

### 💭 그냥 Claude Code 쓸 때

- "이 에러 뭐야?" 같은 간단한 질문
- 함수 하나 뚝딱 만들 때
- 개념 설명 들을 때
- 빠른 프로토타입

> **결론**: 진지하게 개발할 땐 `/sc:`, 가볍게 물어볼 땐 그냥 채팅

---

## 실전 워크플로우

### 새 프로젝트 시작할 때 추천 순서

```
1. /sc:brainstorm "만들 것 설명"   → 요구사항 정리
2. /sc:load src/                   → 기존 코드 불러오기 (있으면)
3. /sc:analyze --focus architecture → 구조 분석
4. /sc:workflow "핵심 기능"        → 구현 계획 수립
5. /sc:implement "기능 설명"       → 실제 구현
6. /sc:test --coverage             → 테스트
7. /sc:save "세션이름"             → 저장
```

### 도메인별 조합

|하고 싶은 것|커맨드 + 에이전트|MCP|
|---|---|---|
|UI 컴포넌트 만들기|`/sc:implement` + `@agent-frontend`|Magic|
|API 설계|`/sc:design` + `@agent-backend`|Sequential|
|보안 점검|`/sc:review` + `@agent-security`|Context7|
|E2E 테스트|`/sc:test` + `@agent-qa`|Playwright|

---

## 4주 학습 로드맵

### [[#1주차 - 기본 커맨드]]

### [[#2주차 - 행동 모드]]

### [[#3주차 - MCP 서버]]

### [[#4주차 - 고급 패턴]]

---

### 1주차 - 기본 커맨드

핵심 3개만 집중해서 익히기:

- `/sc:brainstorm` - 기획할 때
- `/sc:analyze` - 코드 분석할 때
- `/sc:implement` - 구현할 때

**목표**: 커맨드 없이 개발하기 불편해지는 것

---

### 2주차 - 행동 모드

커맨드에 모드 조합하는 법 익히기.  
플래그(`--focus`, `--coverage` 등) 사용법 연습.

**목표**: 같은 커맨드도 상황에 따라 다르게 쓰기

---

### 3주차 - MCP 서버

Tavily, Context7 같은 서버 설치하고 연동해보기.  
`/sc:research`가 얼마나 강력해지는지 체감.

**목표**: MCP 붙이기 전/후 차이 직접 경험

---

### 4주차 - 고급 패턴

세션 저장/불러오기, 팀 작업 패턴, 커스텀 워크플로우 만들기.

**목표**: 나만의 개발 흐름 완성

---

> 💡 **요약**: SuperClaude = Claude Code + 전문가 행동 패턴 주입  
> `/sc:brainstorm` 으로 일단 시작.


---


# 🚀 SuperClaude 커맨드 완전 가이드

[[Super_Claude_사용법]]
## 목차

- [[#커맨드 전체 목록]]
- [[#실행 방식으로 구분하기]]
- [[#카테고리별 커맨드]]
    - [[#기획 & 탐색]]
    - [[#설계]]
    - [[#구현]]
    - [[#품질 & 테스트]]
    - [[#개선]]
    - [[#문서화]]
    - [[#전문가 패널]]
    - [[#유틸리티]]
- [[#헷갈리는 커맨드 비교]]
    - [[#spawn vs task vs implement]]
    - [[#design vs workflow]]
    - [[#task vs implement 언제 뭘 써?]]
- [[#실전 워크플로우]]
- [[#MCP 서버 연동 정리]]

---

## 커맨드 전체 목록

|커맨드|한줄 요약|
|---|---|
|`/sc:pm`|백그라운드에서 항상 돌아가는 프로젝트 매니저|
|`/sc:spawn`|큰 작업을 잘게 쪼개는 플래너|
|`/sc:task`|MCP 연동해서 복잡한 작업 실행|
|`/sc:workflow`|PRD로 구현 계획 생성|
|`/sc:brainstorm`|요구사항 대화로 구체화|
|`/sc:research`|웹 검색으로 최신 정보 수집|
|`/sc:implement`|코드 직접 작성|
|`/sc:design`|아키텍처/API/DB 설계|
|`/sc:analyze`|코드 품질/보안/성능 분석|
|`/sc:troubleshoot`|버그 원인 진단|
|`/sc:test`|테스트 실행 및 작성|
|`/sc:build`|프로젝트 빌드|
|`/sc:improve`|리팩토링 & 최적화|
|`/sc:cleanup`|죽은 코드, 미사용 import 제거|
|`/sc:explain`|코드 설명|
|`/sc:document`|문서 자동 생성|
|`/sc:index-repo`|레포 인덱싱 (토큰 절약)|
|`/sc:spec-panel`|전문가 패널 스펙 리뷰|
|`/sc:business-panel`|비즈니스 전문가 패널 분석|
|`/sc:git`|Git 스마트 커밋|
|`/sc:estimate`|개발 시간/복잡도 추정|
|`/sc:reflect`|진행상황 검증|
|`/sc:load`|세션 불러오기|
|`/sc:save`|세션 저장|

---

## 실행 방식으로 구분하기

커맨드는 크게 두 종류로 나뉨. 헷갈리지 않게 먼저 파악하기.

### 📄 문서만 만들고 끝나는 커맨드 (코드 안 건드림)

- `/sc:brainstorm` → 요구사항 문서
- `/sc:workflow` → 구현 계획서
- `/sc:spawn` → 태스크 계층 구조
- `/sc:research` → 리서치 리포트
- `/sc:estimate` → 추정 리포트
- `/sc:design` → 아키텍처 문서
- `/sc:analyze` → 분석 리포트
- `/sc:spec-panel` → 전문가 리뷰 문서
- `/sc:business-panel` → 비즈니스 분석 문서
- `/sc:troubleshoot` → 진단 리포트 (수정하려면 `--fix` 플래그 필요)

### ⚙️ 실제로 실행/수정하는 커맨드

- `/sc:implement` → 코드 작성
- `/sc:improve` → 개선 적용
- `/sc:cleanup` → 코드 제거
- `/sc:task` → 작업 실행
- `/sc:test` → 테스트 실행
- `/sc:build` → 빌드 실행
- `/sc:git` → Git 작업

---

## 카테고리별 커맨드

### 기획 & 탐색

#### [[#/sc:brainstorm]]

#### [[#/sc:research]]

---

#### /sc:brainstorm

> 아이디어가 막연할 때, 소크라테스식 질문으로 요구사항을 구체화해줌

```
/sc:brainstorm [주제]
/sc:brainstorm [주제] --strategy systematic --depth deep
```

**예시**

```
/sc:brainstorm "AI 기반 프로젝트 관리 툴"
/sc:brainstorm "실시간 협업 기능"
/sc:brainstorm "쇼핑몰 추천 시스템 어떻게 설계할까?"
```

**결과물**: 명확한 요구사항 문서 (코드 X)

---

#### /sc:research

> Tavily MCP로 실제 웹 검색해서 최신 정보 가져옴

```
/sc:research "[검색어]"
/sc:research "[검색어]" --depth quick|standard|deep|exhaustive
```

**예시**

```
/sc:research "React 19 새로운 기능"
/sc:research "Next.js vs Remix 2024 비교"
/sc:research "PostgreSQL vs MongoDB 어떤 걸 써야 해?"
/sc:research "경쟁사 AI 코딩 어시스턴트 분석" --depth exhaustive
```

**깊이 선택 기준**

|옵션|소요 시간|언제|
|---|---|---|
|`quick`|~2분|간단한 사실 확인|
|`standard`|~5분|일반 리서치 (기본값)|
|`deep`|~8분|종합 분석|
|`exhaustive`|~10분|학술 수준 리서치|

---

### 설계

#### [[#/sc:design]]

#### [[#/sc:workflow]]

#### [[#/sc:spawn]]

---

#### /sc:design

> 코드는 안 짜고, **어떻게 만들지** 설계만 함 (청사진)

```
/sc:design [대상] --type architecture|api|component|database
/sc:design [대상] --format diagram|spec|code
```

**예시**

```
/sc:design user-management-system --type architecture --format diagram
/sc:design payment-api --type api --format spec
/sc:design e-commerce-db --type database
/sc:design 마이크로서비스 아키텍처로 전환하는 방법
```

**결과물**: 아키텍처 다이어그램, API 스펙, DB 스키마 (코드 X)

---

#### /sc:workflow

> PRD나 기능 설명으로 **어떤 순서로 만들지** 계획서 생성

```
/sc:workflow [기능 설명 또는 PRD 파일]
/sc:workflow [대상] --strategy systematic|agile|enterprise --depth deep
```

**예시**

```
/sc:workflow "결제 시스템" --strategy systematic --depth deep
/sc:workflow docs/PRD/auth-feature.md
```

**결과물**: 단계별 구현 로드맵 (코드 X)

> **design vs workflow 차이**
> 
> - design = 무엇을 어떻게 구조화할지 (청사진)
> - workflow = 어떤 순서로 만들지 (공사 계획)

---

#### /sc:spawn

> 거대한 작업을 Epic → Story → Task 계층으로 쪼개줌

```
/sc:spawn [복잡한 작업] --strategy sequential|parallel|adaptive
```

**예시**

```
/sc:spawn "이커머스 플랫폼 전체 구축" --strategy adaptive --depth deep
/sc:spawn "사용자 인증 시스템 구현"
```

**결과물**: 태스크 계층 구조 문서 (코드 절대 X, 플래너 역할만)

---

### 구현

#### [[#/sc:implement]]

#### [[#/sc:task]]

---

#### /sc:implement

> 딱 코드만 씀. 뭘 만들지 알 때 바로 사용

```
/sc:implement [기능 설명]
/sc:implement [기능] --type component|api|service|feature
/sc:implement [기능] --framework react|vue|express --with-tests
```

**예시**

```
/sc:implement JWT 기반 로그인/로그아웃 기능
/sc:implement user profile component --type component --framework react --with-tests
/sc:implement 결제 처리 시스템 --type feature --with-tests
/sc:implement 상품 목록 무한 스크롤 기능
```

---

#### /sc:task

> 복잡한 작업을 MCP + 전문가 페르소나 조율해서 실행 (테크 리드 역할)

```
/sc:task [작업] --strategy systematic|agile|enterprise
/sc:task [작업] --parallel --delegate
```

**예시**

```
/sc:task create "엔터프라이즈 인증 시스템" --strategy systematic --parallel
/sc:task execute "기능 백로그" --strategy agile --delegate
```

> 내부적으로 architect, security, backend, frontend 페르소나 자동 활성화

---

### 품질 & 테스트

#### [[#/sc:analyze]]

#### [[#/sc:troubleshoot]]

#### [[#/sc:test]]

#### [[#/sc:build]]

---

#### /sc:analyze

> 코드 감사. 품질/보안/성능/아키텍처 분석

```
/sc:analyze [대상] --focus quality|security|performance|architecture
/sc:analyze [대상] --depth quick|deep --format text|json|report
```

**예시**

```
/sc:analyze src/auth --focus security --depth deep
/sc:analyze --focus performance --format report
/sc:analyze src/components --focus quality
```

---

#### /sc:troubleshoot

> 뭔가 망가졌을 때 원인 찾기. 기본적으로 진단만 하고, `--fix` 붙여야 수정함

```
/sc:troubleshoot [문제] --type bug|build|performance|deployment
/sc:troubleshoot [문제] --trace --fix
```

**예시**

```
/sc:troubleshoot "Null pointer exception in user service" --type bug --trace --fix
/sc:troubleshoot "TypeScript 컴파일 에러" --type build --fix
/sc:troubleshoot "API 응답 속도 저하" --type performance
```

---

#### /sc:test

> 테스트 실행 및 작성. E2E는 Playwright MCP 자동 활성화

```
/sc:test
/sc:test [대상] --type unit|integration|e2e|all
/sc:test --coverage --watch --fix
```

**예시**

```
/sc:test
/sc:test src/components --type unit --coverage
/sc:test --type e2e
/sc:test userService.js 유닛 테스트 작성해줘
```

---

#### /sc:build

> 프로젝트 빌드, 번들링, 최적화

```
/sc:build
/sc:build --type dev|prod|test
/sc:build --clean --optimize --verbose
```

**예시**

```
/sc:build --type prod --clean --optimize
/sc:build frontend --verbose
/sc:build Docker 컨테이너화 설정해줘
```

---

### 개선

#### [[#/sc:improve]]

#### [[#/sc:cleanup]]

---

#### /sc:improve

> 작동은 하는데 더 좋게 만들고 싶을 때. 리팩토링 & 최적화

```
/sc:improve [대상] --type quality|performance|maintainability|style
/sc:improve [대상] --safe --interactive
```

**예시**

```
/sc:improve src/ --type quality --safe
/sc:improve api-endpoints --type performance --interactive
/sc:improve auth-service --type security
```

---

#### /sc:cleanup

> 죽은 코드, 미사용 import, 불필요한 파일 제거

```
/sc:cleanup [대상] --type code|imports|files|all
/sc:cleanup --safe|--aggressive --interactive
```

**예시**

```
/sc:cleanup src/ --type code --safe
/sc:cleanup --type imports --preview
/sc:cleanup --type all --interactive
```

---

### 문서화

#### [[#/sc:explain]]

#### [[#/sc:document]]

#### [[#/sc:index-repo]]

---

#### /sc:explain

> 코드가 어떻게 동작하는지 설명해줌

```
/sc:explain [대상] --level basic|intermediate|advanced
/sc:explain [대상] --format text|examples|interactive --context domain
```

**예시**

```
/sc:explain authentication.js --level basic
/sc:explain react-hooks --level intermediate --context react
/sc:explain 마이크로서비스 시스템 --level advanced --format interactive
```

---

#### /sc:document

> README, API 문서, 주석 등 각종 문서 자동 생성

```
/sc:document [대상] --type inline|external|api|guide
/sc:document [대상] --style brief|detailed
```

**예시**

```
/sc:document src/auth/login.js --type inline
/sc:document src/api --type api --style detailed
/sc:document 이 프로젝트 README 작성해줘
/sc:document userController.js API 문서 만들어줘
```

---

#### /sc:index-repo

> 큰 레포를 58KB → 3KB `PROJECT_INDEX.md`로 압축 인덱싱. 토큰 94% 절약

```
/sc:index-repo
/sc:index-repo mode=update   # 기존 인덱스 업데이트
/sc:index-repo mode=quick    # 테스트 제외 빠른 인덱싱
```

새 프로젝트 처음 열 때 한번 실행해두면 좋음.

---

### 전문가 패널

#### [[#/sc:spec-panel]]

#### [[#/sc:business-panel]]

---

#### /sc:spec-panel

> 소프트웨어 엔지니어링 전문가 10명이 스펙/API/요구사항을 리뷰해줌

**전문가 패널**

|전문가|전문 분야|
|---|---|
|Karl Wiegers|요구사항 엔지니어링|
|Martin Fowler|아키텍처 & 설계|
|Michael Nygard|프로덕션 시스템|
|Sam Newman|마이크로서비스|
|Lisa Crispin|애자일 테스팅|
|Kelsey Hightower|클라우드 네이티브|

**운영 모드**

|모드|설명|
|---|---|
|`--mode discussion`|전문가들이 서로 의견 쌓아가며 협업|
|`--mode critique`|심각도/우선순위 붙여서 체계적 리뷰|
|`--mode socratic`|질문으로 깊은 이해 유도 (학습용)|

```
/sc:spec-panel [스펙 또는 @파일] --mode discussion|critique|socratic
/sc:spec-panel [대상] --focus requirements|architecture|testing|compliance
```

**예시**

```
/sc:spec-panel @auth_api.spec.yml --mode critique --focus requirements,architecture
/sc:spec-panel "user story 내용" --mode discussion
/sc:spec-panel @my_spec.yml --mode socratic --iterations 2
```

---

#### /sc:business-panel

> 비즈니스 전략 전문가 9명이 사업 계획/전략/아이디어를 분석해줌

**전문가 패널**

|전문가|프레임워크|
|---|---|
|Clayton Christensen|파괴적 혁신, Jobs-to-be-Done|
|Michael Porter|5가지 경쟁 요소|
|Peter Drucker|목표 관리|
|Seth Godin|부족 마케팅|
|Nassim Taleb|안티프래질|

**운영 모드**

|모드|설명|
|---|---|
|`--mode discussion`|전문가들이 협력해서 아이디어 발전|
|`--mode debate`|논쟁 구도로 아이디어 스트레스 테스트|
|`--mode socratic`|질문 중심의 깊은 이해|

```
/sc:business-panel [내용 또는 @파일]
/sc:business-panel [대상] --mode discussion|debate|socratic
/sc:business-panel [대상] --experts "porter,christensen" --synthesis-only
```

**예시**

```
/sc:business-panel @business_plan.md
/sc:business-panel @strategy.md --mode debate
/sc:business-panel @pitch_deck.md --synthesis-only
```

**어떤 패널 쓸지 기준**

|문서|패널|
|---|---|
|API 스펙, 요구사항, 아키텍처|`/sc:spec-panel`|
|사업 계획, 전략, 피치덱|`/sc:business-panel`|
|PRD|둘 다 (기술은 spec, 전략은 business)|

---

### 유틸리티

#### [[#/sc:git]]

#### [[#/sc:estimate]]

#### [[#/sc:reflect]]

---

#### /sc:git

> Git 작업 + 스마트 커밋 메시지 자동 생성

```
/sc:git status
/sc:git commit --smart-commit
/sc:git merge feature-branch --interactive
```

---

#### /sc:estimate

> 개발 시간/복잡도 추정

```
/sc:estimate [대상] --type time|effort|complexity
/sc:estimate [대상] --unit hours|days|weeks --breakdown
```

**예시**

```
/sc:estimate "사용자 인증 시스템" --type time --unit days --breakdown
# 결과: DB 설계 2일 + 백엔드 API 3일 + 프론트 2일 + 테스트 1일 = 총 8일 (신뢰도 85%)

/sc:estimate "마이크로서비스 마이그레이션" --type complexity --breakdown
```

---

#### /sc:reflect

> 현재 진행상황 점검 및 검증

```
/sc:reflect --type task|session|completion
/sc:reflect --analyze --validate
```

---

## 헷갈리는 커맨드 비교

### spawn vs task vs implement

세 개가 제일 헷갈리니까 역할로 딱 구분하기.

|커맨드|역할 비유|코드 작성?|
|---|---|---|
|`/sc:spawn`|프로젝트 매니저|❌ 절대 안 함 (분해만)|
|`/sc:task`|테크 리드|⚠️ 위임을 통해 가능|
|`/sc:implement`|개발자|✅ 직접 작성|

**spawn** = 큰 걸 잘게 쪼개는 역할만

```
/sc:spawn "이커머스 플랫폼 구축"
→ Epic: 이커머스 플랫폼
  ├── Story: 사용자 인증
  │   ├── Task: DB 스키마
  │   ├── Task: Auth API
  │   └── Task: 로그인 UI
  ├── Story: 상품 카탈로그
  └── Story: 결제
```

**task** = 여러 도메인 걸친 작업 조율

```
/sc:task create "인증 시스템" --parallel
→ architect 페르소나 활성화 → 설계
→ security 페르소나 활성화 → 검토
→ backend 페르소나 활성화 → 코드 작성 (내부적으로 implement 호출)
→ qa 페르소나 활성화 → 테스트
```

**implement** = 그냥 바로 코드 작성

```
/sc:implement 로그인 폼 --type component --framework react
→ LoginForm.tsx 생성
→ LoginForm.test.tsx 생성
→ 끝
```

**어떤 걸 쓸지 기준**

|상황|커맨드|
|---|---|
|작업이 너무 커서 어디서 시작할지 모르겠음|`spawn`|
|백엔드 + 보안 + 프론트 다 필요한 복잡한 기능|`task`|
|컴포넌트 하나, 함수 하나|`implement`|
|이미 설계 끝났고 코드만 작성하면 됨|`implement`|

---

### design vs workflow

||design|workflow|
|---|---|---|
|**질문**|무엇을 어떻게 구조화?|어떤 순서로 만들어?|
|**결과**|아키텍처, 스키마, 스펙|로드맵, 단계별 계획|
|**비유**|집 설계도|공사 일정표|

**연결해서 쓰는 법**

```
1. /sc:brainstorm → 요구사항 정리
2. /sc:design     → 어떻게 만들지 설계
3. /sc:workflow   → 어떤 순서로 만들지 계획
4. /sc:implement  → 실제 코드 작성
```

---

### task vs implement 언제 뭘 써?

**task가 나은 경우**

- 기능이 API + UI + 보안 다 걸쳐 있을 때
- 코딩 전 아키텍처 검토가 필요할 때
- 인증, 결제 같은 크리티컬한 기능일 때

**implement가 나은 경우**

- 컴포넌트 하나, 함수 하나
- 뭘 만들지 이미 명확할 때
- 간단한 CRUD
- 이미 설계/아키텍처 끝냈을 때

**항상 task 쓰면 안 되는 이유**: 버튼 하나 추가하는데 architect, security, qa 페르소나 다 불러오면 토큰 낭비. 간단한 건 그냥 implement.

---

## 실전 워크플로우

### 새 기능 개발할 때

```
1. /sc:brainstorm "기능 아이디어"         → 요구사항 구체화
2. /sc:design 기능 --type architecture    → 설계
3. /sc:workflow 기능                      → 구현 순서 계획
4. /sc:implement 각 단계                  → 코드 작성
5. /sc:test --coverage                   → 테스트
```

### 버그 고칠 때

```
1. /sc:troubleshoot "에러 내용" --trace   → 원인 진단
2. /sc:implement fix                      → 수정
3. /sc:test                              → 검증
```

### 코드 품질 개선할 때

```
1. /sc:analyze 코드 --focus quality      → 문제 파악
2. /sc:improve 코드                      → 개선 적용
3. /sc:cleanup --type imports            → 정리
4. /sc:test                              → 검증
```

### 엔터프라이즈급 기능 (풀 사이클)

```
1. /sc:brainstorm "기능"                 → 요구사항
2. /sc:business-panel @요구사항.md       → 비즈니스 검증
3. /sc:design 기능 --type architecture  → 아키텍처
4. /sc:spec-panel @설계.md              → 기술 검증
5. /sc:workflow 기능 --depth deep       → 상세 계획
6. /sc:spawn "기능" --strategy adaptive → 태스크 분해
7. /sc:task execute task1 --parallel    → 실행
8. /sc:analyze --focus security         → 보안 리뷰
9. /sc:test --type all --coverage       → 전체 테스트
```

### 새 레포 처음 열 때

```
1. /sc:index-repo                        → 프로젝트 인덱싱 (토큰 절약)
2. /sc:brainstorm 또는 /sc:implement     → 작업 시작
```

---

## MCP 서버 연동 정리

어떤 커맨드가 어떤 MCP를 쓰는지 참고용.

|MCP 서버|역할|주로 쓰는 커맨드|
|---|---|---|
|`tavily`|웹 검색|`research`, `pm`|
|`context7`|공식 문서 조회|`implement`, `improve`, `explain`|
|`sequential`|단계적 추론 (토큰 절약)|`task`, `workflow`, `spec-panel`|
|`playwright`|브라우저 자동화|`test`, `build`, `research`|
|`magic`|UI 컴포넌트 생성|`implement`, `task`|
|`serena`|세션 지속성|`pm`, `task`, `reflect`|

> 커맨드 치면 필요한 MCP는 자동으로 연결됨. 따로 신경 쓸 필요 없음.

---

> 💡 **핵심 흐름**: brainstorm → design → workflow → implement → test 막힐 때마다 troubleshoot, 끝나면 document

# Career Application Coach v1

Notion의 `Experience Master`를 경력 사실의 단일 원본으로 사용하여 취업·이직 지원을 돕는 Codex Skill입니다.

채용공고 분석, 경험 매칭, 경력기술서 구성, 자기소개서 전략 수립을 지원합니다. 자기소개서는 사용자의 경험과 핵심 메시지를 먼저 제안하고, 사용자가 방향을 승인한 뒤에만 초안을 작성합니다.

## 주요 기능

- Experience Master 기반 경력 경험 정리
- 채용공고와 JD의 주요 역할·필수 요건·우대 요건 분석
- 지원 직무에 적합한 경험 3~5개 추천
- STAR 기반 경험 구조화와 데이터 품질 관리
- 목표 직무별 경력기술서 경험 선별·재구성
- 자기소개서 문항 분석과 작성 전략 제안
- 사용자 승인 후 자기소개서 초안 작성
- 기업 지원 통합 관리 DB 연동

## 핵심 원칙

### Experience Master가 사실의 기준

Skill은 이전 대화나 기억보다 Notion `Experience Master`의 현재 데이터를 우선합니다. 확인되지 않은 성과, 수치, 역할 또는 권한을 만들어내지 않습니다.

데이터 신뢰도는 다음과 같이 구분합니다.

- `확정`: 외부 제출 문서에서 사용 가능
- `확인 필요`: 사용자의 검증 후 사용
- `추정`: 외부 제출 문서에서는 원칙적으로 사용하지 않음

### 자기소개서 승인 워크플로

자기소개서 문항을 입력해도 바로 완성본을 작성하지 않습니다.

1. 문항 의도와 평가 역량 분석
2. Experience Master에서 후보 경험 최대 3개 추천
3. 추천 경험, 핵심 메시지, 구성 및 JD 연결 전략 제안
4. 사용자 승인 대기
5. 승인된 경험과 메시지로만 초안 작성

`좋아`, `그걸로 가자`, `2번 경험으로 써줘`처럼 제안한 방향을 명확히 선택한 표현만 승인으로 처리합니다.

## 지원 워크플로

| 워크플로 | 용도 |
| --- | --- |
| Experience Builder | 경험 인터뷰, STAR 정리, Experience Master 업데이트 |
| JD Matcher | 채용공고 분석, 직무 비교, 경험 추천 |
| Cover Letter Planner | 자기소개서 문항 분석과 작성 전략 제안 |
| Cover Letter Writer | 승인된 전략을 기반으로 자기소개서 작성 |
| Career Resume | 목표 직무별 경력기술서 경험 선별 및 재구성 |

## 폴더 구조

```text
career-application-coach/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── notion-data.md
    ├── resume-workshop.md
    └── workflows.md
```

- `SKILL.md`: Skill의 핵심 행동과 승인 규칙
- `agents/openai.yaml`: 표시 이름, 기본 프롬프트, Notion 의존성
- `references/notion-data.md`: Notion 데이터 원본과 필드 규칙
- `references/resume-workshop.md`: 성과·역할·기술 중심 경력기술서 작성 기준
- `references/workflows.md`: 작업별 상세 절차와 출력 형식

## 요구 사항

- Codex의 Skill 기능을 사용할 수 있는 환경
- 연결된 Notion 워크스페이스
- 아래 구조를 가진 Experience Master 데이터베이스
  - 경험명, 회사/브랜드, 기간
  - Situation, Task, Action, Result
  - KPI·정량성과, 기여도
  - 업무 영역, 핵심 역량 태그, 지원 직무 연결
  - 데이터 신뢰도, 정리 상태, 대표 경험

## 설치

Codex에서 다음과 같이 요청할 수 있습니다.

```text
$skill-installer를 사용해서
https://github.com/YunjeeJung/skill-career-application-coach
의 Skill을 설치해줘.
```

수동으로 설치하려면 저장소를 내려받은 뒤 전체 폴더를 Codex의 사용자 Skill 디렉터리에 배치합니다.

```bash
git clone https://github.com/YunjeeJung/skill-career-application-coach.git
```

설치 후 새 작업에서 `$career-application-coach`로 명시적으로 호출할 수 있습니다. 취업·이직 지원 관련 요청에서는 자동으로 선택될 수도 있습니다.

## Notion 연결 설정

이 저장소의 `references/notion-data.md`에는 제작자의 Notion 데이터 구조와 data source 연결 정보가 들어 있습니다.

다른 워크스페이스에서 사용할 경우 다음 값을 본인의 Notion 환경에 맞게 변경해야 합니다.

- Experience Master data source URL
- 기업 지원 통합 관리 data source URL
- 요구사항 원본 페이지 URL
- 실제 데이터베이스의 속성 이름과 선택 옵션

Notion 연결이 없거나 원본 DB를 찾을 수 없는 경우 Skill은 새로운 DB를 임의로 만들지 않고, 사용자가 제공한 자료만으로 제한적으로 동작합니다.

## 사용 예시

### JD 분석

```text
$career-application-coach
이 채용공고를 분석하고 Experience Master에서 가장 적합한 경험을 추천해줘.
```

### 경험 정리

```text
$career-application-coach
24SS 상품기획 경험을 STAR로 정리하고 부족한 정보만 질문해줘.
```

### 자기소개서

```text
$career-application-coach
이 문항의 의도를 분석하고 사용할 경험과 작성 전략을 먼저 제안해줘.
내가 승인하기 전에는 완성본을 작성하지 마.
```

## 보안 및 개인정보

- Notion data source ID는 비밀번호가 아니지만 개인 워크스페이스 구조를 식별할 수 있으므로 공개 여부를 확인하세요.
- GitHub 개인 액세스 토큰, API 키, 비밀번호는 저장소에 커밋하지 마세요.
- 공개 저장소로 배포할 때는 개인 이름, 이메일, 회사 내부 정보 및 비공개 경력 데이터가 포함되지 않았는지 확인하세요.

## 라이선스

현재 별도의 라이선스 파일이 포함되어 있지 않습니다. 다른 사람의 복제·수정·재배포를 허용하려면 MIT 등의 라이선스를 추가하세요.

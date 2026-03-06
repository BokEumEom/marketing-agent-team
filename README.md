# AI 마케팅팀 에이전트

Claude Code로 만든 AI 마케팅팀. 마크다운 파일 15개가 전부다.

CMO가 전략을 짜고, Content Writer가 글을 쓰고, Social Media Marketer가 배포하고, Newsletter Manager가 뉴스레터를 보낸다. 코드는 없다.

## 에이전트 팀

| 에이전트 | 모델 | 역할 |
|---------|------|------|
| CMO | Claude Opus 4.6 | 전략 총괄, 팀 지휘, 성과 분석 |
| Content Writer | Claude Sonnet 4.6 | X 스레드, LinkedIn, 뉴스레터 원고 작성 |
| Social Media Marketer | Claude Sonnet 4.6 | X, LinkedIn, Threads 배포 |
| Newsletter Manager | Claude Sonnet 4.6 | Maily 뉴스레터 구성 및 발송 |

## 채널

- **X/Twitter** — 한국어 스레드, 단문 포스트
- **LinkedIn** — 한국어 아티클, 전문가 포스트
- **Threads** — 캐주얼 포스트
- **Maily** — 격주 뉴스레터 (Paul Graham 스타일)

## 시작하기

### 요구사항

- [Claude Code](https://claude.ai/code) 설치
- Claude Code 에이전트 팀 기능 (실험적 기능)

### 설치

```bash
git clone https://github.com/your-repo/marketing-team-agent
cd marketing-team-agent
```

### 사용법

Claude Code에서 이 프로젝트를 열고 CMO에게 지시한다.

```
이번 주 마케팅 실행해줘
```

또는 특정 작업만:

```
X 스레드 원고 작성해줘. 주제는 "..."
Maily 뉴스레터 작성해줘
LinkedIn 글 작성해줘
```

## 폴더 구조

```
marketing_team_agent/
├── CLAUDE.md                    ← 팀 차터 (모든 에이전트가 읽음)
├── .claude/
│   ├── agents/                  ← 에이전트 정의
│   │   ├── cmo.md
│   │   ├── content-writer.md
│   │   ├── social-media-marketer.md
│   │   └── newsletter-manager.md
│   └── rules/                   ← 공유 규칙
│       ├── brand-voice.md       ← 채널별 톤앤매너
│       ├── utm-parameters.md    ← UTM 링크 규칙
│       └── social-media-tracker.md
├── docs/
│   ├── brand/
│   │   ├── positioning.md       ← 제품 포지셔닝
│   │   └── voice-style.md       ← 보이스 가이드
│   ├── strategy/
│   │   ├── gtm-strategy.md      ← 90일 GTM 전략
│   │   ├── content-calendar.md  ← 콘텐츠 캘린더
│   │   └── weekly-plan.md       ← 주간 실행 계획 ← 여기를 수정
│   └── insights/
│       └── marketing-insights.md ← 성과 인사이트 (CMO가 자동 업데이트)
├── outputs/                     ← 에이전트가 작성한 원고
│   ├── x/
│   ├── linkedin/
│   ├── threads/
│   └── maily/
└── tracker/
    └── social-media-tracker.csv ← 게시 활동 로그
```

## 워크플로우

```
CMO
 ├── weekly-plan.md 확인
 ├── Content Writer → 원고 작성 → outputs/{채널}/ 저장
 ├── Social Media Marketer → 형식 검증 → 검토 요청
 └── Newsletter Manager → Maily 편집 → 발송 요청

사용자 → outputs/ 파일 확인 → "게시해줘"
```

콘텐츠는 항상 `outputs/` 폴더에 파일로 저장된다. 게시 전 직접 확인하고 승인한다.

## 커스터마이징

### 다른 제품/서비스에 적용하기

1. `docs/brand/positioning.md` — 내 제품 포지셔닝으로 교체
2. `docs/brand/voice-style.md` — 브랜드 톤앤매너 수정
3. `docs/strategy/weekly-plan.md` — 이번 주 할 일 업데이트
4. `CLAUDE.md` — 팀 구조나 채널 수정

### 에이전트 추가

`.claude/agents/` 폴더에 `.md` 파일을 추가하면 된다.

```markdown
---
name: agent-name
description: "언제 이 에이전트를 쓸지 설명"
model: claude-sonnet-4-6
color: green
---

에이전트 역할과 지시사항...
```

### 채널 추가/제거

`CLAUDE.md`의 채널 목록과 해당 에이전트 파일의 규칙을 수정한다.

## MCP 서버

현재 연결된 MCP:

| MCP | 용도 |
|-----|------|
| Slack | 팀 알림 (#team-marketing) |
| Firecrawl | 웹 리서치, 트렌드 조사 |

## 비용

Claude API 사용량 기준. 주간 실행 횟수와 콘텐츠 양에 따라 다름.
CMO(Opus)는 전략/분석에, 나머지(Sonnet)는 실행에 사용해 비용을 최적화했다.

## 라이선스

MIT

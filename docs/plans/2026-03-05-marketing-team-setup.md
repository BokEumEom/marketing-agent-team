# AI 마케팅팀 구축 Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Claude Code 에이전트 팀(CMO + Content Writer + Social Media Marketer + Newsletter Manager)으로 X/Twitter, LinkedIn, Threads, Maily 채널을 한국어로 운영하는 AI 마케팅팀을 구축한다.

**Architecture:** `.claude/agents/*.md` 파일로 4개 에이전트를 정의하고, CLAUDE.md + rules/ + docs/ 폴더의 공유 문서로 팀 컨텍스트를 관리한다. 수동 트리거 방식으로 CMO에게 지시하면 전문 에이전트에게 위임하는 구조.

**Tech Stack:** Claude Code Agent Teams, MCP (Slack, Firecrawl), Maily API

---

## 현재 상태 (2026-03-05 기준)

완료된 작업:
- [x] 프로젝트 폴더 구조 생성
- [x] CLAUDE.md (팀 차터)
- [x] .claude/rules/ (brand-voice, utm-parameters, social-media-tracker)
- [x] docs/brand/ (positioning, voice-style)
- [x] docs/strategy/ (gtm-strategy, content-calendar, weekly-plan)
- [x] docs/insights/marketing-insights.md
- [x] .claude/agents/ (cmo, content-writer, social-media-marketer, newsletter-manager)
- [x] tracker/social-media-tracker.csv

---

## 남은 작업

### Task 1: 소셜미디어 MCP 연동 확인

**목표:** X, LinkedIn, Threads 게시를 위한 MCP 서버 또는 API 설정

**파일:**
- 확인: `~/.claude/settings.json` — MCP 서버 설정
- 수정: `.claude/agents/social-media-marketer.md` — 사용 가능한 도구 업데이트

**단계:**

1. MCP 서버 목록 확인
```bash
# ~/.claude/settings.json에서 MCP 설정 확인
cat ~/.claude/settings.json | grep -A 5 "mcpServers"
```

2. X/Twitter MCP가 없으면 social-media-marketer.md에 "승인 대기" 워크플로우 유지
3. 사용 가능한 MCP 서버 목록을 social-media-marketer.md에 반영

---

### Task 2: Maily API 연동

**목표:** Newsletter Manager가 Maily로 뉴스레터를 발송할 수 있도록 설정

**파일:**
- 수정: `.claude/agents/newsletter-manager.md` — Maily API 도구 추가

**단계:**

1. Maily API 키 환경변수 설정
```bash
export MAILY_API_KEY="your-key-here"
```

2. 뉴스레터 발송 스크립트 작성 (필요 시)
```
scripts/maily-send.js
```

3. newsletter-manager.md에 Maily 발송 단계 업데이트

---

### Task 3: Slack 알림 채널 설정

**목표:** 에이전트 활동을 #team-marketing Slack 채널로 알림

**파일:**
- 확인: Slack MCP 설정 (`mcp__claude_ai_Slack__*` 도구)
- 수정: `CLAUDE.md` — Slack 채널 ID 추가

**단계:**

1. Slack MCP로 채널 확인
```
mcp__claude_ai_Slack__slack_search_channels: "team-marketing"
```

2. 채널 ID를 CLAUDE.md에 기록
3. 각 에이전트의 Slack 알림 코드 검증

---

### Task 4: 첫 번째 콘텐츠 작성 테스트

**목표:** 전체 파이프라인 동작 검증 — CMO → Content Writer → Social Media Marketer

**단계:**

1. CMO에게 지시:
```
"이번 주 첫 번째 콘텐츠 작성해줘: X 스레드 원고"
```

2. Content Writer가 X 스레드 원고 반환 확인
3. Social Media Marketer가 형식 검증 및 UTM 링크 생성 확인
4. tracker/social-media-tracker.csv에 draft 기록 확인

---

### Task 5: 주간 계획 실행 테스트

**목표:** "이번 주 마케팅 실행해줘" 명령으로 전체 팀 가동 테스트

**단계:**

1. CMO에게:
```
이번 주 마케팅 실행해줘
```

2. CMO가 weekly-plan.md 읽고 미완료 작업 파악하는지 확인
3. 각 전문 에이전트에게 올바르게 위임하는지 확인
4. 결과 보고 형식이 올바른지 확인
5. insights 파일이 업데이트되는지 확인

---

## 향후 개선 사항 (백로그)

- [ ] X/Twitter MCP 또는 API 연동 (현재 미지원)
- [ ] LinkedIn API 연동
- [ ] Threads API 연동
- [ ] 자동화 레벨 업그레이드: 수동 → 반자율 (cron 설정)
- [ ] 성과 데이터 자동 수집 스크립트
- [ ] A/B 테스트 프레임워크 추가

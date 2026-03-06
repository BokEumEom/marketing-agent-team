# 마크다운 파일 15개로 마케팅팀 만드는 방법

**채널:** X/Twitter (스레드)
**날짜:** 2026-03-05
**캠페인:** 2026-03-launch
**상태:** draft

---

**트윗 1 (후킹)**
마케팅팀을 채용하는 대신 마크다운 파일 15개를 썼다.

결과: CMO, 콘텐츠 라이터, 소셜 마케터, 뉴스레터 매니저가 생겼다.
비용은 하루 3만원.

어떻게 만들었는지 공유한다 🧵

---

**트윗 2**
Claude Code에는 .claude/agents/ 폴더에 .md 파일을 넣으면 에이전트가 된다.

파일 구조:
```
name: cmo
description: "총괄 CMO. 팀 지휘, 성과 분석..."
model: claude-opus-4-6
```

이게 전부다. 코드 한 줄 없다.

---

**트윗 3**
에이전트가 일관되게 행동하려면 공유 컨텍스트가 필요하다.

나는 이렇게 나눴다:
- CLAUDE.md → 팀 차터 (모든 에이전트가 읽음)
- docs/brand/ → 포지셔닝, 톤앤매너
- docs/strategy/ → 주간 계획, 콘텐츠 캘린더
- docs/insights/ → 누적 성과 인사이트

에이전트가 바뀌어도 컨텍스트는 파일에 남는다.

---

**트윗 4**
실행은 이렇게 한다:

"이번 주 마케팅 실행해줘"

→ CMO가 weekly-plan.md 읽고 할 일 파악
→ Content Writer에게 원고 작성 위임
→ outputs/x/ 폴더에 파일 저장
→ "확인해주세요" 알림
→ 내가 파일 열어서 검토 후 "게시해줘"

승인 없이는 아무것도 나가지 않는다.

---

**트윗 5**
파일 목록:

CLAUDE.md, 에이전트 4개, 규칙 3개, 브랜드 문서 2개, 전략 문서 3개, 인사이트 1개, 트래커 1개

= 15개

소셜미디어 API 없어도 원고 생성까지는 지금 바로 쓸 수 있다.
레포 링크 → (링크)

#ClaudeCode #AI자동화 #마케팅자동화

---

**UTM:** `https://github.com/your-repo?utm_source=x&utm_medium=social&utm_campaign=2026-03-launch&utm_content=thread-markdown-15`

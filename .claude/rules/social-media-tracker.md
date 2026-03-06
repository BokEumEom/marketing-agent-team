# 소셜미디어 트래커 규칙

## 파일 위치

`tracker/social-media-tracker.csv`

## CSV 컬럼 구조

```
date,platform,content_type,title,url,utm_campaign,status,notes
```

| 컬럼 | 설명 | 값 예시 |
|------|------|--------|
| date | 게시일 (ISO 8601) | `2026-03-05` |
| platform | 채널 | `x`, `linkedin`, `threads`, `maily` |
| content_type | 콘텐츠 유형 | `post`, `thread`, `article`, `newsletter` |
| title | 포스트 제목 또는 첫 줄 요약 | `AI로 마케팅팀 만든 방법` |
| url | 게시물 URL (게시 후 입력) | `https://x.com/...` |
| utm_campaign | 해당 캠페인명 | `2026-03-launch` |
| status | 상태 | `draft`, `scheduled`, `published` |
| notes | 특이사항, 성과 메모 | `좋아요 120, 리트윗 30` |

## 로깅 규칙

1. **초안 작성 시**: `status=draft`로 먼저 기록한다
2. **게시 직후**: `status=published`, `url` 입력
3. **성과 확인 후**: `notes`에 핵심 지표 추가
4. **중복 금지**: 같은 날 같은 플랫폼에 동일 콘텐츠 기록 금지

## 유효한 status 값

- `draft` — 작성 완료, 미게시
- `scheduled` — 예약 게시 설정됨
- `published` — 게시 완료

## 예시 행

```csv
2026-03-05,x,thread,Claude Code로 AI 마케팅팀 만든 방법,https://x.com/user/status/123,2026-03-launch,published,좋아요 45 리트윗 12
2026-03-05,linkedin,article,AI가 내 마케팅을 대신한다면,https://linkedin.com/posts/123,2026-03-launch,published,조회수 320 반응 28
2026-03-06,maily,newsletter,이번 주 AI 마케팅 인사이트,,2026-03-weekly,draft,
```

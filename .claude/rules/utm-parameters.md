# UTM 파라미터 규칙

## 형식

모든 외부 링크에 UTM을 붙인다.

```
https://example.com?utm_source={source}&utm_medium={medium}&utm_campaign={campaign}&utm_content={content}
```

## 값 규칙

- **소문자만 사용**
- **단어 구분: 하이픈(-)** (언더스코어 X)
- 공백 없음

## utm_source (플랫폼)

| 채널 | 값 |
|------|-----|
| X/Twitter | `x` |
| LinkedIn | `linkedin` |
| Threads | `threads` |
| Maily 뉴스레터 | `maily` |

## utm_medium (매체 유형)

| 유형 | 값 |
|------|-----|
| 소셜미디어 포스트 | `social` |
| 뉴스레터 | `email` |
| 유료 광고 | `paid` |

## utm_campaign (캠페인명)

현재 캠페인 이름을 사용한다. 형식: `YYYY-MM-{캠페인명}`

예시:
- `2026-03-launch` — 런칭 캠페인
- `2026-03-ai-marketing` — AI 마케팅 시리즈
- `2026-03-weekly` — 주간 뉴스레터

## utm_content (콘텐츠 구분)

같은 캠페인 내 다른 콘텐츠를 구분할 때 사용.

예시:
- `blog-post-1`
- `tweet-thread`
- `linkedin-article`

## 예시

```
# X에서 런칭 블로그 포스트 링크
https://github.com/user/repo?utm_source=x&utm_medium=social&utm_campaign=2026-03-launch&utm_content=blog-post-1

# Maily 뉴스레터에서 같은 링크
https://github.com/user/repo?utm_source=maily&utm_medium=email&utm_campaign=2026-03-launch&utm_content=newsletter-1
```

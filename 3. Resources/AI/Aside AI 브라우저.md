---
type: resource
status: active
category: "AI"
source: "웹 검색 (eesel.ai, PiunikaWeb, tabbit 리뷰 등)"
author: "Aside (YC F25)"
url: "https://aside.com"
tags: [resource/ai]
---

# Aside AI 브라우저

> 2026-10-12 기준으로 조사함. 아직 초기 제품이라 변경이 잦을 수 있음.

## 요약 (핵심 3줄)
1. Aside는 AI 에이전트가 내장된 **Chromium 기반 데스크톱 브라우저**다. 크롬 확장이 아니라 독립 앱이다.
2. 별도 연동 없이 **이미 로그인된 사이트를 AI가 직접 조작**해서 여러 단계의 작업을 처리한다.
3. 벤치마크 수치는 **회사 자체 발표**이고 사용자 평가는 반반으로 갈린다. 아직 초기 단계다.

> [!tip] 비유
> 브라우저 안에 비서가 한 명 사는 셈이다. 일반 AI 도구가 서비스마다 연동을 따로 맺어야 한다면, 이 비서는 내 컴퓨터에서 내 계정으로 사이트를 직접 열고 클릭하며 일한다.

## 주요 내용

### 핵심 기능
| 기능 | 설명 |
| --- | --- |
| 브라우저 에이전트 | 이메일, 대시보드, 사내 도구 등 로그인된 사이트를 AI가 직접 조작한다 (예: 송장을 내려받아 이름 바꾸기, 대시보드 수치 수집) |
| 비밀번호 관리자 | 자동 완성으로 로그인하므로 AI 모델은 실제 비밀번호를 보지 못한다 |
| 메모리 | 브라우징 기록을 기기 안에 마크다운 메모리로 저장하고, 사용자가 직접 수정할 수 있다 |
| 사람 승인 | 결제, 게시, 메시지 전송 같은 민감한 작업은 사용자가 승인해야 실행된다 (회사 주장) |
| 개인정보 | 작업 기록은 로컬에 저장되고, 외부 모델에는 작업에 필요한 맥락만 보낸다고 밝힘 |

### 회사와 현황
- Y Combinator 2025년 가을(F25) 배치에 참여한 샌프란시스코 스타트업이다.
- 공개 베타 단계이며 Agent/Skills 기능을 계속 출시하고 있다.
- 주로 Mac에서 쓰여 왔다. 2026년 7월 말 보도에서 8월 Windows 관련 발표를 예고했지만, 실제 출시 여부는 확인하지 못했다.
- 가격은 한 디렉터리에 Pro 플랜 월 $99로 나와 있으나 공식 사이트에서는 확인하지 못했다.

### 주의할 점
- **벤치마크는 자체 발표 수치다.** Online-Mind2Web에서 300개 중 297개(99%) 성공이라고 하지만, 회사가 직접 채점했고 독립 검증은 거치지 않았다.
- **사용자 평가가 갈린다.** Reddit에서 속도와 UI는 칭찬받지만 크래시, 자동 로그아웃, 큰 설치 용량에 대한 불만도 많다.
- AI에게 계정 접근 권한을 주는 구조라서, 중요한 계정에 쓰기 전에는 신중하게 판단해야 한다.

## 활용 방안
- [ ] Windows 버전이 출시됐는지 확인하기
- [ ] 반복 웹 작업(대시보드 수치 수집 등)에 쓸 수 있는지, 중요도가 낮은 계정으로 먼저 시험해 보기

## 출처
- [Aside: the AI browser that does your work, explained (eesel.ai)](https://eesel.ai/blog/aside-ai-browser)
- [Aside AI browser review (eesel.ai)](https://www.eesel.ai/blog/aside-ai-browser-review)
- [Aside AI-Browser im Test (eesel.ai)](https://www.eesel.ai/de/blog/aside-ai-browser-test)
- [Aside browser Windows launch August (PiunikaWeb)](https://piunikaweb.com/2026/07/30/aside-browser-windows-launch-august/)
- [Aside review roundup (tabbit.ai)](https://go.tabbit.ai/aside-browser-review)
- [Aside AI Browser 2026 Guide (tabbit.com)](https://go.tabbit.com/aside-ai-browser)
- [Aside on SourceForge](https://sourceforge.net/software/product/Aside/)
- [Aside (YC) on altss](https://altss.com/companies/yc/aside)
- [Aside on G2](https://www.g2.com/sellers/aside)

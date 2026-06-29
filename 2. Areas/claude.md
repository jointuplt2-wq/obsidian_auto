# 2. Areas

## 목적과 역할
마감이 없고 **지속적으로 일정 수준을 유지·관리**해야 하는 책임 영역입니다.
프로젝트와 달리 "완료"가 없고, 기준선을 지키는 것이 목표입니다.

## 어떤 노트가 들어가는가
- 장기적 책임 영역 (예: "건강", "재무", "직무 역량", "블로그 운영")
- 각 영역의 현황 노트, 체크리스트, 루틴, 기준(SOP)
- 영역에 연관된 프로젝트들을 모아 보는 허브 역할도 가능

## 작업 방식과 규칙
- frontmatter:
  ```yaml
  type: area
  status: active | archived
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  ```
- "끝나는 일"이 보이면 그건 Area가 아니라 `1. Projects/`의 프로젝트다.
- 더 이상 관리하지 않게 되면 `status: archived`로 바꾸고 `4. Archive/`로 이동.
- 지식 자체는 여기 쌓지 말고 `5. Zettelkasten/`을 참조한다.

# 1. Projects

## 목적과 역할
**마감일과 명확한 목표**가 있는 능동적 작업을 관리하는 PARA의 "작업대"입니다.
끝이 정해진 노력 — 완료되면 결과물이 남고, 끝나면 `4. Archive/`로 이동합니다.

## 어떤 노트가 들어가는가
- 구체적 산출물이 있는 프로젝트 (예: "포트폴리오 사이트 제작", "OO 논문 투고")
- 각 프로젝트는 보통 하나의 허브 노트(`00_프로젝트명_Hub.md`)를 가짐
- 프로젝트 진행에 필요한 실행 메모, 태스크, 회의록

## 작업 방식과 규칙
- **참조 우선**: 지식은 여기서 새로 쓰지 말 것. `5. Zettelkasten/`의 노트를 `[[링크]]`/`![[임베드]]`로 끌어와 조립한다.
- 모든 프로젝트 노트 frontmatter:
  ```yaml
  type: project
  status: todo | in-progress | completed
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  due: YYYY-MM-DD   # 있으면 명시
  ```
- 마감일(`due`)이 있는 것만 여기 둔다. 마감 없는 지속 책임은 `2. Areas/`로.
- 완료/중단 시 `status`를 갱신하고 `4. Archive/`로 이동한다.

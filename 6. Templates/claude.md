# 6. Templates

## 목적과 역할
노트 품질과 일관성을 위한 **템플릿 보관소**. Templater/Templates 플러그인이 참조합니다.

## 어떤 노트가 들어가는가
- 노트 타입별 템플릿 (project, area, resource, literature, permanent, docs, archive 등)
- 각 템플릿은 해당 폴더의 `claude.md` 규칙(특히 frontmatter)을 충족해야 함

## 작업 방식과 규칙
- 템플릿은 표준 frontmatter 스켈레톤 + 권장 섹션 구조를 포함한다.
- 동적 값은 Templater 문법 사용: `<% tp.date.now("YYYY-MM-DD") %>`, `<% tp.file.title %>`.
- 폴더 규칙(예: Permanent의 2+ 연결, Literature의 source/author)이 바뀌면 해당 템플릿도 함께 갱신한다.
- 이 폴더 자체는 산출물이 아니므로 Dataview 집계에서 보통 제외한다.

---
type: hub
tags: [hub]
---
# 🚀 Projects Hub

> 이 폴더 운영 규칙: [[운영-가이드]]

## 🔥 진행 중 (in-progress)
```dataview
TABLE status AS "상태", due AS "마감", file.mtime AS "수정"
FROM "1. Projects"
WHERE type = "project" AND status = "in-progress"
SORT due ASC
```

## 📋 대기 (todo)
```dataview
TABLE due AS "마감", file.mtime AS "수정"
FROM "1. Projects"
WHERE type = "project" AND status = "todo"
SORT due ASC
```

## ⏰ 마감 임박 (30일 이내)
```dataview
TABLE due AS "마감", status AS "상태"
FROM "1. Projects"
WHERE type = "project" AND due AND due <= date(today) + dur(30 days) AND status != "completed"
SORT due ASC
```

## ⏸️ 보류 (on-hold)
```dataview
LIST
FROM "1. Projects"
WHERE type = "project" AND status = "on-hold"
```

## ✅ 완료 → Archive 이동 대기
```dataview
LIST
FROM "1. Projects"
WHERE type = "project" AND status = "completed"
```

## 🧹 정리 체크리스트
- [ ] 완료 프로젝트 `4. Archive/`로 이동(Move)
- [ ] 마감(`due`) 없는 프로젝트 → `2. Areas/` 이동 검토
- [ ] 고아 프로젝트(DoD/로그/참조 미비) 정리
- [ ] 태그 감사: 허용 집합 이탈·중복·모호 태그 정리

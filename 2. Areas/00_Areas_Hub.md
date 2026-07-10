---
type: hub
tags: [hub]
---
# 🗂️ Areas Hub

> 이 폴더 운영 규칙: [[운영-가이드]]

## ✅ 활성 영역 (active)
```dataview
TABLE status AS "상태", file.mtime AS "수정"
FROM "2. Areas"
WHERE type = "area" AND status = "active"
SORT file.name ASC
```

## ⏸️ 비활성 (inactive)
```dataview
LIST
FROM "2. Areas"
WHERE type = "area" AND status = "inactive"
```

## 🔗 연결된 프로젝트 (area별)
```dataview
TABLE rows.file.link AS "프로젝트"
FROM "1. Projects"
WHERE type = "project" AND area
GROUP BY area
```

## 🧹 정리 체크리스트
- [ ] active 영역 월 1회 리뷰 로그 업데이트
- [ ] archived 영역 `4. Archive/`로 이동(Move)
- [ ] Area ↔ Projects 연결 상태 확인
- [ ] 태그 감사: 허용 집합 이탈·중복·모호 태그 정리

---
type: hub
tags: [hub]
---
# 📚 Resources Hub

> 이 폴더 운영 규칙: [[운영-가이드]]

## 📂 주제별 자료 (category)
```dataview
TABLE rows.file.link AS "자료", rows.status AS "상태"
FROM "3. Resources"
WHERE type = "resource"
GROUP BY category
```

## ✅ 활성 (active)
```dataview
TABLE category AS "주제", file.mtime AS "수정"
FROM "3. Resources"
WHERE type = "resource" AND status = "active"
SORT file.mtime DESC
```

## 🕒 3개월 이상 미사용 (정리 후보)
```dataview
TABLE category AS "주제", file.mtime AS "최근 수정"
FROM "3. Resources"
WHERE type = "resource" AND status = "active" AND file.mtime < date(today) - dur(90 days)
SORT file.mtime ASC
```

## 🧹 정리 체크리스트
- [ ] 3개월 이상 미사용 자료 → `4. Archive/` 이동 검토
- [ ] 깊은 학습 필요 자료 → `5. Zettelkasten/10. Literature/`로 승격
- [ ] 주제별 하위 폴더 구조 유지
- [ ] 태그 감사: 허용 집합 이탈·중복·모호 태그 정리

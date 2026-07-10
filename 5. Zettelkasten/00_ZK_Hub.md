---
type: hub
tags: [hub]
---
# 💡 Zettelkasten Hub

> 이 폴더 운영 규칙: [[운영-가이드]]
> 흐름: 00. Inbox → 10. Literature → 20. Permanent

## 📥 Inbox (승격 대기)
```dataview
TABLE file.ctime AS "생성일"
FROM "5. Zettelkasten/00. Inbox"
WHERE file.name != "claude"
SORT file.ctime ASC
```

## ⏳ Inbox 정리 대상 (7일 이상)
```dataview
TABLE file.ctime AS "생성일"
FROM "5. Zettelkasten/00. Inbox"
WHERE file.name != "claude" AND file.ctime < date(today) - dur(7 days)
SORT file.ctime ASC
```

## 📖 Literature
```dataview
TABLE file.mtime AS "수정"
FROM "5. Zettelkasten/10. Literature"
WHERE type = "literature"
SORT file.mtime DESC
```

## 💡 Permanent (연결 수)
```dataview
TABLE length(related) AS "연결 수"
FROM "5. Zettelkasten/20. Permanent"
WHERE type = "permanent"
SORT length(related) DESC
```

## 🕸️ 고아 Permanent (연결 2개 미만)
```dataview
LIST
FROM "5. Zettelkasten/20. Permanent"
WHERE type = "permanent" AND length(related) < 2
```

## 🧹 정리 체크리스트
- [ ] 주 1회 Inbox 비우기 (Literature/Permanent 승격)
- [ ] 7일 이상 메모 승격 또는 삭제
- [ ] Permanent 최소 2개 연결 확보 (고아 방지)
- [ ] 연결 강화 (새로운 관계 발견)

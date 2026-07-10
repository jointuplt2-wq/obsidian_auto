---
status: active
created: 2026-07-01
updated: 2026-07-01
tags: [dashboard, hub]
cssclasses: [dashboard]
---

# 🏠 Vault 대시보드

> [!info] 사용법
> 이 노트는 **Dataview** 플러그인으로 자동 갱신됩니다. 파일을 추가/수정하면 아래 표가 자동으로 바뀝니다.
> 표가 코드 그대로 보이면 → 노트 우상단 메뉴에서 **읽기 모드(Reading view)** 로 전환하세요.
> 아래 "한눈에 보기"가 안 보이면 → 설정 → Dataview → **Enable JavaScript Queries** 를 켜세요.

---

## 📊 한눈에 보기

```dataviewjs
const types = ["project", "area", "resource", "literature", "permanent", "daily"];
const labels = {project:"🚀 Projects", area:"🗂️ Areas", resource:"📚 Resources", literature:"📖 Literature", permanent:"💡 Permanent", daily:"📅 Daily"};
const rows = types.map(t => {
  // daily 노트는 type 필드 없이 tags: [daily]로 식별 → 태그 기반 집계 (템플릿 제외)
  const n = t === "daily"
    ? dv.pages().where(p => p.file.tags.includes("#daily") && !p.file.path.includes("6. Templates")).length
    : dv.pages().where(p => p.type === t).length;
  return [labels[t], n];
});
// 고아 노트(연결 0개) 카운트 — 시스템 파일 제외
const orphans = dv.pages()
  .where(p => !p.file.path.toLowerCase().includes("claude")
           && !p.file.path.includes("6. Templates")
           && p.file.name !== "00 Dashboard"
           && p.file.name !== "환영합니다!"
           && p.file.inlinks.length === 0
           && p.file.outlinks.length === 0).length;
rows.push(["🕸️ 고아 노트", orphans]);
dv.table(["구분", "개수"], rows);
```

---

## 🚀 진행 중인 프로젝트

```dataview
TABLE status AS "상태", due AS "마감", updated AS "수정일"
FROM "1. Projects"
WHERE type = "project" AND status != "completed" AND status != "archived"
SORT due ASC
```

## ⏰ 마감 임박 (30일 이내)

```dataview
TABLE due AS "마감", status AS "상태"
FROM "1. Projects"
WHERE type = "project" AND due AND due <= date(today) + dur(30 days) AND status != "completed"
SORT due ASC
```

---

## 🗂️ 관리 중인 영역 (Areas)

```dataview
TABLE status AS "상태", updated AS "수정일"
FROM "2. Areas"
WHERE type = "area" AND status = "active"
SORT updated DESC
```

---

## 📥 Inbox — 정리 대기 (주 1회 비우기)

```dataview
LIST
FROM "5. Zettelkasten/00. Inbox"
WHERE file.name != "claude"
SORT file.mtime DESC
```

---

## 📖 Literature 노트 (원천 자료)

```dataview
TABLE author AS "저자", source AS "출처", created AS "작성일"
FROM "5. Zettelkasten/10. Literature"
WHERE type = "literature"
SORT created DESC
```

---

## 💡 Permanent 노트 — 연결 수 순

> 연결이 적은 노트를 위로 올려, "최소 2개 연결" 원칙을 점검합니다.

```dataview
TABLE length(related) AS "연결 수", tags AS "태그", updated AS "수정일"
FROM "5. Zettelkasten/20. Permanent"
WHERE type = "permanent"
SORT length(related) ASC
```

---

## 🕸️ 고아 노트 (연결 0개 — 손봐야 할 노트)

> 들어오는 링크도, 나가는 링크도 없는 노트입니다. 최소 1곳과 연결하거나 Inbox로 보내세요.

```dataview
LIST
WHERE length(file.inlinks) = 0 AND length(file.outlinks) = 0
  AND !contains(file.path, "CLAUDE") AND file.name != "claude"
  AND !contains(file.path, "6. Templates")
  AND file.name != "00 Dashboard" AND file.name != "환영합니다!"
SORT file.name ASC
```

---

## 🆕 최근 수정된 노트 (10개)

```dataview
TABLE type AS "타입", updated AS "수정일"
WHERE type
SORT updated DESC
LIMIT 10
```

---

## ✅ 완료 · 보관 (Archive)

```dataview
TABLE type AS "타입", status AS "상태"
FROM "4. Archive"
WHERE type
SORT updated DESC
```

---

> [!note] 점검 루틴 (CLAUDE.md 원칙 기반)
> - **주 1회:** 📥 Inbox 비우기 → Literature 또는 Permanent로 이동
> - **월 1회:** 🕸️ 고아 노트 정리, 💡 연결 수 낮은 Permanent 노트 보강
> - **분기 1회:** Archive로 보낼 프로젝트 검토

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

이 저장소는 **Obsidian vault**입니다. Obsidian은 마크다운 기반의 개인 지식 관리(PKM) 도구로, 로컬 파일 시스템에 마크다운 파일을 저장합니다.

## 운영 철학

이 Vault는 **Zettelkasten(ZK)**과 **PARA** 시스템을 결합하여 운영됩니다.

### 핵심 원칙

1. **ZK(지식 발전소) ↔ PARA(작업대) 명확 분리**
   - `5. Zettelkasten/`: 시간 독립적 영구 지식
   - `1. Projects/`, `2. Areas/`: 시간 제약적 실행 작업

2. **참조 우선 원칙**
   - 결과물 제작 시 **복사 금지**
   - 항상 `[[링크]]` / `![[임베드]]` / `[[블록참조#^id]]`로 참조
   - 원본은 단일 진실 공급원(Single Source of Truth)

3. **One Idea per Permanent Note**
   - 퍼머넌트 노트는 하나의 주장/개념만 담음
   - 제목은 명사구 또는 문장형
   - 원자적 지식 단위 유지

4. **연결 강제**
   - 새 퍼머넌트 노트는 **최소 2개 이상** 기존 노트와 연결
   - 원천(Literature)과 해석(Permanent) 분리
   - 고아 노트(orphan notes) 방지

5. **유기적 진화**
   - 단순하게 시작하고 점진적 확장
   - 최소 플러그인으로 시작
   - 사용 빈도 높은 도구만 유지

## 저장소 구조

```
Hulkeinstein/
├── .obsidian/              # Obsidian 설정 및 플러그인
│   ├── plugins/           # 커뮤니티 플러그인
│   │   ├── dataview/     # Dataview 플러그인 (데이터 쿼리)
│   │   ├── templater-obsidian/  # Templater 플러그인 (템플릿)
│   │   └── terminal/     # Terminal 플러그인
│   ├── core-plugins.json  # 활성화된 코어 플러그인 목록
│   ├── community-plugins.json  # 활성화된 커뮤니티 플러그인 목록
│   ├── graph.json        # 그래프 뷰 설정
│   └── workspace.json    # 워크스페이스 레이아웃
├── 0. Docs/               # 문서화 및 운영 규칙
├── 1. Projects/           # PARA: 기한 있는 프로젝트
├── 2. Areas/              # PARA: 지속적 관리 영역
├── 3. Resources/          # PARA: 참고 자료 및 관심사
├── 4. Archive/            # PARA: 완료/중단된 항목
├── 5. Zettelkasten/       # ZK: 지식 관리 시스템
│   ├── 00. Inbox/        # 빠른 메모, 임시 노트
│   ├── 10. Literature/   # 문헌 노트 (원천 자료)
│   └── 20. Permanent/    # 영구 노트 (정제된 지식)
├── 6. Templates/          # 템플릿 파일
├── 7. Attachments/        # 이미지, PDF 등 첨부 파일
└── CLAUDE.md              # Claude Code 운영 가이드
```

### 폴더별 역할

#### 문서화 시스템
- **0. Docs**: 운영 규칙, 정책, 프로세스 문서
  - 평면 구조 (하위 폴더 없음)
  - 상세 Frontmatter + 마이크로 Changelog 사용
  - doc_type으로 분류: policy, procedure, howto, reference, decision

#### PARA 시스템 (시간 기반 실행)
- **1. Projects**: 명확한 목표와 마감일이 있는 프로젝트 (예: "웹사이트 리뉴얼", "논문 작성")
- **2. Areas**: 지속적으로 관리해야 하는 책임 영역 (예: "건강", "재무", "직무 역량")
- **3. Resources**: 관심 주제별 참고 자료 (예: "프로그래밍", "디자인")
- **4. Archive**: 완료되거나 더 이상 활성화되지 않은 항목

#### Zettelkasten 시스템 (지식 발전)
- **00. Inbox**: 아이디어 수집함, 빠른 캡처 (주 1회 정리)
- **10. Literature**: 책/글/영상에서 얻은 원천 노트 (저자의 생각)
- **20. Permanent**: 나만의 해석과 통찰 (내 언어로 재구성)

#### 지원 폴더
- **6. Templates**: 일관성 있는 노트 작성을 위한 템플릿
- **7. Attachments**: 이미지, PDF 등 바이너리 파일 (Git LFS 권장)

## Hub 파일

Hub 파일(`00_XXX_Hub.md`) 운영 규칙: [[운영-가이드]]

## 설치된 플러그인

### 활성화된 코어 플러그인
- **File explorer**: 파일 탐색기
- **Search**: 전역 검색
- **Graph view**: 노트 간 연결 그래프
- **Backlinks**: 역링크 표시
- **Daily notes**: 일일 노트 생성
- **Templates**: 템플릿 기능
- **Canvas**: 캔버스 보드
- **Outline**: 문서 아웃라인

### 커뮤니티 플러그인
- **Templater** (v2.16.0): 고급 템플릿 시스템
  - 동적 템플릿, 스크립트 실행, 사용자 함수 지원
- **Dataview**: 노트를 데이터베이스처럼 쿼리
  - 메타데이터 기반 검색 및 테이블 생성
- **Terminal**: Obsidian 내부 터미널
  - cmd.exe로 설정됨 (Windows)

## 작업 가이드

### 마크다운 파일 생성
- 파일명은 의미 있는 제목 사용
- 한글 파일명 지원
- 공백 대신 하이픈(-) 또는 공백 그대로 사용 가능

### Obsidian 링크 문법
```markdown
[[노트 이름]]                  # 내부 링크
[[노트 이름|표시 텍스트]]      # 별칭이 있는 링크
[[노트 이름#제목]]             # 특정 제목으로 링크
![[이미지.png]]                # 이미지 임베드
```

### Dataview 쿼리 예시

#### 1. 기본 - 모든 마크다운 파일 나열
```dataview
LIST
WHERE file.name != "CLAUDE"
SORT file.name ASC
```

#### 2. 특정 폴더의 파일 보기
```dataview
LIST
FROM "1. Projects"
SORT file.name ASC
```

#### 3. 태그로 필터링
```dataview
LIST
WHERE contains(tags, "project")
SORT file.name ASC
```

#### 4. TABLE 형식으로 메타데이터 표시
```dataview
TABLE type, status, created
WHERE type
SORT created DESC
```

### Templater 사용
- 템플릿 폴더 설정 필요
- `<% tp.date.now() %>` 등 동적 값 삽입 가능
- JavaScript 코드 실행 가능

## 템플릿 시스템

표준화된 템플릿을 사용하여 노트 품질과 일관성을 유지합니다.
8개 템플릿 (project, project-hub, area, resource, literature, permanent, docs, archive)이 버전 관리되며, 각 폴더 CLAUDE.md 규칙을 준수합니다.

템플릿 레지스트리, 버전 관리, 호환성 검증: **[[6. Templates/CLAUDE]]**

## 주의사항

### .obsidian 폴더
- `.obsidian/` 폴더는 사용자별 설정을 포함
- Git에 커밋 시 신중하게 판단:
  - `workspace.json`: 개인 워크스페이스 레이아웃 (보통 제외)
  - `core-plugins.json`, `community-plugins.json`: 팀 공유 시 포함 권장
  - `plugins/`: 플러그인 소스 코드 (팀 공유 시 포함 가능)

### 파일 작업
- 마크다운 파일만 생성/수정
- 이진 파일(이미지 등)은 첨부 파일 폴더에 보관 권장
- Obsidian의 내부 링크는 파일 이동 시 자동 업데이트됨

### 메타데이터 (YAML Frontmatter)
```yaml
---
tags: [태그1, 태그2]
created: 2025-10-13
author: 이름
---
```
- Dataview 쿼리에서 활용 가능
- Obsidian 속성 패널에서 시각적 편집 가능

## 보안 및 백업

### 버전 관리
- **Git 사용 권장**: 일일 커밋으로 변경 이력 추적
- **Obsidian Git 플러그인**: 자동 커밋/푸시 설정 가능
- **커밋 메시지**: 의미 있는 메시지 작성 (예: "Add literature note on productivity")

### 민감 정보 보호
- **디스크 암호화**: Windows BitLocker, macOS FileVault 활성화
- **공개 저장소 금지**: 개인 노트는 private repository 사용
- **민감 노트 분리**: 비공개가 필요한 내용은 별도 vault 관리

### 대용량 파일 관리
- **첨부 파일 분리**: `7. Attachments/` 폴더에 집중
- **Git LFS**: 대용량 이미지/PDF는 Git LFS 사용 고려
- **정기 정리**: 사용하지 않는 첨부 파일 주기적 삭제

### 백업 전략
```
1차: Git remote (GitHub/GitLab)
2차: 클라우드 동기화 (OneDrive/Dropbox)
3차: 외장 하드 (월 1회)
```

## 공통 속성 스키마

모든 노트에 일관된 메타데이터를 사용하여 Dataview 대시보드를 자동화합니다.

### 필수 속성

```yaml
---
type: project | area | resource | literature | permanent | daily
status: active | archived | completed | in-progress | todo
created: 2025-10-13
updated: 2025-10-13
tags: []
---
```

### 선택적 속성

```yaml
---
# 프로젝트 관련
project: "[[프로젝트명]]"    # 연결된 프로젝트
area: "[[영역명]]"           # 연결된 영역
due: 2025-12-31             # 마감일

# 지식 노트 관련
source: "[[출처]]"          # 원천 자료 (Literature)
author: "저자명"            # 원저자
related: ["[[노트1]]", "[[노트2]]"]  # 관련 노트
---
```

### 속성별 표준 값

#### type
- `project`: 프로젝트 허브 노트
- `area`: 영역 관리 노트
- `resource`: 참고 자료
- `literature`: 문헌 노트 (원천)
- `permanent`: 영구 노트 (통찰)
- `daily`: 일일 노트

#### status
- `todo`: 아직 시작 안 함
- `in-progress`: 진행 중
- `active`: 활성 상태 (영역/자료)
- `completed`: 완료
- `archived`: 보관

### Dataview 쿼리 실전 예시

#### 진행 중인 프로젝트 보기
```dataview
TABLE status, due
FROM "1. Projects"
WHERE type = "project" AND status = "in-progress"
SORT due ASC
```

#### 최근 생성된 노트 (모든 타입)
```dataview
TABLE type, created
WHERE type
SORT created DESC
LIMIT 10
```

#### Literature 노트를 저자별로 그룹화
```dataview
TABLE author, source
FROM "5. Zettelkasten/10. Literature"
WHERE type = "literature"
SORT author ASC
```

#### Permanent 노트 연결 개수 확인
```dataview
TABLE length(related) as "연결 수", tags
FROM "5. Zettelkasten/20. Permanent"
WHERE type = "permanent"
SORT length(related) DESC
```

#### 마감일이 가까운 프로젝트 (30일 이내)
```dataview
TABLE due, status
FROM "1. Projects"
WHERE type = "project" AND due AND due <= date(today) + dur(30 days)
SORT due ASC
```

## 베스트 프랙티스

### 노트 작성
1. **구조화된 태그 사용**: 계층적 태그로 분류 (#프로젝트/Hulkeinstein)
2. **일관된 템플릿**: 유사한 노트 타입에는 동일한 템플릿 사용
3. **백링크 활용**: 관련 노트 간 양방향 링크 생성
4. **원자적 노트**: 하나의 노트에 하나의 아이디어 (Permanent Note)
5. **메타데이터 활용**: Dataview로 쿼리 가능한 구조화된 정보 추가

### 연결과 발견
6. **2+ 연결 규칙**: 새 Permanent Note는 최소 2개 기존 노트와 연결
7. **참조 우선**: 복사 대신 `[[링크]]`, `![[임베드]]`, `#^블록참조` 사용
8. **그래프 뷰 활용**: 주기적으로 그래프 뷰에서 고립된 노트 확인
9. **역링크 확인**: 노트 작성 시 자동 생성된 역링크 검토

### 유지보수
10. **주기적 정리**:
    - 주 1회: Inbox 비우기
    - 월 1회: 고아 노트(orphan notes) 확인 및 정리
    - 분기 1회: Archive로 이동할 프로젝트 검토
11. **최소 플러그인 원칙**:
    - 사용 빈도 높은 플러그인만 유지
    - 새 플러그인은 1주일 시험 후 결정
12. **유기적 진화**:
    - 완벽한 시스템을 처음부터 만들려 하지 않음
    - 사용하면서 점진적으로 개선
    - 3개월마다 시스템 회고

### PARA 워크플로우
13. **프로젝트 수명 주기**:
    ```
    1. Projects (진행) → 4. Archive (완료)
    2. Areas (활성) → 4. Archive (중단)
    ```
14. **리소스 정리**:
    - 3개월 미사용 리소스는 Archive 고려
    - 관련 프로젝트가 생기면 다시 활성화

### Zettelkasten 워크플로우
15. **Literature → Permanent 흐름**:
    ```
    읽기 → 00. Inbox (빠른 메모)
         → 10. Literature (원천 정리)
         → 20. Permanent (내 생각으로 재구성)
    ```
16. **연결 먼저, 정리는 나중에**:
    - 완벽한 노트보다 연결된 노트가 더 가치 있음
    - 초안 상태로 두고 연결부터 만들기

## 확장 가능성

향후 추가 가능한 플러그인:
- **Obsidian Git**: 자동 Git 커밋/푸시
- **Calendar**: 일일 노트 달력 뷰
- **Kanban**: 칸반 보드
- **Excalidraw**: 손그림 다이어그램

---

# 🗣️ 영어 연습 루틴 (매 세션 자동 적용)

> 사용자가 **"hi"** 라고 하면 이 루틴을 그대로 시작한다. 설명을 요구하지 말 것.

## 1. 세션 시작 절차

1. **반드시 `date '+%Y-%m-%d %A'` 를 Bash로 실행**해 오늘 날짜·요일을 확인한다. (추측 금지)
2. 요일에 따라 분기한다.

| 요일 | 동작 |
|---|---|
| **월요일 · 목요일** | 메뉴 **없이** 곧바로 **15분 복습 퀴즈** 시작 (묻지 않는다) |
| 그 외 요일 | 아래 **메뉴 3개** 제시 |

### 메뉴 (월·목 제외)

```
| 번호 | 내용 |
|---|---|
| 1 | 🗣️ 영어 대화 연습 |
| 2 | 💻 JavaScript 변수 공부 |
| 3 | 📓 옵시디언 볼트 작업 |
```

- 사용자가 **1** → 자유 영어 대화 시작
- **2번(JavaScript)은 사용자가 명시적으로 고르기 전엔 절대 먼저 시작하지 않는다.**

## 2. 자유 대화 규칙

- 질문은 **한 번에 하나씩**, 짧게. 영어로 묻는다.
- 답변을 받으면 **즉시 교정**한다.
  - 잘 쓴 문장 → 🏆 로 칭찬 (왜 좋은지 한 줄)
  - 틀린 문장 → 표로 `내가 쓴 표현 / 바른 표현 / 설명`
  - 관련 문법·어휘 표를 1~2개 덧붙인다
- **대화 자체에는 한글을 쓰지 않는다.** 문법 설명·교정 블록에만 한글 사용.
- 철자 교정 시 **l / i / I 는 반드시 글자 이름으로** 불러준다 (예: "소문자 엘"). 사용자 폰트에서 구분이 안 됨.
- 사용자는 **한 손으로 타이핑**하므로 오타가 잦다. 오타는 가볍게 짚고 넘어간다.

## 3. 복습 퀴즈 (월·목 강제)

| 항목 | 내용 |
|---|---|
| 시점 | 세션 시작 직후 15분 |
| 방식 | 메뉴 없이 **바로 시작**, 선택권 없음 |
| 출제 | 최근 며칠치 **❌ Corrections** + **반복 실수 추적기** 에서, **반복 실수 최우선** |
| 문항 수 | **7문제** |
| 형식 | 틀린 문장 제시 → 사용자가 직접 고치기 |
| 채점 | 표로 `번호 / 내 답 / 정답 / 결과` · 부분 정답은 0.5점 |
| 중단 | 사용자가 명시적으로 **"복습 그만"** 이라고 할 때만 |

채점 후 **정복한 반복 실수**와 **다음에 또 출제할 항목**을 반드시 적는다.

## 4. 로그 기록 ("Log today's conversation.")

### 저장 위치 (중요)

> ⚠️ **실제 볼트는 `D:` 드라이브다.** 항상 아래 경로에 기록한다.
> `D:\Obsidian\AI Practice\Claude Code\Obsidian Automation\3. Resources\English\`

| 파일 | 용도 |
|---|---|
| `영어 표현 노트 (YYYY_MM).md` | 월별 일일 로그 |
| `복습 노트 (2026).md` | 복습 퀴즈 모음 + 반복 실수 추적기 |
| `단어장_단어 연습.md` | ⛔ **사용자가 직접 관리. 절대 수정하지 말 것** |

### 절차

1. **`date` 명령으로 날짜를 다시 확인**한다. (문맥에서 추측 금지)
2. 섹션 본문을 scratchpad에 Write 도구로 작성한다. (긴 본문은 bash heredoc이 깨짐)
3. 짧은 Python 스크립트로 **목차 행 추가** + **푸터 앞에 섹션 삽입**.
4. 검증: 날짜 섹션 수 = 목차 행 수 = 제목 줄 수, 충돌 마커 0.

### 섹션 구조

```markdown
## 📅 YYYY-MM-DD
> 🏷️ **English Title** (한글 제목) 이모지

### 🎯 오늘의 복습 퀴즈 (N/7 정답)   ← 월·목만
### 💬 오늘의 대화 (Q&A)            ← 질문/답변 표
### ✅ 바른 표현 (잘 쓴 문장)
### ❌ 틀린 단어와 수정본 (Corrections)
### (문법·어휘 표 여러 개)
### 🏎️ 조립 진행 상황
### 💡 오늘의 팁
```

### 삽입 스크립트 패턴

```bash
cd "D:/Obsidian/AI Practice/Claude Code/Obsidian Automation/3. Resources/English" && PYTHONIOENCODING=utf-8 py -3 - <<'PY'
import io
p = '영어 표현 노트 (2026_10).md'
sec = io.open(r'<scratchpad 경로>', encoding='utf-8').read().rstrip('\n')
s = io.open(p, encoding='utf-8').read()
assert s.count('## \U0001F4C5 2026-10-23') == 0        # 중복 방지
title = sec.split('\n')[1].split(' ', 2)[2].strip()     # 제목은 본문에서 복사 (한글 깨짐 방지)
toc_old = '| [[#\U0001F4C5 2026-10-22\\\\|2026-10-22]] |'
s = s.replace(toc_old, '| [[#\U0001F4C5 2026-10-23\\\\|2026-10-23]] | ' + title + ' |\n' + toc_old)
footer = '\n\n## \U0001F4DD \ubb38\ubc95 \ud301 \ubaa8\uc74c'
s = s.replace(footer, '\n\n' + sec + footer)
io.open(p, 'w', encoding='utf-8').write(s)
PY
```

> 📌 목차의 `|` 는 반드시 `\|` 로 이스케이프. Python 문자열에선 `\\\\|`.
> 📌 `PYTHONIOENCODING=utf-8` 없으면 한글이 깨진다.
> 📌 `python` 은 깨진 MS Store 스텁 → **`py -3`** 사용.

### 월이 바뀌면

새 `영어 표현 노트 (YYYY_MM).md` 를 만들고, 이전 달 노트와 `복습 노트 (2026).md` 에 상호 링크를 추가한다.

## 5. 마무리

사용자가 **"See you next time!"** 하면 → 짧고 따뜻한 한글 인사. 오늘의 하이라이트 1~2개 + 다음 복습일 안내.

## 6. 알려진 앱 버그 (2026-10 현재)

> 🐛 **자동전송 버그**: 사용자가 입력하지 않은 메시지(`..`, `ㅋ`, 이전 문장 등)가 **저절로 반복 전송**된다. 거의 매일 발생.

| 대응 | |
|---|---|
| 판별 | 같은 문장·점·자음이 연속 반복되면 자동전송으로 간주 |
| 기록 | **자동전송분은 로그에서 제외**한다. 실제 작성 문장만 기록 |
| 안내 | 사용자에게 입력창 비우고 **앱 재시작** 권유 |
| 제보 | github.com/anthropics/claude-code/issues |

## 7. 사용자 배경 (교정 톤 참고)

- 경기케어센터 거주. 오후 4:30 저녁 → 5:30 취침 → 11시경 잠듦.
- **한 손으로만** 타이핑·조립한다. 오타가 잦고, 작은 부품 조립이 어렵다.
- 공군(ROKAF) **F-4E 팬텀 정비병** 출신, 30개월 복무.
- 취미: LEGO Technic / 플라스틱 모델 조립, 강아지 훈련 영상, 90년대 가요.
- 영어 실력은 꾸준히 향상 중. **칭찬을 구체적으로** 해주면 동기부여가 된다.

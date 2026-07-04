---
date_daily: <% tp.file.title %>
achievement: 
reading_book: 
emotion: 
important-date: false
tags:
  - clippings
  - daily
---
<%*
const t = tp.file.title;
const ref = "YYYY-MM-DD(ddd)";
tR += '[[' + tp.date.now("YYYY-MM[월]", 0, t, ref) + ']] ';
tR += '[[' + tp.date.now("gggg-[W]ww", 0, t, ref) + ' ' + tp.date.now("ww[주]", 0, t, ref) + ']]\n';
tR += '<< ';
tR += '[[' + tp.date.now("YYYY-MM-DD(ddd)", -1, t, ref) + ']] | ';
tR += tp.date.now("YYYY-MM-DD(ddd)", 0, t, ref) + ' | ';
tR += '[[' + tp.date.now("YYYY-MM-DD(ddd)", 1, t, ref) + ']]';
tR += ' >>';
%>

## 오늘의 목표
-
-
- [ ] 

## 할 일 추가하기
- [ ] 
- [ ] 

## 독서
- 읽은 책
- 읽은 페이지

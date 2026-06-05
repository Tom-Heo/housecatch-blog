---
name: naverblog-form
description: naverblog-form/SKILL.md는 네이버 블로그 스마트에디터 ONE에 붙여넣을 수 있는 HTML 파일로 글을 작성하고 서식을 입히는 SKILL이다. 본문을 새로 쓸 때부터 이 형식 규칙을 함께 적용해 강조와 구조를 입힌다. 네이버 블로그 글을 쓰거나 서식 작업을 해야 하는 상황에 사용한다.
---
# naverblog-form


## Table of Contents
- Foundation
    - Overview
    - Triggers
    - Usage
- Context
    - Purpose
    - Glossary
    - Philosophy
- Format
    - Format Token
    - Format Rules
    - Example
- Rules
    - Principles
    - Pitfalls
    - Edge Cases

## Foundation


### Overview
naverblog-form/SKILL.md는 네이버 블로그 스마트에디터 ONE에 붙여넣을 수 있는 HTML 파일로 글을 작성하고 서식을 입히는 SKILL이다. 본문을 새로 쓸 때도, 이미 있는 본문을 다듬을 때도 이 형식 규칙을 따른다.


### Triggers
- 네이버 블로그 글을 쓰거나 서식을 입혀야 하는 상황
- 네이버 블로그에 붙여넣을 HTML이 필요한 상황
- 사용자가 네이버 블로그 글쓰기나 서식 작업을 요청하는 상황

### Usage
1. 작성하거나 다듬을 본문을 확인한다. 새로 쓰는 경우 형식 규칙을 염두에 두고 본문부터 쓴다.
2. 본문의 내용과 흐름을 면밀히 읽는다.
3. Format Rules에 따라 강조와 구조를 판단한다.
4. Format Token 구조로 HTML 파일을 작성한다.
5. /mnt/user-data/outputs/에 .html 파일로 저장한다.
6. 사용자에게 사용 방법을 안내한다: 브라우저로 열기 → 전체 선택 → 복사 → 네이버 에디터에 붙여넣기 → 이미지·링크는 직접 처리.

## Context


### Purpose
네이버 블로그 글에 강조와 구조를 입혀, 스마트에디터 ONE에 붙여넣었을 때 서식이 보존되는 HTML 파일로 만든다. 본문을 새로 쓰는 단계부터 이 형식을 함께 적용한다.


### Glossary
- 인라인 강조: 문장 일부에 입히는 강조. 굵게, 글자색, 형광펜, 취소선.
- 블록: 줄 전체를 차지하는 구조 단위. 문단, 제목, 인용구, 구분선, 목록, 표.
- 플레이스홀더: 붙여넣기로 옮길 수 없는 요소(이미지, 링크)의 자리를 표시하는 표식.
- 스마트에디터 ONE: 네이버 블로그의 현행 글쓰기 에디터.
- 컴포넌트: 스마트에디터 ONE이 내부적으로 관리하는 블록 단위(se-component). 고유 id로 식별되며 외부 HTML로 재현할 수 없다.
- 붙여넣기 보존: HTML을 클립보드로 복사해 에디터에 붙여넣었을 때 서식이 살아남는 것. 시각 결과만 보존되며 의미 정보와 링크 연결은 보존되지 않는다.

### Philosophy
- 형식은 내용을 위해 존재한다.
- 강조와 구조는 독자를 위한 길잡이다.
- 인용구로 핵심을 붙잡고 글의 호흡을 만든다.
- 리듬이 가독성을 만든다. 강조, 인용, 여백으로 글에 결을 준다.
- 되는 것만 깔끔하게 쓴다.
- 일관성이 신뢰를 만든다.
- 정확하기에 아름답다.

### Format Token

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>{글 제목}</title>
<style>
  body { max-width: 720px; margin: 40px auto; padding: 24px 28px; background: #ffffff; color: #1a1a1a; font-family: -apple-system, "Pretendard", "Malgun Gothic", sans-serif; font-size: 16px; line-height: 1.75; }
  p { margin: 0 0 6px; }
  table { border-collapse: collapse; }
  th, td { border: 1px solid #bebebe; padding: 6px 12px; }
</style>
</head>
<body>
{본문}
</body>
</html>
```


### Format Rules

**인라인 강조 (검증 완료)**
- 빨강 강조: `<strong><span style="color:#DA291C;">텍스트</span></strong>` (PANTONE 485 C). 핵심·경고. 항상 굵게 동반.
- 파랑 강조: `<strong><span style="color:#0072CE;">텍스트</span></strong>` (PANTONE 285 C). 핵심·정보. 항상 굵게 동반.
- 노랑 형광: `<span style="background-color:#FEDD00;">텍스트</span>` (PANTONE Yellow C). 일반체로 둔다. 글자색은 검정 기본.
- 굵게: `<strong>텍스트</strong>`. 색 없는 단순 강조.
- 취소선: `<del>텍스트</del>`.

**제목**
- `<h1>`, `<h2>`만 사용한다. h3 이하는 쓰지 않는다.
- 제목은 검정 기본. 색을 넣지 않는다.

**문단·줄바꿈**
- 본문 문단은 `<p>`로 감싼다.
- 줄바꿈은 항상 `<br>`로 만든다. 빈 줄 개수는 위치에 따라 다르다.
- 제목(h2) 위: `<br>` 3개. 섹션 경계를 크게 띄운다.
- 제목 바로 아래(제목과 첫 문단 사이): `<br>` 1개.
- 문단과 문단, 문단과 블록(목록·표·인용구 등) 사이: `<br>` 1개.
- 글 맨 위 h1 아래도 `<br>` 1개.
- 한 줄만 띄우는 곳에 2개를 쓰거나, 섹션 경계를 1개로 좁히지 않는다. 위치별 개수를 지킨다.

**블록**
- 인용구: `<blockquote>텍스트</blockquote>`. 따옴표형 한 종류만 가능하다. 핵심 문장, 단락의 요지, 독자에게 건네는 말은 인용구로 끌어내 강조하고 호흡을 만든다. 아끼지 말고, 글마다 두세 번은 적극적으로 쓴다.
- 구분선: `<hr>`.
- 목록: `<ul>`/`<ol>`. 1단계만. 항목은 `<li>`.
- 표: `<table>`. 헤더행은 `<thead>` + `<th>`. 셀은 `<td>`. 셀 병합 `colspan`/`rowspan`, 셀 배경색, 셀 안 강조, 셀별 정렬(`style="text-align:center|right"`) 모두 사용 가능하다.

**플레이스홀더 (대괄호는 검정, 안쪽 텍스트만 초록 #00B140 PANTONE 354 C)**
- 이미지: `[<span style="color:#00B140;">이미지를 첨부하세요: {사진 설명} 이미지</span>]`. {사진 설명} 자리에 무슨 사진인지 적고, 끝은 '이미지'로 맺는다. (예: `[<span style="color:#00B140;">이미지를 첨부하세요: 누수 얼룩 천장 이미지</span>]`)
- 링크: `[<span style="color:#00B140;">링크를 삽입하세요: {링크 주소}</span>]`. {링크 주소} 자리에 들어갈 링크의 주소나 대상을 적는다. (예: `[<span style="color:#00B140;">링크를 삽입하세요: example.com</span>]`)

**이모지 (검증 완료, 총 10종)**
- ✅ 표 안 '됨/가능'
- 🔴 표 안 '안 됨/불가' (✅의 짝)
- ☑️ 체크리스트 항목, 제목/헤더
- 📌 중요 포인트
- 🔍 분석, 자세히 보기
- 💡 팁
- ⚠️ 주의
- 🚫 금지
- 😢 슬픔, 아쉬움
- 🙏 감사, 부탁

**색상 표기**
- 글자색·배경색은 6자리 hex로 통일한다.
- 빨강 #DA291C · 파랑 #0072CE · 노랑 #FEDD00 · 초록 #00B140.

**문장 부호**
- 줄표(— em dash, – en dash)는 제목과 본문 어디에도 쓰지 않는다. 문장은 쉼표나 마침표로 끊고, 짝을 이루는 설명은 콜론(:)이나 괄호로 대신한다.
- 가운뎃점(·)과 물결표(~)는 그대로 쓴다.

### Example

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>네이버 블로그 서식 샘플</title>
<style>
  body { max-width: 720px; margin: 40px auto; padding: 24px 28px; background: #ffffff; color: #1a1a1a; font-family: -apple-system, "Pretendard", "Malgun Gothic", sans-serif; font-size: 16px; line-height: 1.75; }
  p { margin: 0 0 6px; }
  table { border-collapse: collapse; }
  th, td { border: 1px solid #bebebe; padding: 6px 12px; }
</style>
</head>
<body>

<h1>제목은 h1으로 한 번</h1>
<br>
<p>도입 문단이다. 핵심은 <strong><span style="color:#0072CE;">파랑 강조</span></strong>로, 경고는 <strong><span style="color:#DA291C;">빨강 강조</span></strong>로 표시한다. 키워드는 <span style="background-color:#FEDD00;">노란 형광</span>으로 둔다.</p>
<br>
<br>
<br>
<h2>소제목은 h2</h2>
<br>
<p>표는 강하게 보존된다.</p>
<br>
<table>
<thead>
<tr><th>항목</th><th>여부</th></tr>
</thead>
<tbody>
<tr><td>굵게 · 색 · 형광</td><td>✅ 됨</td></tr>
<tr><td>링크 · 이미지</td><td>🔴 안 됨</td></tr>
</tbody>
</table>
<br>
<blockquote>인용구는 따옴표형 한 종류만 들어온다.</blockquote>
<br>
<p>[<span style="color:#00B140;">이미지를 첨부하세요: 거실 전경 이미지</span>]</p>
<br>
<br>
<br>
<h2>🙏 마무리</h2>
<br>
<p>되는 것만 깔끔하게 쓴다.</p>

</body>
</html>
```


## Rules


### Principles
- 출력은 항상 완전한 HTML 문서 파일이다. /mnt/user-data/outputs/에 .html로 저장하고 사용자가 브라우저에서 복사하게 한다.
- 강조와 구조는 본문을 읽고 직접 판단한다. 본문을 새로 쓸 때도 이 형식을 함께 적용한다.
- 시각 결과만 보존된다. 의미 태그(strong, em 등)의 의미 정보는 붙여넣기 과정에서 사라지므로, 일관성과 간결성을 기준으로 태그를 고른다.
- 컴포넌트는 재현하지 않는다. 인용구 종류, 이미지 등 se-component로 감싸지는 요소는 외부 HTML로 만들 수 없다. 문단·제목·인라인 강조·표·목록·인용구(따옴표형)·구분선만 사용한다.
- 안 되는 것은 플레이스홀더로 둔다. 링크와 이미지는 자리만 표시하고 사용자가 직접 처리하게 한다.
- 강조는 의도를 갖고 쓴다. 필요한 곳에는 분명히 쓰되, 색과 형광은 핵심에만 얹어 남발하지 않는다.
- 색은 정해진 네 가지만 쓴다. 빨강·파랑·노랑·초록 외의 색을 임의로 만들지 않는다.
- 빨강과 파랑은 반드시 굵게와 함께 쓴다. 노랑 형광은 일반체로 둔다.
- 제목 위계는 h1과 h2뿐이다. 더 깊은 단계가 필요해 보여도 h2까지만 쓴다.

### Pitfalls
- 취소선에 `<s>`를 쓰는 실수. `<s>`는 보존되지 않는다. `<del>`을 쓴다.
- 형광펜에 `<mark>`를 쓰는 실수. `<mark>`는 보존되지 않는다. `<span style="background-color:#FEDD00;">`를 쓴다.
- 글자색에 `<font>`를 쓰는 실수. 폐기된 태그다. `<span style="color:...">`를 쓴다.
- 하이퍼링크를 `<a href>`로 거는 실수. 겉모습만 남고 링크 연결은 사라진다. 링크 플레이스홀더로 둔다.
- 외부 이미지를 `<img src>`로 넣는 실수. 네이버는 자사 서버에 업로드된 이미지만 인식한다. 이미지 플레이스홀더로 둔다.
- 인용구 종류를 지정하려는 실수. 버티컬 라인·말풍선·밑줄·포스트잇·프레임은 재현할 수 없다. `<blockquote>`는 따옴표형으로만 들어온다.
- 목록을 중첩하는 실수. 들여쓰기 단계는 보존되지 않는다. 1단계로 편다.
- 목록 시작 번호를 `start`로 지정하는 실수. 무시되며 항상 1부터 시작한다.
- 빈 문단 `<p></p>`로 간격을 벌리는 실수. 씹힌다. 간격은 `<br>`로 만든다.
- 빈 줄 개수를 위치와 무관하게 똑같이 넣는 실수. 제목 위는 3개, 제목 아래와 문단 사이는 1개다.
- 글자 크기를 `font-size`로 조절하는 실수. 위계는 제목(h1·h2)으로 잡는다. 본문에서 크기를 바꾸지 않는다.
- 기울임(`<i>`/`<em>`)이나 밑줄(`<u>`)을 쓰는 실수. 사용하지 않는 강조다.
- 자간(`letter-spacing`)이나 폰트(`font-family`)를 지정하는 실수. 보존되지 않는다.
- 코드블록 `<pre>`를 쓰는 실수. 보존되지 않는다.
- 빨강·파랑을 굵게 없이 색만 쓰는 실수. 두 색은 항상 굵게와 함께 쓴다.
- 노랑 형광에 굵게를 더하는 실수. 노랑은 일반체로 둔다.
- 플레이스홀더 대괄호까지 초록으로 칠하는 실수. 대괄호는 검정, 안쪽 텍스트만 초록이다.
- 플레이스홀더를 설명 없이 비워 두는 실수. 이미지는 무슨 사진인지, 링크는 어떤 주소인지 안쪽에 적는다.
- 줄표(—)를 쓰는 실수. 제목과 본문 어디에도 쓰지 않는다. 쉼표·마침표·콜론으로 대신한다.

### Edge Cases
- 표 셀 안 강조: 허용. `<td>` 안에 `<strong>`·`<span style>`·이모지를 그대로 쓸 수 있다.
- 표 셀별 정렬: 허용. `<td style="text-align:center|right">`로 셀마다 다르게 지정 가능.
- 이모지 위치: 제목 첫머리 또는 문단·항목 첫머리에 둔다. 한 섹션에 하나로 절제한다.
- ✅와 🔴: 표 안에서만 가부 표시로 쓴다. ☑️는 표가 아닌 체크리스트·헤더에 쓴다.
- 특수문자·이모지: 보존된다. 그대로 입력한다.
- 본문이 길어 잘리는 경우: 파일을 나누지 말고 한 문서로 완성한다.

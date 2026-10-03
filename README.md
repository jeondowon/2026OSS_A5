# 오픈소스 스튜디오 01분반

22300650 / 전도원

## Assignment 5. JavaScript DOM & CRUD

## Deployment

Vercel URL: https://2026ossa5-git-main-dowonjeon.vercel.app/

## Key Learning

1. 브라우저가 HTML을 객체 구조(DOM)로 만들고, JavaScript는 HTML 파일이 아니라 이 DOM을 바꿔서 화면을 변경한다는 것을 배웠습니다.
2. 사용자의 행동이 발생하면 브라우저가 Event 객체를 만들어 callback 함수에 전달하고, 그 함수가 DOM을 변경한다는 흐름을 배웠습니다.
3. createElement()와 appendChild()로 요소를 만들어 붙이고 remove()로 삭제하는 방법을 배웠습니다.

## CRUD Service

동아리 회원 관리 서비스를 만들었습니다. 데이터 필드는 id, name, studentId, gender, major, email 6개입니다.

1. Create: 입력값이 validate()를 통과하면 members.push()로 배열에 추가하고, render()로 화면을 갱신합니다. 해당 동작을 완료하면 Form을 reset()하여 입력창을 비웁니다.
2. Read: render()가 members Array를 forEach()로 돌면서 tr, td를 createElement()로 만들어 tbody에 붙여서 테이블로 표시합니다.
3. Update: 수정 버튼을 누르면 값을 Form에 채우고 editingId를 저장합니다. 저장 시 members.find()로 대상을 찾아 값을 바꾸고 render()를 호출합니다.
4. Delete: confirm()으로 확인한 뒤 members.filter()로 해당 id를 제외한(삭제하려고 하는 항목 제외 다른 항목들) 매열을 다시 만들어서 render()를 호출합니다.

Validation은 이름 필수 입력, 학번 8자리, 성별/학부 선택 여부, 이메일 형식(checkValidity()) 5가지를 적용했습니다.

## JavaScript

1. querySelector() / getElementById(): id나 선택자로 HTML 요소를 찾는 기능입니다. js_dynamic.html에서는 입력창과 리스트를, crud.html에서는 Form 입력 요소와 회원 목록을 가져오는 데 사용했습니다.
2. addEventListener(): 요소에 이벤트와 실행할 함수를 연결하는 기능입니다. js_dynamic.html에서는 추가 버튼과 삭제 버튼, crud.html에서는 저장 버튼과 수정, 삭제 버튼 클릭 처리에 사용했습니다.
3. createElement() / appendChild(): 요소를 새로 만들어 부모 요소에 붙이는 기능입니다. js_dynamic.html에서는 li, span, 삭제 버튼을 만들 때, crud.html에서는 render() 안에서 회원마다 tr, td, 버튼을 만들어 tbody에 붙일 때 사용했습니다.
4. confirm() / alert(): confirm()은 확인 창을 띄우고 확인을 눌렀을 때만 true를 반환하고, alert()는 메시지 창을 띄웁니다. crud.html의 삭제 버튼에서 삭제 여부를 확인할 때 confirm()을 사용했고 validate()에서 잘못된 입력을 알릴 때 alert()를 사용했습니다.
5. Array push(): 배열 끝에 새 데이터를 추가하는 기능입니다. crud.html에서 Validation을 통과한 새 회원을 members 배열에 추가할 때 사용했습니다.
6. Array find() / filter(): find()는 조건에 맞는 첫 번째 요소를 반환하고, filter()는 조건에 맞는 요소만 모은 새 배열을 반환합니다. find()는 수정할 회원을 id로 찾을 때, filter()는 삭제할 id를 제외한 배열을 만들 때 사용했습니다.
7. render(): members 배열의 내용을 화면에 그리는 함수입니다.

## AI / Search Usage

Tool: claude

Purpose: 모르는 것을 물어보기 위해, 코드 검증 및 제출 전 검토.

Used:

1. 배열 함수 (push, find, filter)의 기능과 사용법을 알아보기 위해 사용했습니다.
2. 코드에 버그가 없는지 Ai를 활용하여 확인하였습니다.
3. 또한 과제 제출전 빠트린것이 없는지 마지막으로 점검하기 위해서 사용했습니다.

What I Learned - 새로운 함수들을 알게 되었습니다. 특히 find()는 조건에 맞는 첫 번째 요소를 반환하고, filter()는 조건에 맞는 요소만 모은 새 배열을 반환한다는 것을 이해했습니다.

## Problem & Solution

문제
수정 버튼을 눌러 editingId에 id가 저장된 상태에서, 그 회원을 삭제하고 저장 버튼을 누르면 에러가 발생했습니다. 삭제된 회원의 id가 editingId에 그대로 남아 있어서, 저장할 때 members.find()가 대상을 찾지 못하고 undefined를 반환했고, undefined의 name에 값을 넣으려다 에러가 난 것이었습니다.

해결
삭제 버튼의 처리에서 삭제하는 회원의 id가 editingId와 같은지 확인하고, 같으면 editingId를 null로 되돌리고 Form을 reset()하도록 했습니다. 이제 삭제된 회원을 가리키는 editingId가 남지 않기 때문에 에러가 발생하지 않습니다.

## Reflection

Form에 입력한 값이 바로 화면에 나타나는 것이 아니라, Array에 먼저 저장되고 render()가 그 Array를 읽어서 화면을 그린다는 구조를 이해하게 됐습니다.

## tailwind 실행
```
npx tailwindcss -i ./src/rockjoon/init.css -o ./src/rockjoon/output-rockjoon.css --watch
```

## 미해결 문제
- 폰트 설정 하는 방법
- block이 필요한 경우 div안에 span을 넣는 것이 맞는지? span에 block을 주는 것이 맞는지?
- 인기 급상승 여행지 이미지 내부의 텍스트가 흐리게 보이는 이유?
- 노랑풍선에서는 가상요소 이미지를 잘라서 쓰는 이유?


## 해결된 문제
- 폰트 굵기 설정은 <b><em><strong> 등의 태그를 이용
- 검색창 노랑색 보더 설정 안되는 이유 
  - reset.css 에 border 0속성 때문. tailwind는 기본으로 reset이 포함되어 있기 때문에 추가할 필요 없음.
- 자식 요소가 한 개일때도 정렬을 위해 flex를 사용하는 것이 맞는지?
  - 한 개 일때도 flex를 적용하는 것이 좋다.
  - 유연하게 정렬할 수 있기 때문

## 진행하며 배운 것들

### 1. HEADER
- **width와 mx-auto를 이용하여 중앙 정렬**하기
- flex를 사용하여 요소들을 가로로 배치하기
- 수평선 긋기
    - **hr 태그**와 border를 사용하여 해결
- 요소들 간격 벌리기
  - flex일 경우 gap 사용
  - padding, margin 사용

### 2. 이미지 슬라이드
- overflow를 이용하여 넘치는 이미지 처리하기
  - **overflow-x-scroll** 스크롤로 보여주도록 임시 조치
- 이미지 크기 조절
  - w, h가 아니라 min-w, min-h 로 지정해야 **크기가 줄어들지 않는다.**
  - w-full, h-full은 **부모의 너비, 높이를 그대로** 따라간다. 다만 부모에 명시적으로 크기가 지정되어 있어야 함.
  - a 태그는 인라인이기 때문에 block으로 지정하지 않으면 너비 설정 불가능.

### 3. 옐로팡딜
- relative : 자기 자신의 위치에서 t,b, r, l 만큼 움직임.
- absolute
  - absolute는 상위의 relative가 붙은 요소 위치에서 tbrl 만큼 움직임.
  - 상위에 relative가 없으면 body를 기준으로 움직임.
- ::before, ::after
  - html 가상 요소로 주로 기호, 도형, 수식어 등을 표현하기 위해 사용
  - inline이기 때문에 너비, 높이를 가질 수 없다. -> inline-block 으로 변경 해야 함.
  - margin top, bottom 지정 불가 / padding은 전부 지정 가능
- 가격 강조를 위해 폰트 크기가 다를 경우 flex items-baseline을 통해 수직 정렬을 바닥에 맞게 정렬
 - <span class="inline-flex items-center h-[2.4rem] px-2 rounded-[0.4rem] bg-[#5778BB] text-white text-[1.3rem]">해외패키지</span>
### 4. 추천상품
- 해외패키지 : 이미지보다 큰 div를 만들고 이미지를 안에 넣는다. div에 relative를 넣고 absolute div를 만들어 상대 위치로 이미지를 벗어난 영역을 만듬.
- 이미지 아래 글자들은 좌우 여백이 같으므로 하나의 div에 넣어 작업하면 좋을듯 하다.

### 5. 온캉스 여행이 제격!
- a태그와 img태그는 기본적으로 inline속성
- 하지만 a태그는 하위 요소가 block일 경우 a태그도 block이 됨.

### 6. bc카드 할인 배너
- bg-[rgb(251,226,229)]와 같이 테일윈드에서 rgb나 rgba값을 사용 할 수 있음.

### 7. 인기 급상승 여행지
- absolute-[50%]와 같이 상대적인 위치를 지정할 때에는 상위 요소의 마진까지 길이로 포함됨.
- 하지만 시작 지점을 지정하는 것이기 때문에 실제로 중앙에 배치되지 않는다.(중앙부터 시작이기 때문에 중앙보다 아래에 배치됨.)
- transform -translate-y-1/2 를 주어 자식요소의 높이의 절반을 위로 올려 줘야한다.
- 
### 8. Yellow Series
- grid

### 9. 카드 혜택
- 요소 내부에 더 작은 요소가 들어가고, 상하좌우 간격이 각자 달라서 flex를 쓰기 애매할 때는 padding으로 수동 조정.
- 
### 10. footer
- 상위 wraper를 이용하여 길이가 서로 다른 요소들의 끝을 맞출 수 있다.

## 추후 과제
- 가상 돔으로 특수 문자 생성하기 
- 이미지 슬라이드 애니메이션 적용
- nav 메뉴 호버링시 하위 메뉴 보여주기

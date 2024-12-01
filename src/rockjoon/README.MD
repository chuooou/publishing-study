## tailwind 실행
```
npx tailwindcss -i ./src/rockjoon/init.css -o ./src/rockjoon/output-rockjoon.css --watch
```







## 미해결 문제
- 폰트 굵기 설정 하는 방법
- 검색창 노랑색 보더 설정 안되는 이유
- 수평선 긋기
  - border bottom으로 수평선 긋기 (안됨)

## 해결된 문제
- width와 mx-auto를 이용하여 중앙 정렬하기
- flex를 사용하여 요소들을 가로로 배치하기
- 수평선 긋기
    - hr 태그와 border를 사용하여 해결


## 추후 과제
- 가상 돔으로 특수 문자 생성하기 
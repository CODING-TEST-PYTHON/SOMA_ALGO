# 요약
- 시간제한 1초에 1 ≤ W, H ≤ 100 이므로 제약조건은 널널하다고 판단, 즉 구현 문제다
- 구현 순서
  1. 6각형 위치관계를 정의
  2. 그래프로 연결
  3. 어느 방향으로 연결됬는지 확인
  4. bfs로 연결되지않은 부분 개수 카운트
  5. 밖에서 안보이는 위치 마이너스
# 설명
- 건물 안에 있는 흰색과 건물 밖에 있는 흰색을 구별하는 방법이 가장 어려웠음
- 계속해서 건물 안에 있는 흰색 그룹을 찾아내려고 했지만, 그건 실패했고
- 건물 밖에 있는 흰색 그룹은 matrix **끝부분과 맞닿아있다는 점을 발견함**
- 이를 통해 건물 밖에 있는 흰색 그룹을 찾아내서 -> 모든 흰색 그룹을 건문 안과 건물 밖으로 구분 가능해짐
  ```python
  if nnx < 0 or nnx >= w or nny < 0 or nny >= h:
    if tar == 0:
        is_inside = False
  ```

# 포인트
- 6방 탐색
  1. 짝수 라인
  ```python
  dx_even = [1, 1, 0, -1, 0, 1]
  dy_even = [0, 1, 1, 0, -1, -1]
  ```
  2. 홀수 라인
  ```python
  dx_odd = [1, 0, -1, -1, -1, 0]
  dy_odd = [0, 1, 1, 0, -1, -1]
  ```
- 3차원 배열을 통해 어떤 방향으로 연결되어 있는지 확인
  ```python
  graph = [[[0 for i in range(6)] for j in range(w)] for k in range(h)]
  ```
  그래서 각 인덱스(0부터 5)를 6방탐색과 맞춤

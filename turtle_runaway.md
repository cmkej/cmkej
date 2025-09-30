# Turtle Runaway 게임 설명서

## 개요
`Turtle Runaway`는 추격자(Chaser)와 도망자(Runner) 거북이가 등장하는 간단한 게임입니다. 사용자는 WASD 키를 이용해 추격자를 조종하며, 제한 시간 안에 도망자를 잡으면 점수를 획득합니다. 도망자는 AI로 자동으로 움직입니다.

## 게임 규칙
- 추격자가 도망자를 잡으면 +10점 획득
- 제한 시간 내에 잡지 못하면 점수 0점
- 게임 종료 시 "Game Over!" 메시지 출력

## 주요 클래스

### 1. RunawayGame
- 게임의 핵심 클래스
- 주요 기능
  - `__init__(canvas, runner, chaser, catch_radius=50, game_time=30)`: 게임 초기화
    - canvas: tkinter Canvas 객체
    - runner: 도망자 객체
    - chaser: 추격자 객체
    - catch_radius: 잡았다고 판정할 거리
    - game_time: 제한 시간(초)
  - `is_catched()`: 도망자와 추격자 사이의 거리 계산, 잡힘 여부 반환
  - `start(init_dist=400, ai_timer_msec=100)`: 초기 위치 설정 및 게임 시작
  - `step()`: 매 프레임마다 실행, 도망자 AI 실행, 점수 계산, 상태 출력

### 2. ManualMover
- 수동 조작 추격자
- 특징
  - WASD 키로 직선 이동
  - 이동 방향에 맞춰 거북이 회전
  - `move(dx, dy)`: 이동 및 회전 처리
  - `run_ai()`: 수동 조작이므로 구현 없음

### 3. SmartRunner
- AI 도망자
- 특징
  - 추격자 반대 방향으로 이동
  - 랜덤 회전 포함 (예측 불가 움직임)
  - 벽에 가까우면 방향 전환

## 사용 방법
1. 프로그램 실행
2. 추격자(빨간색 거북이)를 WASD 키로 이동
   - W: 위로 이동
   - S: 아래로 이동
   - A: 왼쪽 이동
   - D: 오른쪽 이동
3. 도망자(파란색 거북이)를 잡으면 +10점
4. 제한 시간이 끝나면 점수 0점
5. 게임 종료 시 "Game Over!" 메시지 출력

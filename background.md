# Background
 * 실시간으로 data 모으기
   * 
 * [커피 가루, 뜨거운 물] -> 커피 필터 -> 커피  (필터로 걸러지는 것은 커피 가루)
 * [센서로부터의 신호] -> Low-pass filter -> Low freq (필터로 걸리지는 것은 high freq)
 * [초기 가정, 측정 노이즈] -> kalman filter -> 원하는 상태 (필터로 걸리지는 것은 noise, 불확실성)

## 예제
 * 해저로봇
 * 압력, 온도, 조류
 * 과정
   * 초기 estimate
   * state prediction
   * Measurement update

## 역사
 * NASA
   * non-linear problem의 trajectory estimation
   * 아폴로 달 주변 경로
   * 정확해야하고 계산이 단순해야 (1960년대 온보드 컴퓨터)

## 응용
 * 엔지니어링 분야
   * 측정에 noise가 있는 시스템의 state를 estimation
 * 경제학
   * 특정 화폐의 환전 비율을 estimate
   * 경제의 부의 측정
 * 컴퓨터 비전
   * 물체 트래킹

## 3종류
 * kalman filter(linear)
 * extend kalman filter(non-linear)
   * robotic 분야
   * 실세계는 non-linear > linear
 * unscented kalam filter(아주 non-linear)

## Robotic 분야의 불확실성
 * 이상적인 상황
   * 정확히 10m 지점에 정지
 * 현실 상황
   * 지표면 상태, 바람, 바퀴 미끄러짐, ...
   * blind movement로 계속 진행하면 -> 시간이 지날수록 불확실성이 계속 쌓임
     * robot은 센서를 이용해서 매번 움직임을 측정하는 것이 필요함
     * 하지만 센서도 정확하지 않음
     * 센서를 이용하여 속도를 측정 (비싼 센서라면 정확도가 높겠지만 저렴한 센서의 경우 정확도가 떨어짐)
 * 100회 시도하는 경우
   * 10m 주변으로 지점에 정지
   * 가우시안의 모양

## kalman filter의 장점
 * 적은 센서의 데이터로 estimation이 가능
   * 초기 예측(initial guess)
   * 센서나 움직임의 예상한 불확실성을 고려
 * ex) GPS
   * 수 m의 정확도 
   * 정확도를 높이기 위해서는 센서 추가하기
 * 여러 센서들의 데이터를 종합하여 좀더 정확한 estimate -> 센서 퓨전
 * 

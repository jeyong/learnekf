
## 접근법
 * 1차원 -> 다차원
 * linear, non-linear
 * ROS에서 EKF 구현
 * 일반 filter를 Robotics에 적용
 * IMU로부터 센서 정보 수집
 * EKF ROS 패키지 -> robot의 pose를 estimate

## 실습 - ROS 패키지
 * turtlebot_gazebo : mobile robot
 * robot_pose_ekf : orientation 및 position을 estimation
 * odom_to_trajectory : 시간에 따라 생성된 odometry 값을 trajectory path로 
 * turtlebot_teleop : 키보드로 robot 조정
 * rviz : robot의 방향 및 estimated position을 시각화


## sensor fusion
 * robot에 장착된 센서들로부터 수집한 정보로 위치를 estimation
 * 센서 특징
   * noise
   * error
 * 3가지 센서
   * IMU 센서
   * rotar encoder
   * vision sensor
 * sensor fusion
   * 센서 중에 최소한 2개 이상을 사용

### IMU
 * 9 DOF
   * Gyroscope (3DOF)
   * Accelrometer (3DOF)
   * Magnetometer (3DOF)
 * 이슈
   * drift 발생

### Rotary Encoders
 * wheel의 속도와 position을 측정
 * robot의 position estimation
   * 속도를 적분
 * 이슈
   * 장애물 때문에 굴러가지 않는 경우
   * 미끄러운 바닥으로 인한 부정확하고 noise 측정

### Vision Sensor
 * RGB-D 카메라
   * image를 capture
   * 장애물 방향으로의 depth를 센싱하여 position으로 전환
 * x = f(camera depth)
 * 이슈
   * 빛에 따른 이미지 품질 차이
   * 짧은 거리 측정이 어렵다(RGB-D 스펙에 유의)

### EKF
 * 모든 noise 측정 값을 가지고 
 * noise를 필터링하고 불확실성을 제거하여
 * robot pose에 대한 good estimation을 제공

### EKF package
 * robot_pose_ekf
 * sensors -> robot_pose_ekf -> filter
 * [rotary encoder, imu, odometry] -> robot_pose_ekf -> estimated 3D pose(/robot_pose_ekf/odom_combined)

### odometry package
 * Odometry 값 -> odom_to_trajectory -> Trajectories
 * Rotary Encoders(/odom) 2D -> odom_to_trajectory -> Encoders Trajectory(/odompath)
 * Estimated 3D Pose(/robot_pose_ekf/odom_combined) -> odom_to_trajectory -> estimated 3D Pose Trajectory (/ekfpath)
## 1차원

## 다차원

## 순서
 * 배경지식
 * 왜 Filter가 필요한가?
 * 1차원 Kalman Filter
 * 다차원 kalman Filter
 * extended kalman filter
 
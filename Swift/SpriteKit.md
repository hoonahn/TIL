## Studies of iOS/SpriteKit using Swift
-
#### Example Game; Pierre Penguin Escape

-
#### 물리 시뮬레이션 역학
##### SpriteKit의 물리 시스템
##### 1. Physics Body
  - **dynamic** : 부피를 가지며, 모든 시스템의 힘과 충돌에 온전히 영향 받음. **게임의 대부분의 오브젝트**가 dynamic physics body 사용 가능.
  - **static** : 부피를 갖지만 움직이지 않음. 다른 오브젝트와의 충돌은 가능. 주로 **벽**이나 **정적인 장애물**에 static physics body 사용 가능.
  - **edge** : 부피를 갖지 않고, 이동시키지도 않음. 이 type은 움직임의 경계를 표시함; 다른 피직스 바디가 edge type를 지나치지 않음. **작은 봉쇄 구역**을 만들기 위해 edge type physics body를 겹쳐 배치 가능.

##### 2. Physical 속성
  - **Restriction** : 오브젝트가 다른 오브젝트와 충돌했을 때 상쇄되는 힘의 양을 조절. 이 속성은 오브젝트의 탄성을 변경시킴. (SpriteKit에서는 0.0 ~ 1.0 사이 값을 가짐. default : 0.2)
  - **Friction** : 오브젝트가 다른 오브젝트를 밀어내는 데 필요한 힘을 나타냄. (SpriteKit에서는 0.0 ~ 1.0 사이 값을 가짐. default : 0.2)
  - **Damping** : 오브젝트가 공간을 움직일 때 느려지는 속도. 기본적으로 공기 저항력. Linear Damping은 오브젝트의 속도가 얼마나 빨리 줄어드는지 결정하며, Angular Damping은 회전에 영향을 줌. (SpriteKit에서는 0.0 ~ 1.0 사이 값을 가짐. default : 0.1)
  - **Mass** (Kg) : 충돌하는 다른 오브젝트를 얼마나 밀어낼지 결정하고 이동하는 동안 운동량에 영향을 줌. 물리 엔진은 오브젝트의 부피와 질량을 통해 자동으로 밀도를 결정.
##### 3. Node를 움직이는 힘
  - **Impulse(충격)** : 즉각적, physics body의 속도를 한번에 변화시킴. 미사일, 총알, 앵그리버드 등의 발사체에 적합.
  - **Force(힘))** : 한 물리 계산 주기에 속도를 적용.매 프레임 이전에 적용. 로켓, 자동차 또는 자체 추진되는 모든 장치에 적합.
  - **수동 제어** : physics body의 velocity 속성이나 angularVelocity 속성을 직접 변경. 수동으로 속도 제한을 설정할 때 유용

  - - -

#### 컨트롤
#### 

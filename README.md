# capstone_design_1_2
## capstone_design_1
STU((Security camera Tracking system Using ultrasonic sensor) - 2개의 초음파 센서를 이용해 물체의 움직임을 탐지하고 모터를 제어해 카메라가 움직이는 물체를 추적하여 촬영할 수 있도록 보조하는 시스템)

사무실이나 집에서 사용하는 보안 카메라는 보통 고정된 CCTV이다. 고정식 CCTV는 특정 방향으로만 촬영할 수 있어 카메라에서 멀어지는 움직임을 촬영하기 어렵다. 보안성을 높이기 위해서는 동작 감지 카메라가 효과적이지만 비용이 많이 들기 때문에 사용하기가 어렵다. 따라서, 우리는 일반 카메라에 모션 추적 기능을 추가하고 초음파 센서를 사용하여 모션 감지 및 객체 추적을 통해 보안을 향상시키는 것을 목표로 한다.

이 시스템을 개발하기 위해 사용된 시스템은 윈도우 10이었고, 프로그래밍 언어로는 C 언어가 사용되었다. 이 시스템은 좌우 초음파 센서로 움직임을 감지하고, 두 센서 값의 차이와 변화에 따라 서보 모터를 움직여 물체를 추적한다. 시스템을 켜면 Wi-Fi 연결이 설정된다. 암호를 입력하고 보안 모드로 들어간 후 모드가 활성화되면 일정한 속도로 일정한 범위를 취하게 되고 움직임이 감지되면 물체를 추적하게 된다. 그리고 개체가 탐지되는 즉시 사용자에게 알림이 전송된다.

기존 동작 감지 카메라와 비교해 비용 측면에서 유리하고 접근성도 좋음을 추가함으로써 기존 카메라를 교체할 필요 없이 설치된 카메라에 'STU' Project를 적용하면 카메라의 촬영 반경을 넓히고 기존 cctv와 비교해 보안성을 높일 수 있다. 예를 들어 범죄자가 침입했을 때 범인을 추적해 신체정보 등을 파악할 수 있어 범인을 검거할 때 유용하게 활용할 수 있다. 이 시스템에 대해 추후 연구를 하면 더 많은 발전으로 이어질 수 있다고 생각한다.
## capstone_design_2
하루 평균 8시간, 오랜 시간 앉아 있어야 하는 현대인들은 잘못된 자세로 건강이 악화되고 있다. 다리 꼬기, 쪼그려 앉기 등 건강에 해로운 자세들은 척추나 골반 등 신체에 악영향을 끼친다. 이러한 현대인들에게는 잘못된 자세가 중증 질병의 근원이 되곤 한다. 그래서 우리는 현대인들의 잘못된 자세에 대한 피드백을 주어 평소 자세 습관을 자각시켜 주고 바른 자세를 유도하면 좋을 것 같다는 생각을 했다. 우리는 압력 센서를 기반으로 압력 분포에 따라 사용자의 바르지 못한 자세를 인지하여 알려줌으로써 바른 자세를 의식하도록 하는 서비스를 생각했다. 평소 본인의 바르지 못한 자세를 자각시켜 조금이라도 바른 자세로 앉게끔 유도하는 것을 목표로 삼았고, 때문에 자세 교정 방석이 아닌 바른 자세 방석이라는 명칭을 사용하였다.

자세 판단 기준 수립을 위해 ‘FSR 센서 어레이를 이용한 방석형 자세 판별 시스템의 구현’이라는 논문을 프로젝트에 참고하였다. 논문에서 압력 센서를 이용해 측정한 대표적인 착석 자세 5가지와 자세 판단 기준을 참고하였다. 그다음은 방금 논문의 내용인 자세 판단 알고리즘에서 바른 자세 및 앞, 뒤, 좌, 우 기울임 5가지 자세를 판단할 수 있었고 이를 기준 삼아 프로젝트를 진행하였다. 자세를 측정하는 하드웨어는 아두이노 우노와 FSR 센서로 구성했고 무선으로 사용하기 위해 건전지를 사용하였다. 그리고 센서로 검출된 데이터를 블루투스 모듈을 통해서 앱으로 전달하게 했다. 프로젝트에서 사용하는 계측 센서는 31개의 FSR 압력 센서로 구성되어 있으며, 착석 시 넓은 부위의 압력 분포를 측정하기 때문에 보다 정확한 착석 정보 검출이 용이하다는 특징이 있다. 

FSR 센서에 분포되어 있는 각각의 31개 압력 센서들은 압력 수치가 높을수록 더 진하게 색을 나타냈다. 바른 자세, 왼쪽과 오른쪽으로 기울인 자세, 그리고 앞으로 숙인 자세 및 뒤로 숙인 자세 5가지 자세 구별 가능하다. 구별 방식은 앞서 참고한 논문의 자세 판단 알고리즘을 이용하였고, 착석 데이터의 앞, 뒤, 좌, 우 압 력 분포의 비율이 모두 30% 미만일 경우 바른 자세로 구분하였고, 기울임 자세로 판단된 경우 앞, 뒤 비율의 합과 좌, 우 비율의 합을 비교하여 기울임의 방향을 구분하였다. //│ L │-│ R │>0 (왼쪽 압력센서 수치 값에서 오른쪽 압력 센서 수치 값을 뺀 값이 0보다 큼) 성립될 때 좌 기울임, 성립되지 않을 때 우 기울임, //│ F │-│ B │>0 (앞쪽 압력센서 수치 값에서 뒤쪽 압력 센서 수치 값을 뺀 값이 0보다 큼)이 성립될 때 앞 기울임, 성립되지 않을 때 뒤 기울임으로 판별하였다.

애플리케이션을 만들 때 안드로이드 스튜디오를 사용하였고, 앱 내의 내부 데이터베이스를 이용하여 통계 데이터를 사용하였다. 그리고 사용 언어로는 C, JAVA 등을 사용하였다. 사용자가 방석에 착석하면 아두이노 압력 센서가 압력의 세기를 측정한다. 아두이노와 앱은 블루투스로 통신하며 앱에는 실시간 압력 분포 및 측정된 데이터는 앞서 설명했던 논문 내용을 기준으로 5가지 자세로 구별된 실시간 자세, 통계 등이 표시되고 바르지 못한 자세로 앉았을 때 사용자에게 push 알림이 간다. 또한 데이터베이스에 아두이노 측정값 정보가 저장된다. 사용자가 바른 자세 방석을 의자 위에 올려놓은 뒤 앱을 실행하고 블루투스를 켜면 작동한다. 앱에서는 실시간 자세, 통계, 설정, 이용 방법, 메뉴가 있다. 실시간 자세 창에서는 실시간 압력 센서들의 압력 분포와 현재 자세 상태, 현재 자세 유지 시간 등이 표시된다. 통계 창에서는 그동안 사용자가 앉았던 자세 데이터를 통계화한 정보를 제공한다. 설정 창에서는 push 알림 기능 on/off와, push 알림 간격 설정, 데이터 삭제 등이 가능하다. 이용 방법 창에는 이용 방법을 설명해 준다. 바르지 못한 자세로 앉았을 경우 바른 자세로 앉으라는 push 알림이 온다.

기대 효과로 평소 자신의 앉은 자세를 파악할 수 있고 피드백을 통해 자세를 교정할 수 있고, 자세 데이터를 통해 현대인의 앉은 자세를 분석하는 기반이 될 수 있다. 그리고 의료 목적으로 데이터 수집 및 이용 가능하다.

## 수료증
- 호남정보보호지원센터 • 조선대학교에서 실시한 정보보호 실무인력 양성교육 "AI기반 악성코드 탐지기술 실습교육" 을 이수함.

20.07.31 (3시간)

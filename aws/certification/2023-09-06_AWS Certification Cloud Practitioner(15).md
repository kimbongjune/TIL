
### EC2 인스턴스 역할 데모

1. EC2 인스턴스에서 유저 조회하기

	SSH나 EC2 인스턴스 연결을 이용해 EC2 인스턴스에 접속하여 AWS 명령어를 입력한다.


	```bash
	aws iam list-users
	```


	![자격증명을 찾을수 없으니 “aws configure” 명령어를 입력하라는 오류가 발생한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb3c9a17-a284-4c31-b0b0-93cd446d2d0a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101706Z&X-Amz-Expires=3600&X-Amz-Signature=07657f82fe6f1e37560b2f79a4b03bda3ba0064250ee9f52bad7d3be79e51d8b&X-Amz-SignedHeaders=host&x-id=GetObject)


	※Amazon Linux에는 기본적으로 AWS 명령어가 설치되어있어서 위와 같은 aws 명령어 사용이 가능하다. 만약 다른 OS로 인스턴스를 실행하였다면 2-8을 참고하여 리눅스용 aws 명령어를 설치하여야 한다.

	- 이전 방법(2-9-2 참조)과 같이 “aws configure” 명령어를 이용하여 자격 증명, 액세스 ID, 비밀 액세스 키, 리전 등을 입력할 수 있겠지만 아주 좋지 안은 방법이다.
	- “aws configure” 명령어를 이용하여 EC2 인스턴스에 상세 개인정보를 입력하게 된다면 해당 계정 내의 누구라도 EC2 인스턴스에 접속하여 인스턴스에 입력된 자격 증명 정보를 탈취할 수 있기 때문이다.
	- 위와 같은 문제가 발생할 수 있으므로 IAM 역할을 이용하여 인스턴스에 역할을 부여 해주어야 한다.
2. EC2 인스턴스에 IAM 역할 부여하기

	![인스턴스 정보에서 확인할 수 있듯이 현재는 IAM 역할이 인스턴스에 부여되어있지 않다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a81edc7b-ff47-4d69-8bb5-3be16224fa40/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101707Z&X-Amz-Expires=3600&X-Amz-Signature=bcea81998968836570ad55df5ab63a7f38d6ee5710e59a204f6857814e374548&X-Amz-SignedHeaders=host&x-id=GetObject)


	![IAM 역할을 부여 할 인스턴스를 체크 후 “작업” → “보안” → “IAM 역할 수정” 을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7eb0dc8b-174c-4a71-9aa0-32ed9f3b4ea3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101707Z&X-Amz-Expires=3600&X-Amz-Signature=763d742d0fb119f28468d8fd777acd8c755abba050c4777eeaa25433a070e6ba&X-Amz-SignedHeaders=host&x-id=GetObject)


	![이전에 생성하였던 IAM 역할(DemoRoleForEC2)를 선택 후 “IAM 역할 업데이트” 버튼을 클릭한다.
	만약 계정변경 혹은 다른 사유로 인해 역할이 없다면 2-12를 참고하여 역할을 생성 후 진행하면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/88c74cc7-eddd-4943-97a8-c64ce56123be/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101707Z&X-Amz-Expires=3600&X-Amz-Signature=f14d83050a7eb0d5e91baee6d7abe545e9119b9dfbbf20fa3860ac9eedcf3444&X-Amz-SignedHeaders=host&x-id=GetObject)


	![인스턴스 정보에서 확인할 수 있듯이 현재는 IAM 역할이 인스턴스에 정상적으로 부여 되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/097c055d-71de-4964-9dd1-553682496471/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101707Z&X-Amz-Expires=3600&X-Amz-Signature=bd0a21117ad424e1061cd72609799a659e60695e8c47bdb939b81e594e47aa5f&X-Amz-SignedHeaders=host&x-id=GetObject)


	다시 EC2 인스턴스 연결 창으로 돌아가 동일한 명령을 수행한다.


	```bash
	aws iam list-users
	```


	![이전과 다르게 정상적으로 유저가 조회되는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/79375b71-e46f-488a-8eff-1df863fa9d0d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230906%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230906T101707Z&X-Amz-Expires=3600&X-Amz-Signature=f613a482e567fb1fcb5236515fc20d7d0325f1d92bfe1ea5a5ef193456cdb140&X-Amz-SignedHeaders=host&x-id=GetObject)


	위와 같은 동작이 가능한 이유는 “DemoRoleForEC2” 역할에 부여된 권한이 “IAMReadOnlyAccess” 권한이기 때문이다.


### EC2 인스턴스 구매 옵션

1. 간략 요약
	1. On-Demand Instances(주문형 인스턴스)
		- 요청에 따라 언제든 인스턴스를 생성할 수 있어 단기 워크로드에 적합하다.
		- 가격을 예측할 수 있고 초당 비용을 지불한다.
	2. Reserved(예약)
		- 1년 혹은 3년 기간으로 사용할 수 있어 장기 워크로드에 적합하다.
		1. Reserved Instances(예약형 인스턴스)
			- 인스턴스를 변경 없이 오랜 기간 사용하기로 했다면 적합하다.
		2. Convertible Reserved Instances(전환형 예약 인스턴스)
			- 유연성 있는 인스턴스가 필요한 경우(시간에 따라 인스턴스의 유형을 변경하려면) 적합하다.
	3. Saving Plans(사용량 약정)
		- 1년 혹은 3년 기간으로 사용할 수 있어 장기 워크로드에 적합하다.
		- 인스턴스 유형 약정이 아니라 특정 사용량을 약정한다.
	4. Spot Instances(입찰제 인스턴스)
		- 아주 짧은 단기 워크로드에 적합하다.
		- 가격이 매우 저렴하다.
		- 시장가가 높아지게 되면 인스턴스를 손실할 수 있어 신뢰성이 낮다.
	5. Dedicated Hosts(전용 호스트)
		- 물리적 서버 전체를 예약하여 인스턴스 배치를 제어할 수 있다.
	6. Dedicated Instances(전용 인스턴스)
		- 하드웨어를 공유하지 않고 사용하는 인스턴스이다.
	7. Capacity Reservations(용량 예약)
		- 특정한 AZ(가용영역)의 용량을 원하는 기간동안 예약할 수 있다.
2. 인스턴스 유형간 상세 정보
	1. On-Demand Instances(주문형 인스턴스)
		- 사용 한 만큼 지불한다(Pay for what you use)
			- Linux나 Windows를 사용한다면 첫 1분이 지난 후부터 초당 비용이 청구되며 다른 OS를 사용한다면 시간당 비용이 청구된다.
		- 인스턴스 유형중 가격이 제일 높으나 선결제가 없으며 장기 약정도 필요하지 않다.
		- 사용 유형
			- 연속적인 단기 워크로드(애플리케이션 동작을 예측할 수 없는 워크로드)
	2. Reserved Instances(예약형 인스턴스)
		- 온디맨드에 비해 비용을 약 72% 절약할 수 있다.
		- 특정 인스턴스 속성을 예약한다.(인스턴스 유형, 리전, 테넌시, OS 등)
		- 예약 기간으로 1년 OR 3년을 지정할 수 있으며 3년을 선택 할 경우 할인율이 더 높아진다.
		- 전체 선결제나 부분 선결제도 가능하며, 선결제 없이도 할 수 있으며 전체 선결제 를 선택 할 경우 할인율이 가장 높다.
		- 특정 리전으로 범위를 지정하거나 특정 AZ(가용 영역)의 용량을 예약하도록 영역을 지정할 수 있다.
		- 사용 유형
			- 안정적인 워크로드(애플리케이션이 안정된 상태로 사용되는 ex) 데이터베이스 등)
		- 마켓 플레이스에서 예약 인스턴스를 구매하거나 판매할 수 있다.
	3. Convertible Reserved Instances(전환형 예약 인스턴스)
		- 특별한 유형의 예약 인스턴스이다.
		- 인스턴스 유형을 변경할 수 있고 인스턴스 제품군과 OS, 범위, 테넌시 등이 변경 가능하다.
		- 유연성이 높아 할인율은 줄어든다(온디맨드에 비해 66% 수준)
	4. Saving Plans(사용량 약정)
		- 장기 사용량에 따라 할인을 적용받을 수 있으며 온디맨드에 비해 비용을 약 72% 절약할 수 있다.
		- 시간당 10$의 비용을 1년 OR 3년동안 약정한다.
		- 초과하는 사용량은 온디맨드 가격으로 청구된다.
		- 특정 인스턴스 제품군과 리전에 한해 사용할 수 있다.
		- 인스턴스 크기에 구애받지 않으므로 .xlarge 인스턴스 사용이 가능하다.
		- OS의 경우 Windows와 Linux간 전환이 가능하다.
		- 테넌시의 경우 호스트, 전용 및 기본값을 전환할 수 있다.
	5. Spot Instances(입찰제 인스턴스)
		- 가장 파격적인 할인을 제공한다.(온디맨드에 비해 비용을 약 90% 절약할 수 있다.)
		- 언제든 인스턴스가 중지될 수 있어 신뢰성이 낮다.(스팟 인스턴스에 지불하고자 하는 가격보다 스팟 가격이 높으면 인스턴스가 중단된다.)
		- AWS에서 가장 비용 효율적인 인스턴스이다.
		- 사용 유형
			- 서비스가 중단되어도 복구하기 쉬운 워크로드에 적합하다.
			- ex)배치작업, 데이터분석, 이미지처리, 분산 워크로드 등
		- 중요한 작업이나 데이터베이스에는 적합하지 않다.
	6. Dedicated Hosts(전용 호스트)
		- 사용 사례에 맞춘 EC2인스턴스 용량을 가진 물리적 서버이다.
		- 사용 유형
			- 규정 준수 요구사항이 있는 경우
			- 기존의 서버 결합 소프트웨어 라이선스를 사용해야 하는 경우(라이선스 비용은 사용 소켓, 코어, VM 소프트웨어 라이선스 당 청구된다.)
		- 온디맨드 형식으로 초당 청구되거나 1년 OR 3년 기간을 예약할 수 있다.
		- 실제 물리적인 서버를 예약하기 때문에 AWS에서 가장 비싼 유형의 인스턴스이다.
	7. Dedicated Instances(전용 인스턴스)
		- 전용 하드웨어에서 실행되는 인스턴스이며 물리적인 서버와는 다르다.
		- 같은 계정의 다른 인스턴스와 하드웨어 공유도 가능하다.
		- 인스턴스 배치는 제어할 수 없다.
	8. Capacity Reservations(용량 예약)
		- 원하는 기간 동안 특정한 AZ(가용 영역)에 온디맨드 인스턴스를 예약한다.
		- 필요할 때 마다 용량에 액세스 할 수 있다.
		- 시간 약정이 없기 때문에 언제든지 용량을 예약하거나 취소할 수 있다.
		- 요금할인은 없다.
		- 요금을 할인받기 위해선 예약인스턴스 혹은 사용량 약정과 결합 해야한다.
		- 인스턴스 실행 여부와 관계 없이 온디맨드 요금이 청구된다.
		- 사용 유형
			- 특정한 AZ(가용 영역)에 존재하는 단기적인 연속적 워크로드에 적합하다.

### EC2 인스턴스를 위한 공동책임 모델

- EC2 서비스에 AWS가 가지는 책임, 사용자가 가지는 책임을 명확하게 구분하여아 한다.
- AWS
	- 모든 데이터 센터와 인프라에 관한 보안 책임(global network security)
	- 사용자가 물리적 호스트와 분리된 상태인지 확인하는 책임(Isolation on physical hosts)
	- 서버 장애로 인한 하드웨어 교체(Replacing faulty hardware)
	- 책임사항 준수(Compliance validation)
- 사용자의 책임
	- 클라우드 내의 보안
	- 보안그룹 규칙
	- OS 패치 및 업데이트
	- EC2 인스턴스에 설치되는 모든 소프트웨어 및 유틸리티에 대한 책임
	- IAM 역할의 할당 방법 이해와 올바른 권한 부여에 대한 책임
	- 인스턴스 내의 데이터가 안전한지 확인하는 책임

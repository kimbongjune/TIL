
### AWS 예산 설정

1. 예산 설정하기

	우선 예산을 설정하기 위해 결제 대시보드로 이동하여야 한다.


	![본인 계정을 클릭 후 “결제 대시보드”를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9dda2f25-b5ab-42b5-9e14-d3fd44e1bb00/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080016Z&X-Amz-Expires=3600&X-Amz-Signature=505d0d9f51435ba85bf4859603606f49c55b32577a8eca550e0261d00cfc8a32&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Budgets” 탭을 클릭한 후 “예산 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ddf4b143-137d-441d-bd4e-0a3114a2e799/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080016Z&X-Amz-Expires=3600&X-Amz-Signature=00ff758d42f86014811e5b2fad36556a19326312021a8c5906b0883ec13a2f0e&X-Amz-SignedHeaders=host&x-id=GetObject)


	![기본 옵션을 사용할 것이기 때문에 “템플릿 사용(단순)” 체크, “제로 지출 예산” 체크 후 본인의 사용 할 규칙의 이름을 기재 후 예산이 발생했을 때 알림을 받을 이메일을 작성 후 “예산 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a72a0b0-5731-417d-a3d7-874bfc3a2bbb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080016Z&X-Amz-Expires=3600&X-Amz-Signature=9b134cfab0a1d701caceced26793042b7b3dd12f3929a62c9a82d8cd7e9df420&X-Amz-SignedHeaders=host&x-id=GetObject)


### EC2 기초

1. Amazon EC2란?
	- 아마존에서 가장 인기있는 서비스이다.
	- Elastic Compute Cloud의 약자로 AWS에서 제공하는 서비스형 인프라 이다(IaaS)
	- EC2는 하나의 서비스가 아니며 높은 수준에서 많은 서비스를 포함하고 있다.
		- EC2 인스턴스 : 가상머신을 EC2에서 임대하여 사용할 수 있다.
		- EBS : Elastic Bloc Store의 약자로 EC2의 데이터저장소(가상 드라이버) 이다.
		- ELB : Elastic Load Balancer의 약자로 로드밸런서 역할을 수행한다.
		- ASG : Auto Scailing Group의 약자로 수직, 수평으로 EC2 를 확장한다.
2. EC2에서 선택할 수 있는 항목
	1. OS(Operation System) - 운영체제
		- Linux
		- Windows
		- MacOS
	2. 컴퓨팅 성능과 CPU 코어 개수
	3. RAM 용량
	4. 스토리지
		- HDD
		- SSD
		- NAS
	5. 네트워크
		- 속도
		- 공인아이피
	6. 보안
		- 방화벽
	7. 부트스트랩 스크립트
		- EC2 User Data

EC2 사용자 데이터로 EC2 인스턴스 생성하기

1. EC2 인스턴스 실행하기

	![EC2 서비스로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/06687dae-8d4a-4c5d-9945-77cd297e6850/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=f8e69defb4a3e8ba2a067349ac18cb42db97331914a05cf0757e76ff7dcd672b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“인스턴스” 탭으로 이동하여 “인스턴스 시작” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/176630d3-3f4c-43ca-8a70-46bdbd2cd4c8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=eb58cb6d297b438487c3ba0f42233b4784db98a42aa02c1ca5947aa3bc6bc769&X-Amz-SignedHeaders=host&x-id=GetObject)


	
인스턴스 이름 및 OS 선택


	![서버 이름을 작성 후 OS는 “Amazon Linux” 를 선택한 후 이미지는 “Amazon Linux 2 AMI….” 을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/762f6ed1-1270-45b2-aa4a-6c69fa433c6e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=d55772faebf439ab835a13d02c56c31e37539ebdacf9d5fe35ffd74baaa282b0&X-Amz-SignedHeaders=host&x-id=GetObject)


	OS 아키텍쳐와 인스턴스 유형 선택


	![아키텍처는 “64비트(x86)” 을 선택한 후 인스턴스 유형은 프리티어 사용이 가능한 “t2.micro”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e8e7d0e-6f90-4cd4-b367-81fdf899a10b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=5db8b7f791430312023d5cd8d1c511a3ffad556b326d8261846518e6e2c16d1a&X-Amz-SignedHeaders=host&x-id=GetObject)


	SSH 키페어 생성


	![SSH 접속을 위해 “새 키 페어 선택” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f516e063-4dd7-46c0-b436-808363ce91c9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=42e4a7b7f838e9578386cad0b1e51ba0bb9c80050514950fdd54a637deddbcfb&X-Amz-SignedHeaders=host&x-id=GetObject)


	![사용 할 키 페어 이름을 입력 후 키 페어 유형은 “RSA”로 선택한다. 만약 사용중인 OS가 Linux, MacOS, Windows 10 이상이라면 프라이빗 키 파일 형식은 “.pem”을 선택하고, Windows 10 미만 이라면 “.ppk”를 선택 후 “키 페어 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/15ab8bdc-a692-4371-a3d6-463bfded1af2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=119985b0b6f754bccf518b7b5b19c952efb21717c15c202b8039033d74c8762a&X-Amz-SignedHeaders=host&x-id=GetObject)


	네트워크 설정


	![네트워크 설정에서는 EC2 인스턴스에 사용할 방화벽을 설정하게 된다. 여기선 SSH접속을 위하여 “에서 SSH 트래픽 허용” 을 체크 후, 웹페이지를 구동할 것이기 때문에 “인터넷에서 HTTP 트래픽 허용” 을 체크한다. 위와같이 설정하게 된다면 방화벽 규칙 즉, 보안그룹은 launch-wizard-1이라는 이름으로 생성된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb43fcc7-ec06-48d1-b551-da9139cc5059/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=11297039e927546986215c226cf37c7847f9513051c0dc8c1a2a4f6d0894316b&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지 구성


	![스토리지는 기본값인 8Gb에 gp2 루트 볼륨을 사용한다. EC2인스턴스에 할당되는 루트볼륨은 기본값으로 EC2 인스턴스가 종료되면 삭제된다. 이를 확인하기 위해 “어스밴스드”를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7142440a-fe67-47d6-b7b6-52a644623d47/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=0b79a9e86180e138c5c21943dc21bac46bf1db54d16bfebef98b5ade00f1dac9&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지 구성(고급)


	![볼륨 옆의 화살표를 클릭하게 되면 위와 같은 화면이 표시되는데, “종료 시 삭제” 의 값은 “예” 가 기본값인 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0627d8ca-dad0-4b80-a0c5-77078b47fffb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=0172daeb221ab65cebdbcca31c89dd14298e3eb998e556414c7dbe6bae3dbbb5&X-Amz-SignedHeaders=host&x-id=GetObject)


	고급 세부 정보


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/523c9dc5-af54-4553-aa0b-94940dfbe768/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=6cc3ac8937911d2723e2a812c0c398269bf7a24887e731d5051ac63708b97f4e&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/03334987-bb2b-4e6f-9c90-475f5671ce9e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=92c799f6e27b3142049f5c5f124dfa2793c7ccaae0508418965e6ef45cc2edc2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fa689dba-51d9-466a-9db5-5dd605d1569d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=817852744e85dd16d95cf3ca5f3cc085d017f1ee2705412a52f1543b0196dfda&X-Amz-SignedHeaders=host&x-id=GetObject)


	![나머지 옵션은 별도 설정하지 않으며, 사용자 데이터 입력 필드에 하단의 코드를 복사하여 붙여넣는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d19853fa-d8b4-409f-aeaa-6ddeb38cc0e5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=6628b83638898dbded49d48166e892e73830ebe2aa74c502f6cd2bd258157802&X-Amz-SignedHeaders=host&x-id=GetObject)


	```bash
	#!/bin/bash
	# Use this for your user data (script from top to bottom)
	# install httpd (Linux 2 version)
	#패키지 업데이트
	yum update -y
	#아파치 웹서버 설치
	yum install -y httpd
	#아파치 웹서버 실행
	systemctl start httpd
	#부팅시 아파치 웹서버 자동 실행
	systemctl enable httpd
	#간단한 html을 아파치 루트 디렉토리에 생성
	echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
	```


	※사용자 데이터 : 인스턴스를 최초 실행 시 사용자 데이터 스크립트를 이용하여 인스턴스를 부트스트래핑 할 수 있다. 인스턴스 수명 주기중 단 한번만 실행된다.


	인스턴스 생성 및 전체 설정 화면


	![설정을 확인 후 “인스턴스 시작” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0199a5fa-3872-4da9-83af-6b45b4271707/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=966042521d158f86e1c399a0b29b58403af7d8d13570a859dc429e2dbfc12ccc&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“모든 인스턴스 보기” 버튼을 클릭하여 인스턴스 목록으로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8327f6c7-1374-41b8-8fc5-6e22f8df0f7a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080019Z&X-Amz-Expires=3600&X-Amz-Signature=53b8d7d56a91e1987957cf68eadea4030d0928923aff1e51a647b11ffc72a245&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 인스턴스 살펴보기

	![위 체크박스를 체크하면 아래와 같은 개요 창이 펼쳐진다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a53c7c84-2d81-4342-98ca-08b505605efa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=3444265b66d7340bb8bd63582e3b1c399186e661c64b65f5094a94159afa3917&X-Amz-SignedHeaders=host&x-id=GetObject)


	세부정보


	![인스턴스의 고유 아이디와, public ip, AWS 내부에서 사용 할 private ip와 현재 인스턴스의 실행상태, OS 종류, SSH key pair 등의 정보를 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4577dc28-f529-43b5-9f16-ca56db72cdaf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=723379d28a51de5a093d0b4fc9292aded0c55ec8b0da7982a20fd1d93ee2a140&X-Amz-SignedHeaders=host&x-id=GetObject)


	보안


	![생성한 보안그룹 “launch-wizard-1” 에서 설정 한 내용대로 SSH 접속을 위한 22번포트와 http 접속을 위한 80번 포트가 인바운드 규칙으로 생성되었고, 인터넷 접속을 위한 아웃바운드 규칙이 적용된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/77f222b5-2b6a-4e46-9df6-8ec5ef521706/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=49fd907302985cb0a3fc4b8f6d1d52f248e0869fa77ba4f33127dfcc7445f188&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지


	![스토리지는 8GB가 정상적으로 적용되어있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5f992db4-2a0f-406a-bdde-dd3ea8c46944/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=fa0910ab15ed84642520baff44ea7bf23c33a8db20d63cb8d91d49defc14d227&X-Amz-SignedHeaders=host&x-id=GetObject)


	웹페이지 열기


	![현재 인스턴스에 할당 된 public ip를 복사하여 웹 브라우저에 붙여넣기 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5c9c0968-ce88-4cd8-9649-77e5317b4c89/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=9ed894c30a2eda1e64d78a196327ba50487f8d6166d328456cc2ebf9b5c2f66b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 웹페이지가 동작하는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc452183-d2d3-4067-bb69-1bbf73064657/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=74c4be96985044c99831651d9ddeb9caa60e813a8b280dfaa07f10a8a2db2067&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 정지하기


	![“인스턴스 상태” 탭에서 “인스턴스 중지” 를 클릭한다.
	클라우드 내에선 언제든지 서버를 실행하고 종료할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/01885a34-0260-4485-a1e3-f9f76864aa35/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=b245932d5ee6a9455bb9c9e4a1e17fff86a76a84342bc7e6c3ad20e28566bd9a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![인스턴스가 중지 되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/242d7b04-ae37-4c5d-9671-4d7363afb1be/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=2c0650da66624e68b44935fa082e2b5acd67e311dd8f0e2fdfa8e68a2ed27bda&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 재시작 하기


	![“인스턴스 상태” 탭에서 “인스턴스 시작” 을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80d04714-4c1f-48d9-a3e7-3061e7e81580/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=f08e24862d28bc94986c9f78c4edb02ae8af0f8da6d289156a1271793ffb4e79&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 종료 시 주의사항


	![인스턴스를 종료 후 재시작시 public ip가 이전과 다른 것을 확인할 수 있다.
	AWS가 public ip를 바꿀 수도 있다는 의미이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b63f796b-ad47-4443-81e4-a9719878fdfa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080020Z&X-Amz-Expires=3600&X-Amz-Signature=8a7f9e41353dd68059b06fb685072e0a2b8ff0dcc4f205af6e96f466d35410a1&X-Amz-SignedHeaders=host&x-id=GetObject)


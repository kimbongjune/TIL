
### AWS 예산 설정

1. 예산 설정하기

	우선 예산을 설정하기 위해 결제 대시보드로 이동하여야 한다.


	![본인 계정을 클릭 후 “결제 대시보드”를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9dda2f25-b5ab-42b5-9e14-d3fd44e1bb00/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080808Z&X-Amz-Expires=3600&X-Amz-Signature=ae8c9caa9e7391302da55b7924a338b58b889f50eae76a3b6584972933fca47e&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Budgets” 탭을 클릭한 후 “예산 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ddf4b143-137d-441d-bd4e-0a3114a2e799/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080809Z&X-Amz-Expires=3600&X-Amz-Signature=2c54a953e644ef966544c97c5f0c2fe23e535c7d3e4923e627e5b0da10a8cb00&X-Amz-SignedHeaders=host&x-id=GetObject)


	![기본 옵션을 사용할 것이기 때문에 “템플릿 사용(단순)” 체크, “제로 지출 예산” 체크 후 본인의 사용 할 규칙의 이름을 기재 후 예산이 발생했을 때 알림을 받을 이메일을 작성 후 “예산 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a72a0b0-5731-417d-a3d7-874bfc3a2bbb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080809Z&X-Amz-Expires=3600&X-Amz-Signature=dd7e3552c72bbb0fa6820e35b73b1ba43327ccff4872a28f6c4aff8a70bdb164&X-Amz-SignedHeaders=host&x-id=GetObject)


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

	![EC2 서비스로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/06687dae-8d4a-4c5d-9945-77cd297e6850/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=f7b6ef110f0bb0b00fae7508d858911f02baba68456b82a570d4900a5c34bcf8&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“인스턴스” 탭으로 이동하여 “인스턴스 시작” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/176630d3-3f4c-43ca-8a70-46bdbd2cd4c8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=24b88c3a28c415675d90ad11220438b23361aaa524560b1753ccd6dd2cafade8&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 이름 및 OS 선택


	![서버 이름을 작성 후 OS는 “Amazon Linux” 를 선택한 후 이미지는 “Amazon Linux 2 AMI….” 을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/762f6ed1-1270-45b2-aa4a-6c69fa433c6e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=57c86132dd9cf82531dad278773f3410ec6173e12d899f87890f63014bf938b2&X-Amz-SignedHeaders=host&x-id=GetObject)


	OS 아키텍쳐와 인스턴스 유형 선택


	![아키텍처는 “64비트(x86)” 을 선택한 후 인스턴스 유형은 프리티어 사용이 가능한 “t2.micro”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e8e7d0e-6f90-4cd4-b367-81fdf899a10b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=19665b86fcb6fc70d14dfab8c9918acf1bcfe1efd08c24ab0558d0a69be38f5c&X-Amz-SignedHeaders=host&x-id=GetObject)


	SSH 키페어 생성


	![SSH 접속을 위해 “새 키 페어 선택” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f516e063-4dd7-46c0-b436-808363ce91c9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=c06a75109f97be7762f539d271a7bb3b1b2eed2e8f1b8ee28dffb1c6972b7e71&X-Amz-SignedHeaders=host&x-id=GetObject)


	![사용 할 키 페어 이름을 입력 후 키 페어 유형은 “RSA”로 선택한다. 만약 사용중인 OS가 Linux, MacOS, Windows 10 이상이라면 프라이빗 키 파일 형식은 “.pem”을 선택하고, Windows 10 미만 이라면 “.ppk”를 선택 후 “키 페어 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/15ab8bdc-a692-4371-a3d6-463bfded1af2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=c78449f098904111ef8e64355afc072d65b29af282fab960d8c4f8452eab5991&X-Amz-SignedHeaders=host&x-id=GetObject)


	네트워크 설정


	![네트워크 설정에서는 EC2 인스턴스에 사용할 방화벽을 설정하게 된다. 여기선 SSH접속을 위하여 “에서 SSH 트래픽 허용” 을 체크 후, 웹페이지를 구동할 것이기 때문에 “인터넷에서 HTTP 트래픽 허용” 을 체크한다. 위와같이 설정하게 된다면 방화벽 규칙 즉, 보안그룹은 launch-wizard-1이라는 이름으로 생성된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb43fcc7-ec06-48d1-b551-da9139cc5059/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=784389fe04bf49c1a1ab2d80e6905fb26136fb2c449c9e93420c90926acdaf68&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지 구성


	![스토리지는 기본값인 8Gb에 gp2 루트 볼륨을 사용한다. EC2인스턴스에 할당되는 루트볼륨은 기본값으로 EC2 인스턴스가 종료되면 삭제된다. 이를 확인하기 위해 “어스밴스드”를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7142440a-fe67-47d6-b7b6-52a644623d47/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=bd09ab7c236fca9eab19c330997bcddbfca4eb6aa647cea8434bc896d97fa6e0&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지 구성(고급)


	![볼륨 옆의 화살표를 클릭하게 되면 위와 같은 화면이 표시되는데, “종료 시 삭제” 의 값은 “예” 가 기본값인 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0627d8ca-dad0-4b80-a0c5-77078b47fffb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=ce734234bfbbd340e4c9704764d7b7c1163534422e2a9e88b9847a1147fb6fcf&X-Amz-SignedHeaders=host&x-id=GetObject)


	고급 세부 정보


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/523c9dc5-af54-4553-aa0b-94940dfbe768/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=81332244e622821dd3cf5d139491bb737e1ab69c2dff12e39b6217bd24ec5cad&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/03334987-bb2b-4e6f-9c90-475f5671ce9e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=5e89769845d1ca2aa0ed3b71d2462d541fd2ca54ccda943555f5505e7b1d9a6d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fa689dba-51d9-466a-9db5-5dd605d1569d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=479c946509c2efb84fb3c5c5cfbd009f135f752a047f5feb8ac8067f1d933644&X-Amz-SignedHeaders=host&x-id=GetObject)


	![나머지 옵션은 별도 설정하지 않으며, 사용자 데이터 입력 필드에 하단의 코드를 복사하여 붙여넣는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d19853fa-d8b4-409f-aeaa-6ddeb38cc0e5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=a36ec80d4898a31b91855f6f822719cc56dd241916c2ef802080fafe0a8f48cd&X-Amz-SignedHeaders=host&x-id=GetObject)


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


	![설정을 확인 후 “인스턴스 시작” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0199a5fa-3872-4da9-83af-6b45b4271707/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=0967aa2159f11978f40a301270544f41957d7febbaac5627cdd422bd63e3a025&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“모든 인스턴스 보기” 버튼을 클릭하여 인스턴스 목록으로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8327f6c7-1374-41b8-8fc5-6e22f8df0f7a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=a012f95213c5403766d7665c9f15d993674cb59b022e1232e526862f4cebed5f&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 인스턴스 살펴보기

	![위 체크박스를 체크하면 아래와 같은 개요 창이 펼쳐진다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a53c7c84-2d81-4342-98ca-08b505605efa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=a46e6f4eb2aad16f533a4bedc8d2b8081ccba031b9ab0896919a9683473eeedc&X-Amz-SignedHeaders=host&x-id=GetObject)


	세부정보


	![인스턴스의 고유 아이디와, public ip, AWS 내부에서 사용 할 private ip와 현재 인스턴스의 실행상태, OS 종류, SSH key pair 등의 정보를 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4577dc28-f529-43b5-9f16-ca56db72cdaf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=e645496945acf30bbea014795803d3711bba4ebdf06f28cbac021435079ad920&X-Amz-SignedHeaders=host&x-id=GetObject)


	보안


	![생성한 보안그룹 “launch-wizard-1” 에서 설정 한 내용대로 SSH 접속을 위한 22번포트와 http 접속을 위한 80번 포트가 인바운드 규칙으로 생성되었고, 인터넷 접속을 위한 아웃바운드 규칙이 적용된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/77f222b5-2b6a-4e46-9df6-8ec5ef521706/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=bc3abfa399b7ab434ab050b9d4c34c676b5cf7039f5b57a935c6993bd48aa040&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지


	![스토리지는 8GB가 정상적으로 적용되어있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5f992db4-2a0f-406a-bdde-dd3ea8c46944/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=3a70343573832fbe9bdedc8b14c5b340ec090027bea25d340031fc52b074098b&X-Amz-SignedHeaders=host&x-id=GetObject)


	웹페이지 열기


	![현재 인스턴스에 할당 된 public ip를 복사하여 웹 브라우저에 붙여넣기 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5c9c0968-ce88-4cd8-9649-77e5317b4c89/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=c7ca4fa98409b6b462a8b29357d43a1a3fba3f404031ed0432826fbd4945107c&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 웹페이지가 동작하는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc452183-d2d3-4067-bb69-1bbf73064657/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=f9fe254ea6356eb69cbbeba300c789fe8554d0f714efedd33200a6469d97eebc&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 정지하기


	![“인스턴스 상태” 탭에서 “인스턴스 중지” 를 클릭한다.
	클라우드 내에선 언제든지 서버를 실행하고 종료할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/01885a34-0260-4485-a1e3-f9f76864aa35/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=f2954f37802e23080d6374ba87d3a397632126d74e4b190cd3fe9d5a67ca05fc&X-Amz-SignedHeaders=host&x-id=GetObject)


	![인스턴스가 중지 되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/242d7b04-ae37-4c5d-9671-4d7363afb1be/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=bab97280f601f7a5d51927ece01acf374b2b8ca44797d63117c12bd23040c277&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 재시작 하기


	![“인스턴스 상태” 탭에서 “인스턴스 시작” 을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80d04714-4c1f-48d9-a3e7-3061e7e81580/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=0d79be7fe20cea959e523b6ff64ea5aae092f119154778a34816736e3e10b2f0&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 종료 시 주의사항


	![인스턴스를 종료 후 재시작시 public ip가 이전과 다른 것을 확인할 수 있다.
	AWS가 public ip를 바꿀 수도 있다는 의미이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b63f796b-ad47-4443-81e4-a9719878fdfa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230903%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230903T080812Z&X-Amz-Expires=3600&X-Amz-Signature=a87ca6cc6e2bcce26dd5fd99ff4650c2ad5794fa17bd156b3bd38041bc60f7e5&X-Amz-SignedHeaders=host&x-id=GetObject)


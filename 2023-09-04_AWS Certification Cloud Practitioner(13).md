
### EC2 인스턴스 유형 기본사항

1. EC2 인스턴스 타입
	1. 범용 인스턴스(General Purpose)
		- 웹서버나 코드 저장소와 같은 다양한 작업에 적합하다.
		- 컴퓨팅, 메모리 ,네트워킹 간 균형이 적절하게 분배되어있다.
	2. 컴퓨팅 최적화 인스턴스(Compute Optimized)
		- 컴퓨팅 집약적 작업에 최적화된 인스턴스
		- 일부 데이터의 일괄처리, 미디어 트랜스코딩, 고성능 웹서버 HPC(High performance computing) - 고성능 컴퓨팅, 머신러닝, 전용 게임서버 등 작업에 적합하다.

	c. 메모리 최적화 인스턴스(Memory Optimized)

		- 메모리에서 대규모 데이터셋을 처리하는 유형의 작업에 빠른성능을 제공
		- 고성능 인메모리 데이터베이스, 캐시 스토리지, 대규모 비정형 데이터의 실시간 처리를 실행하는 애플리케이션에 적합

	d. 스토리지 최적화 인스턴스(Storage Optimized)

		- 로컬 스토리지에서 대규모의 데이터셋에 액세스할 때 적합하다.
		- 고주파 온라인 트랜잭션 처리(OLTP), 데이터베이스, 캐시 데이터베이스, 데이터 웨어하우스, 분산 파일 시스템 등에 적합하다.

### 보안 그룹 및 클래식 포트 개요

1. 보안 그룹
	- 보안 그룹은 AWS 클라우드에서 네트워크 보안을 실행하는데 핵심이 된다.
	- EC2 인스턴스에 들어오고 나가는 트래픽을 제어한다.
	- 허용 규칙만 포함하면 된다.
	- IP 주소를 참조해 규칙을 만들 수 있다.
	- EC2 인스턴스의 방화벽이다.
	- 포트 액세스를 통제하며 인증된 IP 주소의 범위를 확인하여 제어한다.
	- 인바운드 및 아웃바운드 네트워크를 통제한다.
2. 보안 그룹 다이어그램

	![허용된 ip에서의 접속은 허용되지만 허용되지 않은 ip의 접속은 차단한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/018d0108-6383-4c2e-b83f-06f7674d4a73/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101028Z&X-Amz-Expires=3600&X-Amz-Signature=4e2fecaa4745c6735a3518f8fec3a965f9ab008c75b8b0edaaeae56c14644bcf&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 보안 그룹에 대해 알아야 할 사항
	- 여러 인스턴스에 연결할 수 있다.(보안 그룹와 인스턴스간 1:1 관계는 존재하지 않는다.)
	- 지역과 vpc 결합으로 통제되어있다. (지역을 이동하게 되면 새 보안그룹을 생성하거나 다른 vpc를 생성해야 한다.)
	- 보안그룹은 EC2 외부에 존재한다. (트래픽이 차단되면 EC2 인스턴스는 확인할 수 없다)
	- time out 에러의 원인은 잘못 된 보안 그룹 설정에 있으며, connection refused 에러는 대부분 어플리케이션 내에서 발생한 에러이다.
4. 포트 정보
	- 22번 : SSH(Secure Shell)로 원격 접속 시 사용된다.(Linux)
	- 21번 : .FTP(File Transfer Protocol)로 파일 공유시스템에 파일을 업로드 및 다운로드 할 때 사용된다.
	- 22번 : SFTP(Secure File Transfer Protocol)로 FTP에 보안 기능을 접목하였다. SSH와 동일하게 22번 포트인 이유는 SFTP 내부적으로 SSH를 사용하기 때문이다.
	- 80번 : HTTP로 인터넷 연결 시 사용된다.
	- 443번 : HTTPS로 인터넷 보안 연결 시 사요오딘다.
	- 3389 : RDP(Remote Desktop Protocol)로 원격 데스크톱 연결 시 사용된다.(Windows)

### 보안 그룹 실습

1. 보안 그룹 살펴보기

	![“네트워크 및 보안” 탭의 “보안 그룹”을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/29621859-799e-4284-be0b-b23aeb45e72e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=8dc26bc186afee3b3737c04d7b58411859f3b9731b555ece606f2e12d0d3dcc1&X-Amz-SignedHeaders=host&x-id=GetObject)


	세부정보


	![두개의 보안그룹이 존재하는 것을 확인할 수 있다. “default”는 기본적으로 생성되는 보안 그룹이며, “launch-wizard-1”은 EC2인스턴스 생성 시 생성한 보안 그룹이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/207ad392-840a-4351-a81e-995341643307/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=4eafc6191decc4dbd0b82389e3913ea47ce385234543724a07ea2bea414c4031&X-Amz-SignedHeaders=host&x-id=GetObject)


	인바운드 규칙


	![인바운드 규칙은 외부에서 EC2 인스턴스 내부로 들어오는 연결을 위해 사용되는 규칙이다.
	첫번째 규칙은 22번 포트(SSH)이며 두번째 규칙은 80포트 (HTTP) 이다. “인바운드 규칙 편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b4cd9022-f78c-4887-8b7c-80b41864c051/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=8afde1b5a934232c1d61f3d90ece2d5f85795d7437f11a5f5e8c3bff3450bca9&X-Amz-SignedHeaders=host&x-id=GetObject)


	인바운드 규칙 편집


	![첫번째 규칙은 모든 IP를 허용하고 22번 포트로 들어오는 모든 접속을 허용 한다는 의미이며,
	두번째 규칙은 모든 IP를 허용하고 80번 포트로 들어오는 모든 접속을 허용 한다는 의미이다.
	이전에 80번 포트(웹서버)에 접속 되었던 것을 확인 해보았다. 보안 그룹이 정상적으로 동작하는지 확인하기 위해 80번 포트 규칙을 삭제 후 저장한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8c16b5e2-abf4-4fd5-a701-26c5972e9d49/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=e5b267958a52da01b8516631e6ef51d249ce48aa744b232bf92371d82a822645&X-Amz-SignedHeaders=host&x-id=GetObject)


	보안 그룹 검증


	![규칙이 정상적으로 삭제되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/13bd1b9e-ad50-4cd1-a4f8-c600447906d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=2f2368dfeee8d5c95b684abe92751052e415e61f336b0eb575a39c313d42941b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![웹서버에서 timeout 에러가 발생하였으며 접속되지 않는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/19365aa0-e156-4c4e-9938-7cf24967a951/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=8a88c42b613249249636b69dcd35dc92a5c115d5da5094d2c91a413f7c06c0b3&X-Amz-SignedHeaders=host&x-id=GetObject)


	인바운드 규칙 추가


	삭제한 80번 포트 규칙을 추가한다.


	![“인바운드 규칙 편집” 탭으로 다시 접속하여 “규칙 추가” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/067ba614-4a29-4044-89b2-dcd074e5517d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=662de86b3d607dfdece1de64dbb71cb096d7aa0f5cca418757141986e0d5cfb1&X-Amz-SignedHeaders=host&x-id=GetObject)


	![많이 사용되는 규칙은 기본값이 지정 되어있다. “HTTP”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b592b36c-5723-4646-80e3-4fed3bc94778/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=bb218c4829d391de809c8cbfcdc16f14baa03e2651cd07d45c7b93879a536c70&X-Amz-SignedHeaders=host&x-id=GetObject)


	![모든 IP를 허용하기 위해 “0.0.0.0/0” 을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ffef14ae-ea48-4744-8718-4fafd744b1c6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=1839c5a290ad4b370c4187dec0ccd368f37bcfa9edc2acfdee677698a34d629f&X-Amz-SignedHeaders=host&x-id=GetObject)


	![작성한 규칙을 저장하기 위해 “규칙 저장” 을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e66e8b81-7867-4333-b95a-a7bbd8517c4d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=fea932fa6be8ef86bf806451068b4f42fc11c5fecbbce53ef8cb2a7d87ec5511&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 22번 포트와 80번 포트 둘 다 인바운드 규칙에 적용 된 것을 확인할 수 있다.
	public ip를 웹브라우저에 입력하여 웹페이지가 정상적으로 동작하는지 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4bde0f13-d275-4b5d-aadf-ebc5acf3380c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=0550ed91753e7b1c3d5018ba4116d2791219b0682b4594f061a3c02e4618d4b3&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 정상적으로 동작하는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ea87eb5c-35cf-43b5-a666-09d25e8ca787/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230904%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230904T101030Z&X-Amz-Expires=3600&X-Amz-Signature=c6621efd1865ed9b679473045e961f9fc703fd623cc76bc51f17371115660b9b&X-Amz-SignedHeaders=host&x-id=GetObject)


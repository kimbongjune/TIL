
### 애플리케이션 로드 밸런서(ALB) 실습

1. 로드 밸런서에 연결하기 위한 인스턴스 실행
	- 4-6-1 에서 진행했던 실습과 동일하게 인스턴스를 실행한다
		- 로드밸런서에 연결 할 것이기 때문에 두개의 인스턴스를 실행한다.
		- 또한 사용자데이터에 변경점이 조금 있다.

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

	- 첫번째 서버 실행 옵션

		![서버 이름을 제외한 나머지 옵션은 두번째 인스턴스와 동일하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/90bcb942-204b-4391-99de-309ea5353195/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101649Z&X-Amz-Expires=3600&X-Amz-Signature=1c03b1cb37e998d5d52450903afa3cee132b751bbba9c78bed8a32027dc31c52&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 두번째 서버 실행 옵션

		![서버 이름을 제외한 나머지 옵션은 첫번째 인스턴스와 동일하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c9aee895-2acc-4c04-8e7b-6e20ad0e3bea/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101650Z&X-Amz-Expires=3600&X-Amz-Signature=bb4ca11a2555b38d1087050deb5a09ed88797583451a037e289060f9c5fd096d&X-Amz-SignedHeaders=host&x-id=GetObject)


		![두개의 서버가 실행되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cbdfcd45-f65a-42d4-816d-f1ce14a3efe5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101650Z&X-Amz-Expires=3600&X-Amz-Signature=8ce7848b85df1eff7315ccc3d01c2e953302077eb6e7d55cc465e46a2322f4d7&X-Amz-SignedHeaders=host&x-id=GetObject)


	실행된 서버의 웹페이지 접속

	- 각 각 서버의 public ip를 복사하여 정상적으로 아파치 웹서버가 실행되어 html을 읽어들였는지 확인한다.
		- 첫번째 서버 웹페이지

			![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f7906b0a-827b-46c9-93f9-e7a783566275/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=1117a94cd65e43e17239c4d74601a35f42ec4200935388b64fdbcedd0c489a5c&X-Amz-SignedHeaders=host&x-id=GetObject)

		- 두번째 서버 웹페이지

			![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6c832b55-ebb1-49dd-b484-fe390ec2a399/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=f21e286dd6006aa7915b4e5059f568415671088a13cb34db618dd6105ff34fcc&X-Amz-SignedHeaders=host&x-id=GetObject)

		- 두 서버가 정상적으로 실행 되었음과, 각각 public ip 및 private ip가 다른 것을 확인 할 수 있다.
1. 로드 밸런서 생성하기

	![“로드밸런서” 탭으로 이동하여 “Create load balancer” 버튼을 클릭하여 로드밸런서를 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0056f58e-f7db-4fc8-a3b5-357fadc08817/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=e742cdf291ad493ead6cd9843c45c11ea5fa478e7162e30f275c5989dfb3a0f1&X-Amz-SignedHeaders=host&x-id=GetObject)


	![동일한 서비스를 제공하는 애플리케이션의 엔드포인트가 동일하기를 원하는 상황이니 가장 적합한 옵션인 Application Load Balancer(ABL)를 생성하도록 한다. “create” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/86349fb7-6be7-41b6-b192-aa1e198a5730/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=ecb5344248bb66aecc7f8a2e1dab1ac1125ab8a46d60da05c697073e23a305e2&X-Amz-SignedHeaders=host&x-id=GetObject)


	기본 설정


	![로드밸런서의 이름을 작성 후(여기선 “DemoALB” 라는 이름으로 작성하였다) 외부 인터넷 접속이 되어야 하니 “Internet-facing”을 체크한다. 단순하게 IPv4만을 이용할 것이기 때문에 “IPv4”를 체크한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80c2e2bc-5f1a-46ab-a9cf-6bd6ca73521e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=40028e90e14c07a3f3e943191c9240d794edb0e28a06ac9e8cb7127e7e10783a&X-Amz-SignedHeaders=host&x-id=GetObject)


	네트워크 매핑


	![1개의 VPC와 여러 서브넷에 배포해야 하므로 다중 가용 영역을 선택한다. 이는 가용성을 높이며, 가용 영역이 세개는 되어야 효율적이다. 여기선 모든 가용 영역을 체크한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91c75bdf-4008-4db8-bfcf-c3275e4fed26/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=4a0f31730142da3d3ff2a36de077ea84955a21ee121aba2a3710b6af3bda74cb&X-Amz-SignedHeaders=host&x-id=GetObject)


	![가용 영역 체크 후 화면](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/524d57b7-50af-4bbf-8c49-0c2d28410685/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=a855142181c1b694eeb3e697b64872ba679c2b3082f41b9418bee9a79d893a31&X-Amz-SignedHeaders=host&x-id=GetObject)


	보안 그룹


	로드밸런서를 위한 새로운 보안그룹을 생성한다.


	![기본 보안그룹 삭제 후 “Create new security group” 클릭](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7321536a-65c5-4bd2-8b5d-c1eaada4312c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=81a9f07728e8c5e841f49b25ea329b38a720739d7bc75ca43db2515aac74c0ee&X-Amz-SignedHeaders=host&x-id=GetObject)


	![새 탭에서 보안 그룹 생성 페이지가 열리면 임의의 보안그룹 이름을 작성(여기선 “demo-sg-load-balancer”로 작성 하였다) 후 임의의 설명을 작성한다.(여기선 “SG for ALB”로 작성하였다.) 이후 “인바운드 규칙”에 HTTP(80번 포트)를 모든 아이피에서 허용하는 옵션으로 추가 후 “보안 그룹 생성” 버튼을 클릭한다. 보안 그룹은 3-6을 참조하여 설정을 확인하면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/72270c28-63d8-4d40-8105-a05d57ba23cc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=cca6a54df1306e642ca87a951d9920b47d287be9b2c01a320ded6c48a584b36c&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 로드밸런서 생성 화면으로 돌아와 보안 그룹을 새로고침 후 방금 생성한 “demo-sg-load-balancer”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4e438ce1-6b07-4042-aaf7-bf070d693c91/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=fdc04d702ac380effd8c545032529ac9ae887d935630d609d969fb722aa44d78&X-Amz-SignedHeaders=host&x-id=GetObject)


	리스너와 라우팅 - 1


	![로드밸런서는 특정 포트의 요청을 리스닝 후 대상 그룹에 라우팅 하는 역할을 수행한다. 여기서 대상 그룹이란 인스턴스의 묶음이다. 현재 대상 그룹이 존재하지 않으니 “Create target group”을 클릭하여 새로운 대상 그룹을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/934fdc1d-73b7-4d14-acfa-394c58871148/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=d9d8eb3959f23fe5b798085f0a9194eec4118f24a8fbdd38117f1bf002392268&X-Amz-SignedHeaders=host&x-id=GetObject)


	대상 그룹 생성


	![인스턴스 기반의 대상 그룹이기 때문에 “Instances”를 체크 후 임의의 대상 그룹 명을 작성한다(여기선  “demo-tg”로 작성하였다) 80번 포트를 사용할 것이기 때문에 기본 값으로 HTTP 프로토콜의 80번 포트를 사용하며 프로토콜 버전 또한 기본값인 HTTP1을 사용한다. “Next” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc299a90-cbaf-4431-bd10-61869f73bc85/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=2c6acb19612894f6e3794d85fe6a9fc1f6e495d308397f26fdfc197802e28de0&X-Amz-SignedHeaders=host&x-id=GetObject)


	![80번 포트가 사용 가능한 두개의 인스턴스를 체크 후 “Include as pending below” 버튼을 클릭하여 인스턴스를 검증한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/574c4811-1416-4bc1-a748-aca1be671636/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=3e93cdc32a7ddb44df9ca8f83612471f1302c82d53a7df4887e5cf7bb6718dd5&X-Amz-SignedHeaders=host&x-id=GetObject)


	![선택한 두개의 인스턴스가 검증 중이며, “Create target group” 버튼을 클릭하여 대상 그룹을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fa104ba8-89a2-42be-a55e-2ac767fcff7f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=18da4e2097f789e9d4b0b769a561f5b1806fa5090b3b1f20956b35a59b523d78&X-Amz-SignedHeaders=host&x-id=GetObject)


	![대상 그룹이 정상적으로 생성 되었다. 다시 로드밸런서 생성 화면의 “리스너와 라우팅” 탭으로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ed944e59-721c-48ad-8c4e-bc1a58ddadf3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=942b0238a8abb91e72eecfae248fe6bc886080f3dff3cd7b7973685af916b0cd&X-Amz-SignedHeaders=host&x-id=GetObject)


	리스너와 라우팅 - 2


	![새로고침 후 생성한 대상 그룹을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/add77198-1188-45ef-a4e9-eaec71925d97/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=360381eb808c7dc2dd0d167fe2580952d321de70d7070b7f2b6b8cace44613cb&X-Amz-SignedHeaders=host&x-id=GetObject)


	로드밸런서 생성 요약


	![IPv4와 외부 인터넷을 허용하였으며 80번 포트만 허용하는 보안그룹을 가지고있다. 4개의 가용 영역을 걸친 VPC이며 80번 포트를 리스닝 하고있다는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/885492d6-e166-4aa6-bb72-f836ca965e07/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=941ca8a1b637237fa9c927bb7da4f0e6fe28982371d358fde73753d67dd84c36&X-Amz-SignedHeaders=host&x-id=GetObject)


	로드밸런서 생성 전체 화면


	![설정을 다시 한번 확인 후 “Create load balancer” 버튼을 클릭하여 로드밸런서를 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/67e5619a-e8bf-40bb-ad9e-9f7ee16f3b5a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=bb2f38e924fd880c293d189c8621e30b781610b80f2e6de3c064a17ff063aedd&X-Amz-SignedHeaders=host&x-id=GetObject)


	로드밸런서 생성 완료


	![로드밸런서가 정상적으로 생성 되었으며 프로비저닝 상태에서 활성화 상태가 될 때 까지 잠시 기다린 후 다음 실습을 진행한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/09878d7a-61dc-4b47-91c8-a3762bd9a7ba/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101651Z&X-Amz-Expires=3600&X-Amz-Signature=569713279888830cb0f903c4b8fc8d4af950e55dad2ecd0b70eb79b1cecd6619&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 로드밸런서 동작 확인하기

	![생성한 로드밸런서의 “DNS name”을 복사 후 웹페이지에서 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/aed2a336-99b5-45b1-bd10-84f36eb9267a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=1744f6567f5f9a60a0cf62a4899a007344ff450f8641414d2e78163b7d604dc4&X-Amz-SignedHeaders=host&x-id=GetObject)


	![첫번째 EC2 서버의 private IP가 표시된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/edf0c06c-0666-405f-9743-f152002d6697/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=052a6ad5b7a5bb859c7295ffefdb68b355b91a538c549f98737a6efe06f2e050&X-Amz-SignedHeaders=host&x-id=GetObject)


	![두번째 EC2 서버의 private IP가 표시된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c867912c-90d2-4d24-a403-c9e1866da12f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=60d22cf13ba4e95733732804c9096c80baa54387347b1d07cb39aaeb27b553ba&X-Amz-SignedHeaders=host&x-id=GetObject)


	동일한 DNS(웹페이지 주소)를 입력하였을 때 내부적으로 연결된 두개의 인스턴스에 트래픽을 분산하는 것을 확인할 수 있다.


	이는 대상 그룹 내에 존재하는 인스턴스 두개가 전부 정상적으로 동작중이기 때문이다.


	
대상그룹 확인하기


	![“대상 그룹” 탭에서 그룹 내 인스턴스를 확인하고자 하는 그룹을 선택 후 “Target” 탭으로 이동하여 인스턴스의 상태를 확인해본다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c675bfc7-f27a-45a5-85ab-04a67871f2cb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=92d6502dd3655900336f60c23c44bc022fc92e8c6681f1ffb5df64ff5952e312&X-Amz-SignedHeaders=host&x-id=GetObject)


	하나의 서버 강제 종료시 로드밸런서 동작 확인하기


	![“인스턴스” 탭에서 대상 그룹에 연결되어있는 인스턴스중 하나를 중지한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/52fb71d2-fa7f-40a8-a6a5-cda6493668b7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=a4df0e4a199f9d67e432333ee708c4babd0496ef7f900752098d4a9d40d914ad&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 “대상 그룹” 탭으로 돌아와 인스턴스의 상태를 확인 해보면 하나의 인스턴스가 종료된 것을 확인 할 수있다. 반영이 되어있지 않다면 새로고침 버튼을 클릭하여 반영한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/78d79302-ec02-4145-9128-eedbcc70441b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=391c7d7e153ba7ed644e0fa6184a207f060d12fabc65d707f5a3161cf4131281&X-Amz-SignedHeaders=host&x-id=GetObject)


	![로드밸런서 DNS로 접속하여 아무리 새로고침 하더라도 하나의 인스턴스에만 트래픽이 요청되는 것을 확인 할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cf13a8c3-9974-4ea7-b5ff-2f80150e19bf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230908T101652Z&X-Amz-Expires=3600&X-Amz-Signature=abf1d0de0c8ab5f8aa54a08e8610215ac03f1d7ff7bbe9f8593fe05a7c6d35e4&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 탭에서 중지한 인스턴스를 재 시작 후 대상 그룹에서 다시 확인해본다면 두개의 인스턴스 모두 정상적인 것을 확인 할 수 있을 것이다. 또한 인스턴스 재 시작 후 로드밸런서의 DNS로 웹페이지 요청을 하게 된다면 두개의 서버에 트래픽이 분배되어 서로 다른 private ip를 확인할 수 있다.


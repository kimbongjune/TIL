
### Auto Scaling Group(ASG) 개요

1. Auto Scaling Group(오토 스케일링 그룹) 이란?
	- 현실에서 웹사이트 로드는 시간에 따라 다르다.
		- ex) 쇼핑몰을 이용하는 사용자는 낮에 쇼핑몰을 이용 할 가능성이 밤에 이용 할 가능성보다 높다. 즉, 낮에 로드가 더많다.
	- 오토 스케일링 그룹의 목적은 스케일 아웃이다.
		- 늘어난 로드에 맞춰 EC2 인스턴스를 스케일 인 한다.
		- 줄어든 로드에 맞춰 EC2 인스턴스를 스케일 아웃 한다.
		- 이를 통해서 어느 시점이든 실행하는 머신 숫자를 최소, 최대로 보장할 수 있다.
		- 오토 스케일링 그룹이 만들어지거나 EC2 인스턴스를 제거하면 이 인스턴스들이 로드 밸런서에 등록되거나 등록 해지됨을 확인할 수 있다.
		- 서버의 상태가 비정상이면 오토 스케일링 그룹은 이를 감지해서 비정상 인스턴스를 등록을 해지하고 종료 후 새로운 정상 인스턴스로 교체한다.
	- 항상 최적의 용량에서 실행하기 때문에 비용 절감이 가능하다.
	- 로드밸런서와 함께 동작한다.
		- 다이어그램

			![웹페이지 트래픽에 따라 로드밸런서는 인스턴스에 요청을 보내며, 트래픽이 증가함에 따라 오토 스케일링 그룹은 자동으로 인스턴스를 증가 후 로드밸런서에 등록한다. 이 작업은 사용자가 오토 스케일링 그룹에 설정한 최대 개수의 인스턴스에 도달할 때 까지 반복된다.
			로드가 줄어들면 반대로 인스턴스는 사용자가 오토 스케일링 그룹에 설정한 최소 개수 혹은 희망 개수까지 인스턴스를 감소 및 로드밸런서에서 제거한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/01cb9f7e-c26a-45d3-896b-4e30b2cd1102/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093401Z&X-Amz-Expires=3600&X-Amz-Signature=6c84e3cd79f927f5abb5b088f33e6d3b9036c2ac770c8af11f7ec72a0fd605d0&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 오토 스케일링 그룹 동작 다이어그램

		![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a675b5b7-4225-4475-998b-14e067dedc8a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=2d3b7eb2884e47ebfd2a16639050ca295b6a4a7e513fc2869903d9385e12a722&X-Amz-SignedHeaders=host&x-id=GetObject)


### Auto Scaling Group(ASG) 실습

1. 오토스케일링 그룹 생성하기

	오토 스케일링 그룹 생성 - 1


	![“Auto Scaling 그룹” 탭에서 “Auto Scaling 그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/310df773-aa91-4094-bdd7-a040a3516e1c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=61a987d7c422f2f3bdce18cf8d1b9e2964b9f7aa13e3b7e76cbe43cf22facb53&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 이름을 작성(여기선 “DemoASG”로 작성하였다.) 후 “시작 템플릿 생성”을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/20478e14-3da8-44d0-bc56-5482bbd8938d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=e88251683b97593de29ce400b5fa41569d07c24d18e70a3098b8716d2024d6aa&X-Amz-SignedHeaders=host&x-id=GetObject)


	※시작템플릿 : 오토 스케일링 그룹 내 EC2 인스턴스 시작 방법을 정의한다.


	시작템플릿 생성하기


	![임의의 이름을 작성(여기선 “DemoLaunchTemplate”로 작성하였다.)한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/187033ea-bbb2-441d-85c8-dff6569212a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=198e746a91ef6d3c5f42b2411bb421bf83e5531ef81d7994fd541cea92743cb5&X-Amz-SignedHeaders=host&x-id=GetObject)


	시작 템플릿 콘텐츠


	![오토 스케일링 그룹에서 인스턴스를 시작할 때 사용 할 OS를 지정한다. “Amazon Linux”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a3e19407-7c73-4ada-aa43-921df82043aa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=a1fdc8138feb6d7a5989b1a806171d970bc02338f378857661896ad996bbf961&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 유형


	![오토 스케일링 그룹에서 인스턴스를 시작할 때 사용 할 서버 용량을 선택한다. 프리티어 사용이 가능한 “t2.micro” 인스턴스를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cf50b6f1-8fa4-428c-ab13-50108222e176/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=a8f5bb9f4d09db7ba190952c1c0426f2fbf109a02733763028e35bf99c301e2d&X-Amz-SignedHeaders=host&x-id=GetObject)


	키 페어


	![보유하고 있는 키페어를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/58c1aefd-1fd7-4bd9-bb09-4d3b09883309/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=33c35eb1ba840ba7844eab5c35d17621a8dcf23381852946784be582b9974ec2&X-Amz-SignedHeaders=host&x-id=GetObject)


	네트워크 설정


	![“기존 보안 그룹 선택” 후 이전에 생성했던 보안그룹 “launch-wizard-1”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e444bc4b-b186-4eb6-8e3d-139b7347ef8f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093402Z&X-Amz-Expires=3600&X-Amz-Signature=9e0d54b8b54b3d6e237ab6cf0bce3a947839f475eba8eb5380a2384576eb0cdd&X-Amz-SignedHeaders=host&x-id=GetObject)


	고급 세부 정보


	![“사용자 데이터” 탭에 이전에 사용했던 아파치 웹서버 설치 및 실행 스크립트를 작성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e8db1494-032a-497a-95fd-5842fc1c5f18/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=5e4d6db8911718390376f161f2dff9ef29c7df8cd475d7a7b4bdaef76ce8e13b&X-Amz-SignedHeaders=host&x-id=GetObject)


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


	전체 구성 화면 및 시작 템플릿 생성


	![전체 설정을 확인 후 “시작 템플릿 생성” 버튼을 클릭하여 시작 템플릿을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7bd85356-4e00-49a4-a79c-b6b3c2e5a6df/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=30129936fb0ba2679505050f51ed369cc7a657877b8105e1ecc015088dc12fe9&X-Amz-SignedHeaders=host&x-id=GetObject)


	오토 스케일링 그룹 생성 - 2


	다시 오토 스케일링 그룹 생성 화면으로 돌아가서 실습을 진행한다.


	![방금 생성한 시작 템플릿을 선택 후 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a99f72f4-e580-4627-9a14-e67947da8af5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=73fc7c0b02d5e4a9f0701678c1bf88955bba6de1b63056ac55ce782ae84d1481&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 시작 옵션 선택


	![인스턴스가 실행 될 수 있는 가용 영역을 선택한다 현재 리전에 존재하는 모든 가용영역을 체크한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f894d5a-fddb-49a6-980d-a25ceb8fe25b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=a9c744427521c8379a56665dd0f09ea4b7c81f542304959174ee1f29e0b13b48&X-Amz-SignedHeaders=host&x-id=GetObject)


	![설정을 확인 후 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a053d154-0135-4186-b5be-60f05515f82b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=8f0e13770b1df5de6033c972be7c4e5437144f5c5b9f94d65b101bf2065bd10b&X-Amz-SignedHeaders=host&x-id=GetObject)


	**고급 구성 옵션**


	로드 밸런싱


	![이전 과정에서 실습하였던 로드밸런싱을 그대로 사용 할 것이기 때문에 “기존 로드밸런서에 연결” 옵션을 선택 후 해당 로드밸런서에 연결되어있는 대상그룹을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6466e5e9-260f-4077-8919-e82ab010ae06/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=19ee09303693f59cd9beb0194cae86fc6f2d1571bcdd37ef282de703c753b969&X-Amz-SignedHeaders=host&x-id=GetObject)


	상태확인


	![“Elastic Load Balancer 상태 확인 켜기”를 체크하여 오토 스케일링 그룹에서 로드밸런서의 상태를 체크할 수 있도록 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e7e5fd7b-c17a-4b7f-bb8f-48e27e7d9f27/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=e33586294ee86f499e7c317b43070a92eafc59216f62137579df73193805ad36&X-Amz-SignedHeaders=host&x-id=GetObject)


	전체 설정 확인


	![설정을 다시 확인 후 “다음”버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8cf9bc91-2cfa-4508-807c-3919e9d863a7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=f0520d874f8e0dccd4859aed4eeed537bd43456abd3e753c00ce296d73df0446&X-Amz-SignedHeaders=host&x-id=GetObject)


	**그룹 크기 및 크기 조정 정책 구성**


	그룹 크기


	![오토 스케일링 그룹이 유지하고자 하는 인스턴스의 개수를 작성한다 여기선 “원하는 용량 : 2”, “최소 용량 : 1”, “최대 용량 : 4” 로 지정하였다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0630ba83-39f3-47db-97e2-6ce54cd0534f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=fcac9d54a64cfc6d0e4919f7152c86ddd488bf32f143216cd3e988b048cb1100&X-Amz-SignedHeaders=host&x-id=GetObject)


	※원하는 용량, 최소 용량, 최대 용량

		- 원하는 용량 : 오토 스케일링 그룹이 시작 할 때 생성 할 초기 인스턴스 개수
		- 최소 용량 : 오토 스케일링 그룹의 옵션에 따라 최소한으로 보유 할 인스턴스의 개수 오토 스케일링 그룹의 크기는 최소값 보다 작아질 수 없다.
		- 최대 용량 : 오토 스케일링 그룹의 옵션에 따라 최대한으로 보유 할 인스턴스의 개수 오토 스케일링 그룹의 크기는 최대값 보다 커질 수 없다.

	크기 조정 정책


	![실제로 운영하는서버에서 오토 스케일링 그룹을 사용 할 때에는 당연히 “대상 추적 크기 조정 정책”을 선택하여 특정 조건을 생성하고, 만족할 때 인스턴스를 생성 및 삭제 하여야하지만 여기선 공부 용도이기 때문에 작성하지 않았음](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9a9e932b-533e-4162-8f85-ad38ee65dbce/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=0213bdc1747ce5b35d458c27a79df35ea33ee1704261d1763ac85bcd324306ab&X-Amz-SignedHeaders=host&x-id=GetObject)


	전체 설정 확인


	![설정을 확인 후 “다음”버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/60ec5227-07d6-4c52-b308-59ad80ddf04f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=1c833d1dea8df921f3daea93d80206e15e498b15c1afaaaf27f221a63e8fc367&X-Amz-SignedHeaders=host&x-id=GetObject)


	**알림 추가**


	![알림을 추가하면 인스턴스의 시작, 종료, 시작 실패, 종료 실패 등 여러 유형에 대하여 이메일 알림을 받을 수 있다. 추가하지 않고 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/588dd66d-fca9-4ce4-b09a-1262c7377770/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=3b6477643ad3b806174e0ab71dd3e7657768e39b708d662481fc44b94e67ddce&X-Amz-SignedHeaders=host&x-id=GetObject)


	**태그 추가**


	![해당 오토 스케일링 그룹을 식별하기 위한 고유 태그를 작성 할 수있다. 추가하지 않고 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d416f4c5-4529-4d2b-95b5-eb7539045ca7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=1ec4d2e567c3bd179b13a1a07a1e8e10b66ff297fbd1322b96056c0a614213ee&X-Amz-SignedHeaders=host&x-id=GetObject)


	**검토**


	![위에서부터 설정한 옵션들을 다시 확인 후 “Auto Scaling 그룹 생성” 버튼을 클릭하여 오토 스케일링 그룹을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e9052952-e8fd-424f-874e-adeab570f2a2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093403Z&X-Amz-Expires=3600&X-Amz-Signature=e32747d93158fda76746ae35799ae1685edd0916ba29423054274d17a2b6b2f6&X-Amz-SignedHeaders=host&x-id=GetObject)

1. 생성한 오토 스케일링 그룹 살펴보기

	![“Atuo Scaling Group” 탭에서 오토 스케일링 그룹에 대한 정보를 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/711d47df-b5e5-4c95-8d7c-209288c07dca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=5a85205784c0af1eef271401e1b8ef781af553ed714ffe22761b2fcb3021e17a&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 관리


	![“인스턴스 관리” 탭에서 현재 오토 스케일링 그룹에 의해 실행되고 있는 인스턴스를 확인 할 수 있다. 현재 상태는 정상적으로 실행되고 있는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/99c0d9d1-3738-4f50-b47f-f232d7a46121/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=ada05bb72a39d256b7f13f83e2625a447010773af1cec11e01d9ae117b1ffe1d&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 확인


	![“인스턴스” 탭에서 확인할 수 있듯이 현재 인스턴스 두개가 실행중인 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4e268693-2602-4222-9249-a3dba57fd3fb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=52e824bf7d51dfbade680bfe644eaab4a500f08f9dd0e5c37d010a0035450080&X-Amz-SignedHeaders=host&x-id=GetObject)


	![첫번째 서버 정보](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f34bca1a-fbfc-47f9-a2b2-d17adac35495/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=79dba94cd3f199bdf825258475f14ac856538493c942539faa611932aecd54c5&X-Amz-SignedHeaders=host&x-id=GetObject)


	![두번째 서버 정보](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9661bce2-03f3-4908-8f5f-26f5dfff7629/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=e3f6da95a8c5d7a5a8a184500ff41e9998c3c8644cb3c46db13e866e4f7e7ff1&X-Amz-SignedHeaders=host&x-id=GetObject)


	대상 그룹 확인


	![“대상 그룹” 탭에서 오토 스케일링 그룹에 연결된 대상 그룹을 선택 후 “Targets” 탭으로 들어가보면 위에서 확인했던 두개의 인스턴스가 대상 그룹에 속해있는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ed1144eb-be6b-48ab-aa1a-640070beacc1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=01eb42d23d3311bce620b1e639065c4480d383972ee8618f3670761f16f9ff9d&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 로드밸런서 DNS로 접속하여 확인

	![“로드밸런서” 탭으로 이동하여 오토 스케일링 그룹과 연결되어있는 로드밸런서를 선택 후 “DNS name”을 복사하여 웹페이지에서 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/19e18b72-2722-42f4-b6c7-0caec61a15a9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=2824ff5414e7151032c7099e50357e6af273733bd643ab730af40567a92b77ce&X-Amz-SignedHeaders=host&x-id=GetObject)


	![첫번째 서버의 private ip가 표시된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/791a0409-149e-45be-af10-037c62e87e1f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=a4a51e0383ddf5b1963a99b30ac65f6f99a4d3e2b9d3132de24b5dd768e5f383&X-Amz-SignedHeaders=host&x-id=GetObject)


	![두번째 서버의 private ip가 표시된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/73de0c9d-0e71-4a9a-aea9-ad2dc84c0911/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093404Z&X-Amz-Expires=3600&X-Amz-Signature=3e8ec8fe638267b1a65f79188fbbf09cf8fb57e4074b97f580c8f689b77a1d39&X-Amz-SignedHeaders=host&x-id=GetObject)


	※정상적으로 로드밸런서가 동작하는 것을 확인할 수 있다.

3. 인스턴스 종료 시 오토 스케일링 그룹 동작 확인하기

	오토 스케일링 그룹이 생성한 인스턴스 중 하나를 종료 시켜본다


	![두개의 인스턴스 중 임의의 인스턴스 한개를 종료시켜본다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2ebf798e-5564-4c70-bf71-fdbf9510d883/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093405Z&X-Amz-Expires=3600&X-Amz-Signature=730b5fdd2f43914c4735c0a84c26cd375ab60726802d9a68d72eca5630a609c7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Auto Scaling 그룹” 탭으로 돌아와 오토 스케일링 그룹을 체크 후 “인스턴스 관리” 탭으로 이동 해보면 하나의 인스턴스의 상태가 비 정상인 것을 오토 스케일링 그룹에서 확인 한 것을 알 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/708057d9-ae4a-48ef-870b-74f66dbdfe1a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093405Z&X-Amz-Expires=3600&X-Amz-Signature=efffca7b076626f2516759ebad17ef6d13663654616a6b0ab749b9ff2d5edc69&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“활동” 탭으로 들어가 스크롤을 내려보게 되면 오토 스케일링 그룹이 동작한 행위들을 확인 할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b8aac2d8-a165-4aac-b4c8-a43ab1e56f2e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093405Z&X-Amz-Expires=3600&X-Amz-Signature=7e0772d4cc77d8d8177bcb80a36524404994ad65fb93e1fa4a3b35f4e2b950ca&X-Amz-SignedHeaders=host&x-id=GetObject)


	![작업 기록을 살펴보게 되면 오토 스케일링 그룹이 인스턴스의 상태를 체크 하다 하나의 인스턴스에 오류가 발생하여 해당 인스턴스를 그룹에서 제거하고 새로운 인스턴스를 생성한 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91fb9d04-f476-4ff5-8e75-e350a0c4c4c6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093405Z&X-Amz-Expires=3600&X-Amz-Signature=d7afc05c1ab934c9c9eed0ca40020cfbeed76ffedeec64179b4abf626f11f240&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 탭으로 돌아와 실행중인 인스턴스를 다시 확인해본다.


	![종료한 인스턴스를 제외 하고 두개의 인스턴스가 실행중인 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5b6a9fc7-75d8-4860-adbe-4c2742a9972e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230909%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230909T093405Z&X-Amz-Expires=3600&X-Amz-Signature=e3dc468575be9f76b2bb0352c4c69801908e68118ccadf3974b86d77d9c88e9a&X-Amz-SignedHeaders=host&x-id=GetObject)


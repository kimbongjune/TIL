
### AWS 클라우드 개요

1. AWS 클라우드의 역사

	![AWS 클라우드의 역사](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4d081eb4-e241-43a1-b065-9896bcedd894/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230827%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230827T094743Z&X-Amz-Expires=3600&X-Amz-Signature=724cea19937bffebbb4dac4397d38a99dcf379b30876e6a12c7c7bffa22c7666&X-Amz-SignedHeaders=host&x-id=GetObject)

1. AWS에서 할 수 있는 것들

	모든것이 가능하다. 몇가지 예를 들자면

	1. 복잡하고 확장 가능한 애플리케이션을 만들 수 있다.
	2. 다양한 산업분야에 적용 가능하다.
	3. 기업의 IT를 이전하기 위한 백업과 스토리지
	4. 빅데이터 분석
	5. 웹사이트호스팅
	6. 모바일, 소셜 등에 대한 백엔드개발
	7. 게임 서버
1. AWS의 글로벌 인프라
	1. AWS Regions(AWS 리전)
		- 전세계에 걸쳐 있으며 각각 이름이 존재한다. ex)us-east-1, us-east-3 …
		- Region이란 데이터센터의 집합이다.
		- 대부분의 서비스들은  특정 리전에 연결되어 국한된다. 즉, 한 리전에서 서비스를 사용하다 다른 리전에서 그 서비스를 사용하려고 하면 서비스를 처음 이용하는 것이다.
		- AWS Region 선택에 영향을 미칠 수 있는 요인
			- 법률준수 : ex) 특정 정부는 애플리케이션을 배포하게 될 대상 국가 내에 데이터가 보관되기를 원한다.
			- 지연시간 : 가까운 거리일 수록 지연시간이 줄어든다. ex) 한국 사용자가 많은 서비스의 경우 한국가 가까운 Region을 선택하는것이 바람직하다.
			- 모든 Rigion이 동일한 서비스를 가지고있지 않다 : 일부 리전에는 특정 서비스를 제공하지 않으므로 해당 서비스를 제공하는지 확인 하여야한다.
			- 비용 : 각 Rigion마다 요금이 달라지므로 요금제를 확인하여야한다.
	2. AWS Avalibility Zones(AWS 가용 영역)
		- 가용영역은 리전 내에 존재한다. 대부분 3개를 보유하고 있으며, 최소는2개, 최대는 6개의 가용영역을 보유한다.
		- 각각의 가용영역은 여분의 전원, 네트워크, 통신 기능을갖춘 하나 또는 두개의 개별적 데이터센터로 이루어져있다.
		- 각각의 가용영약들이 재난 발생에 대비하여 서로 분리되어있다. 즉, 특정 가용영역에 문제가 발생하여도 다른 가용영역에는 영향이 없다.
		- 이런 데이터센터와 가용영역들은 높은 대역폭의 초저지연 네트워킹으로 연결되어 리전을 형성한다.

		![예시 - 시드니 Region](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6a93f932-d25e-4a8f-bb03-ed9873fb68ce/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230827%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230827T094748Z&X-Amz-Expires=3600&X-Amz-Signature=84933877551c4ad122de13ea913ee20b6587f2452d740f19991d647284f511c8&X-Amz-SignedHeaders=host&x-id=GetObject)

	3. AWS Data Centers(AWS 데이터 센터)
		- 각각 여분의 전원, 네트워크, 통신기능을 갖춘 데이터센터이며 하나 또는 두개가 보여 하나의 가용영역을 구성한다.
	4. AWS Edge Locations(AWS 엣지로케이션)
		- AWS 의 CDN들의 여러 서비스들을 가장 빠른 속도로 제공(캐싱) 하기 위한 거점이다.
		- 리전과 가용영역과 별개로 AWS의 CDN 서비스인 CloudFront과 AWS의 DNS 서비스인 Route53의 캐시서버를 의미한다.
	5. AWS Points of Presence(AWS 전송지점)
		- AWS는 42개국 84개의 도시에 200개 이상의 전송지점을 보유하고있다.
		- 최소 지연시간으로 최종 사용자에게 컨텐츠를 전달하는 데에 유용하다.

	![https://infrastructure.aws/](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/af14c51b-6681-442e-ab18-e2c81351d686/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230827%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230827T094744Z&X-Amz-Expires=3600&X-Amz-Signature=7aea7ed77955d6027d4468ad05da33994336ddd6e8044968079067a6e7956420&X-Amz-SignedHeaders=host&x-id=GetObject)


	**—요약—**

	- AWS는 각 국가 중심도시를 기준으로 AWS Region을 보유하고있다.
	- 각각의 Region은 AWS의 사설 네트워크로 연결되어있으며
	- 각 Region 내에 여러개의 Avalibility Zone(가용영역)을 보유하고있다.
	- Avalibility Zone 내에는 한개 내지 두개의 Data Center가 존재한다.

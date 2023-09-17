
### S3 스토리지 클래스 개요

1. S3 Storage Classes(S3 스토리지 클래스) 개요
	- S3에서 “**객체**”를 생성할 때 스토리지 클래스를 선택할 수 있다.
	- 스토리지 클래스를 수동으로 수정할 수도 있다.
	- S3 수명 주기 구성을 이용해서 모든 스토리지 클래스 간에 객체를 자동으로 이동시킬 수도 있다.
	- S3 Durability(내구성) and Availability(가용성)
		- Durability(내구성)
			- S3로 인해 객체가 손실될 수 있는 확률을 의미한다.
			- S3의 내구성은 99.99999999999%로 매우 높다.
			- 단순 확률 계산상 S3에 천만개(10,000,000)의 객체를 저장했을 때 1만년에 한번 한개의 객체가 손실된다.
			- 모든 스토리지 클래스의 내구성은 동일하다.
		- Availability(가용성)
			- 얼마나 쉽게 서비스를 이용할 수 있는지에 대한 지표이다.
			- 각각 스토리지 클래스마다 상이하다.
			- ex) S3 Standard의 가용성은 99.99%이며 이는 1년에 약 53분동안 서비스를 이용할 수 없다는 뜻이다.(서비스를 처리할 때 오류가 생긴다는 의미임)
	- 스토리지 클래스 종류
		- Amazon S3 Standard General Purpose
		- Amazon S3 Standard Infrequent Access(IA)
		- Amazon S3 One Zone-Infrequent Access
		- Amazon S3 Glacier Instant Retrieval
		- Amazon S3 Glacier Flexible Retrieval
		- Amazon S3 Glacier Deep Archive
		- Amazon S3 Intelligent Tiering
2. 스토리지 클래스 대항목 구분 및 설명
	- Amazon S3 Standard - General Purpose
		- 99.99%의 내구성을 지니고있다.
		- 자주 액세스하는 데이터를 저장할 때 사용한다.
		- 기본값으로 사용하는 스토리지 유형이다.
		- 지연 시간이 짧고 처리량이 높다.
		- 두 곳에서 발생하는 동시 기능 장애를 감당할 수 있다.
		- 빅데이터 분석, 모바일 및 게임 애플리케이션 콘텐츠 배포 등에 적합하다.
	- Amazon S3Stroage Classes - Infrequent Access
		- 자주 액세스하지 않지만 필요할 때 빠르게 액세스해야 하는 데이터에 적합하다.
		- Amazon S3 Standard보다 요금이 저렴하지만 검색 요금이 추가로 발생한다.
		- 종류
			- Amazon S3 Standard Infrequent Access(IA)
				- 99.9%의 가용성을 지니고있다.
				- 재해 복구와 백업에 이상적이다.
			- Amazon S3 One Zone-Infrequent Access
				- 단일 가용영역에서 내구성이 높다(99.999999999%)
				- 가용 영역이 파괴되면 데이터가 손실될 수 있다.
				- 99.5%의 가용성을 지니고있다.
				- 온프레미스 데이터나 다시 생성 가능한 데이터의 보조 백업 복사본 저장에 적합하다.
	- Amazon S3 Glacier Storage Classes
		- 콜드 스토리지로 아카이브와 백업에 적합한 저 비용 객체 스토리지이다.
		- 스토리지 비용에 검색 비용이 포함되어있다.
		- 종류
			- Amazon S3 Glacier Instant Retrieval
				- 밀리초 단위의 검색이 가능하다.
				- 분기에 한번 데이터에 액세스할 때 적합하다.
				- 최소 스토리지 기간은 90일이다.
				- 밀리초 내에 액세스가 필요한 백업에 적합하다.
			- Amazon S3 Glacier Flexible Retrieval
				- 유연한 검색 기능을 제공한다.
					- 1 ~ 5분의 빠른 검색
					- 3 ~ 5시간의 표준 검색
					- 5 ~12시간의 무료 대량 검색
				- 최소 스토리지 기간은 90일이다.
			- Amazon S3 Glacier Deep Archive
				- 장기보관 스토리지이다.
				- 두가지 검색 옵션이 존재한다.
					- 12시간의 표준 검색 옵션
					- 48시간의 대량 검색 옵션
				- 검색 시간이 많이 소요되지만 가장 저렴하게 이용할 수 있다.
				- 최소 스토리지 기간은 180일이다.
	- Amazon S3 Intelligent Tiering
		- 사용 패턴을 기반으로 액세스 계층 간에 객체를 이동시킨다.
		- 매월 모니터링과 자동화 요금이 발생한다.
		- 검색 요금은 발생하지 않는다.
		- 계층 이동 시나리오
			- Frequent Access 계층에 자동으로 저장된다.
			- 30일 동안 액세스하지 않은 객체는 Infrequent Access 계층으로 이동된다.
			- 90일 동안 액세스하지 않은 객체는 Archive Instant Access 계층으로 이동된다.
			- 옵션으로 90일 ~ 700일간 액세스하지 않은 객체는 Archive Access 계층으로 이동하게 설정할 수 있다.
			- 옵션으로 180일 ~ 700일간 액세스 하지 않은 객체는 Deep Archive Access 계층으로 이동하게 설정할 수 있다.
3. 스토리지 클래스 비교 도표

	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/75051eef-2bda-4517-9375-0365b1906a0d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230917T102619Z&X-Amz-Expires=3600&X-Amz-Signature=63f43883a4397f8496dfe6d5807bdb9db4bf949e9a4583a4226992ca60084b58&X-Amz-SignedHeaders=host&x-id=GetObject)


	스토리지 클래스간 주요점 비교 도표


	[객체 스토리지 클래스 – Amazon S3](https://aws.amazon.com/ko/s3/storage-classes/)


	스토리지 클래스간 주요점 비교 참고링크



### 클라우드 컴퓨팅 출현 이전 기존 IT

1. 웹사이트의 원리
	- 호스팅 된 서버에 웹 브라우저가 서버로 엑세스 하여 웹사이트를 시각화 한다.
	- 서버와 클라이언트 사이에는 네트워크가 존재하고 클라이언트가 네트워크를 찾아 라우팅을 요청하는 과정에 네트워크를 사용하여 데이터를 서버에 보내고 응답을 얻으면 웹사이트를 확인할 수 있다.
	- 클라이언트가 서버를 찾고, 서버가 클라이언트를 찾기 위해선 IP주소가 필요하다
	클라이언트에도 IP가 존재하고, 서버에도 IP가 존재한다.

	![웹서버 동작 개요도](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a2d89d12-a0b1-4493-9f89-6a3c43e97bf4/client_server.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230824T142324Z&X-Amz-Expires=3600&X-Amz-Signature=6d79d449d67c123fbef3052aa33af6bd4bec8a1e47efb5b19fe47eefe9572c50&X-Amz-SignedHeaders=host&x-id=GetObject)

1. 서버의 구성
	- CPU: CPU는 일련의 연산을 하는데사용된다.
	- RAM: 정보를저장하고 빠른 검색을 할 수 있게 지원한다.
	- storage: 장기적으로 저장되어야 할 데이터 저장소(db)
	- **network**: **router**, **switch**, DNS 서버 등

	※ network(네트워크) : **서로 연결 될 케이블과 라우터, 서버의 묶음**


	※ router(라우터) : **컴퓨터 네트워크 간 데이터패킷을 전달할 때 어디로 어떻게 보낼지 파악한다.**


	※ switch(스위치) : **패킷이 목적지에 도착하면 패킷을 네트워크의 정확한 클라이언트에게 전달한다.**


	![네트워크 라우팅 개요도](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c93e7a17-3f23-4973-8e7e-e6472b63387b/cleint_router_switch.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230824T142324Z&X-Amz-Expires=3600&X-Amz-Signature=2f948fb6f14655f14332bb3fc6e27fb9da1f9e26e2ec23ef6c6e40bf0e7a8784&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 온프레미스 환경의 서버
	- 기존에 서버를 사용하기 위해선 서버를 구매하여 특정 공간에 설치하여 사용하였다.
	- 하지만 점점 규모가 커지면 더 많은 서버가 필요해지고 필요 공간이 요구된다.
	- 규모가 커짐에 따라 수익도 증가하고 증가 한 수익으로 더 넓은 공간, 혹은 데이터센터를 구하여 더 많은 서버를 구매하여 설치하게 된다.
	- 이러한 일련과정은 몇가지 큰 문제점이 있다
		- 데이터센터나 특정 공간에 서버를 놓게되면 기타 발생금액이 생긴다
			- 추가적인 전원장치, 서버 쿨러, 유지보수 비용 등
		- 서버를 교체하거나 추가할 때 시간이 오래걸린다.
			- 서버를 주문하는시간, 데이터센터와 연결하는 시간 등
		- 확장에 한계가 있다.
			- 규모를 특정 배수 ex)10배 로 확장하기 위해서는 특정 배수 만큼 ex)10배 의 서버가 필요하다. 하지만 공간과, 시간에 제약조건이 있다.
		- 문제 발생에 대처하기 어렵다
			- 24시간동안 모니터링 할 팀이 별도로 필요하다
		- 물리적인 문제
			- 재난, 정전, 화재 등에 취약하다

위 일련 과정을 외부화 하여 사용하는 것이 클라우드 서버이다.


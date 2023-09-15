
### S3 서버 액세스 Logging

- S3 액세스 로그
	- 외부 감사 목적인 경우 S3 웹사이트에 모든 액세스를 기록해야한다.
	- 승인되거나 거부된 계정에서 S3로 보낸 모든 요청이 기록된다.
	- 해당 데이터를 분석 도구로 분석해서 파일이 삭제됐거나 요청을 너무 많이 받는 등의 정보를 파악할 수 있다.
	- 문제의 근본 원인과 사용량감사 및 의심스러운 패턴 파악등에 유용하다.
	- 설정을 활성화하면 버킷에 요청이 발생하며 버킷을 자동으로 정리해서 모든 요청이 로깅 버킷에 기록된다.

### S3 서버 액세스 Logging 실습

1. 액세스 로깅 저장을 위한 S3 버킷 생성

	![“버킷” 탭에서 “버킷 만들기” 버튼을 클릭하여 새 버킷을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/adbbdfe3-a958-44a4-b844-c722b41f2026/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101923Z&X-Amz-Expires=3600&X-Amz-Signature=29845e98c51120049cdf36a136279eb5992e85eec85f626f6ae633491f1d30cc&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 버킷 이름, 사용할 리전을 선택 후 “버킷 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/004ddc00-bc95-4272-88aa-60e326f7be8c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101923Z&X-Amz-Expires=3600&X-Amz-Signature=13551cfc31404930c7eb7bc2b2ea18ee0b3149b1836bf3d8fa3618acb3ccb5b8&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 버킷 생성 옵션에 대한 내용은 6-2-2를 확인한다.

2. 웹페이지 호스팅이 설정된 버킷에서 서버 액세스 로깅 설정

	![정적 웹사이트가 배포되어있는 버킷의 버킷 정보 페이지로 이동하기 위해 버킷 이름을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8a350c21-edfc-4e26-bfb5-aa1ef5988a14/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=57c268a5e3df7cbe7f6d12f934838264aeaa4c2720a1f5674f434a1f8400e238&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“속성” 탭 하위 “서버 액세스 로깅”탭의 “편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5f403d90-e223-4f46-ad5d-65cb8ae14d8f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=b9985f0a3fb5bc0cb6b5af697a7ab1d1308de2daf972871b6348fe5a0bfa8454&X-Amz-SignedHeaders=host&x-id=GetObject)


	![서버 액세스 로깅 활성화 후 “S3찾아보기” 버튼을 클릭하여 로깅을 위해 생성한 버킷을 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/109de3f5-e211-4c56-9ebb-9ecfa7ae2328/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=ef1535868ea2c3c595e23d5be01ce681e6b5467dc91641e191568ec1f1434921&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 선택 후 “경로 선택” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/56dc5425-b2d9-487e-a9d5-d24ef8a9c4eb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=488a5ccc55b30baa3bfe0ee297a77112d516c024fd697be326148a4617d47ca8&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 명이 입력되었다. 해당 버킷명 뒤에 “/${원하는 디렉토리 명}” 을 입력하여 하위 디렉토리를 생성할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4556f45d-48a9-4308-854a-98ecb35f6262/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=85e9ae77486f2739112cc16a02aa594e5d5da3f416270ef1af8defc3528fb6ec&X-Amz-SignedHeaders=host&x-id=GetObject)


	![하위 디렉토리 추가 여부는 선택이다. “변경 사항 저장” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e9ecd945-6283-45d4-8d85-c761b14668fb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101924Z&X-Amz-Expires=3600&X-Amz-Signature=7ecf99d2f6aaf67068193deda5a81c40655c28f89dd15e71bccf4513569c48d1&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 서버 액세스 로깅 검증

	![버킷 정보 페이지로 돌아가 임의의 객체를 클릭한다 여기선 “index.html”을 클릭하였다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/58616131-3441-4b2b-8dd3-edd75a859f40/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=5c2b26997d42d9dda25269bd632e1ae96d8eb962a76f4a6570bfffbfa1120071&X-Amz-SignedHeaders=host&x-id=GetObject)


	![객체 URL을 복사 후 브라우저의 새 탭에서 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/95d01fee-f277-4b5e-a8f6-b2d40b8b425e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=9b5639688fdd65fa59a85a36e6b1850bfed965094fa715b7cb25d881c6fa3020&X-Amz-SignedHeaders=host&x-id=GetObject)


	![이 작업은 “index.html” 객체에 접근하는 작업이였으며, 액세스 로깅 활성화로 인해 해당 객체에 접근한 내용이 액세스 로그로 작성되어 로깅 버킷에 저장될 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/49e41681-6259-4b87-9c41-97b3321e99e3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=37eba2750edcc7d9b803c37392343d56234cb8f0e81b737ec19365c66a3ab0a8&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 더 많은 로그파일 작성을 위해 해당 버킷의 객체를 한번씩 객체 URL을 이용해 접근해보면 좋다. 또한 로깅 작업에는 시간이 오래걸리니(1~2시간) 다른 작업을 하다 확인해보면 된다.

4. 액세스 로깅 살펴보기

	![로깅 버킷에 객체 액세스에 대한 로그가 쌓여있는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/799de39e-19f9-415e-92ba-5ddc68df2d93/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=6401a3b6c28cd44b54f9ad4da9d089dfbf427bf261ee9c5ee3e63658c95cbd8b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 로그 파일을 선택 후 “다운로드” 버튼을 클릭하여 다운로드 받는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4a208b10-fd5d-4df3-87fd-3a3406953133/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=1eaf01a712527228f4e202dc1675a3e2f08de895b1f689dba46d3e67ee86bb05&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 텍스트 에디터를 이용해 로깅 파일을 열어보게 되면 요청한 IP주소, 암호화 설정 등을 확인할 수 있다. 해당 로그파일을 읽는 방법은 아래 링크를 참조하도록 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0c4528c3-0159-431a-8c26-9bd7c561eabc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230915%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230915T101934Z&X-Amz-Expires=3600&X-Amz-Signature=2344b4a4a50c513d9b8cec6ed29d8d40c535db044e1f34c103d1f4124cf69905&X-Amz-SignedHeaders=host&x-id=GetObject)


	[bookmark](https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/LogFormat.html)



### S3 보안 : 버킷 정책

1. S3 보안
	- S3 보안에는 다양한 구성 요소가 있다.
		- 사용자 기반(User based)
			- IAM 사용자를 정의하고 사용자에 IAM 정책을 연결하여 S3 버킷에 액세스 할수 있다.
		- 리소스 기반(Resource based)
			- 버킷 정책을 정의하여 버킷에 바로 연결되는 정책으로 다른 계정의 요청이나 공용 요청 등을 허용 혹은 거절할 수  있다.
			- 객체 ACL(Object Access Control List)
				- 객체 수준에서 어떤 사용자가 어떤 행동을 할 수 있는지 상세하게 정의한다.
			- 버킷 ACL(Bucket Access Control List)
				- 버킷 수준에서 어떤 사용자가 어떤 행동을 할 수 있는지 상세하게 정의한다.
	- IAM 정책과 버킷 정책
		- IAM 권한이 IAM 정책과 연결되어 역할의 사용자나 그룹이 S3 버킷**에** 액세스를 허용한다.
		- S3 버킷 정책으로 버킷이 직접 사용자에 액세스를 허용한다.
		- 통합 정책에는 명시적 거부가 존재하지 않는다.
		- 즉 IAM을 통해 누군가에게 직접 액세스 권한을 주거나 S3 객체 버킷 정책을 통해 액세스 권한을 부여하면 액세스가 가능하다.
	- 암호화
		- 객체를 암호화 하여 어떠한 사용자도 객체를 수신하거나 해독하지 못하게 한다.
2. 정책 기반의 S3 접근 권한 예시
	- IAM 권한을 이용한 S3 버킷 액세스

		![AWS 내 존재하는 IAM 유저의 경우 IAM 정책을 이용해 버킷에 액세스가 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cad8cf48-87dc-4f32-9f5b-01253d03908b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034454Z&X-Amz-Expires=3600&X-Amz-Signature=77cf02ab68cd94a474dea5a691e531d578343529179b909ce955413a9ed2d2c3&X-Amz-SignedHeaders=host&x-id=GetObject)

	- S3 버킷 정책을 이용한 퍼블릭 액세스

		![AWS 계정이 아닌 웹사이트 접속 사용자가 객체를 읽기 위해선 S3 버킷 정책에 퍼블릭 액세스 정책이 필요하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53e4a3af-0c95-43e4-b3e3-e794c9c74770/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034455Z&X-Amz-Expires=3600&X-Amz-Signature=62ac299d6b226e0519fe448fc300af366918d6b91100afe8ee99ff40b1b4711c&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 다른 서비스에서 S3 액세스

		![EC2 인스턴스에 직접 IAM 정책을 부여할 수 없으니 EC2인스턴스 역할에 IAM 권한을 부여하여 버킷에 액세스가 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/541e835f-88f0-4214-8b6a-c13da99d9ef0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034455Z&X-Amz-Expires=3600&X-Amz-Signature=00f710aa1e6d184c5fe510334b3daa0cd07cd70f51b903c2f0b85c3a392998be&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 교차 계정 액세스(다른 AWS 계정 내 IAM 유저)

		![퍼블릭 액세스 정책이 아닌 교차 계정 액스(Allows Cross-Account) 권한을 부여하여 올바른 버킷 정책을 수립한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/76c61fd8-3447-433f-b2f3-58e6987d46c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034455Z&X-Amz-Expires=3600&X-Amz-Signature=eb41e22163e62c9db3a23e8feeb5147ae31c55947b12146edffbef61c6d070f6&X-Amz-SignedHeaders=host&x-id=GetObject)

1. 버킷 정책 종류
	- 제이슨 기반 정책(Json based policies)

		IAM 정책에서 사용했던 Json 포맷과 비슷한 형태를 띄고있다.


Resource : 어떤 객체와 버킷에 액세스 권한을 부여할지 정의함


Effect : 허용 또는 거부


Action : 허용 또는 거부할 일련의 API


Principal : 접근할 사용자에 대한 정의


![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/56eefa12-4a48-4a05-b1f2-3c3e4cc2a7b3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034457Z&X-Amz-Expires=3600&X-Amz-Signature=3a1cf8dd78d196965b1d9f109b5a5e5e8809a0c03e78e391ca9bfddb93dd6678&X-Amz-SignedHeaders=host&x-id=GetObject)

	- S3 버킷 정책
		- 버킷에 관한 공용 액세스 권한을 부여할 수 있다.
		- 객체를 암호화 해서 업로드할 수 있다.
		- 교차 계정 액세스를 이용해 다른 계정에 액세스 권한을 부여할 수 있다.

### S3 보안 : 버킷 정책 실습

1. 퍼블릭 액세스 차단 설정 변경

	![버킷 정보 페이지에서 “권한”탭으로 이동하여 버킷정책 설정 이전에 퍼블릭 액세스 차단 설정을 변경해야 한다. “편집”버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/268da13b-b52d-4545-9dcf-277bd7bcf832/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034457Z&X-Amz-Expires=3600&X-Amz-Signature=5d9af8cc35398d216f8dc0ebcf038eaeb5866c8100180eca366a5b233e7b003b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![모든 체크박스가 해제 되어있게 변경 후 “변경 사항 저장” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a1e1462c-f76a-4b99-b732-6b8887f04570/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034457Z&X-Amz-Expires=3600&X-Amz-Signature=620a25a56806d5a283023e8a99ba7cbd8825fb88cd2fd37a5d3946247fd24a98&X-Amz-SignedHeaders=host&x-id=GetObject)


	![팝업창에서 설정을 변경하기 위해 “확인”을 입력 후 “확인” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f18fcfa4-e78d-4564-8d9d-f703fae8a2b0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034457Z&X-Amz-Expires=3600&X-Amz-Signature=e1e79556feb3b2250c0e2ead1d90c9476ae02d9136b5cdd874c1b4ab2026ff49&X-Amz-SignedHeaders=host&x-id=GetObject)


	![퍼블릭 액세스 설정을 비활성화 하여야 버킷정책 수정이 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6146cc1d-78ce-4988-b5e2-dd6a1245ebff/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034457Z&X-Amz-Expires=3600&X-Amz-Signature=4d1dc37d7e3f99fde3ff2c21e956f967af4b355c6f00b1d65a199f20864f6a58&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 버킷 정책 수정

	![“편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/93bda4e6-2e4a-4b65-a642-ac8ea5dd20f6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=cd486187486fdf41f371888c6d7744ee04f4d68bacca62179ba4455bb828511e&X-Amz-SignedHeaders=host&x-id=GetObject)


	정책 설정시 크게 세가지 방법이 있다.

	1. 정책 예제
		- AWS에서 제공하는 버킷 정책에 대한 예제를 이용하여 정책을 수정할 수 있다.
	2. 정책 생성기
		- 버킷 정책에대한 설정을 화면을 보며 JSON파일을 작성해주는 웹페이지에서 정책을 생성할 수 있다.
	3. 직접 작성
		- JSON파일을 직접 작성하여 정책을 설정할 수 있다.

	여기서는 정책 생성기를 이용하여 정책을 설정할 것이다.


	![“정책 생성기” 버튼을 클릭하여 정책 생성기 페이지를 새탭에서 실행한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/aa798952-937c-4e58-8e89-f77acf5b3b41/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=b179b66716198a4e52e88aca79d178c9ae41ca8589f9b174f42fe1ca2f47bafb&X-Amz-SignedHeaders=host&x-id=GetObject)


	![위와 같은 페이지가 새 탭에서 열릴것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e509088d-f07b-4d10-804d-4a35ccd568bd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=525c9cc8a81827126d48ebad8608c5fca9c7d8e8745781007d6ce9e9493c9cdd&X-Amz-SignedHeaders=host&x-id=GetObject)


	Select Policy Type(정책 타입 선택)


	![S3 버킷에 대한 정책을 설정할 것이기 때문에 정책 타입은 “S3 Bucket Policy”를 선택한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a5f4eb5-a45f-4b3e-bec8-e2e4f1bccc36/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=6947dee37e75da6c8c9a6bb2a6f95d2105fbbf84fa261688fcf3c4e8f3f24a09&X-Amz-SignedHeaders=host&x-id=GetObject)


	Add Statement(s)(정책 상태 추가)


	![Effect에는 권한에 허용을 뜻하는 “Allow”를 선택하고, Principal에는 접근할 사용자에 대한 정의를 한다. 여기선 모든 사용자에 대한 허용의 뜻으로”*”를 입력한다. Actions에는 해당 버킷에 연결할 정책API를 설정한다. 여기서는 버킷의 모든 객체에 접근할 수 있는 “GetObject” 정책을 연결한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/96febe19-484f-43f6-ad5d-1af2e147214d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=88baf406705648460e47686880d6880a4b4ec79472310a2191cd1e668d40e5b2&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ S3 버킷의 이름 확인하기


	![버킷 정책 페이지에서 버킷의 ARN을 확인할 수 있다. 빨간 박스의 이름을 복사하여 Amazon Resource Name (ARN)에 붙여넣으면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/374d3d8d-8d29-406b-91ec-b6307c82b109/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=b88f04142e086a26465f96844e3db4f66d6977eae284e6e19d9847519dfef286&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Amazon Resource Name (ARN)에는 본인이 소유하고있는 S3버킷의 이름 + /를 입력한다. 이름은 S3콘솔에서 확인할 수 있다.
	ex) “arn:aws:s3:::kbj-ccp-2023-v1/”
	”/*”의 의미는 버킷 하위 디렉토리 전체에 대한 권한을 부여한다는 의미이다.
	설정을 확인 후 “Add Statement” 버튼을 클릭하여 정책을 추가한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1259a894-7cd2-470e-924b-e1865c97e3bb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=e0490004af8b54660b0793a46f0a300e724c7f67886fb4b4df837f1a2f417e3d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Add Statement”버튼을 클릭하게 되면 하단에 정책을 생성할 수 있는 버튼이 활성화 된다 “Generate Policy” 버튼을 클릭하여 생성된 정책을 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/85657ace-8b70-4bf3-861b-70d0f4d733d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=79b16fa1f6567a79f9f33c5368fa0c7016f5df96e3d5ac335d5450ca45cf6298&X-Amz-SignedHeaders=host&x-id=GetObject)


	![생성된 Json 포맷의 문자열을 복사 후 버킷 정책 생성 페이지로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8e326a21-2290-41d9-bb68-80d5593d8d9d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=bf2c4b1076f5c95215be903f8b8fd6f15415748838fb1ddf091e2096934d3172&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“정책” 탭에 복사한 Json 문자를 붙여넣은 후 “변경 사항 저장” 버튼을 클릭하여 정책을 설정한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b9c6d2cd-5d2d-4635-89a4-10194c5af35f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=ce75b80fb247e61d7cd5ab6a02952f22f8defd656d334d3295866e4865212ca1&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 정보페이지에서 확인할 수 있듯이 해당 버킷은 이제 퍼블릭 액세스가 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0e5b9d02-ebbd-4cba-9dd0-325914428a81/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034458Z&X-Amz-Expires=3600&X-Amz-Signature=84e72b5357015784ae7a0003bafa2c29f227326c5831e89b0166d3f09949f6d0&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 버킷 정책 검증

	6-2-6-b 에서 실습했던 내용을 다시 진행한다.


	![버킷 탭에서 이전 실습에서 업로드했던 coffee.jpg 객체를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/64b7e613-b5aa-49cd-9c47-1504d261e42d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034459Z&X-Amz-Expires=3600&X-Amz-Signature=baa12c918ce0072057fc6de57008373b592024c8e90ab15ec5afcd0ca6d5094f&X-Amz-SignedHeaders=host&x-id=GetObject)


	![객체 URL을 복사하여 브라우저의 새 탭에서 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7934a8db-d0d3-4341-ad96-62c75289c5cf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034459Z&X-Amz-Expires=3600&X-Amz-Signature=b83eb3a4ff7f7a2ae22fe282bf10af1cf225e71fe4d454f059c026465077ef7b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 정책 설정 전 객체URL 접속시 발생했던 에러](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f1603f5-6ea2-40d6-8e6b-0184c579c7b1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034459Z&X-Amz-Expires=3600&X-Amz-Signature=8c3e2a5d579e63a6095f47bac56721b861c6b0d4bd28334b1ab5ed9f7d08bf84&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 정책 설정 후 객체 URL 접속](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b4cae4ac-33e7-4913-b07c-cd4c9999e156/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230912%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230912T034459Z&X-Amz-Expires=3600&X-Amz-Signature=b4b2ec8c3f13032cecc2591644a60a5b556f4fdcbae4988f089792e654a2d1bb&X-Amz-SignedHeaders=host&x-id=GetObject)


	정상적으로 객체에 접근이 가능한 것을 확인할 수 있다.


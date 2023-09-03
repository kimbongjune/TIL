
### AWS 액세스 키 ,CLI 및 SDK

1. AWS 액세스 방법
	- AWS에 액세스 하는 방법 은 크게 세가지가 있다.
		- 웹 인터페이스
			- AWS 관리 콘솔을 이용하여 서비스를 이용하는 방법
			- 사용자 이름 및 비밀번호와 MFA인증으로 보호된다.
	- AWS 명령 인터페이스(AWS CLI)
		- AWS에 액세스 할 컴퓨터에서 사용 하는 방법
		- **액세스 키**에 의해 보호된다.

	※ 액세스 키 : **개인 자격증명 도구이며 별도의 파일을 다운로드 받아 적용하면 터미널에서 AWS에 액세스를 가능하게 해준다.**

	- AWS 소프트웨어 개발자 키트(AWS SDK)
		- 애플리케이션 코드 내에서 AWS의 API를 호출하고자 할 때 사용한다.
		- CLI와 동일하게 액세스 키에 의해 보호된다.
2. 액세스 키 개요
	- 액세스키는 각각의 사용자들이 본인의 액세스 키를 직접 관리하며 분실하거나 동료와 공유 하는 등 행위를 금지해야 한다.(비밀번호와 동일한 역할)

### 윈도우에서 AWS CLI 설정

1. AWS CLI 설치하기

	인터넷에 “AWS CLI installer windows” 를 검색하여 AWS 홈페이지로 접속한다.


	[bookmark](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)


	![본인 환경에 맞는 OS를 선택하여 설치파일을 다운로드 받는다. 여기선 윈도우용 설치파일을 다운로드 할 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/07c94815-ff1a-40d7-a8b6-8f78ee28d23b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=6f757de175c69a55d7b92e68736a7ff164ff24bf235cc92a915782da00acdf9a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![위에 표시 한 링크를 클릭하여 윈도우용 설치파일(msi)파일을 다운로드 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/17807374-4fdb-4ff7-ae45-9975c266eb06/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=02673d9444376294183c8f8b370c6e7d0816f6357e76fc71a102f2f6b7025bdb&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다운로드가 완료되면 다운로드 한 msi 파일을 실행 한 후 실행 절차를 따라가면 된다. “Next” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/af743a38-d016-478f-b60e-ace39d79011b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=694d87f19c1cabc08a169357ebb34f343df0490abb4b6ddff3cff055d0bd7e3d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![약관 수락 후 “Next” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3f4a5db3-42f3-4e62-811d-bad71af2cb15/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=94f1b66d41d9e8f6a23ab2455c032979727cdc6755bed279abf7e04fe1f74d46&X-Amz-SignedHeaders=host&x-id=GetObject)


	![신규 설치 이니 별도의 커스텀 없이 실행한다. 본인 환경에 맞게 설치 폴더를 설정 후 “Next” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/df7b6b14-af2b-469f-a420-4dee0b78a965/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=283e531c74835cc6b004297ec347917efab23b38bdf8ca414999ee8fee4e5c11&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Install” 버튼을 클릭해 설치를 시작한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ba378a48-cb93-466a-8db7-5dad293a93df/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=42ec5d1887f7f8405e4466728260d5706f27fbfbb238d7c698e6e170165be18a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![설치가 완료 되었다면 “Finish” 버튼을 클릭하여 종료한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/259971ac-a54a-44a1-8a3c-bd1b339de928/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=2bc319f5c22e758a8bfda11c2c9b39744b9840f42e00e585dab27d3c9419d17f&X-Amz-SignedHeaders=host&x-id=GetObject)

2. AWS CLI 설치 확인

	위에서 설치한 AWS CLI가 정상적으로 설치되었는지 확인하기 위해 윈도우의 CLI(Command Prompt)를 실행하여 확인해본다.


	![키보드의 Window키 + R 버튼으로 실행 화면을 띄운 후에 cmd를 연다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/264b5027-feb0-461e-8f4b-53d61e211a7e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=325d959f3917831be25278836432dcda7f32984640cccd9a6b2cdf3b31c92cb2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![커맨드 창에 “aws --version” 을 입력 후 엔터를 친다. 위와 같이 aws-cli/2~~ 가 출력이 되면 정상적으로 설치 된 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3dea3ca0-79e1-4528-8617-ebb31ebe625b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103809Z&X-Amz-Expires=3600&X-Amz-Signature=633a9d8692139cc366bb04547d6d57d28b30da40552cbc6a08e37eb045f0009d&X-Amz-SignedHeaders=host&x-id=GetObject)


### AWS CLI 실습

1. 액세스 키 생성

	![“사용자” 탭으로 이동하여 액세스 키를 생성 할 유저를 클릭한다.(root는 제외한다)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d125639d-1691-4aab-b035-32a9111b415f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103810Z&X-Amz-Expires=3600&X-Amz-Signature=b3009f078fa96f7afd8834cef8140f65e5c2d2e66d504adbbce66ef9a484cb81&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“보안 자격 증명” 탭을 클릭 후 “액세스 키 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/79844663-8180-49c0-8064-e1be31a771de/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103810Z&X-Amz-Expires=3600&X-Amz-Signature=8a9e373c0f13848769a9eeb4aec34000490b2059d9ac02c0251613572e8511b7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“Command Line Interface(CLI)” 체크박스를 체크 후 하단의 권장사항 체크박스를 체크 후 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6b251ae9-010e-4c3a-b693-33952b4ab66c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103810Z&X-Amz-Expires=3600&X-Amz-Signature=6e9c70f4271cf11c8b91f5defac7704d230f09eb49e3d36af60834f5ce1becde&X-Amz-SignedHeaders=host&x-id=GetObject)


	![생성 할 액세스 키에 대한 설명 태그를 작성 후 “액세스 키 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6902cd5e-c4e6-44ee-816b-bb9f212d15ef/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103810Z&X-Amz-Expires=3600&X-Amz-Signature=7599608f7552f6d1847c3b33b32ee92fad89d918b839472bc204048d72790cd2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![생성 한 “액세스 키” 와 “비밀 액세스 키”는 절대 타인에게 노출되면 안되며, 반드시 본인만 숙지하고 있어야 한다. 하단의 “,csv 파일 다운로드”는 액세스 키 생성시 단 한번만 다운로드가 가능하기에 다운로드 후 별도로 보관 하는 것이 좋다. 모두 확인 하였다면 “완료” 버튼을 눌러 액세스 키를 생성한다. 이어서 바로 실습 할 것이기 때문에 “액세스 키”와 “비밀 액세스 키”를 복사하여 별도로 메모장에 작성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f6bd3624-6fd8-4f53-85bf-99fc8a632fc4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103810Z&X-Amz-Expires=3600&X-Amz-Signature=8b592953f6c5efa02fb2a1d4225e57b396c5e81cde72366944b2f9f30380381b&X-Amz-SignedHeaders=host&x-id=GetObject)

2. AWS CLI 구성하기

	윈도우의 CLI창으로 돌아와 실습을 진행한다.


	커맨드 창에 “aws configure” 를 입력한다.


	![커맨드 입력  후 복사 해놓은 “액세스 키”를 붙여넣은 후 엔터키를 누른다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d351b68b-36f7-479c-9b1c-e9165069d157/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103812Z&X-Amz-Expires=3600&X-Amz-Signature=8d3e52ab9ac649561321599f4e330922493851e41b28735af008069d9c44a3b7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![복사해놓은 “비밀 액세스 키”를 붙여넣은 후 엔터키를 누른다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2fc22a55-f104-4523-a1ed-5b7b1c243397/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103812Z&X-Amz-Expires=3600&X-Amz-Signature=6898b6b7868980dde789eb4e18a4cc27f00880f90dcb8bce9f2fb97c38fc451d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![가장 가까운 리전 이름을 입력 후 엔터키를 누른다. 여기선 “us-east-1”로 진행 한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/95b34d60-adbd-4c61-9323-5a84f1c041f0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103812Z&X-Amz-Expires=3600&X-Amz-Signature=3b17a3cfbc7d10bcb69b564435fd586f077cc6413100c94a12a05ac6953ff46a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![별도의 텍스트 입력 없이 엔터키를 누른다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4faa2b95-9574-4ac3-be5c-d5848ca8cab0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103812Z&X-Amz-Expires=3600&X-Amz-Signature=52071e8cd56a5c1716426e9bb4a69df0b82fa8ce8ec584540a03983530168bb6&X-Amz-SignedHeaders=host&x-id=GetObject)


	![AWS CLI 구성이 완료되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ad4faa6c-00db-4449-a5df-44a77ea6db13/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103812Z&X-Amz-Expires=3600&X-Amz-Signature=b277a818b5fd66ee0d3c707ca0e53dcf743efdb2ed6cecf277b3055bfc66cf27&X-Amz-SignedHeaders=host&x-id=GetObject)

3. AWS CLI 사용해보기

	“aws iam list-users” 명령어를 입력해 유저 목록을 조회 하여본다.


	![AWS 콘솔 화면과 동일한 정보를 가져올 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f4f0799f-04e3-44cb-8e0b-ebf21d20a2fa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103813Z&X-Amz-Expires=3600&X-Amz-Signature=e587493371ad8761c33e87c59cc3c830e82ce775dcadd4f23bf3682fe8cda8a8&X-Amz-SignedHeaders=host&x-id=GetObject)

4. 권한 박탈시 CLI 확인해보기

	위 4-1 에서 실습한 내용과 동일하게 admin 유저를 admin 그룹에서 제거한 뒤 진행한다.


	“aws iam list-users” 명령어를 입력해 유저 목록을 다시 조회 하여본다.


	![동일한 명령어를 입력하였지만 액세스 키 유저가 가진 권한이 부족하여 명령어가 동작하지 않는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9c54b5a0-aeff-4ec4-bf17-1a85a99a63a3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230831%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230831T103814Z&X-Amz-Expires=3600&X-Amz-Signature=6c82daabc6b00311895db4899eddc9f7e8ea86b8f9b8be26cd03b1b0b592730a&X-Amz-SignedHeaders=host&x-id=GetObject)


	실습이 완료 되었으니 위 4-1 에서 실습한 내용과 동일하게 admin 유저를 admin 그룹에 다시 추가 하도록 한다.


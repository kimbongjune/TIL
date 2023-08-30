
### IAM MFA 개요

1. 개인정보 보호 방어 메커니즘

	AWS에서 개인정보(개인, 그룹 등) 보호 방어 메커니즘에는 두가지 방법이 있다.


	1 비밀번호 정책 정의

		- 비밀번호가 강력할 수록 계정의 보안이 철저해진다.
		- 비밀번호 정책 옵션
			- 비밀번호 최소 길이
			- 특정 유형의 글자(대문자, 소문자, 숫자, 특수문자 등)
			- 사용자들의 비밀번호 변경 허용/금지
			- 비밀번호 만료 기간 설정
			- 비밀번호 변경시 기존 비밀번호 사용 금지
		- 비밀번호 정책으로 무작위공격(브루트포스) 등에 대한 해킹을 막아낼 수 있다.

	2 MFA(Multi-Factor Authentication_**)**_

		- 비밀번호 이외의 보안장치를 같이 사용하는 것
		- 비밀번호를 해킹 당해도 해커가 물리적인 보안장치를 가지고 있지 않은 이상 계정을 침해당하지 않는다.
		- MFA 장치 옵션
			- 가상MFA장치(Virtual MFA device)
				- 구글 OTP(Google Authenticator), Authy 등 어플리케이션으로 사용 가능하다
			- 범용 두번재 인자(Universal 2nd Factor(U2F) Security Key)
				- Yubico 사의 Yubikey(USB형 물리적 디바이스)
			- 하드웨어 키 팝(Hardware Key Fob MFA device)
				- Hemalto 사의 OTP 기기
			- 미국 정부 하드웨어 키 팝(Hardware Key Fob MFA device for AWS GovCloud)
				- SurePassID 사의 OTP 기기

### IAM MFA 실습

1. 비밀번호 정책

	비밀번호 정책 변경하기


	![“IAM” 서비스의 “계정 설정” 탭으로 접속 후 “편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/377b9613-e421-4cbe-86fa-87cea7bc5030/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105145Z&X-Amz-Expires=3600&X-Amz-Signature=db660fbeedcba620e4189b797efc38d54e30569830ecceff6a2558bb6c1036dc&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“사용자 지정” 체크박스를 체크 후 원하는 비밀번호 정책을 설정하면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0382ace7-abce-4ac6-b8ea-0b6a2a47cb42/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105145Z&X-Amz-Expires=3600&X-Amz-Signature=3e62a300864e10473203f26178a1023598c0880337bc2de21c5720a477aeb6cd&X-Amz-SignedHeaders=host&x-id=GetObject)

2. MFA

	MFA 추가하기


	![로그인 한 계정의 “IAM” 서비스의 “대시보드” 탭으로 접속한 뒤 “MFA 추가” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e2e161c4-90a6-4b21-a910-dca5d190d055/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105146Z&X-Amz-Expires=3600&X-Amz-Signature=34e682f800f18c9c22ffc13081eaf76705fd246d0d6b969c1b6fae34c52969a0&X-Amz-SignedHeaders=host&x-id=GetObject)


	![새로운 창에서 위와 같은 화면이 보일 것 이며, “MFA 할당” 버튼을 클릭하여 MFA를 등록한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5931f339-e045-430c-97f1-28b5e0012b57/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105146Z&X-Amz-Expires=3600&X-Amz-Signature=df2a67bf4fac04d26e0f6fbb43edc20d5aef3802fe976bddd6b2dfcd95cbcc4d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![어플리케이션에서 표시 될 “디바이스 이름” 을 설정하고 “인증 관리자 앱” 을 체크 한 뒤 “다음” 버튼을 클릭하여 디바이스 탭으로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2388156b-52e8-42fe-bb0d-009dac6c3b44/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105146Z&X-Amz-Expires=3600&X-Amz-Signature=f40fbc7ae090491b7d571240ab6868acc4fb18e6f659d2e6bd0f732304444347&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“QR 코드 표시” 레이아웃을 클릭 하면 QR코드가 표시되며 해당 QR코드를 본인이 설치 한 MFA 어플리케이션에서 스캔 후 순차적으로 표시되는 MFA코드 두개를 연달아 입력 후 “MFA 추가” 버튼을 클릭하여 MFA 설정을 완료한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d8d18fc3-e36a-4f90-8b55-6db408a9e109/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105146Z&X-Amz-Expires=3600&X-Amz-Signature=523ae3936c290388b0714e421474cb8b3ecb586f101f4d7d3aef0bcde9aa4812&X-Amz-SignedHeaders=host&x-id=GetObject)


	![설정이 완료되면 위와 같은 녹색의 레이아웃이 표시 될 것이다. 이후로는 해당 계정으로 로그인 시 MFA 어플리케이션에 표시된 OTP번호를 입력 후 로그인 해야한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1d98bac0-3756-4a66-b10c-a9d837ceb979/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230830%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230830T105146Z&X-Amz-Expires=3600&X-Amz-Signature=abda9170132bb76264332de683b5dc6afd45f2fb7f7b32ef978c0dff019c111e&X-Amz-SignedHeaders=host&x-id=GetObject)


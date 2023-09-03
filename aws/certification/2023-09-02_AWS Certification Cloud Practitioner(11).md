
### IAM 보안도구


IAM 보안도구의 종류는 두가지가 있다.

- IAM 자격증명 보고서(IAM Credentials Report)
	- 위 보안도구는 계정수준(account-level) 에서 가능하며 보고서는 계정에 있는 사용자와 다양한 자격 증명의 상태를 포함한다.
- IAM 액세스 관리자(IAM Access Advisor)
	- 위 보안도구는 사용자 수준(user-level) 에서 가능하며 액세스 관리자는 사용자에게 부여된 서비스의 권한과 해당 서비스에 마지막으로 액세스한 시간을 확인할 수 있다.
	**최소권한의 원칙**의 원칙에 따랐을 때 사용하기 좋다.

	※ 최소 권한의 원칙 : **사용자가 자신의 책임을 수행하기 위해 절대적으로 필요한 항목에만 액세스할 수 있어야 한다는 개념**


### IAM 보안도구 실습

1. IAM 자격증명 보고서(IAM Credentials Report)

	IAM 자격증명 보고서를 다운로드 한다.


	![“자격 증명 보고서” 탭에서 “보안 인증 보고서 다운로드” 를 클릭하여 CSV 파일을 다운로드 하여 확인해본다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/08698e49-8451-4ea4-af78-dafc07349bd9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230902%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230902T083402Z&X-Amz-Expires=3600&X-Amz-Signature=9c0e0d23f36e2bd39756098acd7dda880d365483c1ac8e711926f07c1c3f5f6a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![자격 증명 보고서 파일의 일부이다. ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d7c3022c-2f39-490b-bdd5-648ef8503fe6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230902%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230902T083402Z&X-Amz-Expires=3600&X-Amz-Signature=f089870fc458d7e1396ef83c1aaa4e900a7e3062591cc2c51f08e8b9c7a30eb0&X-Amz-SignedHeaders=host&x-id=GetObject)


	자격증명 보고서에서 확인할 수 있는 정보는 다양하며 몇가지 내용을 열거하자면


	마지막 로그인 시간, 비밀번호 변경 시간, MFA 사용 여부 등이 있다.

2. IAM 액세스 관리자(IAM Access Advisor)

	특정 유저의 액세스 관리자 조회하기


	![“사용자” 탭에서 액세스 관리자를 조회할 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4507e401-3c3d-4620-8590-eed155c20a23/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230902%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230902T083403Z&X-Amz-Expires=3600&X-Amz-Signature=bd1ea2b22237ecfc3f58221cdaefc85c6876a208d301a469fe426baffd04b2ee&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“액세스 관리자” 탭을 클릭하여 해당 유저에 대한 AWS 서비스 액세스 정보를 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a3c935df-55c4-4996-b78f-719c31fe8e1d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230902%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230902T083403Z&X-Amz-Expires=3600&X-Amz-Signature=e47231fd81cc78708e5a7d3179d4959f559f11760ecccbbe340ad314a1bb11be&X-Amz-SignedHeaders=host&x-id=GetObject)


### IAM을 위한 공동 책임 모델


IAM 서비스에 AWS가 가지는 책임, 사용자가 가지는 책임을 명확하게 구분하여아 한다.

- AWS의 책임
	- 인프라스트럭처(Infrastructure)
	- 글로벌 네트워크 보안(global network security)
	- 구성과 취약성 분석 서비스(Configuration and vulnerability analysis)
	- 책임사항 준수(Compliance validation)
- 사용자의 책임
	- 자체 사용자와 그룹, 역할과 정책을 생성, 관리 모니터링
	- 모든 계정에 대한 MFA 활성화
	- 키 관리(키를 자주 교체 하여야 한다)
	- IAM 도구를 이용한 적합한 권한 적용 여부 확인
	- 액세스 패턴 분석 및 계정 권한 검토

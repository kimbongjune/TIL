
### AWS CloudShell

1. AWS CloudShell

	AWS CloudShell은 AWS CLI를 대체하여 AWS 콘솔에서 AWS 명령어를 사용할 수 있는 기능이다. 


	![AWS 콘솔에서 우측 상단의 버튼을 클릭하면 AWS CloudShell을 사용할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2628dd74-39d6-448c-8932-382b24169e49/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103950Z&X-Amz-Expires=3600&X-Amz-Signature=5136363fd0e5c6dfae39eb6ee4b6f6432d4529875d2c4508967366bd079fe662&X-Amz-SignedHeaders=host&x-id=GetObject)


	CLI와 동일하게 동작하는지 몇가지 명령어를 입력하여 확인 해본다.


	“aws iam list-users” 명령어를 입력해본다.


	![AWS CLI와 동일한 결과가 출력되는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/32967dee-5d2f-47b5-9d19-0e6894c67059/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103950Z&X-Amz-Expires=3600&X-Amz-Signature=76bbafdc87b38cd5f5f06982dde5025c71fb817f9c90f9862942b8e35c2b1fd4&X-Amz-SignedHeaders=host&x-id=GetObject)


	AWS CloudShell은 사용자가 계정에 로그인 후 사용할 수 있다. 계정 자격증명이 완료된 시점이므로 AWS의 API를 호출할 수 있는 것이다.


	AWS CloudShell은 로그인 한 계정의 개인 쉘 이기 때문에 파일을 생성하거나, 파일 업로드 및 다운로드 기능을 제공한다. 즉, 전역 파일 공유가 가능하다.


### AWS 서비스에 대한 IAM 역할


IAM 역할

	- IAM 역할은 사용자에게 권한을 이용해 계정에 대한 접근 권한을 부여 및 박탈 하듯이 AWS 서비스에 대한 권한이다.
	- IAM 역할은 사용자가 직접 실행하는 것이 아닌, AWS 서비스에 의해 사용되게 만들어졌다.
	- ex) EC2 인스턴스가 특정 업무를 수행하기 위해 다른 서비스에 접근하는 상황이 발생한다면 EC2 인스턴스에 IAM 역할을 부여 해주어야 가능하다.
	- 

### IAM 역할 실습

1. 역할 생성하기

	![“역할” 탭으로 이동하여 “역할 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/363aa9b0-19da-43c3-8d82-a8d7bc23e980/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103952Z&X-Amz-Expires=3600&X-Amz-Signature=728b84f74d20d74cdcdbc965361ae48af43696d375a8c491dcb97adc73a936f6&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의로 테스트를 할 것이기 때문에 “AWS 서비스”를 체크 후 “EC2”를 체크 한 후”다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/52c3e509-3552-49f5-bb75-0f22d84dd543/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103952Z&X-Amz-Expires=3600&X-Amz-Signature=f1b2aac15430a13c1f8c79088b8b3196234a07a9c97b0a41d7adaa937513da61&X-Amz-SignedHeaders=host&x-id=GetObject)


	※AWS 서비스에 대한 역할은 EC2, Lamda 뿐만 아니라 많은 서비스에 대한 역할을 지원한다.


	EC2 서비스에 임의의 권한을 부여해보도록 한다.


	![여기선 “IAMReadOnlyAccess” 권한을 부여해보도록한다.
	”IAMReadOnlyAccess”를 검색 후에 체크 한 뒤에 “다음” 버튼을 클릭한다.
	이렇게 설정하게 되면 EC2 인스턴스가 IAM으로 부터 IAM 유저를 읽는 권한이 부여된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b7859ebb-9b04-4f4e-8341-1511b0a45d81/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103952Z&X-Amz-Expires=3600&X-Amz-Signature=9f2957d8235032d34b3db76f15d4cebd82de0eb833c23a51ee7a3877fd52c088&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 역할 이름을 설정 한 뒤 설정을 확인 한 후에 “역할 생성” 버튼을 클릭해 역할을 생성한다.
	여기서는 “DemoRoleForEC2” 라는 이름을 사용하였다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5eed4274-e12e-4e2c-bb4d-0c63f08fc037/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103952Z&X-Amz-Expires=3600&X-Amz-Signature=fd2f0fe82e91cfcf473e683fac5091668b92bd5c9b0296d1955ff38947b080b0&X-Amz-SignedHeaders=host&x-id=GetObject)


	![방금 생성한 역할을 클릭해 역할이 잘 생성 되었는지 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c8a9f60c-0ecd-45f8-85b2-477bf7e2e184/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230901%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230901T103952Z&X-Amz-Expires=3600&X-Amz-Signature=13f62013c88575626f3e7229c1977ac13a7e16ae5162d4f9aafa94db397f0998&X-Amz-SignedHeaders=host&x-id=GetObject)


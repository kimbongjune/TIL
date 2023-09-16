
### S3 Replication 개요

- S3 Replication(복제) (CRR & SRR)
	- 버킷 버전관리 옵션을 활성화 하여야 사용 가능하다.
	- 버킷은 서로 다른 계정에 존재할 수 있다.
	- 복제는 비동기식으로 진행된다.
	- 복제를 진행하기 위해선 반드시 S3에 파일을 복제할 수 있는 IAM 권한을 부여 하여야한다.
	- 복제의 종류
		- CRR(Cross Region Replication - 리전 간 복제)
			- 사례
				- 짧은 지연시간을 위해 사용한다.
					- ex) 유럽 리전에 있는 버킷을 미국 리전으로 복제한다.
		- SRR(Same Region Replication - 동일 리전 복제)
			- 사례
				- 로그를 집계한다.
					- ex) 프로덕션 계정과 테스트 계정 간의 실시간 복제를 하여 동일한 지역에서 다른 워크로드로 데이터를 확인한다.

### S3 Replication 실습

1. 버킷 복제 실습을 위한 새 버킷 생성

	일반 구성


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7fb3cff2-8f15-463d-bb4d-a51b4fcce7d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110829Z&X-Amz-Expires=3600&X-Amz-Signature=76a5e9b66a0b03d7586549c0440a7e571ad547c1406c3855bee13e4315a4e165&X-Amz-SignedHeaders=host&x-id=GetObject)


	임의의 버킷 이름을 작성한 후 리전은 복제를 진행할 버킷(최초 생성한 웹 호스팅이 활성화 되어있는)과 다른 리전을 선택하여야한다.


	버킷 버전 관리


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c8ee7f28-b471-474d-b3a6-67dca763ad83/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110829Z&X-Amz-Expires=3600&X-Amz-Signature=55553849fb474d61b4626960a17caa5153490733fecb6ce647dcefe2be50bf74&X-Amz-SignedHeaders=host&x-id=GetObject)


	이전 실습에서는 버킷 생성 후 설정을 수정 하여 버킷 버전 관리를 활성화 하였지만, 버킷 생성시에도 버킷 버전 관리를 활성화 한채로 생성할 수 있다. 버킷 버전 관리 옵션을 활성화 한다.


	전체 설정 확인 및 버킷 생성


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f60cefd-c3e2-4c20-8bbd-b6621ec7afb6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110829Z&X-Amz-Expires=3600&X-Amz-Signature=0459b00d97c4f804ca47a82f102877211763e6908bd7b14bc9de0a5c5eed63b7&X-Amz-SignedHeaders=host&x-id=GetObject)


	설정을 확인 후 “버킷 만들기” 버튼을 클릭한다.

2. 버킷 복제 설정하기

	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7a44687e-f769-4107-b582-376f91bc64e6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=19f9a6a706177801439000c960515628df1e457c71665b009d30554762df85b5&X-Amz-SignedHeaders=host&x-id=GetObject)


	데이터를 옮길 버킷을 클릭한다. 여기선 index.html 등 파일이 존재하는 웹사이트 호스팅이 활성화 된 버킷을 선택하였다.


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/42e9f67e-b753-4d38-b95d-22b091ab3ef0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=b54a73f0a47b9d1445717d47079df3933e0111da6f1b17f3fb8c2f043e67d6a2&X-Amz-SignedHeaders=host&x-id=GetObject)


	“관리” 탭으로 이동하여 “복제 규칙 생성” 버튼을 클릭한다.


	복제 규칙 구성


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8e566584-d9bc-4c4c-8b8f-67fc323aacc0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=9dc33877e47964a4fc9bd1eb4697cdab5d5280f75ee8a66cebc69c75756f69f1&X-Amz-SignedHeaders=host&x-id=GetObject)


	임의의 복제 규칙 이름을 작성(여기선 “demo-rule”로 작성하였다)을 작성한다.


	소스 버킷


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f9a97d27-bec0-45db-b45a-5eea61135301/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=b50f076e0ba44770f8663740c5ec032b779ae762bcc70e36b9c52f7d108ecf7a&X-Amz-SignedHeaders=host&x-id=GetObject)


	테스트 용도이기 때문에 “버킷의 모든 객체에 적용” 옵션을 체크하여 버킷 내의 모든 데이터를 복제한다.


	대상


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5d179f84-2d97-436c-9cb3-9f197e2be649/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=c2d1ae5cf09ee8ffd7133aef6ed5b670a1064a93639e088dce3ef22d0473d288&X-Amz-SignedHeaders=host&x-id=GetObject)


	6-10-2에서 진행했던 버킷 찾아보기 기능을 이용하여 복제할 버킷을 선택한다.


	IAM 역할


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3c89f05d-4d6e-4d36-8af6-19818d8e6dc5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=9cf1d81ff25cb221646a77787a477801cb885d15ee81eca2187511bfa4e1fb1e&X-Amz-SignedHeaders=host&x-id=GetObject)


	버킷에 적용할 새로운 역할을 생성하기 위해 “새 역할 생성”을 클릭한다.


	전체 설정 확인 및 복제 규칙 저장


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f4a30b8a-9fc2-42e1-b0dd-1f09ffd83b9c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=af2d89e1f6bf676e10e5264dd9c8cfa2c1dbb19605a2013cc19677a41da8ab63&X-Amz-SignedHeaders=host&x-id=GetObject)


	설정을 확인 후 “저장” 버튼을 클릭한다.


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e390af33-d092-4842-b88b-80cf0e4d87d7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=e0fb03dcaf4bed96bee42bd5e3f2d5d6745b91bf2a32507307b0ae6b132b2046&X-Amz-SignedHeaders=host&x-id=GetObject)


	이전에는 존재하지 않는 옵션이였으나 현재는 버킷 복제를 저장하게 되면 두가지 옵션중 선택할 수 있다.
	복제 규칙을 설정하기 이전에 버킷에 존재했던 데이터를 복제하거나, 버킷 규칙 설정 이후에 업로드 되는 데이터만 복제할 수 있다. 여기선 “예, 기존 객체를 복제합니다.”를 체크 후 “제출” 버튼을 클릭한다.


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3c6200d7-7017-4ba7-b27f-b3aefbcf79c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=9ae631d7d8ffdc0cc800de594b64c826f87b2235449b2639cd4649295391e8a7&X-Amz-SignedHeaders=host&x-id=GetObject)


	“완료 보고서” 탭에서 “완료 보고서 생성” 옵션을 체크 해제 후 “저장” 버튼을 클릭한다.

3. 버킷 복제 검증하기

	원본 버킷 확인


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9161b0c5-2b24-4a22-9fe6-bf4455d0c1dd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110831Z&X-Amz-Expires=3600&X-Amz-Signature=82f7e0c29569a2a4838a219e61c31bf07806c35b746500064e2727d8ee5cd84c&X-Amz-SignedHeaders=host&x-id=GetObject)


	버킷 복제를 설정한 원본 버킷 정보 페이지로 이동하여 “객체” 탭에서 “버전 표시”를 활성화 한 후 객체 정보를 확인해본다.


	복제 버킷 확인


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b22a063d-482b-4ae3-8ffc-dd37f88aced8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110830Z&X-Amz-Expires=3600&X-Amz-Signature=d0c32877b2429890edf75c170c64bb243efdf86f7b9612775f477462aac2acab&X-Amz-SignedHeaders=host&x-id=GetObject)


	복제 엔드포인트로 설정한 버킷 정보 페이지로 이동해 “객체” 탭에서 “버전 표시”를 활성화 한 후 객체 정보를 확인해보면 원본 버킷내에 존재하는 모든 객체가 복제되었으며 버전 이름도 동일한 것을 확인할 수 있다.


	원본 버킷에 파일 업로드


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6a39b8d3-f925-44f1-8fe1-b5a1da5a8ce5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110831Z&X-Amz-Expires=3600&X-Amz-Signature=10e1acea994ddc7f9b9698f6328ed29e0d6fae895cca9a17dddc9b5a9ac339f8&X-Amz-SignedHeaders=host&x-id=GetObject)


	원본 버킷에 기존 버전이 “null”로 되어있던 임의의 파일(여기선 “beach.jpg”파일)을 루트 디렉토리에 업로드하여 버전을 갱신한다. 버전ID를 기억하도록 한다. 여기선 “xSRTyAsh58.E8C_Oc5ZBGZ2pUM9VtkIi”가 해당 객체의 버전ID이다.


	복제 버킷에서 확인


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/28c31411-6a2e-4df4-9d82-676d5d363baf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230916T110831Z&X-Amz-Expires=3600&X-Amz-Signature=d44a8d890ee644cb26e7cd4b9e621895687e9301984acd9d71561fdce0e1b27f&X-Amz-SignedHeaders=host&x-id=GetObject)


	복제된 버킷에서 볼 수 있듯이 “beach.jpg” 객체의 버전ID가 “xSRTyAsh58.E8C_Oc5ZBGZ2pUM9VtkIi”로 동일하다.


	※ 이로서 버킷 복제는 서로 다른 리전간 복제가 가능하며 비동기로 처리되는것을 확인할 수 있다.


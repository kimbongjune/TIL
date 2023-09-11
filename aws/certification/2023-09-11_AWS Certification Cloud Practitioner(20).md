
### S3 핸즈온

1. 실습 전 파일 다운로드

	[index.html](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b3bb53f0-a0e6-4435-8abc-87fd8a67f844/index.html?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122947Z&X-Amz-Expires=3600&X-Amz-Signature=c9a017da54ef760b970b5abbc70d0902eb378166ff3cbff04e189f9924e02c77&X-Amz-SignedHeaders=host&x-id=GetObject)


	[beach.jpg](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f164abd0-e149-4289-8377-921669125ef9/beach.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122947Z&X-Amz-Expires=3600&X-Amz-Signature=ed74ec6351abe10e42fa7035484a560ded732012d4dd811d2c54a6bcc881d968&X-Amz-SignedHeaders=host&x-id=GetObject)


	[coffee.jpg](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/46729ace-97a9-49eb-a273-bb369465d291/coffee.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122947Z&X-Amz-Expires=3600&X-Amz-Signature=68ebca7d91fb180ed0e42094d3dd09ae0f99db79feac82de419cbeccfdf71a40&X-Amz-SignedHeaders=host&x-id=GetObject)

2. S3 버킷 생성하기

	![검색창에 “S3”를 검색하여 S3 서비스 콘솔로 이동 후 “버킷 만들기” 버튼을 클릭하여 버킷을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1ae883c4-0357-4bed-871f-b6a4a659d172/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=34221cce6fc8e6ad1cec07d6a481716e39b5f848ab0db9c83b179547267a67ae&X-Amz-SignedHeaders=host&x-id=GetObject)


	_**off the record(동일한 버킷 이름 생성시 발생하는 현상 확인)**_


	![버킷 이름에 “test”를 입력 후 “버킷 만들기” 버튼을 클릭하면 test라는 버킷 이름은 AWS내의 다른 사용자가 이미 사용하고있는 버킷 이름이기 때문에 사용할 수 없어 에러가 발생한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2cbe6baa-37e9-42fc-8b1a-cd07ad563106/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=8daaddf8cb21ca09a2b8b1dc4d41407c28e9efd3a729d075715ee830140dd009&X-Amz-SignedHeaders=host&x-id=GetObject)


	일반 구성


	![AWS 내에서 사용된 적 없는 고유 버킷이름을 입력 후 리전을 선택한다. 리전은 본인 현재 위치와 가장 가까운 리전을 선택하면 지연시간이 제일 적다. 여기선 테스트를 위해 임의의 리전(us-west-2)로 사용하였다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0717faea-08ce-4ff8-a11c-f0bd27c49b20/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=1bd37db5b5a466f1547462ebb7a9fa308f5196b7b41c6eebef12a4915a22a83b&X-Amz-SignedHeaders=host&x-id=GetObject)


	객체 소유권


	![기본값인 “ACL 비활성화됨(권장)” 을 사용한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/83c96cf1-2780-41bb-adfa-7931555cc832/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=1788ada050b98ad7f0afc27f601ace47aaf91410ed8e7123a7baa99df2ce956b&X-Amz-SignedHeaders=host&x-id=GetObject)


	이 버킷의 퍼블릭 액세스 차단 설정


	![기본값인 “모든 퍼블릿 액세스 차단)”을 사용한다. 보안 단계가 한단계 추가된 샘이다.
	생성 후에도 버킷 옵션에서 변경할 수 있으며 추후 실습 할 예정이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/be087b5b-7f24-4528-974f-627f0d21bdf4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=bfd77c74ec763a32d56c3864485972e6ec8ea003e5235c27a507405c0f075f71&X-Amz-SignedHeaders=host&x-id=GetObject)


	전체 설정 확인 및 버킷 생성


	![위에서 설명한 본문 외의 설정은 건드리지 않았다. 설정을 확인 후 “버킷 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e7e73505-e6f1-4cc0-b2a0-8f2406e1f997/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122948Z&X-Amz-Expires=3600&X-Amz-Signature=f8aec063f1eeb2635a32a4d8889ad2353b91824bd72b02c94e3836b529123c6a&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 버킷 살펴보기

	![정상적으로 버킷이 생성되었다. 이름을 클릭하여 버킷 정보 페이지로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f27d397d-b888-4bd0-937f-67fef3dbe74f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=4ed9215960395f167d639774d9f49e7135cdf0a04c943b28310aa2af4e0fd609&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버킷 정보 페이지에서 해당 버킷에 대한 상세 정보를 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/40a2adf4-beb1-4cc1-aeb4-80b1fbee5d56/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=35cc708bb2752f53713d4d63c6bd64aba485bf5c6cdcc883d97358cfa8098bd6&X-Amz-SignedHeaders=host&x-id=GetObject)

4. 객체 업로드하기

	![버킷 정보 화면에서 “업로드” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3221ec21-365a-443d-8371-51d7a5c97a64/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=69479878cccb37e905c141937fcb43df83ccffaa7e4852d3621f212396c3b756&X-Amz-SignedHeaders=host&x-id=GetObject)


	![드래그 & 드랍 또는 “파일 추가” 버튼을 클릭하여 위에서 6-2-1에서 다운로드받은 coffee.jpg 파일을 업로드한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9b2b68a6-9b88-4e0f-b080-a402f3dd53f3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=a28cae3f98b2a841427f0ce50153c4b3b04319e0a0ad497403afd6216b51c48a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![coffee.jpg가 업로드 할 객체가 올라간 것을 확인할 수 있으며 아래 대상이 현재 파일이 저장될 위치 이다 현재는 버킷의 루트이다. 또한 파일에 권한과 속성 등을 설정할 수 있지만 추후 다루기 때문에 지금은 “업로드” 버튼을 클릭하여 객체를 업로드한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ad56f7ee-8668-46de-b242-4853fef4d634/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=67c3453371ed002a86cb772725d554d3db7e344583b95f25237aaf3245beb300&X-Amz-SignedHeaders=host&x-id=GetObject)


	![객체가 정상적으로 업로드 되었다. “닫기” 버튼을 클릭하여 버킷 정보 페이지로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d218d7c4-f0b5-42b8-96a4-62bc66f60718/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122949Z&X-Amz-Expires=3600&X-Amz-Signature=7809f4509f0bdef2a538621c7ee47a0ae4c7bf92b2436250c77813a7dc63df6b&X-Amz-SignedHeaders=host&x-id=GetObject)

5. 업로드 된 객체정보 확인하기

	![버킷 정보 페이지에서 객체 이름을 클릭하면 해당 객체에 대한 정보 페이지로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e4b6a298-c301-4dbb-9a66-d688ea614b8f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122950Z&X-Amz-Expires=3600&X-Amz-Signature=253437118da8722a7195b92ffe8e2ecc3702cddaff08f2217dc9549ccae31e49&X-Amz-SignedHeaders=host&x-id=GetObject)


	![업로드 된 객체의 정보(이름, 소유자, 리전, 크기, 유형, URL) 등을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ca4a69f5-f821-423a-af45-9d12b8979fde/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122950Z&X-Amz-Expires=3600&X-Amz-Signature=0234fb3bbeff626bf20f8d0b20cebb190f808d52fc984618b103169a1a8b3535&X-Amz-SignedHeaders=host&x-id=GetObject)

1. 객체 열기

	S3버킷에서 객체를 여는 방법은 두가지가 있다.


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7f5aadfa-d846-49d8-adbd-99e7142981ad/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122950Z&X-Amz-Expires=3600&X-Amz-Signature=8fd6618f559b1235321a0c193f412f43dc4e9121815223bd2eb8242547076f04&X-Amz-SignedHeaders=host&x-id=GetObject)

	1. S3 콘솔에서 직접 열기

		위 사진에서 빨간색으로 표시한 “열기” 버튼을 클릭한다.


		![새 탭에서 특이한 URL을 동반하여 사진이 열리는 것을 확인할 수 있다. 이러한 URL을 “미리 서명된 URL” 이라고 한다. 로그인 한 AWS 계정의 자격 증명이 해당 URL 안에 포함되어있어 퍼블릭 접근 권한이 없어도 파일이 열리는 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/532a38e1-8f5e-4a90-92e0-2a9096602f26/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=fc26ad2bc7c00cc8d260a681d907102058ecf399dea8b95199f55773b8ff3e1e&X-Amz-SignedHeaders=host&x-id=GetObject)

	2. 객체 URL을 이용한 열기

		위 사진에서 초록색으로 표시한 “객체 URL”을 복사하여 브라우저의 새 탭에서 이동한다.


		![단순한 URL과 함께 에러 XML이 화면에 출력된다. 위 에러는 객체에 접근 권한이 없어서 발생하는 에러이다. 6-2-2에서 설정한 “이 버킷의 퍼블릭 액세스 차단 설정” 옵션때문에 발생한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6f1603f5-6ea2-40d6-8e6b-0184c579c7b1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=0ae00f893d24edfc0b27d3789bfdac70c45a6ea8848346b486b738ebc5694869&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 퍼블릭 액세스에 대한 허용은 다음 실습 때 진행하므로 지금은 넘어가도록 한다.

2. 폴더 생성하기

	![버킷 정보 페이지로 돌아와 “폴더 만들기” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9998618e-96b8-4abe-9df9-3a054b10bce6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=409d93375bb11fe4b183d55e236517bda082b4c9b027a73a9de0d01716339b7f&X-Amz-SignedHeaders=host&x-id=GetObject)


	![임의의 폴더명(여기선 “images” 라고 작성하였다)을 작성 후 “폴더 만들기” 버튼을 클릭하여 폴더를 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2dade295-cd20-4191-9c4a-b5691e41443d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=7d292e2c0797b3e7c8d1497d711f372d37ac1c9110a3d50a55d10c37079d4aec&X-Amz-SignedHeaders=host&x-id=GetObject)


	![폴더가 정상적으로 생성되었으며 해당 폴더에 객체를 업로드 할 수 있게 되었다. 해당 폴더 이름을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e978077d-5acf-428d-85b1-16d41297ca7c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=8740bc256511cd2ccd8b788e522a14d8fa2976045d74a749e0f61752222a426e&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 폴더 안에 객체 업로드하기

	![“업로드” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/63381d04-afac-4091-b066-a0ec99a035c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=ed051430cfa4a7654331cf7d4e490ee45910068a32468706a3680274e8fdddf2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![6-2-1에서 다운로드한 “beach.jpg”객체를 업로드한다. 대상 탭에서 볼 수 있듯이 경로가 루트가 아닌 것을 확인할 수 있다. “업로드”버튼을 클릭하여 객체를 업로드한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/720814f1-e6bf-4ab8-a431-f4bb2a874fe5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122951Z&X-Amz-Expires=3600&X-Amz-Signature=c1236fe48dbce0066b964a3d95d56d4f4ad46eff6fb5224bfee75bea53f3a14a&X-Amz-SignedHeaders=host&x-id=GetObject)

4. 객체 삭제하기

	![위 경로를 클릭하여 버킷의 루트로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e38da3be-144c-46d6-a92c-64c329f63420/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122952Z&X-Amz-Expires=3600&X-Amz-Signature=cb7ee67c1635aae12bd5f350bc16150b558c3f292c64d56f24ed472bd4b0b8ef&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제하고자 하는 폴더 혹은 객체를 선택 후 “삭제”버튼을 클릭한다. 여기선 “images” 폴더를 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d2f9e93a-9640-4cd6-b7e2-84a4471ba647/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122952Z&X-Amz-Expires=3600&X-Amz-Signature=dc5fa573b5154e2fec1982759f611d0c5c54e45987a3f6e5e303f42c98852c75&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“영구 삭제”를 입력하여 삭제에 대한 확인 후 “객체 삭제” 버튼을 클릭하여 객체를 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/62809dcd-6173-46ea-bca3-0fe970b584ad/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122952Z&X-Amz-Expires=3600&X-Amz-Signature=0d31478a41746d6bbf2bffa4cac093e3d3a5617506280d066d91b0a9e9d7b205&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 객체나 폴더 삭제시 영구적으로 삭제되며(버전 or 복구옵션 비활성화시) 폴더를 삭제할 경우 폴더 안의 객체도 같이 삭제된다.


	![객체가 정상적으로 삭제 되었으며 “닫기”버튼을 클릭하여 버킷의 루트로 돌아간다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2474d4a9-49cf-4ed1-ba1d-221bdbe2dc64/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122952Z&X-Amz-Expires=3600&X-Amz-Signature=ef3a07e124fc6665668c045464437ced9e991fa7d4909b5dba44afe22c7ea6f3&X-Amz-SignedHeaders=host&x-id=GetObject)


	![images 폴더가 삭제되어 목록에 표시되지 않는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7209aac6-750d-4af5-a9ff-f351b158ca83/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122952Z&X-Amz-Expires=3600&X-Amz-Signature=76cd31d94d185802df6c1d2e2cc2c9839cc61be89bcf7892db8b27efff383421&X-Amz-SignedHeaders=host&x-id=GetObject)


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

		![AWS 내 존재하는 IAM 유저의 경우 IAM 정책을 이용해 버킷에 액세스가 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cad8cf48-87dc-4f32-9f5b-01253d03908b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122957Z&X-Amz-Expires=3600&X-Amz-Signature=0e46875494ee9fea7ed794294be8d88add25f851d41b998f58e65a684a4bedc9&X-Amz-SignedHeaders=host&x-id=GetObject)

	- S3 버킷 정책을 이용한 퍼블릭 액세스

		![AWS 계정이 아닌 웹사이트 접속 사용자가 객체를 읽기 위해선 S3 버킷 정책에 퍼블릭 액세스 정책이 필요하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53e4a3af-0c95-43e4-b3e3-e794c9c74770/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122958Z&X-Amz-Expires=3600&X-Amz-Signature=334822d5af9a6095c271381a28e6604dd622518b2ba30e78345e5d439388de92&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 다른 서비스에서 S3 액세스

		![EC2 인스턴스에 직접 IAM 정책을 부여할 수 없으니 EC2인스턴스 역할에 IAM 권한을 부여하여 버킷에 액세스가 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/541e835f-88f0-4214-8b6a-c13da99d9ef0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122958Z&X-Amz-Expires=3600&X-Amz-Signature=569c6231a1bb7c5da7a4543c0977232aa9525603a1f1de0e3e08f63e631388d1&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 교차 계정 액세스(다른 AWS 계정 내 IAM 유저)

		![퍼블릭 액세스 정책이 아닌 교차 계정 액스(Allows Cross-Account) 권한을 부여하여 올바른 버킷 정책을 수립한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/76c61fd8-3447-433f-b2f3-58e6987d46c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T122958Z&X-Amz-Expires=3600&X-Amz-Signature=15175ed85372ddbc28ccf0bae754023ec4ae40690ec4b1f1022925c61c435430&X-Amz-SignedHeaders=host&x-id=GetObject)

1. 버킷 정책 종류
	- 제이슨 기반 정책(Json based policies)

		IAM 정책에서 사용했던 Json 포맷과 비슷한 형태를 띄고있다.


Resource : 어떤 객체와 버킷에 액세스 권한을 부여할지 정의함


Effect : 허용 또는 거부


Action : 허용 또는 거부할 일련의 API


Principal : 접근할 사용자에 대한 정의


![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/56eefa12-4a48-4a05-b1f2-3c3e4cc2a7b3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230911T123014Z&X-Amz-Expires=3600&X-Amz-Signature=52d2188f915cfd4865324e7762d625b42a560b6e1334b7ea6af224be3919c8a4&X-Amz-SignedHeaders=host&x-id=GetObject)

	- S3 버킷 정책
		- 버킷에 관한 공용 액세스 권한을 부여할 수 있다.
		- 객체를 암호화 해서 업로드할 수 있다.
		- 교차 계정 액세스를 이용해 다른 계정에 액세스 권한을 부여할 수 있다.

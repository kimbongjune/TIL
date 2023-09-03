
### IAM 정책

- IAM 정책 구조
	- IAM 정책은 JSON 파일로 관리된다. 아래의 예시로 확인할 수 있다.

		![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ba03ce26-6b3a-4d9d-b6a5-439da5f58267/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094423Z&X-Amz-Expires=3600&X-Amz-Signature=3fb78d5f21f2e3703520048ee1b3c161485f1a4fa3460f9396e51c1d296e5590&X-Amz-SignedHeaders=host&x-id=GetObject)


		version : version은 보통은 날짜로 되어있으며 정책 언어의 버전이다.


		id : 정책을 식별하는 고유 식별번호(선택사항)


		statement : 하나 이상의 정책 문장

		- Sid : 문장 ID로 문장 식별자(선택사항)
		- Effect : 문장이 특정API에대한 접근을 허용(Allow)할지 거절(Denny)할지에 대한 내용
		- Principal : 해당 정책이 적용 될 사용자, 계정, 역할
		- Action : Effect에 기반해 허용 혹은 거부 할 API의 호출 목록
		- Resource : 적용 될 Action의 리소스 목록
		- Condition : 해당 예제에는 없지만 statement가 적용 될 시기를 결정

### IAM 정책 실습

1. 권한 적용 확인하기

	IAM 권한은 적용 즉시 반영된다. Root 계정으로 로그인 한 AWS 콘솔과, 이전에 생성한 admin 유저로 로그인 한 AWS 콘솔 두개를 띄워놓고 확인한다.


	admin 계정으로 IAM 유저 목록 확인(admin 계정으로 진행)


	![“IAM” 서비스의 “사용자” 탭으로 이동한다.
	admin 계정은 관리자 권한을 부여한 그룹 내에 속해있기 때문에 현재 계정의 유저 목록을 확인할 수 있다. 유저의 권한 삭제가 반영되는지 확인하기 위해 해당 페이지에서 이동하지 않는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/62a29e66-522f-4c2d-9130-73c924078809/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=1d982c7680c294a309807499112d7a1ae7d9eda76e74a9dad7c037420066b515&X-Amz-SignedHeaders=host&x-id=GetObject)


	Root 계정으로 admin 그룹에서 admin 유저 삭제(Root 계정으로 진행)


	![“IAM” 서비스의 “사용자 그룹” 탭으로 이동하여 “admin” 그룹을 클릭하여 그룹 요약 탭으로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6b893d35-6382-4851-8ecf-0ac71bbd783b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=e717efe7123bee984db15186fda9ed9827c8ff5947d527ade8e348baa7ec5953&X-Amz-SignedHeaders=host&x-id=GetObject)


	admin 그룹에서 admin 유저 삭제


	![“admin” 유저를 체크 후 “삭제” 버튼을 클릭하여 현재 그룹에서 유저를 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3a1773e-5865-47dc-b8bb-1d75224afee7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=67c225d7456e7d9dcc04d2da5980f837f686ff9966de956b6776c32c30d7ac26&X-Amz-SignedHeaders=host&x-id=GetObject)


	삭제 재확인


	![텍스트 입력 필드에 삭제하고자 하는 유저 이름을 입력 후 “삭제” 버튼을 눌러 유저를 그룹에서 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/489dcbc4-5d0d-42d9-8f16-3a2d04c62396/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=70d935d9cda37e6ed22daebb1057c93fb7f6a8084a36020ab99a128fa6a71ddc&X-Amz-SignedHeaders=host&x-id=GetObject)


	삭제 완료


	![유저가 그룹에서 삭제가 정상적으로 실행되면 위와 같은 화면이 출력된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2199c929-b881-43ec-8dcf-137a3bf502c7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=c237357d609448a40807efe92cd8e07e2975056b8ad27f87275530e89ef7f884&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 박탈 확인(admin 계정으로 진행)


	admin 계정의 AWS 콘솔에서 새로고침한다.


	![정상적으로 해당 유저에 대한 권한이 박탈 된 것을 확인할 수 있다. 이 또한 유저에게 새로운 권한을 부여 후 확인하기 위해 페이지에서 이동하지 않는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0af7bbef-b5ad-4c10-ac5c-6b556894d06c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=cf7cebddf9cd31876d9a1b45e1bba9b60ea4a1ca08f6811744044918f80ea1f2&X-Amz-SignedHeaders=host&x-id=GetObject)


	특정 유저에게 권한 부여하기(Root 계정으로 진행)


	![“사용자” 탭에 들어가 권한을 부여 할 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/303e0b69-59f6-4373-b7c7-e5ecda8a8587/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=39c4eb7055ea0f6106acc3f205809d6211e46eda5053d044defb899efbf8740e&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 추가


	![“권한 추가” 드롭박스를 클릭하면 “권한 추가” 와 “인라인 정책 생성” 옵션이 표시된다. 여기서는 “권한 추가” 를 클릭해 기존 AWS 권한에 해당 유저를 연결 할 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3581bc9-2285-4d3b-8987-a6f9c01227d9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=b1419dc0ab6b2151c6f968332078919d1e05b2c850b203a1ca4d26e3dcdf1bbc&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 권한 추가 : 이전에 그룹 생성시 그룹에 권한을 부여했던 것과 같이 AWS에서 제공하는 기본 권한 목록을 선택하여 부여하는 것이다.


	※ 인라인 정책 생성 : AWS에서 제공하는 기본 권한 목록 내의 세부 항목을 사용자가 선택하여 별도의 권한 정책을 생성 후 부여하는 것이다.


	IAM 읽기 권한 추가


	![“직접 정책 연결” 체크박스를 체크 후 하단의 AWS 정책 목록중 “IAMReadOnlyAccess” 정책을 찾아 체크박스를 체크 후 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/215b1f15-6f0d-4bd1-b1f2-700ac5791b9b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=78a461a23848117b313e9160b181dd371ba2839e3695c94327747ffa7f65575c&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 한번 권한 부여에 대한 내용을 확인 후 “권한 추가” 버튼을 클릭하여 권한을 부여한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2a183dcc-a994-4594-9285-bb9b270baff6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=e505ad67f452ee4c478ef28c537cd3c801b7497b2b3b7690a6f0159825a63031&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 추가 완료


	![정상적으로 admin 계정에 대해 “IAMReadOnlyAccess” 권한이 부여되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fb8b82b6-7736-4bf2-adc0-5b96116ee42a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=426494624b137657ab463f7d2473268bd9bec524fae45f6e62f0a7a19d993472&X-Amz-SignedHeaders=host&x-id=GetObject)


	부여된 권한 확인(admin 계정으로 진행)


	admin 계정의 AWS 콘솔에서 새로고침한다.


	![정상적으로 사용자 목록을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/18fe247c-65db-4814-b1f5-515c8de1a096/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=0bd771a3a3728b04c5667d6579bc0a9f497de39830ff1987c57430e875e65d1e&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한이 부여되지 않은 작업 수행


	![“사용자 그룹” 탭에서 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1448ea56-1fcd-4198-bfdd-ae1db855c1ca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=b465ba13993d7d7bbb469d5295d6ceeb60a4d8757e20539fcb411d3c11313eec&X-Amz-SignedHeaders=host&x-id=GetObject)


	![별도의 추가작업 없이 사용자 그룹 이름 작성 후 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/52c1336e-b23f-4c0c-91d0-770b2e3f260c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=7a38a66212950ba5d90b73bfe77e99de8f02973f517cb456a1a376fea04d767d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![현재 admin 계정은 그룹을 생성 할 권한이 없기 때문에 그룹이 정상적으로 생성되지 않은 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7ee3cf4f-4293-4f67-b777-c526234df266/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=b93931abca653b23a494245f8ddc4666b5c38a90c058a500dbbb00cc87ab99df&X-Amz-SignedHeaders=host&x-id=GetObject)


	사용자의 권한 목록 확인(Root 계정으로 진행)


	다시 admin 유저를 admin 그룹에 추가한다.


	![“사용자 그룹” 탭에서 그룹 이름을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2772d824-77a8-400e-86db-fa44ffef3aba/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=3a9705bd8bfa7112624dd843b8dce49a92ab3f996ae364e617351552c48401ca&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“사용자 추가” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/84f4e4fd-accd-4b34-bff8-22908af00a40/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=8541b6cbc1d9de8354e34b8ad6cd121011ec193ea47d58da814ad67558234ef5&X-Amz-SignedHeaders=host&x-id=GetObject)


	![그룹에 추가 할 사용자를 체크 후 “사용자 추가” 버튼을 클릭하여 사용자를 그룹에 추가한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d13ebbf8-138c-4e3c-9ec0-9244af80210d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=042b5503271d32637ca7c29106b3f22319bb2ce376261f1a78994b0c69b4d276&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 유저가 그룹에 추가 되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f7c84492-3d36-44a6-b96d-e51da3c512c9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=0b9a5c01dcd1d4ea84a81453ecee28f0f4d9953a5533e696c23f7087d2118237&X-Amz-SignedHeaders=host&x-id=GetObject)


	새로운 그룹 생성


	![“사용자 그룹” 탭의 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0cca6806-224b-48e9-bb06-730f2a0c6897/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=ed8abcd2bdd0e38890d6fff5f1e8db09b34bbc04fe89d098fc902ce0c4fe1f56&X-Amz-SignedHeaders=host&x-id=GetObject)


	![테스트 후 삭제 할 것이기 때문에 임의의 그룸 이름을 입력하고 생성 할 그룹에 추가 할 사용자를 체크 한 뒤 아무 권한이나 체크한다. 여기선 “AWSDirectConnectReadOnlyAccess” 권한을 부여 해 볼 것이다. 이후 “그룹 생성” 버튼을 클릭해 그룹을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2017e475-c2e2-4a85-a3e6-3acc091dce5f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=7eef8140634d38d9c22700670487410cc90d36d85ca9b3b1f08952e887a7af07&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 “test” 그룹이 생성되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2b5b780c-7cd0-4a0b-ab81-21aab335f80b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=fb8074a261f681fd612637443858163abc9dfdb3bc0f53610750d8fa028fc050&X-Amz-SignedHeaders=host&x-id=GetObject)


	유저의 권한 목록 확인하기


	![“사용자” 탭에서 권한을 확인 해 볼 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d563e6eb-6b30-456c-b939-d395f52390c7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=f2bf48794d0df630f8bb2001aa31595260bfb8757de0761e83a383f1e1c74d4b&X-Amz-SignedHeaders=host&x-id=GetObject)


	![해당 유저에 부여되어있는 권한을 확인할 수 있으며 권한 별로 연결방식을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/893931c9-fe25-438f-902e-849de6af8660/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=7a33d03dd659f2cbea49dbefeaf35b0aa2fc446ddbde6daec27e060187c8fc00&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 정책의 작동 방식


	![“정책” 탭에서 “AdministratorAccess” 정책을 찾아 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b6f01f1-d40e-4f3d-9a42-0f10b7faa486/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=ea7fb9c6ff59b2944755fbeaee5b96648ba72f2a1110291c66dffcf3242fef48&X-Amz-SignedHeaders=host&x-id=GetObject)


	![대시보드 안의 “{}JSON” 버튼을 클릭하여 “AdministratorAccess” 권한 정책에 대한 JSON 포맷을 확인해본다. 위의 2-3 항목에서 봤던 JSON 형태와 동일한 형태의 JSON 포맷이 보일 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d9b77b88-7553-4e86-9556-d32609a9a7ca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=7f4ff60c26abb064f003088c693af8036c793fa01d570d537efe876405c977ae&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ AdministratorAccess : 위 JSON 포맷에서 볼 수 있듯이 권한을 허용(ALLOW) 하고 모든 API 목록(Action)에 대해 허용하며 모든 API 내의 리소스(Resource)에 대한 권한 임을 확인할 수 있다. 


	정책 생성 하기


	![“정책” 탭에 접속하여 “정책 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/90c086af-6ee7-4a16-8c7f-038631b8f468/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=4917ef9f0b69dcebe32e42edf63c17911cf65aa4bb332c2ccdaf039fb3804527&X-Amz-SignedHeaders=host&x-id=GetObject)


	정책 생성 방법에는 두가지 방법이 있다.

	- 직접 JSON 파일을 작성하는 방법
	- 비주얼 에디터 사용하기
	- 직접 JSON 파일 작성하기

		![해당 과정에서는 JSON파일을 직접 작성하여 정책을 생성하지는 않을 것이나, 정책을 생성하기 위해선 “JSON” 버튼을 클릭 후 아래 JSON파일을 포맷에 맞춰 작성하면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/38ae4498-25ee-4a94-b514-dfc024cf6f4b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094426Z&X-Amz-Expires=3600&X-Amz-Signature=b85ba378760afb35d6a30db734aaf178a3228bbf8d784b2511b50be2d945fa9a&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 비주얼 에디터 사용하기

		![“시각적 편집기” 버튼을 클릭 후 “서비스 선택” 을 클릭하여 정책 목록을 조회한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6dd424b0-670d-4c67-a688-66df27d694f5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=aa86ff8cb89bc253efcbcd94830d3ae6d5dec2b8310c432c75b473e62f4b0f05&X-Amz-SignedHeaders=host&x-id=GetObject)


		![여기선 임의의 권한을 부여하기 위해 “IAM”을 검색 후 “IAM”을 클릭한다. 그러면 IAM 하위의 Resource 목록이 조회 될 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/17e4d9a9-2351-4437-ba57-fee12f4f22a9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=61f220624fa890d79987b9566bfdc487319dae4a2b67d8127a744e581839c39c&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“ListUsers”검색 후 체크한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91500790-339c-4c08-a4c0-4b1fef7c7c0d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=32860b01bce38baeebdd0abadeb12a00bbb65ec3cffdb0b746c5cb9edd4a584e&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“GetUser” 검색 후 체크 한 뒤에 “리소스” 를 클릭해 리소스 지정 항목을 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bf6786bc-9618-4fa9-a5c2-f847661a5381/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=d63c7b98f3ff0f275231a9d551e77d8e4b05c09c536ba5f7ec3fb1172e8f3798&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“모든 리소스” 를 체크 한 뒤 “JSON” 버튼을 클릭하여 작성한 권한이 JSON파일에 반영 되었는지 확인해본다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a856a8eb-33d0-423d-b49c-78aea40bc8da/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=e5168540a9103ea4931a7dfd2fa9c8c9a809f46d051d16e61661e9bb3cb90ffd&X-Amz-SignedHeaders=host&x-id=GetObject)


		![정상적오르 JSON파일에 반영 된 것을 확인할 수 있다. 여기선 실제로 정책을 생성하지는 않을 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a33e4869-ff6f-48c5-b64d-d811fd479b95/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094427Z&X-Amz-Expires=3600&X-Amz-Signature=00b868a799363f429d96547bb5c072456ad4f94fa6ce97c5e76d894b70aaf6c5&X-Amz-SignedHeaders=host&x-id=GetObject)


	그룹 삭제하기


	기존 admin 계정에 추가했던 test 그룹을 삭제한다.


	![“사용자 그룹” 탭에서 삭제 할 그룹을 체크 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/22aa5f55-caea-44c1-a46f-f6da6e6b1dc4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=e85897dbfb121aa42f2a0708afdb532ebffd9013d086480330805de67f27d942&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제 할 그룹 이름을 재입력 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6929587d-58aa-4340-875b-2f086c2383f9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=91f480d1601861606c1aa6e7d2778beeb56dd55ec84f6ded2bfead611f7b0b28&X-Amz-SignedHeaders=host&x-id=GetObject)


	※주의 : 위 문구에서 볼 수 있듯이 그룹을 삭제하면 그룹에 부여되어있는 권한도 삭제되기 때문에 그룹에 속해있는 유저들의 권한도 동시에 박탈된다.


	![정상적으로 그룹이 삭제되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d4f500ba-01fd-4bb9-95df-5c1930d4ce50/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=8b3229768195fce0653c684569b55fc04808fadf16fb0ee9e75406f118eff02e&X-Amz-SignedHeaders=host&x-id=GetObject)


	사용자의 권한 박탈하기


	![“사용자” 탭에서 특정 권한을 삭제 할 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4b58032d-2734-41a3-b663-71492076fe41/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=4b2d7b5517e7e6fcd6c4048058be4685ce0a80d80d5de3e612a996874eed30ff&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제 할 권한을 체크 후 “제거” 버튼을 클릭하여 사용자에게 부여되어있는 특정 권한을 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/94d41213-73e7-4460-806b-497b9a3fbdd4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=6246f1559b68c8360153f0c5adc162b604c456602b0d8bc1939a1cc2066f5699&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Alert 창에서 확인을 누르면 정상적으로 권한이 삭제된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/09623a34-cad6-465e-b754-05487f8f00db/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094424Z&X-Amz-Expires=3600&X-Amz-Signature=90ff3da65501e9c53d93a5b59eac96c0af89636b09f030b8b961b7adda78d05c&X-Amz-SignedHeaders=host&x-id=GetObject)


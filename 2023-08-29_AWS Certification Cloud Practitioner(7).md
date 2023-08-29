
### IAM 정책

- IAM 정책 구조
	- IAM 정책은 JSON 파일로 관리된다. 아래의 예시로 확인할 수 있다.

version : version은 보통은 날짜로 되어있으며 정책 언어의 버전이다.


id : 정책을 식별하는 고유 식별번호(선택사항)


statement : 하나 이상의 정책 문장

- Sid : 문장 ID로 문장 식별자(선택사항)
- Effect : 문장이 특정API에대한 접근을 허용(Allow)할지 거절(Denny)할지에 대한 내용
- Principal : 해당 정책이 적용 될 사용자, 계정, 역할
- Action : Effect에 기반해 허용 혹은 거부 할 API의 호출 목록
- Resource : 적용 될 Action의 리소스 목록
- Condition : 해당 예제에는 없지만 statement가 적용 될 시기를 결정

![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ba03ce26-6b3a-4d9d-b6a5-439da5f58267/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094120Z&X-Amz-Expires=3600&X-Amz-Signature=f22688b3c632face04b98827c5b7dffb41e7f07b5b27b1376aab18b8b8e8dcce&X-Amz-SignedHeaders=host&x-id=GetObject)


### IAM 정책 실습

1. 권한 적용 확인하기

	IAM 권한은 적용 즉시 반영된다. Root 계정으로 로그인 한 AWS 콘솔과, 이전에 생성한 admin 유저로 로그인 한 AWS 콘솔 두개를 띄워놓고 확인한다.


	admin 계정으로 IAM 유저 목록 확인(admin 계정으로 진행)


	![“IAM” 서비스의 “사용자” 탭으로 이동한다.
	admin 계정은 관리자 권한을 부여한 그룹 내에 속해있기 때문에 현재 계정의 유저 목록을 확인할 수 있다. 유저의 권한 삭제가 반영되는지 확인하기 위해 해당 페이지에서 이동하지 않는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/62a29e66-522f-4c2d-9130-73c924078809/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=c5f4009963700805f8cf4c94a3585550ab270b926166305d1d2e5bff2456141b&X-Amz-SignedHeaders=host&x-id=GetObject)


	Root 계정으로 admin 그룹에서 admin 유저 삭제(Root 계정으로 진행)


	![“IAM” 서비스의 “사용자 그룹” 탭으로 이동하여 “admin” 그룹을 클릭하여 그룹 요약 탭으로 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6b893d35-6382-4851-8ecf-0ac71bbd783b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=7d3f88a415116c7edea3f984280900e00c111999cd33c3111406d7b00788ffe5&X-Amz-SignedHeaders=host&x-id=GetObject)


	admin 그룹에서 admin 유저 삭제


	![“admin” 유저를 체크 후 “삭제” 버튼을 클릭하여 현재 그룹에서 유저를 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3a1773e-5865-47dc-b8bb-1d75224afee7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=419201833dd5452f6ee21215b14b5dc559d9119baa335607f5247fc09798515a&X-Amz-SignedHeaders=host&x-id=GetObject)


	삭제 재확인


	![텍스트 입력 필드에 삭제하고자 하는 유저 이름을 입력 후 “삭제” 버튼을 눌러 유저를 그룹에서 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/489dcbc4-5d0d-42d9-8f16-3a2d04c62396/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=3b6549851df5c8d94a99e5826b9eda4fbe1c7ea9134e19ad943b667b5e581481&X-Amz-SignedHeaders=host&x-id=GetObject)


	삭제 완료


	![유저가 그룹에서 삭제가 정상적으로 실행되면 위와 같은 화면이 출력된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2199c929-b881-43ec-8dcf-137a3bf502c7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=9c03810693333a80802c0743f29807940fd9fc8344d3f266a92185682038534e&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 박탈 확인(admin 계정으로 진행)


	admin 계정의 AWS 콘솔에서 새로고침한다.


	![정상적으로 해당 유저에 대한 권한이 박탈 된 것을 확인할 수 있다. 이 또한 유저에게 새로운 권한을 부여 후 확인하기 위해 페이지에서 이동하지 않는다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0af7bbef-b5ad-4c10-ac5c-6b556894d06c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=62460edfe174bd3287b5e0ea822c7afd17733e1b7edbc93ba4be2d0cd8f056ba&X-Amz-SignedHeaders=host&x-id=GetObject)


	특정 유저에게 권한 부여하기(Root 계정으로 진행)


	![“사용자” 탭에 들어가 권한을 부여 할 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/303e0b69-59f6-4373-b7c7-e5ecda8a8587/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=ea83c35f11fdc866979e71a7d05b66c44c58694b00a3cba610f4e133cc0cba71&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 추가


	![“권한 추가” 드롭박스를 클릭하면 “권한 추가” 와 “인라인 정책 생성” 옵션이 표시된다. 여기서는 “권한 추가” 를 클릭해 기존 AWS 권한에 해당 유저를 연결 할 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3581bc9-2285-4d3b-8987-a6f9c01227d9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=3450b7d607f2596f87a690fe71ba66da7944150eab4f8936a430cc5dcb92083d&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ 권한 추가 : 이전에 그룹 생성시 그룹에 권한을 부여했던 것과 같이 AWS에서 제공하는 기본 권한 목록을 선택하여 부여하는 것이다.


	※ 인라인 정책 생성 : AWS에서 제공하는 기본 권한 목록 내의 세부 항목을 사용자가 선택하여 별도의 권한 정책을 생성 후 부여하는 것이다.


	IAM 읽기 권한 추가


	![“직접 정책 연결” 체크박스를 체크 후 하단의 AWS 정책 목록중 “IAMReadOnlyAccess” 정책을 찾아 체크박스를 체크 후 “다음” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/215b1f15-6f0d-4bd1-b1f2-700ac5791b9b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=f19c44121853e0338dd8734bbec250215c681959cb414aed80d2f1ae2cba02ad&X-Amz-SignedHeaders=host&x-id=GetObject)


	![다시 한번 권한 부여에 대한 내용을 확인 후 “권한 추가” 버튼을 클릭하여 권한을 부여한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2a183dcc-a994-4594-9285-bb9b270baff6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=c8c5e9ce0152f10960e427c54eef4f1a607391230488cf3ac058082202ad920e&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 추가 완료


	![정상적으로 admin 계정에 대해 “IAMReadOnlyAccess” 권한이 부여되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fb8b82b6-7736-4bf2-adc0-5b96116ee42a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=10a1b2ec75d74ce1a469c2de6a33d9da8b20a66f1b8920276019b85e64a4c835&X-Amz-SignedHeaders=host&x-id=GetObject)


	부여된 권한 확인(admin 계정으로 진행)


	admin 계정의 AWS 콘솔에서 새로고침한다.


	![정상적으로 사용자 목록을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/18fe247c-65db-4814-b1f5-515c8de1a096/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094121Z&X-Amz-Expires=3600&X-Amz-Signature=6b3a25c8c2f909d3e122e77344326f8aeeef718112ad04c0918e9f0e4523c7ea&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한이 부여되지 않은 작업 수행


	![“사용자 그룹” 탭에서 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1448ea56-1fcd-4198-bfdd-ae1db855c1ca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=0d57f5f9276f537e0decc60bfb98c660ae68fb7e7e1aeedefc2fe9f86e11ed34&X-Amz-SignedHeaders=host&x-id=GetObject)


	![별도의 추가작업 없이 사용자 그룹 이름 작성 후 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/52c1336e-b23f-4c0c-91d0-770b2e3f260c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=7044e26a3fdf9cf4aedbe4af9ee1945d11db96158e0d6be2ff62f68f10cd4bc2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![현재 admin 계정은 그룹을 생성 할 권한이 없기 때문에 그룹이 정상적으로 생성되지 않은 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7ee3cf4f-4293-4f67-b777-c526234df266/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094121Z&X-Amz-Expires=3600&X-Amz-Signature=202961a58c13e6f81ec63e25fba7c2eaa40800199b7e5e39dccff367e9d0e4c7&X-Amz-SignedHeaders=host&x-id=GetObject)


	사용자의 권한 목록 확인(Root 계정으로 진행)


	다시 admin 유저를 admin 그룹에 추가한다.


	![“사용자 그룹” 탭에서 그룹 이름을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2772d824-77a8-400e-86db-fa44ffef3aba/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=4671451d061439869cef98b8acddf8a3539066efd2f6a95e37ecc0b9722bb55f&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“사용자 추가” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/84f4e4fd-accd-4b34-bff8-22908af00a40/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=38bfbcb5c14150bc64c98f803e460c5966fbc5d0424f84bfbb268f7e099a54d7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![그룹에 추가 할 사용자를 체크 후 “사용자 추가” 버튼을 클릭하여 사용자를 그룹에 추가한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d13ebbf8-138c-4e3c-9ec0-9244af80210d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=2af3d8a1644334d4b32c1afe06488d8f1008816b2d60979744cd1e3a9b95a636&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 유저가 그룹에 추가 되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f7c84492-3d36-44a6-b96d-e51da3c512c9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094121Z&X-Amz-Expires=3600&X-Amz-Signature=2ba6cd54e3cc6da8ad0bd197ae7d6e69f6cd3573261bc1f9cfc2ca5bdf08a2b4&X-Amz-SignedHeaders=host&x-id=GetObject)


	새로운 그룹 생성


	![“사용자 그룹” 탭의 “그룹 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0cca6806-224b-48e9-bb06-730f2a0c6897/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=8c28631aa5d0d07a3762c951c7f03f3d9eafe3f5e7c005dcd1272d36e4f966fc&X-Amz-SignedHeaders=host&x-id=GetObject)


	![테스트 후 삭제 할 것이기 때문에 임의의 그룸 이름을 입력하고 생성 할 그룹에 추가 할 사용자를 체크 한 뒤 아무 권한이나 체크한다. 여기선 “AWSDirectConnectReadOnlyAccess” 권한을 부여 해 볼 것이다. 이후 “그룹 생성” 버튼을 클릭해 그룹을 생성한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2017e475-c2e2-4a85-a3e6-3acc091dce5f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=988850a16fd8ea3f23cb442eaf72ccdc656734a8082d16ecc42e05a6afdb0d01&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 “test” 그룹이 생성되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2b5b780c-7cd0-4a0b-ab81-21aab335f80b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=d57d8473d7d7fd53cc8fd660db5d8c85d8311928e2c4b8ae75506bd9c1a02ea2&X-Amz-SignedHeaders=host&x-id=GetObject)


	유저의 권한 목록 확인하기


	![“사용자” 탭에서 권한을 확인 해 볼 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d563e6eb-6b30-456c-b939-d395f52390c7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=3c3302418f1c1ce45cf2b2a83a2e00f281055f73f15d6d9a441da6be6c5d1dfd&X-Amz-SignedHeaders=host&x-id=GetObject)


	![해당 유저에 부여되어있는 권한을 확인할 수 있으며 권한 별로 연결방식을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/893931c9-fe25-438f-902e-849de6af8660/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=c2ae570319446452c6fca523bee4c17a3ff47d36d1e678c06676ce7f2363de2c&X-Amz-SignedHeaders=host&x-id=GetObject)


	권한 정책의 작동 방식


	![“정책” 탭에서 “AdministratorAccess” 정책을 찾아 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b6f01f1-d40e-4f3d-9a42-0f10b7faa486/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=94b19ebb3443b9e8716915beae490e62cfea1be929538353f86267ed7b3179d3&X-Amz-SignedHeaders=host&x-id=GetObject)


	![대시보드 안의 “{}JSON” 버튼을 클릭하여 “AdministratorAccess” 권한 정책에 대한 JSON 포맷을 확인해본다. 위의 2-3 항목에서 봤던 JSON 형태와 동일한 형태의 JSON 포맷이 보일 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d9b77b88-7553-4e86-9556-d32609a9a7ca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=33b4d1e1ec151175542026395068338821752c8df72aae5d54fcf1beff32e17e&X-Amz-SignedHeaders=host&x-id=GetObject)


	※ AdministratorAccess : 위 JSON 포맷에서 볼 수 있듯이 권한을 허용(ALLOW) 하고 모든 API 목록(Action)에 대해 허용하며 모든 API 내의 리소스(Resource)에 대한 권한 임을 확인할 수 있다. 


	정책 생성 하기


	![“정책” 탭에 접속하여 “정책 생성” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/90c086af-6ee7-4a16-8c7f-038631b8f468/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094121Z&X-Amz-Expires=3600&X-Amz-Signature=0c88ba5af2c68b76a81f02fc5c34a28bd31a4c18f3625694fb04d7605153aa3d&X-Amz-SignedHeaders=host&x-id=GetObject)


	정책 생성 방법에는 두가지 방법이 있다.

	- 직접 JSON 파일을 작성하는 방법
	- 비주얼 에디터 사용하기
	- 직접 JSON 파일 작성하기

		![해당 과정에서는 JSON파일을 직접 작성하여 정책을 생성하지는 않을 것이나, 정책을 생성하기 위해선 “JSON” 버튼을 클릭 후 아래 JSON파일을 포맷에 맞춰 작성하면 된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/38ae4498-25ee-4a94-b514-dfc024cf6f4b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094123Z&X-Amz-Expires=3600&X-Amz-Signature=288324580ea654e098da6b2e3c7108ef59c6f1ac3ab6877a1c0b55091b1302d1&X-Amz-SignedHeaders=host&x-id=GetObject)

	- 비주얼 에디터 사용하기

		![“시각적 편집기” 버튼을 클릭 후 “서비스 선택” 을 클릭하여 정책 목록을 조회한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6dd424b0-670d-4c67-a688-66df27d694f5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=a3847f46f969de957a4df0351df822f55176b7896871d53a6fd77ad1e5929549&X-Amz-SignedHeaders=host&x-id=GetObject)


		![여기선 임의의 권한을 부여하기 위해 “IAM”을 검색 후 “IAM”을 클릭한다. 그러면 IAM 하위의 Resource 목록이 조회 될 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/17e4d9a9-2351-4437-ba57-fee12f4f22a9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=0390276597629b5c99f6842b815f632de35bc39fabf594dce5fd610d67da474f&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“ListUsers”검색 후 체크한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/91500790-339c-4c08-a4c0-4b1fef7c7c0d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=bfcbd07087efa62ccdc402c6738718793056cb8ae1d35eb862c9209e065ce046&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“GetUser” 검색 후 체크 한 뒤에 “리소스” 를 클릭해 리소스 지정 항목을 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bf6786bc-9618-4fa9-a5c2-f847661a5381/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=a825b8e72d82fc67ad4d880c1305bed486fb1abdac6ad43d1bb749d7c5c02189&X-Amz-SignedHeaders=host&x-id=GetObject)


		![“모든 리소스” 를 체크 한 뒤 “JSON” 버튼을 클릭하여 작성한 권한이 JSON파일에 반영 되었는지 확인해본다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a856a8eb-33d0-423d-b49c-78aea40bc8da/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=32470dec183e4200dcce220b28b9c0d61941c722ab3c9465543b5d07ebe942b9&X-Amz-SignedHeaders=host&x-id=GetObject)


		![정상적오르 JSON파일에 반영 된 것을 확인할 수 있다. 여기선 실제로 정책을 생성하지는 않을 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a33e4869-ff6f-48c5-b64d-d811fd479b95/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094124Z&X-Amz-Expires=3600&X-Amz-Signature=94384567f4f874c92ae5103133ae56dd27e2fed9bd62c718e885120658a1c26f&X-Amz-SignedHeaders=host&x-id=GetObject)


	그룹 삭제하기


	기존 admin 계정에 추가했던 test 그룹을 삭제한다.


	![“사용자 그룹” 탭에서 삭제 할 그룹을 체크 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/22aa5f55-caea-44c1-a46f-f6da6e6b1dc4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=a2bfbea35fcebd2877c8a4a7e68dddb465513b15689d7de501a7e960d9d22abd&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제 할 그룹 이름을 재입력 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6929587d-58aa-4340-875b-2f086c2383f9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=685ef1fb3592a426aeec13a37e804d4e1044c5e9bd7548e124ffd3aacfcb8a0b&X-Amz-SignedHeaders=host&x-id=GetObject)


	※주의 : 위 문구에서 볼 수 있듯이 그룹을 삭제하면 그룹에 부여되어있는 권한도 삭제되기 때문에 그룹에 속해있는 유저들의 권한도 동시에 박탈된다.


	![정상적으로 그룹이 삭제되었다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d4f500ba-01fd-4bb9-95df-5c1930d4ce50/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=5af37ab467c3388aa9c7a7cbd0c45a2b427f91d5affa007c8a8bac45ed4b5557&X-Amz-SignedHeaders=host&x-id=GetObject)


	사용자의 권한 박탈하기


	![“사용자” 탭에서 특정 권한을 삭제 할 유저를 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4b58032d-2734-41a3-b663-71492076fe41/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=7e7c8666ebb679598b7c1a48695c72ee177a079a77301d47f7b34c79d64e588c&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제 할 권한을 체크 후 “제거” 버튼을 클릭하여 사용자에게 부여되어있는 특정 권한을 삭제한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/94d41213-73e7-4460-806b-497b9a3fbdd4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094122Z&X-Amz-Expires=3600&X-Amz-Signature=abf2a2f2764cc707bcdb3d9f20d2f04a82d49924f41d38d518a9e2e4e761b6b7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![Alert 창에서 확인을 누르면 정상적으로 권한이 삭제된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/09623a34-cad6-465e-b754-05487f8f00db/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230829%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230829T094121Z&X-Amz-Expires=3600&X-Amz-Signature=10183e0faf676cba854d16a6ba9358a06c138db3ff75a5bd277546ae609747a7&X-Amz-SignedHeaders=host&x-id=GetObject)


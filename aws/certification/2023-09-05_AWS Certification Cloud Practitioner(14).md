
### SSH 개요

1. AWS EC2인스턴스에 SSH접속 방법

	![현재 EC2 Instance Connect는 amazon linux2만 가능하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8629519e-cc6e-4ba1-b87c-7d5b197fb2d0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100707Z&X-Amz-Expires=3600&X-Amz-Signature=28af79c9034666e0228e88f1050861ac5f285953e8b51f557042ee8ce4f176d6&X-Amz-SignedHeaders=host&x-id=GetObject)


### Windows10을 사용하여 SSH 실행 방법

1. 주의 사항
	- pem 파일에는 공백이 있으면 안되므로 언더바(_)로 치환 하거나 공백 문자를 제거해야한다.
	- Windows에서 pem 파일을 이용한 ssh 연결 시 pem파일에 대한 권한 상속 문제(WARNING: UNPROTECTED PRIVATE KEY FILE!)가 발생할 수 있다. 
	3번 트러블 슈팅에서 확인 후 조치하면 된다.
2. cmd로 ssh 연결하기

	Windows10 이상의 OS에서는 CMD 혹은 PowerShell에서 ssh 연결 명령어를 지원한다.


	![CMD 창을 실행 시킨 후 ssh 명령어를 입력하여 지원하는지 확인 해본다. 위와 같은 명령어 출력이 된다면 지원 되는 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1792ccc9-fa70-4c91-8030-4f94615d79e2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=0d7dadcb0f5dc137c8801e8e9360ec032972bffe5367c64532dc0169eb0afa22&X-Amz-SignedHeaders=host&x-id=GetObject)


	인스턴스 생성시 같이 생성한 키 페어를 저장한 디렉토리로 이동한다.


	![cd 명령어로 pem 파일이 있는 디렉토리로 이동 후 dir 명령어로 디렉토리 내의 파일 목록을 조회한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d04946ff-f920-4358-aa42-175c803dcd71/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=7a69b24749bef94dc322b25e27241daacbc838a410cfe10469ba2fd40219b734&X-Amz-SignedHeaders=host&x-id=GetObject)


	키페어(pem파일)과 인스턴스의 public ip를 이용해 ssh 접속한다.


	```bash
	ssh -i ${pem_파일_이름.pem} ec2-user@${인스턴스_public_ip}
	```


	![위와 같은 커맨드가 출력되면 정상적으로 ssh 접속이 된 것이다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2f8bea92-ab10-4809-b6bb-29c1ea3f0add/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=2e75f3c15ddb24ba7f319521a00ce60999206621b40ce077cdbc5d9b3cbea67f&X-Amz-SignedHeaders=host&x-id=GetObject)


	접속이 되었는지 확인하기


	이전에 사용자 데이터를 이용해서 인스턴스 실행 시 웹서버를 실행시켰었다. 해당 html파일이 정말 존재하는지 확인해본다.


	```bash
	cd /var/www/html
	ls
	```


	![index.html 파일이 존재하는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5618bee5-a377-45d4-b81a-f55e0817f10d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=8027eff5776ccb2f3da5bcd24c060f3a0ea105c37b1c66f8dc2674295f37e898&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 트러블 슈팅

	아래와 같이 WARNING: UNPROTECTED PRIVATE KEY FILE! 에러가 발생했을 때 조치 방법을 설명한다.


	![Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a334d658-3ca2-4770-98f6-ac6977cbc21d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=6ac2dff32cf2b8db5b5f23a1194f3f4caf1e8959dc7232b6bba95655ff052571&X-Amz-SignedHeaders=host&x-id=GetObject)


	![pem 파일에서 오른쪽 마우스 클릭 후 “속성” 탭을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/34adb080-e040-4bcf-b052-da3c4e42e5c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=9296e09c5444f5713d48ac73b65dbf2ca278a260c243af1559020039ff3ba4a2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![속성 창에서 “보안” 탭을 클릭 후 “고급” 탭을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4be78063-2179-40af-98d9-05701d8074fe/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=13d9552ab93995b60fd53fcbede368c5e41a5c77f0e2c7966c651bad1a22e8b1&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“상속 사용 안함” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/711e3a82-1dab-4ae5-8aff-2314d7cca04b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=bc1daf7caf6287ec239045ad2c2402e5c4f1ac97bdf9e17e8e332295778d6f86&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“이 개체에서 상속된 사용 권한을 모두 제거합니다.” 를 클릭 후 팝업창이 닫히면 “적용” 버튼 및 “확인” 버튼을 눌러 변경사항을 저장한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/99fab911-f674-4563-a3af-3d4dfed6d993/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100709Z&X-Amz-Expires=3600&X-Amz-Signature=3de5eb0b72347b047d8ce7e4eb2fad346d368625c5ca6c71bbce0fd0d7576bb4&X-Amz-SignedHeaders=host&x-id=GetObject)


### EC2 인스턴스 연결

1. EC2 Instance Connect
	1. 주의사항
		- 위 연결 방법은 현재 Amazon Linux 2 버전을 사용 해야만 가능하다.
	2. 연결 해보기

		AWS 인스턴스 콘솔로 이동하여 진행한다.


		![“인스턴스” 탭에서 연결 할 인스턴스를 체크 후 “연결” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c654fa74-14c4-4fbd-a405-0c03d1fc88f3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100712Z&X-Amz-Expires=3600&X-Amz-Signature=2a4db6cfd73573f783d419269b5dc128c0f6b6b16c96da81c76f016e1321221c&X-Amz-SignedHeaders=host&x-id=GetObject)


		![기본 사용자 이름으로 “ec2-user”가 입력 되어있으나, 특정 사용자를 OS에 추가하였다면 변경하여도 된다. 정보를 확인 후 “연결” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0ab21d62-0cc5-4f3f-9078-c20a17f52d87/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100712Z&X-Amz-Expires=3600&X-Amz-Signature=f6319e57938843caf8da85937550b083cec08ca3af4f5b80027ad2c906dc1054&X-Amz-SignedHeaders=host&x-id=GetObject)


		※위 과정에서는 별도의 SSH 인증이 필요하지 않다. 이는 AWS에서 인스턴스에 연결할 때 임시 SSH키가 업로드 되며 그에따라 연결이 실행되기 때문이다.


		위와 같은 과정을 진행하였다면 새로운 브라우저 탭에서 서버에 연결된 것을 확인할 수 있다.


		![Windows CMD에서 SSH 연결 할 때와 비슷한 화면이 출력된다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/50a5c858-b3f8-485a-9e85-790db582be85/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100712Z&X-Amz-Expires=3600&X-Amz-Signature=95c00cec8dc275dcb450996ae385b84e8cf0c162fd321be023e78c88721fa814&X-Amz-SignedHeaders=host&x-id=GetObject)


		이전에 사용자 데이터를 이용해서 인스턴스 실행 시 웹서버를 실행시켰었다. 해당 html파일이 정말 존재하는지 확인해본다.


		```bash
		cd /var/www/html
		ls
		```


		![동일하게 index.html 파일이 존재하는 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a10b584-fa73-4bde-bd75-65ac95b1283f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230905%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230905T100712Z&X-Amz-Expires=3600&X-Amz-Signature=b819caccfa8ec694980318746dc6c6697a5bfdc136cd2f101080b73988377dcf&X-Amz-SignedHeaders=host&x-id=GetObject)


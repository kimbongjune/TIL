
### S3 버전 관리 개요

- S3 버저닝
	- 버킷 내 파일을 교체 및 업데이트하고자 할 때 파일에 대한 버전을 관리한다.
	- 이전버전을 유지할 수 있으며 현재 버전에서 되돌아갈 수 있다.
	- 버킷 수준에서 활성화 되는 옵션이다.
	- 파일 업데이트시 마다 새로운 버전을 얻게된다.
	- 버전관리의 모범 사례
		- 의도치 않은 삭제를 방지할 수 있다.
		- 누군가 파일을 삭제하면 이전 버전으로 복원할 수 있다.
		- 파일이 잘못된 경우 이전버전으로 롤백할 수 있다.
	- 버전 관리 활성화 이전에 업로드된 모든 파일은 버전이 “null”이 된다.
	- 버전 관리를 중단하고 이전 버전을 삭제하지 않으면 계속 S3버킷 내에 파일이 잔존한다.

### S3 버전 관리 실습

1. 버전 관리 활성화

	![버킷 정보 페이지에서 “속성” 탭으로 이동 후 “버킷 버전 관리” 탭의 “편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2c6e4c41-c2d9-4abd-824d-6259fcabfae7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=20be2f32a67f440a62d6780fd6e46f3b5ae28df63d0b9eed634af4255f279727&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“버킷 버전 관리”를 “활성화” 후 “변경 사항 저장” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3276c3d6-7cd6-4454-8989-bff97a393a32/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=66700551a9cdef9179a5e5259cad37f5e6a949e48fe9002893102fae2786e2ff&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 버킷 버전 관리 적용 확인

	우선 “index.html” 파일을 수정하도록한다.


	![사용하기 편한 에디터에서 html 내의 콘텐츠를 일부 변경한다.
	여기서는 “I love coffee” 문구를 “I Really love coffee”로 변경하였다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/76bb0ed5-9c5c-4400-bf1e-5e05dc262969/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=3a81a93fe68c1854fe5e0d40a826ecd667b03239496928164126ca3420619c3a&X-Amz-SignedHeaders=host&x-id=GetObject)


	변경한 “index.html”파일을 버킷에 업로드한다.


	![버킷 정보 페이지의 “객체” 탭으로 이동하여 “업로드” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/db7d150b-eb1e-4db2-8561-3a3f1b048081/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=1e0836e5fd1dd9289f5cba4a04740da2541803ce7acbb40e4acad71739c6835c&X-Amz-SignedHeaders=host&x-id=GetObject)


	![변경한 “index,html”파일을 업로드한다. “업로드” 버튼을 클릭하여 파일을 업로드한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c9a694b2-d80a-4d07-a57c-b08bdb764d18/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=bef621b0771b5eae120fcefd74673214217b98920d78f03bf5c589aa238ee31a&X-Amz-SignedHeaders=host&x-id=GetObject)


	![업로드한 “index,html”을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f4f54e1c-d58c-428d-902a-7d3fc87251c3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=e85e1cb0b2d25afeb790b4d11d61f3e501887f5e643d0a5ebaa17984cb2e6be2&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“버전” 탭으로 이동하여 index.html 버전을 확인해보면 최초 업로드한 index.html은 버전이 “null”로 표시되고 다시 업로드한 index.html은 특이한 문구로 버전ID가 생성된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8647cf26-93df-42e8-bd93-cf7304286722/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=a2b4ffefd6b95217c375a7b21e7909fa9e772f5a788521500fdbaf6f77aa47cd&X-Amz-SignedHeaders=host&x-id=GetObject)


	![기존에 확인했던 “버킷 웹 사이트 엔드포인트”를 웹페이지에서 이동하여 확인해보면 html에서 변경한 문구가 웹페이지에 반영된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1095f2b6-654e-4b02-a4da-95a8c8531647/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103748Z&X-Amz-Expires=3600&X-Amz-Signature=d80590c4c569a035521733635b8d3617cc8842b6255ebe1b1693de8f396c59a1&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 버킷 정보 페이지에서 버전 확인하기

	![버킷 정보 페이지에서 “버전 표시” 스위치를 이용해 바로 버전을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/59d2b488-8989-4968-b121-59bc596e9508/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=3d5a2fdfccd09a22417f680f97f500d53719454562dc3a6cd400165719580ab6&X-Amz-SignedHeaders=host&x-id=GetObject)


	![버전 표시 활성화](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/939ae3bb-ac79-4439-9c48-ec26dd20586a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=05e39113e2dfdb89713b587d5d53eda2a14f9ab251bf0886a93463f9505a1a55&X-Amz-SignedHeaders=host&x-id=GetObject)

4. 버전 롤백하기

	![롤백하길 원하는 파일의 이후 버전을 선택하여 삭제한다. 여기선 최근에 업로드한 “index.html”을 삭제한다. 파일 선택 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e9876583-aa92-4258-866b-4ddac1483e50/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=7cec43c3726f669dde50a4e6e882fbd056b4ddef8f827a7ad5be8e71bd621705&X-Amz-SignedHeaders=host&x-id=GetObject)


	![객체 삭제를 확인하기 위해 “영구 삭제”를 입력 후 “객체 삭제”버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/98c659b1-f13d-4738-8d79-1ddeb0cc5ef4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=358ab8d8ceaa4d2ea0d202217a6154101b8f544636d76e3f4627cdbe876201f0&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“index.html”의 버전이 삭제되어 초기 업로드한 “index,html”파일만 남은것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2eb825b0-e030-45e9-9682-4e84ab6bede3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=69e45c5e45df23433ac860276ca5d64cc3d3b8872a3ea28fc2efd73075fc0ba5&X-Amz-SignedHeaders=host&x-id=GetObject)

5. 버전 롤백 검증

	![호스팅 웹페이지에서 새로고침하면 이전 버전의 index.html 파일로 복원되어 문구가 변경된것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/38052928-65e1-4845-9ca4-6fd8ffbd98fc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103750Z&X-Amz-Expires=3600&X-Amz-Signature=58eeea2204a142a5dc34715320dff868ad9193724618451c4e1a1291e808b590&X-Amz-SignedHeaders=host&x-id=GetObject)

6. 삭제한 객체 복구

	![버전 표시를 비활성화 후 “coffee.jpg” 파일을 선택 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/14d0c646-9631-4a7f-b47c-72eb70a29d49/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103751Z&X-Amz-Expires=3600&X-Amz-Signature=baef2702aa51ae1bc4bd4d562a85b64b09ce017bc9c93853843c86bba68d157e&X-Amz-SignedHeaders=host&x-id=GetObject)


	![호스팅 웹페이지에서 새로고침하면 이미지가 깨져서 표시되는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/79b09de5-c018-45d4-82c6-1623c3e8fb5d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103751Z&X-Amz-Expires=3600&X-Amz-Signature=3d0db801c75df10b2410ef312ace7f473a85e4e91d001c46dfeabf318eefc602&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제한 객체가 버전이 표시되어 삭제 마커가 표시되는것을 확인할 수 있다. “삭제 마커”가 붙어있는 객체를 체크 후 “삭제” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b8318ef9-9d84-4348-a75c-1a7120523964/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103751Z&X-Amz-Expires=3600&X-Amz-Signature=cf9e5e61432859b2fc9cb1ab9a6a6addf461104834691f3695752176f0596e01&X-Amz-SignedHeaders=host&x-id=GetObject)


	![삭제된 “coffee.jpg”가 복구된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a3ba13f-732a-4771-9a71-f60838d32226/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103751Z&X-Amz-Expires=3600&X-Amz-Signature=12d49056d48e842546938bab72664f1582c92d92a4b4d783ccf553b69b2952f7&X-Amz-SignedHeaders=host&x-id=GetObject)


	![호스팅 웹페이지에서 새로고침하면 다시 이미지가 표시된 것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/054b3b9a-5539-4a09-a43a-3ac15c528755/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230914%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230914T103751Z&X-Amz-Expires=3600&X-Amz-Signature=c3d7303ba21b8c2b666ad2470327eeb1a0c992ebb5c70ca4aa269e171e69d7a1&X-Amz-SignedHeaders=host&x-id=GetObject)


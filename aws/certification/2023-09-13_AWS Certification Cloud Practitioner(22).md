
### S3 웹사이트 개요

- 객체를 공용으로 사용하는 이유중 하나는 Amazon S3에 웹사이트를 호스팅할 수 있기 때문이다.
- Amazon S3는 정적 웹사이트를 호스팅하는데 유용하며 www(World Wide Web)에서 액세스가 가능하다.
- S3 웹사이트 URL 형식은 두가지이다.
	- <bucket-name>.s3-website

		-<AWS-region>.amazonaws.com

	- <bucket-name>.s3-website

		**.**<AWS-region>.amazonaws.com

- URL이 사용 가능하면 버킷의 모든 파일에 바로 액세스할 수 있지만 S3버킷을 퍼블릭으로 설정하지 않으면 403(금지 또는 액세스 거부) 에러가 발생한다.

### S3 웹사이트 실습

1. 웹사이트 실습을 위한 파일 업로드

	![버킷의 루트 디렉토리(coffee.jpg 파일이 위치하는)에 웹사이트를 위한 파일을 업로드 해야한다. “업로드” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/933462f7-2260-4655-89ea-4baeb4c53b87/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114243Z&X-Amz-Expires=3600&X-Amz-Signature=6034505922672231d02c6b07ad742f529f0cd57568714f52c6c6e069526dd41d&X-Amz-SignedHeaders=host&x-id=GetObject)


	![6-2-1에 있는 “index.html”과 “beach.jpg”파일을 업로드한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e59e243c-a6a0-424e-a47f-e34840053e61/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114243Z&X-Amz-Expires=3600&X-Amz-Signature=8f5b19a0591efe9c246fb1b52349484daf89d336d2838d184dd0ea9705101eff&X-Amz-SignedHeaders=host&x-id=GetObject)

2. 정적 웹사이트 호스팅

	![웹사이트 호스팅을 위해 버킷 정보 페이지에서 “속성” 탭으로 이동 후 하단의 “정적 웹 사이트 호스팅” 탭의 “편집” 버튼을 클릭한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/12d4e69a-6582-447e-b6d9-838130645076/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114244Z&X-Amz-Expires=3600&X-Amz-Signature=6bf67a87bda2e12ccf905f903da0f6e668b226835d27f6db032c6998638970aa&X-Amz-SignedHeaders=host&x-id=GetObject)


	![“정적 웹 사이트 호스팅” 을 “활성화”한 후 “호스팅 유형”은 기본 옵션인 “정적 웹 사이트 호스팅”을 체크한다. “인덱스 문서”는 웹사이트의 기본 페이지를 지정하는 것이며 업로드한 “index.html”을 작성한다. 
	기타 옵션으로 에러페이지 혹은 다른 페이지로 리다이렉션 하는 옵션을 추가할 수 있다.
	설정을 확인 후 “변경 사항 저장”버튼을 클릭하여 정적 웹 사이트 호스팅 설정을 활성화한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1a4de47d-c5e5-42bc-8d7e-50a2e215f8b6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114244Z&X-Amz-Expires=3600&X-Amz-Signature=07b08006acfb4ea68d494f5e2da5509bdaecf4a9f51355d239159e971acef922&X-Amz-SignedHeaders=host&x-id=GetObject)

3. 웹사이트 접속하기

	![버킷 정보 페이지로 돌아오게 되면 하단에 정적 웹 사이트의 엔드포인트가 만들어진 것을 확인할 수 있다. 해당 엔드포인트를 복사 후 브라우저의 새 탭에서 이동한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6fa16aff-1108-4d08-9ec4-6699441659db/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114244Z&X-Amz-Expires=3600&X-Amz-Signature=7a02739ec63c4672e2483e825515012d2d796b4450cdf570f2abe4451e4657e5&X-Amz-SignedHeaders=host&x-id=GetObject)


	![정상적으로 웹페이지가 열리는것을 확인할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e0c1258-aa4a-4800-9262-7934eabad6ec/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230913T114244Z&X-Amz-Expires=3600&X-Amz-Signature=a88526632484bdfa85c7f78f0ed96773c3296e8530c6686269f286ca9c2b4f3c&X-Amz-SignedHeaders=host&x-id=GetObject)


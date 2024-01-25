# [tikkle] post_image_profileUrl (2023.8.2)

기능 : 토큰 확인 

       어떤  크기의 사진인지, 어느 회원의 정보인지 id 입력 받음

데이터베이스 조회해서 해당 url 가져옴

      size 값이 0이면 모든 url 반환

| 이미지 종류 | 버킷명 | 파일명 |  |
| --- | --- | --- | --- |
| 프로필 | tikkle-profile/ 36, 48, 64, 128 | {userId}-{time stamp}.JPG |  |

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
→하나만 리턴 | 200 - 11 | const return_body = {
success: true,
data: url,
detail_code: "11",
message: "success - return one image url",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 성공
→ 모든 url리턴 | 200 - 10 | const return_body = {
success: true,
data: JSON.stringify(retData),
detail_code: "10",
message: "success - return all image urls",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
|  |  |  |
| 실패
→ db 오류 | 500 - 00 | console.log(" post_image_profileUrl 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→ 사이즈 값 틀림 | 400 - 00 | console.log("ERROR : size value is null or invalid");
const return_body = {
success: false,
detail_code: "00",
body: "input image size again",
returnToken: null,
};
return res.status(400).send(return_body); |

TEST

사진 한장 가져오기

```jsx
const axios = require("axios");

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_image_profileUrl",
			{
				imageSize: 36,
				userId: 18,
			},
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o",
				},
			}
		);

		// Ensure data exists before logging it
		if (response && response.data) {
			console.log(response.data);
		} else {
			console.log("Response or response data is undefined");
		}
	} catch (error) {
    if (error.response && error.response.status) {
      console.error("[status code] ", error.response.status);
    }
    if (error.response && error.response.data) {
      console.error("response data : ", error.response.data);
    }
  }
}

fetchData();
```

사진여러장

```jsx
const axios = require("axios");

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_image_profileUrl",
			{
				imageSize: 0,
				userId: 18,
			},
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o",
				},
			}
		);

		// Ensure data exists before logging it
		if (response && response.data) {
			console.log(response.data);
		} else {
			console.log("Response or response data is undefined");
		}
	} catch (error) {
    if (error.response && error.response.status) {
      console.error("[status code] ", error.response.status);
    }
    if (error.response && error.response.data) {
      console.error("response data : ", error.response.data);
    }
  }
}

fetchData();
```
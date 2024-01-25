# [tikkle] get_image_deleteProfile (2023.8.2)

기능 : 토큰 확인 아이디 추출

       그 아이디의 image 속성 정도 지움

s3의 src, online 버킷의 이미지도 전부 삭제

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
data: sqlResult,
detail_code: "00",
message: "success to delete profile image",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→db 연결중 오류 | 500 - 01 | console.log(" get_image_deleteProfile 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "01",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
s3의 src 삭제중 에러 | 500 - 02 | console.log("get_image_deleteProfile 에서 에러가 발생했습니다.", error);
const return_body = {
success: false,
detail_code: "02",
message: "Error deleting src object in s3",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
s3 의 사이즈별 이미지 삭제중 에러 | 500 - 03 | console.log("get_image_deleteProfile 에서 에러가 발생했습니다.", error);
const return_body = {
success: false,
detail_code: "03",
message: "Error deleting object in s3 : " + imageSize[i],
returnToken: null,
};
return res.status(500).send(return_body); |

TEST

성공

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_image_deleteProfile",
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
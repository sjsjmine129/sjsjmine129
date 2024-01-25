# [tikkle] get_notification_list (2023.8.16)

기능 : 토큰  풀어서 아이디 가져옴

그 아이디의 알림들을 가져옴 & read로 정보 바꿈

삭제된거 가져오지 않음, 시간으로 정렬

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
		success: true,
		data: retData,
		detail_code "00",
		message: "success get notification list",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→ sql오류 데이터 확인시 | 500 - 01 | console.log("get_notification_list 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "01",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body);		}; |
| 실패
sql 업데이트오류 | 500 -02 | console.log("get_notification_list 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "02",
message: "SQL error: error when update data",
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
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_notification_list",
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
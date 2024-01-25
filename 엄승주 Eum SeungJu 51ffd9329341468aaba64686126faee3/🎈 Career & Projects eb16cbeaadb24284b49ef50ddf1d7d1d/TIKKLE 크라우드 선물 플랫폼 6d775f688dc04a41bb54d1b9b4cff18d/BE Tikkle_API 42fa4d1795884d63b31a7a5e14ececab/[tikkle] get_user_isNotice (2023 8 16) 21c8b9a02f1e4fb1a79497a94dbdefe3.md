# [tikkle] get_user_isNotice (2023.8.16)

기능 : 토큰 확인해서 그 값의 유저 id 가져옴

          그 id의 회원 정보 가져와서 읽지 않은 데이터가 있는지 확인

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
→ 티클링중 아님 | 200 - 10 | const return_body = {
success: true,
detail_code: "10",
message: "No notification!",
data: { is_notification: false },
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 성공
→ 티클링중  | 200 - 11 | const return_body = {
			success: true,
			detail_code: "11",
			message: "There is notification you should read!",
			data: { is_notification: true },
			returnToken: returnToken,
		};
		return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→DB  오류 | 500 - 00 | console.log("get_notification_list 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |

TEST

안읽은 데이터 존재 

```jsx
const axios = require("axios");
axios.defaults.headers.common["User-Agent"] =
	"Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)";

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_user_isNotice",
			{
				headers: {
					authorization:
						**"**eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjE2OTMzNjI5OTAsImlzcyI6IkxpRm9saSJ9.2q1rnumRYD5G6ZajAdHkU3HibgTRDbzhgGNFoPAw2qY,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjQyODUzNjIwOTAsImlzcyI6IkxpRm9saSJ9.3lO5YCgVXXzrz5LrodPQoccq11ZHvHdwKAflg22RXXc**"**,
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

안읽은 데이터 없음

```jsx
const axios = require("axios");
axios.defaults.headers.common["User-Agent"] =
	"Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)";

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_user_isNotice",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MTgsImlhdCI6MTY5MTY0NTI5NiwiZXhwIjoxNjkxNjQ2MTk2LCJpc3MiOiJMaUZvbGkifQ.e9kkE0lkij8NtWmegnaQWq93DvfWbU8lk-EGgLmCQO8,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MTgsImlhdCI6MTY5MTY0NTI5NywiZXhwIjoxNjk0MjM3Mjk3LCJpc3MiOiJMaUZvbGkifQ.fSi6fprFa7YyBVzQIV8MSWVtcszrvFW6EAr9C-OLnVA",
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
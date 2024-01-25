# [tikkle] get_user_checkTikkling (2023.8.11)

기능 : 토큰 확인해서 그 값의 유저 id 가져옴

          그 id의 회원 정보 가져와서 티클링 중인지 값 리턴

만약 티클링 중이라면 티클링 아이디를 리턴

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
→ 티클링중 아님 | 200 - 11 | const return_body = {
		success: true,
		data: 0,
		detail_code: "11",
		message: "Not Tikkling",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
| 성공
→ 티클링중  | 200 - 10 | const return_body = {
success: true,
data: sqlResult[0].id,
detail_code: "10",
message: "Tikkling",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→DB  오류 | 500 - 00 | console.log("get_user_checkTikkling에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |

TEST

티클링 중

```jsx
const axios = require("axios");
axios.defaults.headers.common["User-Agent"] =
	"Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)";

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_user_checkTikkling",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjE2OTMzNjI5OTAsImlzcyI6IkxpRm9saSJ9.2q1rnumRYD5G6ZajAdHkU3HibgTRDbzhgGNFoPAw2qY,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjQyODUzNjIwOTAsImlzcyI6IkxpRm9saSJ9.3lO5YCgVXXzrz5LrodPQoccq11ZHvHdwKAflg22RXXc",
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

티클링 중 아님

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_user_checkTikkling",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNDQ4OTg0LCJleHAiOjE2OTA0NDk4ODQsImlzcyI6IkxpRm9saSJ9.cwvCm392PrzZVoY9IzTuW3vYcQHINqpNyccuCOEftgs,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNDQ4OTg0LCJleHAiOjE2OTMwNDA5ODQsImlzcyI6IkxpRm9saSJ9.WTDMgraj24NQ_44InepS0xQJKjeU6fsWSNHYpppyHQU",
				},
			}
		);
		// Ensure data exists before logging it
		if (response && response.data) {
			console.log(response.data);
		} else {
			console.log("Response or response data is undefined");
		}
	}catch (error) {
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
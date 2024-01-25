# [tikkle] get_auth_checkToken (2023.7.27)

기능 : 앱 켜졌을 때 기기에 토큰 데이터 있으면 작동시키고 토큰확인 & 로그인 자동

부가사항 : 토큰길이 500자로 제한 걸어둠

## Output

|  | statusCode-detail_code | return |
| --- | --- | --- |
| 성공
새 토큰 x | 200-10 | const return_body = {
success: true,
detail_code: "10",
message: "success : no new access token",
returnToken: null,
};
return res.status(200).send(return_body); |
| 성공
새 토큰 o | 200-11 | const return_body = {
success: true,
detail_code: "11",
message: "success : new access token",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 실패 
→ ref 토큰 오류 | 401-99 | console.log("get_auth_checkToken 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "99",
message: "the token value is null or invalid : Log in again",
returnToken: null,
};
return res.status(401).send(return_body); |
|  |  |  |
|  |  |  |

TEST

성공

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_auth_checkToken",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjE2OTMzNjI5OTAsImlzcyI6IkxpRm9saSJ9.2q1rnumRYD5G6ZajAdHkU3HibgTRDbzhgGNFoPAw2qY,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjQyODUzNjIwOTAsImlzcyI6IkxpRm9saSJ9.3lO5YCgVXXzrz5LrodPQoccq11ZHvHdwKAflg22RXXc"				},
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

access 에러

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_auth_checkToken",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYwLCJleHAiOjE2OTEzODM5NjAsImlzcyI6IkxpRm9saSJ9.jcmQ2Zva2-rF8v0mDBHD4ASpn8n_FWk0hZTqc4zqx1w,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYxLCJleHAiOjE2OTM5NzUwNjEsImlzcyI6IkxpRm9saSJ9.FETQpjR23b-quPe2kMJrvJbDF2PVoTOUhRSKdGItlLo",
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

reff 에러

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.get(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/get_auth_checkToken",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYwLCJleHAiOjE2OTEzODM5NjAsImlzcyI6IkxpRm9saSJ9.jcmQ2Zva2-rF8v0mDBHD4ASpn8n_FWk0hZTqc4zqx1w,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYxLCJleHAiOjE2OTM5NzUwNjEsImlzcyI6IkxpRF2PVoTOUhRSKdGItlLo",
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
		console.error(`Error fetching data: ${error}`);
	}
}

fetchData();
```
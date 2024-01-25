# [tikkle] authtoken  ← 토큰 오류 (detail_code : 99)

기능 : 토큰 확인하는 미들웨어

## Output

|  | statusCode-detail_code | return |
| --- | --- | --- |
| 성공 |  |  |
| 실패 
→ 토큰 없음
    토큰 오류
    리프레시 토큰 오류 | 401-00 | console.log("authtoken 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "99",
message: "login again",
returnToken: null,
};
return res.status(401).send(return_body); |
|  |  |  |
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
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYwLCJleHAiOjE2OTEzODM5NjAsImlzcyI6IkxpRm9saSJ9.jcmQ2Zva2-rF8v0mDBHD4ASpn8n_FWk0hZTqc4zqx1w,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxMzgzMDYxLCJleHAiOjE2OTM5NzUwNjEsImlzcyI6IkxpRm9saSJ9.FETQpjR23b-quPe2kMJrvJbDF2PVoTOUhRSKdGItlLo",
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
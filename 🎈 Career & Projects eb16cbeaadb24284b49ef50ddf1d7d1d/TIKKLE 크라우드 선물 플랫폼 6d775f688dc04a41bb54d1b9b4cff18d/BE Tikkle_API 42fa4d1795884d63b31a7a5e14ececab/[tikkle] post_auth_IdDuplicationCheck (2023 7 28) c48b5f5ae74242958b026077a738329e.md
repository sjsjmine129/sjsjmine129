# [tikkle] post_auth_IdDuplicationCheck (2023.7.28)

기능 : 입력 이이디가 중복인지 아닌지 확인 시켜 줌

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
→ 중복 없는 id  | 200 - 10 | const return_body = {
success: true,
detail_code: "10",
message: "No duplication",
returnToken: null,
};
return res.status(200).send(return_body); |
| 성공
→ 중복인 아이디 | 200 - 11 | const return_body = {
success: true,
detail_code: "10",
message: "No duplication",
returnToken: null,
};
return res.status(200).send(return_body); |
|  |  |  |
| 실패 
→입력 id 형태 오류 | 400 - 00 | console.log("post_auth_IdDuplicationCheck 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "inputId value is null or invalid: input data again",
};
return res.status(400).send(return_body); |
| 실패
→DB  연결 오류 | 500 - 00 | console.log(
"post_auth_IdDuplicationCheck 에서 에러가 발생했습니다 : ",
err
);
const return_body = {
success: false,
detail_code: "00",
message: "Database connection error",
returnToken: null,
};
return res.status(500).send(return_body); |
|  |  |  |

TEST fornt code

성공케이스

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_IdDuplicationCheck",
			{
				inputId: "sup1214_1212",
			},
			{
				headers: {
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

id 중복

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_IdDuplicationCheck",
			{
				inputId: "sup1214",
			},
			{
				headers: {},
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

긴 아이디

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_IdDuplicationCheck",
			{
				inputId:
					"sup1214asdfasdfasdfasdfasdfasdfsafasdfasdfsadfsadfsadfasdfsadfasdfsafsadfasdf_1212",
			},
			{
				headers: {},
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
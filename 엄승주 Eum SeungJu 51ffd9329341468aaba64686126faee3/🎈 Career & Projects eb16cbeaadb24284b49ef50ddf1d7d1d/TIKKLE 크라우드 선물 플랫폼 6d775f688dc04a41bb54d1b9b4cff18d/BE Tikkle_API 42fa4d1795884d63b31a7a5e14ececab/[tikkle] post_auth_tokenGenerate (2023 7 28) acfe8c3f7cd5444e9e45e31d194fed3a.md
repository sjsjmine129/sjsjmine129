# [tikkle]  post_auth_tokenGenerate (2023.7.28)

기능 : 유저 아이디 받아서 등록된 유저인지 확인 후(삭제된 유저인지 확인), 토큰 발급 해줌 

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | success: true,
data: JSON.stringify({
accessToken: accessToken,
refreshToken: refreshToken,
}),
detail_code: "00",
message: "success to generate token",
returnToken: null,
};
return res.status(200).send(return_body); |
| 실패 
→입력 id 형태 오류 | 400 - 00 | console.log("post_auth_tokenGenerate 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "id value is null or invalid",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패
→유저 정보 없음 | 404 - 03 | console.log("post_auth_tokenGenerate 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "03",
message: "There is no user of input id",
returnToken: null,
};
return res.status(404).send(return_body); |
| 실패
→DB  연결 오류 | 500 - 02 | console.log(" post_auth_tokenGenerate 에서 에러가 발생했습니다 : ", err);
const return_body = {
success: false,
detail_code: "02",
message: "Database connection error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→삭제된 유저 | 404 - 04 | console.log("post_auth_tokenGenerate 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "04",
message: "Deleted user",
returnToken: null,
};
return res.status(404).send(return_body); |
| 실패
→ 토큰 생성중 오류 | 500 - 05 | console.log("post_auth_tokenGenerate 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "05",
message: "cannot make token",
returnToken: null,
};
return res.status(500).send(return_body); |

TEST

되는 값

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_tokenGenerate",
			{
				id: 18,
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

삭제된 유저

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_tokenGenerate",
			{
				id: 4,
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
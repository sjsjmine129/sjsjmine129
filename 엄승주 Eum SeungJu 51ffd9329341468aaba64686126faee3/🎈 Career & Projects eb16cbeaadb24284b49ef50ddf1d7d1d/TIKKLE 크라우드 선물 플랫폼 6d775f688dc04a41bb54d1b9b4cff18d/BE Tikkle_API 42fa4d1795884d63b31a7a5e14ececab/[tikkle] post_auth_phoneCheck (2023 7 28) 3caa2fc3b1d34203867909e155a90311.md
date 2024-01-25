# [tikkle] post_auth_phoneCheck (2023.7.28)

기능 : 앱에 들어와서 토큰이 없는 경우 전화번호를 입력받음 (람다 작동이전 다른 곳에서 처리)

           번호를 입력 받아서 데이터 베이스에 있으면 otp로 로그인을

           없으면 회원가입으로 넘어감

           전화번호 형식 확인 필요

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
→ 회원정보 존재하는 번호 | 200 - 10 | const return_body = {
			success: true,
			detail_code: "10",
			message: "login",
			returnToken: null,
			userId: sqlResult[0].id,
		};
		return res.status(200).send(return_body); |
| 성공
→ 회원정보 없는 번호 | 200 - 11 | const return_body = {
success: true,
detail_code: "11",
message: "sign up",
returnToken: null,
};
return res.status(200).send(return_body); |
|  |  |  |
| 실패 
→입력 번호 형태 오류 | 400 - 00 | console.log("post_auth_phoneCheck 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "phone number value is null or invalid : input data again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패
→DB  연결 오류 | 500 - 02 | console.log(" post_auth_phoneCheck 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "02",
message: "Database connection error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→ 번호에 회원정보 여러개 | 500 -03 | console.log(" post_auth_phoneCheck 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "03",
returnToken: null,
message: "many same number",
};
return res.status(500).send(return_body); |

TEST

새 번호

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_phoneCheck",
			{
				phone: "01012347778",
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

있는 번호

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_phoneCheck",
			{
				phone: "01053783514",
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

wrong format of number

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_phoneCheck",
			{
				phone: "010-4141-1231",
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
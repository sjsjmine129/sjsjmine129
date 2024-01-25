# [tikkle] post_auth_registerUser (2023.8.21)

기능 : 회원의 정보 받아서 회원 가입시킴

 성공시 회원의 아이디 리턴

8.21 : 만 14세 미만의 회원은 가입 불가 → 체크해서 오류 냄

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
data: sqlResult.insertId,
detail_code: "00",
message: "sign up success!",
returnToken: null,
};
return res.status(200).send(return_body); |
|  |  |  |
| 실패 
→이름 데이터 형태 오류 | 400 - 01 | console.log("ERROR : name value is null or invalid");
const return_body = {
success: false,
detail_code: "01",
message: "input name again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패 
→생일 데이터 형태 오류 | 400 - 02 | console.log(" post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "02",
message: "birthday value is null or invalid : input birthday again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패 
→nick 데이터 형태 오류 | 400 - 04 | console.log("post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "04",
message: "nick value is null or invalid : input nick again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패 
→phone 데이터 형태 오류 | 400 - 05 | console.log(" post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "05",
message: "phone value is null or invalid : input phone again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패 
→gender 데이터 형태 오류 | 400 - 06 | console.log("post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "06",
message: "gender value is null or invalid : input gender again",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패
→ 쿼리 오류 | 500 - 00 | console.log(" post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "Database post error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→ 만 14세 미만 | 400 - 03 | console.log("post_auth_registerUser 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "03",
message: "if your age is under 14 you cannot use this servise!",
returnToken: null,
};
return res.status(400).send(return_body);body); |

TEST

되는 경우 (이미 한번 했어서 전화번호, 닉네임 볕경 필요)

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_auth_registerUser",
			{
				name: "John Doe",
				birthday: "1990-08-15",
				nick: "john_doe121212",
				phone: "1234568890",
				gender: "male",
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
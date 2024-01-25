# [single] post_auth_makeOtp (2023.8.14)

기능 : 번호를 받아서 SNS로 문자(otp) 전송

프론트에서 확인하는 법. → 직접 데이터 넣으면 됩니당 : bcryptjs npm 설치 필요

```jsx
const bcrypt = require("bcryptjs");

async function handler() {
	const encryptedOTP =
		"$2a$10$iEb5UqTr8QGTY5ksptzsM.BS8ybD9W1LCaOObV57HBbIpeNujpLl6"; //직접입력

	// Simulate user input
	const userInput = "userInputPassword";

	// Compare the stored hashed password with the user input
	const isMatch = bcrypt.compareSync(userInput, encryptedOTP);

	if (isMatch) {
		console.log("Password is correct.");
	} else {
		console.log("Password is incorrect.");
	}
}

handler();
```

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
		success: true,
		data: storedHashedPassword,
		detail_code "00",
		message: "success to send otp",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body);
} |
|  |  |  |
|  |  |  |
| 실패
→sns 전송 오류 | 500 - 00 | console.log("get_auth_makeOtp 에서 에러가 발생했습니다.", err);
		const return_body = {
			success: false,
			detail_code: "00",
			message: "SNS post error",
			returnToken: null,
		};
		return res.status(500).send(return_body); |
|  |  |  |

TEST

```jsx
const axios = require("axios");
axios.defaults.headers.common["User-Agent"] =
	"Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)";

async function fetchData() {
	try {
		const response = await axios.post(
			"https://v2t9k67qhj.execute-api.ap-northeast-2.amazonaws.com/default/get_auth_makeOtp",
			{
				phone: "01041286535",
				hash: "@@@HASH@@@",
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
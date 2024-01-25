# [single] post_user_email (2023.7.31)

기능 : 토큰을 해제해서 id 가져옴

         문의 내용 받아서 이메일로 작성

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
data: "inquire send success",
detail_code: "00",
message: "inquire send success",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 실패 
→ 이메일 전송 실패 | 400 - 00 | console.log("fail to send inquire");
const return_body = {
success: false,
detail_code: "00",
message: "fail to send inquire",
returnToken: returnToken,
};
return res.status(400).send(return_body); |
| 실패
→토큰 오류 | 401 - 99 | console.log("ERROR : the token value is null or invalid", error);
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
		const response = await axios.post(
			"https://1vnpt0v3p1.execute-api.ap-northeast-2.amazonaws.com/default/post_user_email",
			{
				title: "I have many problem!!!",
				content:
					"Dear AWS Team,I hope this message finds you well. My name is [Your Name], and I represent [Your Company/Organization]. We are currently exploring cloud solutions to enhance our operations and improve scalability.We have heard great things about Amazon Web Services (AWS) and are keen to learn more about the range of services and solutions you offer. Specifically, we are interested in understanding how AWS can help us with [mention your specific requirements, such as data storage, computing power, machine learning, security, etc.].Could you kindly provide us with more information about the AWS services that align with our needs? Additionally, we would appreciate details on pricing, support options, and any success stories from similar companies that have benefited from AWS.Thank you in advance for your time and assistance. We are looking forward to hearing from you soon.Best regards,",
			},
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkwNDQzNTAxLCJleHAiOjE2OTA0NDQ0MDEsImlzcyI6IkxpRm9saSJ9.X09845lp7oKh9b61N6eAFJXaNjp-4qZLx_9Ybw1cRDc,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkwNDQzNTAxLCJleHAiOjE2OTMwMzU1MDEsImlzcyI6IkxpRm9saSJ9.EMBAjUGMp0GIqJ2P90Gy5bRg_X5yv4TbyQRvOeGapzs",
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
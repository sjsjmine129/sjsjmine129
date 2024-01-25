# [tikkle] put_user_address (2023.8.17)

기능 : 

유저 테이블에 주소 저장

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
detail_code: "00",
message: "success to update address",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
| 실패 
→ 인풋 데이터 오류 | 400 - 00 | console.log("put_user_addressd의 입력 데이터에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00",
message: "address value is null or invalid",
returnToken: null,
};
return res.status(400).send(return_body); |
|  |  |  |
| 실패
→쿼리  오류 | 500 - 00 | console.log("put_user_address의 query에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |
|  |  |  |

TEST

성공

```jsx
const axios = require("axios");
axios.defaults.headers.common["User-Agent"] =
	"Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)";

async function fetchData() {
	try {
		const response = await axios.put(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/put_user_address",
			{
				zonecode: "16881",
				address: "경기 용인시 수지구 실험로 111",
				detail_address: "반포자이아파트 111동 6301호",
			},
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
# [tikkle] post_user_friend (2023.7.28)

기능 : 토큰 분해해서 본인 id, 친구 아이디는 바디에서 받음

관계를 검색해서 본인과 상대방의 관계 데이터 존재하는지 &

만약 나-친구, 친구-나 관계가 이미 존재한다면 그 데이터는 추가 x

만약 관계가 없으면 추가x

나-친구 관계가 이미 있으면 “already friend” 리턴

나-친구 관계가 없어서 추가 했으면 “success" 리턴

친구-나 의 관계는 추가 됬든 안됬든 성공 여부와는 상관 x

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
이미 관계가 존재 | 200 - 10 | const return_body = {
success: true,
detail_code: "10",
message: "already friend",
returnToken: returnToken,
};
return res.status(200).send(return_body);
		}),
	}; |
| 성공
친구로 만듬 | 200 - 11 | const return_body = {
success: true,
detail_code: "11",
message: "success post user friend",
returnToken: returnToken,
};
return res.status(200).send(return_body);}; |
|  |  |  |
| 실패
스스로를 친구 추가 불가 | 400 - 00 | console.log("post_user_friend 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "00”,
message: "You cannot be friend yourself",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패
→DB  쿼리 데이터 추가 오류 | 500 - 00 | console.log(" post_user_friend 에서 에러가 발생했습니다.", err);
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
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_user_friend ",
			{
				friendId: 21,
			},
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o",
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
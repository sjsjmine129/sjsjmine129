# [tikkle] delete_user_wishlist (2023.7.31)

기능 : 토큰으로 유저 아이디 가져오고 제품 아이디도 가져온다

          위시리스트를 검색해서 삭제한다

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
success: true,
data: retData,
detail_code: "00",
message: "success delete user wishlist",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→DB  쿼리 오류 | 500 - 00 | console.log("delete_user_whishlist에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "Database post error",
returnToken: null,
};
return res.status(500).send(return_body); |
|  |  |  |

TEST

한번 삭제 한놈이라 안될 수도

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.delete(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/delete_user_wishlist",
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjE2OTMzNjI5OTAsImlzcyI6IkxpRm9saSJ9.2q1rnumRYD5G6ZajAdHkU3HibgTRDbzhgGNFoPAw2qY,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjQyODUzNjIwOTAsImlzcyI6IkxpRm9saSJ9.3lO5YCgVXXzrz5LrodPQoccq11ZHvHdwKAflg22RXXc”,
				},
				data: { productid: 4 },
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
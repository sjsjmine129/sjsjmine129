# [tikkle] post_user_wishlist (2023.7.31)

기능 :  토큰으로 id 확인 & 상품 아이디를 받아서 

     상품데이터 가져와서 삭제여부, 재고 여부 확인 하고 문제 없으면 위시리스에 데이터에 추가 

상품에 위시리스트등록 수 증가

## Output

|  | statusCode - detail-code | return |
| --- | --- | --- |
| 성공
 | 200 - 00 | const return_body = {
		success: true,
		data: retData,
		detail_code: “00”,
		message: "success post user wishlist",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
| 실패
삭제된 상품이거나 이미 위시리스트에 있는 경우 | 500 - 02 | console.log(" post_user_wishlist 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "02",
message: "deleted product or already exist in wishlist",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→DB  오류,  위시리스트 등록시 | 500 - 01 | console.log("post_user_wishlist 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "01",
message: "SQL error : while insert into user_wish_list",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
DB 오류, 상품에 위시리스트 등록 수 늘리기 시 | 500 - 03 | console.log("post_user_wishlist 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "03",
message: "SQL error: while update wishlist_count",
returnToken: null,
};
return res.status(500).send(return_body); |

TEST

성공 → 이미 데이터 있어서 중복됨

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_user_wishlist",
			{
				productId: 6,
			},
			{
				headers: {
					authorization:
						"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjE2OTMzNjI5OTAsImlzcyI6IkxpRm9saSJ9.2q1rnumRYD5G6ZajAdHkU3HibgTRDbzhgGNFoPAw2qY,eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiaWF0IjoxNjkzMzYyMDkwLCJleHAiOjQyODUzNjIwOTAsImlzcyI6IkxpRm9saSJ9.3lO5YCgVXXzrz5LrodPQoccq11ZHvHdwKAflg22RXXc”,
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

삭제된 상품

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_user_wishlist",
			{
				productId: 5,
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
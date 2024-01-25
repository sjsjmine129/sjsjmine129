# [tikkle] post_product_info (2023.7.31)

기능 : 위시리스트나 바로 상품으로 넘어가는 경우 사용

          상품데이터를 1개 가져옴

          데이터 없거나 하면 오류

## Output

|  | statusCode - detail_code | return |
| --- | --- | --- |
| 성공
 | 200 - 00 | const return_body = {
success: true,
data: retData,
detail_code: "00",
message: "success get product info",
returnToken: returnToken,
};
return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
|  |  |  |
| 실패
→DB  오류 | 500 - 00 | console.log(" post_product_info 에서 에러가 발생했습니다.");
		const return_body = {
			success: false,
			detail_code:"00",
			message: "SQL error",
			returnToken: null,
		};
		return res.status(500).send(return_body); |

TEST

성공

```jsx
const axios = require("axios");
axios.defaults.headers.common['User-Agent'] = 'Tickle/1.0.0 (ReactNative; HwAzefScFOQ0kSJ)';

async function fetchData() {
	try {
		const response = await axios.post(
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_product_info",
			{
				productId: 5,
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
# [tikkle] post_payment_getApiToken (2023.10.10)

기능 : API용 토큰 발급

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
		success: true,
		data: response.access_token,
		detail_code: "00",
		message: "success get token info",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→ 토큰 받아오기 오류 | 500 - 00 | console.log("get_payment_apiToken 에서 에러가 발생했습니다.");
		const return_body = {
			success: false,
			detail_code: "00",
			message: "import token get error",
			returnToken: null,
		};
		return res.status(500).send(return_body); |
|  |  |  |
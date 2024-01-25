# [tikkle] post_payment_getData (2023.10.10)

기능 :  결제 아이디로 결제 정보 불러오기

input : 

```
"body": {
		"merchant_uid": "mid_1696556775916"
	}
```

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00 | const return_body = {
		success: true,
		data: result,
		detail_code: "00",
		message: "success get product info",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
|  |  |  |
| 실패
→ 토큰 받아오기 시 메인에서 알수 없는 오류 | 500 - 00 | console.error(`🚨error -> ⚡️ post_payment_getData : 🐞${err}`);
return res.status(500).send(createResponseBody(false, "00", "서버 에러")); |
| 실패
→ 토큰 받아오기 객체에서 오류 | 500-00 | console.error(`🚨error -> ⚡️ post_payment_getData : 🐞${err}`);
console.error(
🚨error -> ⚡️ getPaymentApiToken : 🐞import token get error
);
throw new ExpectedError({
status: "500",
message: 서버에러,
detail_code: "00",
});
return res.status(500).send(createResponseBody(false, "00", "서버 에러")); |
| 실패
→ 포트원 axios에러 | 500-01 | console.error("Error:", error);
		return res.status(500).send(createResponseBody(false, "01", "서버 에러")); |
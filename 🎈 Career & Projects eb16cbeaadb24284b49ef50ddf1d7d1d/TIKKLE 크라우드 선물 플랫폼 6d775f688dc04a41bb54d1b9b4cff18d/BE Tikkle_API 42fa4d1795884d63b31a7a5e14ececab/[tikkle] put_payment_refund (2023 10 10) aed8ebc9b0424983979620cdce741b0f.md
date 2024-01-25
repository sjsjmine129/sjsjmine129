# [tikkle] put_payment_refund (2023.10.10)

기능 :  구매한 티클 환불

*//payment를 생성*

*//payment 객체 생성*

*//DB상의 결제정보와 비교*

*//완료된 결제인지 확인*

*//아직 사용하지 않은 티클인지 확인*

*//포트원 토큰 가져오기*

*//아이엠 포트 결제 취소*

*//결제 환불 처리 in Tikkle DB (sendingTikkle state = 3, payment state = PAYMENT_CANCELLED)*

input : 

```
"body": {
		"merchant_uid": "mid_1696556775916",
			"reason" : "단순 변심"
	}
```

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00 | return res
			.status(200)
			.send(
				Response.create(true, "00", "결제 환불 처리 완료", null, returnToken)
			); |
|  |  |  |
|  |  |  |
| 실패
→ 메인에서의 오류 | 500 - 00 | console.error(`🚨 error -> ⚡️ put_payment_refund : 🐞 ${err}`);
return res.status(500).send(Response.create(false, "00", "서버 에러")); |
| 실패
→ 각 객체내 method 에서의 오류 | 500-00 | console.error(`🚨 error -> ⚡️ put_payment_refund : 🐞 ${err}`);
		if (err.status) {
			return res
				.status(err.status)
				.send(Response.create(false, err.detail_code, err.message));
		}
		return res.status(500).send(Response.create(false, "00", "서버 에러")); |
| 실패
→ 우리 db에는 환불이 반영되었는데 결제사에서 에러가 난 경우
우리가 직접 조치를 취해줘야 하는 상황 | 500-07 |  |
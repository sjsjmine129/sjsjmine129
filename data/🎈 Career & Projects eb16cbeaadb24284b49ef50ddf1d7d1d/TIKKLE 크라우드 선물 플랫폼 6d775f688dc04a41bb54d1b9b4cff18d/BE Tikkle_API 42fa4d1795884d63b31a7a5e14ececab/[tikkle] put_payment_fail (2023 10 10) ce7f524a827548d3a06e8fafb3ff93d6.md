# [tikkle] put_payment_fail (2023.10.10)

기능 :  구매시도 중도 정지 or 실패시 데이터 변경

input : 

```
"body": {
		"merchant_uid": " ㄴㅇㄹㄴㅇㄹㄴㅇㄹㄴㅇ "
	}
```

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00 | return res.status(200).send(Response.create(true, "00", "결제 실패 처리 완료", null, returnToken)); |
|  |  |  |
| 실패
→ 티클 존재 x | 403-00 | throw new ExpectedError({
status: "403",
message: 비정상적 접근 : 존재하지 않는 티클,
detail_code: "00",
}); |
| 실패 남 티클링
→다른사용자의 결제정보 | 401-00 | throw new ExpectedError({
status: "401",
message: 비정상적 접근 : 다른 사용자의 결제 정보,
detail_code: "00",
}); |
|  |  |  |
| 실패
→ 서버오류 | 500-00 | return res.status(500).send(Response.create(false, "00", "서버 에러")); |
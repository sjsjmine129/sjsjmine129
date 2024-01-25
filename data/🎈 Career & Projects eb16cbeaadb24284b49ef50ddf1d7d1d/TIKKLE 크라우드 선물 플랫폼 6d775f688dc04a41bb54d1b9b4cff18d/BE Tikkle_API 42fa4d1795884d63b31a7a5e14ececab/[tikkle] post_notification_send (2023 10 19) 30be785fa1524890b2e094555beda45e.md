# [tikkle] post_notification_send (2023.10.19)

기능 : 알림 정보 받아서 데이터베이스에 저장 

        인풋 데이터 확인

        데이터베이스에서 알림 받는 사람 데이터 확인

        알림 종류에 따라 메세지, url들 생성

        데이터베이스에 저장

          & SNS로 전송

receive_user_id는 “id”column으로 전달됨

source_user_id는 “source_user_id”column으로 전달됨

| 내용 | 문구 | 비고 | 딥링크 형태 | 푸시알림 여부 | 테스트 |
| --- | --- | --- | --- | --- | --- |
| 1. 새로운 친구 | 000님이 가입했어요.  | 친구 페이지로 라우트 | null | x | x |
| 2. 친구의 생일 | 000님의 생일을 축하해주세요. | 홈으로 라우트 | null | o |  |
| 3. 티클링 시작 | 000님의 티클링이 시작되었어요. | deeplink
없으면 홈 | 티클링 상세 | o | o |
| 4. 다가오는 나의 생일 | 생일이 5일 남았네요. 티클링을 시작해보세요. | 상점으로 라우트 | null | o |  |
| 5. 티클 도착 | 000님이 보낸 티클을 확인해보세요.  | 홈 라우트 | 티클링 상세 | o | x |
| 6 티클링 완료 | 티끌링이 완료되어 배송이 시작되었어요. | 홈 라우트 | //main | o | o → 수집시 오는게 아니라 배송신청시 감 |
| 7. 티클링 종료 |  | 홈라우트 | 없음 | o |  |
| 8. 받은 티클 환불 | 000님이 티클을 환불했어요. | deeplink
없으면 profile | 티클링 상세 | o | o |
| 9. 결제 취소(실패)
이 람다에서 사용 x |  |  |  |  |  |

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200 - 00  | const return_body = {
		success: true,
		detail_code:"00",
		message: "send notification success!",
		returnToken: returnToken,
	};
	return res.status(200).send(return_body); |
|  |  |  |
| 실패 
→ 인풋데이터 오류 | 400 - 00 | console.log("post_notification_send 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "00",
message: "inputId userId is null or invalid",
returnToken: null,
};
return res.status(400).send(return_body); |
| 실패
→DB 회원정보 확인  오류 | 500 - 02 | console.log("post_notification_send 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "02",
message: "SQL error",
returnToken: null,
};
return res.status(500).send(return_body); |
| 실패
→DB 알림 정보 저장  오류 | 500 - 03 | console.log("post_notification_send 에서 에러가 발생했습니다.", err);
const return_body = {
success: false,
detail_code: "03",
message: "Database post error",
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
			"https://frrk5g3voe.execute-api.ap-northeast-2.amazonaws.com/dev/post_notification_send",
			{
				receive_user_id: 2,
				notification_type_id: 1,
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
# post_tikkling_sendtikkle

기능: 다른 유저에게 티클을 보냅니다.

## Input

{ "headers": { 

"Authorization": { 

"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME", "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o" } },  

"body": {
    "tikkling_id": 5,
    "tikkle_quantity": 30,
    "message": "선물이지롱"
  }

"queryStrignParameters": {} 

}

## Output

|  | statusCode | body |
| --- | --- | --- |
| 성공
→자신에게 보낸경우 티켓을 지급받지 못함 | 200-01 | {
const return_body = {
success: true,
detail_code: “01”,
message: 티클을 성공적으로 보냈습니다. 자신의 티클 보내기에서는 티켓을 받을 수 없습니다.
returnToken,
}
 |
| 성공
→이미 티켓을 지급받은경우 | 200-02 | {
const return_body = {
success: true,
detail_code: “02”,
message: 티클을 성공적으로 보냈습니다. 이미 티켓을 지급 받았습니다.
returnToken,
}
 |
| 성공
→ 정상적으로 티켓을 지급 | 200-03 | {
const return_body = {
success: true,
detail_code: “03”,
message: 티클을 성공적으로 보냈습니다. 티클링 티켓 1개를 획득하였습니다.
returnToken,
}
 |
| 실패
→ 비정상적인 요청, 존재하는 티클링이 없습니다. | 404-00 | {
const return_body = {
success: false,
detail_code: “00”,
message: "잘못된 요청, 티클링을 찾을 수 없습니다.",
returnToken: null,
} |
| 실패
→종료된 티클링에 티클을 전송 | 403-01 | {
const return_body = {
success: false,
detail_code: “01”,
message:
"티클을 보낼 수 없습니다. (티클을 줄 수 있는 상태가 아닙니다.)",
returnToken,
} |
| 실패
→티클수가 초과됨 | 403-02 | {
success: false,
detail_code: “02”,
message: "티클을 보낼 수 없습니다. (줄 수 있는 티클링 조각 수 초과)",
returnToken,
} |
| 실패
→티클수가 초과됨(유저가 보내는 사이에 다른 유저가 보낸 상황) | 403-03 | {
success: false,
detail_code: “03”
message: "티클전송중 타인이 먼저 티클전송을 하였습니다. 티클을 보낼 수 없습니다. (줄 수 있는 티클링 조각 수 초과 or 티클을 줄 수 있는 상태가 아닙니다.)",
returnToken,
} |
| 실패
→실제 가격에 맞는 티클 수가 아님 |  |  |
| 실패
→ 티클링의 기간이 일정 기간을 초과 |  |  |
| 실패 
→ 토큰 없음
    토큰 오류
    리프레시 토큰 오류 | 401-99 | console.log("authtoken 에서 에러가 발생했습니다.");
const return_body = {
success: false,
detail_code: "99",
message: "login again",
};
return res.status(401).send(return_body); |
| 실패
→서버 에러 | 500-00 | {
success: false,
detail_code: "00",
message: "서버 에러",
returnToken: null,
} |
# put_tikkling_cancel

기능: 티클을 하나도 받지 않은 티클링을 종료

## Input

{ "headers": { 

"Authorization": { 

"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME", "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o" } }, "body": {

tikkling_id: 3

}, 

"queryStrignParameters": {} 

}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
 | 200-00 | {
success: true,
detail_code: "00",
message: “티클링을 성공적으로 취소하였습니다.”,
returnToken,
} |
| 실패
→이미 종료된 티클링에 해당 api를 시도 | 400-00 | success: false,
detail_code: “00”,
message: "이미 종료된 티클링입니다.",
returnToken,
} |
| 실패
→이미 티클을 받을 상태 | 401-00 | {
success: false,
detail_code: “00”,
message: "비정상적 요청, 티클이 도착한 상태에서는 티클링을 취소할 수 없습니다.,
returnToken,
} |
| 실패
→ 존재하지 않는 티클링 id에 해당 api를 요청 | 404-00 | {
success: false,
detail_code: “00”,
message: "비정상적 요청, 티클링을 찾을 수 없습니다.",
returnToken: null
} |
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
} |
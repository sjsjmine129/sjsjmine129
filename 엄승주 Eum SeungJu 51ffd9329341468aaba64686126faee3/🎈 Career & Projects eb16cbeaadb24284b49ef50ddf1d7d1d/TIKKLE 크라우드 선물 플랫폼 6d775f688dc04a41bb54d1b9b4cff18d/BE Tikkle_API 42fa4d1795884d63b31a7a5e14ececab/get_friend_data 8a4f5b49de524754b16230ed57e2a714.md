# get_friend_data

기능 : 이 함수는 사용자의 차단된 친구 목록 또는 차단되지 않은 친구 목록을 데이터베이스에서 조회하는 역할을 합니다.

url /get_friend_data/block

## Input

mode: block ⇒ 차단된친구

mode: unblock ⇒ 차단되어있지 않은 친구

{
"headers": {
"Authorization": {
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME",
"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o"
}
},
"body": {},
"queryStrignParameters": {
"mode": "block"
}
}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200-01 | {
success:true,
detail_code: “01”,
message: "차단된 친구 목록 조회 성공”
data:[
{
name:John,
image:john.jpg,
nick:johnny},
],
returnToken:exampleNewAccessToken}"
} |
| 성공 | 200-02 | {
success:true,
detail_code: “02”,
message: "차단되지 않은 친구 목록 조회 성공”
data:[
{
name:John,
image:john.jpg,
nick:johnny
},
],
returnToken
} |
| 실패
→파라미터 입력오류 | 400-00 | {
success: false,
detail_code: "00",
message:
"비정상적 요청, 잘못된 유효하지 않은 mode를 parameter로 전송했습니다.",
returnToken: null,
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
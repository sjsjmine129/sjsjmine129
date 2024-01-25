# get_friend_search

## Input

{
"headers": {
"Authorization": {
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME",
"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o"
}
},
"body": {},
"queryStrignParameters": {
"nick": "sup1214"
}
}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공 | 200-00 | 
{
success: true,
data: :[{\"id\":1,\"name\":\"김영희\",\"nick\":\"younghee95\",\"image\":null,\"relation_state_id\":null}],,
detail_code: "00",
message: "성공적으로 친구를 찾았습니다.",
returnToken,
}
relation_state_id 가 null이면 친구 관계 x, 1→ 친구, 2→ 친구신규, 3→ 친구 차단 |
| 실패 
→ 아무것도 입력하지 않음 | 400-01 | {
success: false,
detail_code: "01",
message: "비정상적 요청, nick은 빈 문자열이면 안 됩니다.",
}
 |
| 실패 
→ 문자열을 입력하지 않음 | 400-02 | {
success: false,
detail_code: "02",
message: "비정상적 요청, nick은 문자열이어야 합니다.",
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
|  |  |  |
# post_friend_phoneCheck

기능 : 자신의 전화번호 부에 있는 친구중 서비스의 회원으로 등록되어 있는 이용자를 불러옴

## Input

{
"headers": {
"Authorization": {
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME",
"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o"
}
},
"body": {
"phone_list": [
"01012345678",
"01053783514"
]
}
}

## Output

|  | statusCode | return body |
| --- | --- | --- |
| 성공 | 200-00 | 
{
success: true,
data: [{phone:01012345678,user_id:3},{phone:01053783514,user_id:2}],
detail_code: "00",
message: "전화번호 조회 성공",
returnToken,
} |
| 실패
→ 문자열로 된 리스트가 아닙니다. | 400-01 | {
success: false,
detail_code: "01",
message: "비정상적 요청, phone_list는 문자열의 배열이어야 합니다.",
returnToken: null,
} |
| 실패
→ 빈리스트일때 | 400-02 | {
success: false,
detail_code: "02",
message: "비정상적 요청, phone_list는 빈 배열이면 안 됩니다.",
returnToken,
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
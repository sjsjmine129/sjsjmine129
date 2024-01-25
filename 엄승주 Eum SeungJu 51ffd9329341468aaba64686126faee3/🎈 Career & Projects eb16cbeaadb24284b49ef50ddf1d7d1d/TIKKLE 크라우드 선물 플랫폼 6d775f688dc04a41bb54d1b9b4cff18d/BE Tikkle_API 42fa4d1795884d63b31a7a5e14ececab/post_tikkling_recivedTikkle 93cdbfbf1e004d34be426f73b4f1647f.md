# post_tikkling_recivedTikkle

기능: 받은 티클내역 확인하기

## Input

{ "headers": { 

"Authorization": { 

"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME", "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o" } }, "body": {

tikkling_id: 3: 

}, 

"queryStrignParameters": {} 

}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
 | 200-00 | {
success:true,
detail_code: “00”
data:[{
id:4,
tikkling_id:5,
user_id:4,
created_at:2023-08-09T11:06:22.000Z,
message:메롱 안축하,
quantity:2,
name:최준호,
image:null
},
{id:3,tikkling_id:5,user_id:3,created_at:2023-08-09T11:06:22.000Z,message:메메롱 추축하,quantity:3,name:박지민,image:null}
],
message: ”특정 티클링의 받은 티클 정보 조회 성공”,
returnToken:eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MywiaWF0IjoxNjkxNTQ2ODEzLCJleHAiOjE2OTE1NDc3MTMsImlzcyI6IkxpRm9saSJ9.ShfrjHmgA9equOLFw_eIVRYIwKqoyspi_Au5_UBXYjg
} |
| 실패
→ 숫자외 다른 것을 입력했거나 입력하지 않음 | 400-00 | {
success: false,
detail_code: "00",
message: "잘못된 요청, tikkling_id는 숫자여야 합니다.",
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
returnToken: null,
message: "서버 에러",
} |
# get_tikkling_friendInfo

기능 : 친구의 진행중인 티클링 정보 get

## Input

{
"headers": {
"Authorization": {
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTA1MjE2NDYsImlzcyI6IkxpRm9saSJ9.w-4NVe-YbhdeXUPKmiZpOZMi8it_FmwNp3jrbIYh4ME",
"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NSwiaWF0IjoxNjkwNTIwNzQ2LCJleHAiOjE2OTMxMTI3NDYsImlzcyI6IkxpRm9saSJ9.Cl7fT5xT3VxAwpL7QbL8k7z9vaFkaWXr6iDlgReYo0o"
}
},
"body": {},
"queryStrignParameters": {}
}

## Output

|  | statusCode | return |
| --- | --- | --- |
| 성공
 | 200 | {success:true,
detail_code: “00”,
data:[{
id:5,
user_id:3,
funding_limit:2023-08-30T00:00:00.000Z,
created_at:2023-08-08T18:41:53.000Z,
tikkle_quantity:100,
product_id:5,
terminated_at:null,
state_id:1,
tikkle_count:5,
name:상품B,
thumbnail_image:상품B_이미지_URL,
brand_name:브랜드B,
user_name:박지민,
birthday:1990-12-01T00:00:00.000Z,
nick:jimin90,
phone:01034567890,
gender:female,
friend_image:null,
address:인천광역시 중구,
detail_address:인하동 101-11,
is_tikkling:0,
device_token:device_token_3}],
message:친구의 티클링 정보 조회 성공,
returnToken
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